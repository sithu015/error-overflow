# Log File of Evaluation on GPT-2 Model Generated Myanmar Hatespeech Sentences with PPL

Hatespeech စာကြောင်း တစ်သောင်းခန့် နဲ့ ဆောက်ထားတဲ့ GPT-2 model ကို သုံးပြီး မြန်မာစာ hatespeech စာကြောင်းတွေကို generate လုပ်ကြည့်ခဲ့ပါတယ်။ အဲဒီ testset ၅စုံကို Language Model တစ်ခု ဆောက်ပြီး PPL တိုင်းကြည့်တဲ့ log ဖိုင် ပါ။  

## Corpus Information

syllable segmentation လုပ်ထားတဲ့ LU Lab. in-house corpus ရဲ့ information က အောက်ပါအတိုင်းပါ။  

```
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc$ ls
segmentation-data-updated2.cleaned.syl
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc$ head -n 3 ./segmentation-data-updated2.cleaned.syl
လု သာ မောင်း ပြိုင် သာ ပြိုင် ကို ယ့် ကိုယ် ပိုင် ကား မ ဟုတ် ပြ ဿ နာ ဖြစ် ရင် ထွက် ပြေး အေး အေး ဆေး ဆေး ဖြစ် သွား ရင် ပြန် မောင်း လု သာ မောင်း
သမ္မ တ ဦး ထင် ကျော်
အင်း လေး သူ ဆို လည်း ကောင်း တာ ပဲ ကစ် ကစ် က ဖြူ ဖြူ ဖွေး ဖွေး လေး ဆို တော့ ရှမ်း မ လေး တွေ တော့ ထိုင် ငို နေ တော့ မှာ ပဲ အင်း လေး ကို အ ရမ်း ချစ် တယ် အင်း လေး နဲ့ ကစ် နဲ့ လိုက် ပါ တယ် တ သက် လုံး တ ကယ် လာ နေ ရင် အ ရမ်း ကောင်း မှာ ပဲ ချစ် တယ် မ ကစ် ဇင် ဇင် တို့ မွန် ပြည် နယ် လာ လည် ပါ လား ဖိတ် ခေါ် ပါ တယ် ကျိုက် ထီး ရိုး ဘု ရား ဖူး ရင် မော် လ မြိုင် မြို့ ကို လာ လည် ပါ ရှမ်း က မဲ တာ လား အင်း သူ မ က မဲ တာ လား မူ ကြို က လေး မေး တောင် သိ တယ် အင်း သူ မ က ဘယ် လောက် ပဲ ပိုက် ဆံ ရှိ ပါ စေ အ လောင်း စည် သူ မင်း ကျိန် စာ တိုက် ခဲ့ လို့ ရေ ခြံ ရော ကုန်း ခြံ ရော ကုန်း နေ အောင် လုပ် ရ တာ ဖြူ နေ ဦး မယ် အ သား က ကြ ည့် ပြော အင်း သူ မ လုပ် ရင် ရေ ကူး တတ် ရ မယ် နော် ရေ မ ကူး တတ် ရင် အ လောင်း တွေ ခု ချိန် ထိ ဆယ် မ ကုန် သေး ဘူး အ သဲ မ မ ကစ် ချစ် လိုက် တာ ကောင်း တယ် လုပ် ပစ် လိုက် အ မ ကစ် သာ နေ ရင် ရှမ်း ပြည် အ ပြီး ပြန် လာ မယ် နေ နိုင် လား ဘ ဝ ကို ဖြတ် သန်း တဲ့ အ ခါ အ ရိုး ဆုံး က အ ကောင်း ဆုံး ပါ ပဲ မ လုပ် ပါ နဲ့ ကစ် လေး ရယ် ရန် ကုန် ကို အ မြန် ပြန် လာ ပါ ကိုယ် အ ရမ်း သ တိ ရ လို့ ပါ ကွာ ချစ် တာ ချစ် စ ရာ လေး အ ရမ်း ကြိုက် မ မ နေ ပါ ကစ် လေး ရယ် သာ ယာ လိုက် တာ အဲ့ နား မှာ အိမ် တစ် လုံး သွား ဝယ် လိုက် မှာ ပေါ့
```

filesize information:  

```
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc$ wc ./segmentation-data-updated2.cleaned.syl
  212836  7094461 69535996 ./segmentation-data-updated2.cleaned.syl
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc$
```

## Hatespeech Corpus Information

I also need to add Hatespeech data ...  
မဟာတန်းကျောင်းသူ နန်းဣန္ဒြေကျော် စုပေးထားတဲ့ hatespeech corpus ကိုလည်း corpus မှာ ပေါင်းထည့်မှ အဆင်ပြေမှာမို့ အဲဒီ corpus ကိုလည်း အထက်က corpus နဲ့ ပေါင်းဖို့ပြင်ဆင်ခဲ့တယ်။  

```
(base) ye@lst-gpu-3090:~/exp/myHatespeech/nanoGPT/myHatespeech_char$ head hs_data_4Oct2023.clean.txt
ဖော်လော်မော် မ ဟုတ် လို့ ပေါ့ 🤣 🤣
နား ကို မ လည် တာ
ဆောက်မြင်ကပ် ထင် တာ ပဲ
ကွမ်းယာ မှာ ထည့် စား တဲ့ စမုန်စပါး ထင် တယ်
ဖလော်မော် next version
ငါ လည်း သိ ချင် နေ တာ 😁 အဲ့လို စကား တွေ ကျ နားမလည် လို့ သင် ပေး ကြ ပါ ဦး 😂
ငါ မ သိ လို့ ကိုကို့ ကို မေး ကြည့် တာ ကိုကို က လည်း baby က လွဲ ရင် မ သိ ဘူး တဲ့ 🥺
ဖော်လော်မော် နဲ့ ညီမ တော် တယ် လေ 😬
sမွေး ကြီး တဲ့ 😂
$မွှေး ပါ
```

tail command output က အောက်ပါအတိုင်း။  
မြင်ရတဲ့အတိုင်း ဒီ corpus ကလည်း word segmentation လုပ်မထားပါဘူး။  

```
(base) ye@lst-gpu-3090:~/exp/myHatespeech/nanoGPT/myHatespeech_char$ tail hs_data_4Oct2023.clean.txt
သူ့ ကို ဘာ ကြည့် ပြီး vote ပေး ကြ တာ ပါ လိမ့် $ရူးမ ဘာ မ ဟုတ် တဲ့ ကိစ္စ ကြောင့် ရွှေကြို အခွင့်အရေး ကို ဆုံးရှုံး မ ခံ နိုင် လို့ ဆို ပြီး ပြော တဲ့ $ရူးမ
ဖင်အရှည်ကြီးခံလိုက် တစ်ခါတည်း အကုန် ကြို ပြီး သား ပဲ 🦭
အိပ်မက် က အမ တစ် ယောက် ပဲ ရှိ တာ လား 🥲
SattPatt !! ဘာ မ ဟုတ် တဲ့ ပြဿနာ တဲ့ PayloeeeMaaaGGG
စောက်ဆင့်မရှိ တဲ့ ဟာ တွေ က လည်း အခုတလော ခပ်စိပ်စိပ် တွေ့ လာ ရ တယ် 🤣🤣🤣🤣🤣 ရေး ချင် လွန်း လို့ မ ဟုတ် ဘူး နော် ရှက် တတ် ဦး မ လား လို့ ဝင့် မန့် တာ
ဘာ မ ဟုတ် တာ လေး တဲ့ အာ့ ဆို ဟုတ် တဲ့ ဟာ ဘောပဲမနေ နော် အမကြီး
ထမင်းစားတိုင်းလူမဖြစ်နိုင်ဘူး ဆို တာ ခု မှ အရှင်လတ်လတ် မြင် ဖူး တော့ တယ် ကောင်မ မွေးကတည်းကအသေလေးမွေးလာရမှာ
အော် ဘာ မ ဟုတ် တာ တဲ့ လား ပြောထွက်တဲ့ပါးစပ်လေးကိုအက်ဆစ်လေးနဲ့သွားဆေးစေချင်
ဗန်းကိုင် နဲ့ မအလ ဘောကိုင်
စိတ်မပူ နဲ့ ရွှေကြို ပြီး ရင် ဖင်ခံ ရ မှာ ညီမလေး fighting 22 နှစ် က ငါ 25 နှစ် ထက် အို နေ တော့ အား တောင် နာ တယ် 😂 😂
(base) ye@lst-gpu-3090:~/exp/myHatespeech/nanoGPT/myHatespeech_char$
```

Copied above file to the LM building folder.  
အထက်ပါ corpus ဖိုင် နှစ်ဖိုင်ကို ppl တွက်မယ့် ဖိုလ်ဒါဆီကို ကော်ပီကူးယူခဲ့တယ်။  

```
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc$ cp /home/ye/exp/myHatespeech/nanoGPT/myHatespeech_char/hs_data_4Oct2023.clean.txt .
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc$ wc ./hs_data_4Oct2023.clean.txt
  10140  171358 2172104 ./hs_data_4Oct2023.clean.txt
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc$
```

## Syllable Breaking for Hatespeech Data

ထုံးစံအတိုင်းပဲ မြန်မာစာရဲ့ word segmentation မှာက 100% မှန်တာ မရှိလို့ syllable နဲ့ပဲဖြတ်ပြီး language model ဆောက်မယ်လို့ ဆုံးဖြတ်ခဲ့တယ်။  
Downloading sylbreak.pl to the server machine:   

```
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc$ wget https://raw.githubusercontent.com/ye-kyaw-thu/sylbreak/master/perl/sylbreak.pl
--2023-10-23 16:03:43--  https://raw.githubusercontent.com/ye-kyaw-thu/sylbreak/master/perl/sylbreak.pl
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 185.199.110.133, 185.199.109.133, 185.199.108.133, ...
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|185.199.110.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2356 (2.3K) [text/plain]
Saving to: ‘sylbreak.pl’

sylbreak.pl            100%[==========================>]   2.30K  --.-KB/s    in 0s

2023-10-23 16:03:43 (33.2 MB/s) - ‘sylbreak.pl’ saved [2356/2356]

(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc$
```

hatespeech data က syllable segmentation မလုပ်ရသေးတာမို့ sylbreak perl ဖိုင်ကို သုံးပြီးတော့ syllable breaking လုပ်ခဲ့တယ်။  
Syllable breaking ...   

```
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc$ perl ./sylbreak.pl -i ./hs_data_4Oct2023.clean.txt -s " " > ./hs_data_4Oct2023.clean.txt.syl
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc$
```

make confirmation ...  

```
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc$ head ./hs_data_4Oct2023.clean.txt.syl
ဖော် လော် မော် မ ဟုတ် လို့ ပေါ့ 🤣 🤣
နား ကို မ လည် တာ
ဆောက် မြင် ကပ် ထင် တာ ပဲ
ကွမ်း ယာ မှာ ထ ည့် စား တဲ့ စ မုန် စ ပါး ထင် တယ်
ဖ လော် မော် n e x t v e r s i o n
ငါ လည်း သိ ချင် နေ တာ 😁 အဲ့ လို စ ကား တွေ ကျ နား မ လည် လို့ သင် ပေး ကြ ပါ ဦး 😂
ငါ မ သိ လို့ ကို ကို့ ကို မေး ကြည့် တာ ကို ကို က လည်း b a b y က လွဲ ရင် မ သိ ဘူး တဲ့ 🥺
ဖော် လော် မော် နဲ့ ညီ မ တော် တယ် လေ 😬
s မွေး ကြီး တဲ့ 😂
$ မွှေး ပါ
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc$
```

## Combining Two Datasets

General domain အတွက် ပြင်ထားခဲ့တဲ့ in-house corpus နဲ့ hatespeech corpus နှစ်ခုကို ဖိုင်တစ်ဖိုင်အဖြစ် အောက်ပါအတိုင်း ပေါင်းလိုက်တယ်။  

```
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc$ cat segmentation-data-updated2.cleaned.syl hs_data_4Oct2023.clean.txt.syl > seg_hs_corpus.txt
```

ပေါင်းပြီးသွားတဲ့အခါမှာ filesize information က အောက်ပါအတိုင်းပါ။  

```
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc$ wc seg_hs_corpus.txt
  222976  7335893 71778129 seg_hs_corpus.txt
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc$
```

## KenLM Installation

Statistical language model ကို KenLM နဲ့ပဲ ဆောက်မယ်လို့ ဆုံးဖြတ်ခဲ့။  
Clone KenLM ...  

```
(base) ye@lst-gpu-3090:~/tool$ git clone https://github.com/kpu/kenlm
Cloning into 'kenlm'...
remote: Enumerating objects: 14161, done.
remote: Counting objects: 100% (474/474), done.
remote: Compressing objects: 100% (328/328), done.
remote: Total 14161 (delta 162), reused 406 (delta 132), pack-reused 13687
Receiving objects: 100% (14161/14161), 5.91 MiB | 5.57 MiB/s, done.
Resolving deltas: 100% (8042/8042), done.
(base) ye@lst-gpu-3090:~/tool$
```

Check the folder:   

```
(base) ye@lst-gpu-3090:~/tool$ cd kenlm/
(base) ye@lst-gpu-3090:~/tool/kenlm$ ls
BUILDING             compile_query_only.sh  Doxyfile     pyproject.toml  util
clean_query_only.sh  COPYING                LICENSE      python
cmake                COPYING.3              lm           README.md
CMakeLists.txt       COPYING.LESSER.3       MANIFEST.in  setup.py
(base) ye@lst-gpu-3090:~/tool/kenlm$
```

Installation of KenLM on LST Server machine:  

```
(base) ye@lst-gpu-3090:~/tool/kenlm$ mkdir -p build
(base) ye@lst-gpu-3090:~/tool/kenlm$ cd build
(base) ye@lst-gpu-3090:~/tool/kenlm/build$ cmake ..
CMake Deprecation Warning at CMakeLists.txt:1 (cmake_minimum_required):
  Compatibility with CMake < 3.5 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


-- The C compiler identification is GNU 11.4.0
-- The CXX compiler identification is GNU 11.4.0
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working C compiler: /usr/bin/cc - skipped
-- Detecting C compile features
-- Detecting C compile features - done
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++ - skipped
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Could NOT find Eigen3 (missing: Eigen3_DIR)
-- Found Boost: /usr/lib/x86_64-linux-gnu/cmake/Boost-1.74.0/BoostConfig.cmake (found suitable version "1.74.0", minimum required is "1.41.0") found components: program_options system thread unit_test_framework
-- Found Threads: TRUE
-- Found ZLIB: /usr/lib/x86_64-linux-gnu/libz.so (found version "1.2.11")
-- Found BZip2: /usr/lib/x86_64-linux-gnu/libbz2.so (found version "1.0.8")
-- Looking for BZ2_bzCompressInit
-- Looking for BZ2_bzCompressInit - found
-- Looking for lzma_auto_decoder in /usr/lib/x86_64-linux-gnu/liblzma.so
-- Looking for lzma_auto_decoder in /usr/lib/x86_64-linux-gnu/liblzma.so - found
-- Looking for lzma_easy_encoder in /usr/lib/x86_64-linux-gnu/liblzma.so
-- Looking for lzma_easy_encoder in /usr/lib/x86_64-linux-gnu/liblzma.so - found
-- Looking for lzma_lzma_preset in /usr/lib/x86_64-linux-gnu/liblzma.so
-- Looking for lzma_lzma_preset in /usr/lib/x86_64-linux-gnu/liblzma.so - found
-- Found LibLZMA: /usr/lib/x86_64-linux-gnu/liblzma.so (found version "5.2.5")
-- Looking for clock_gettime in rt
-- Looking for clock_gettime in rt - found
-- Configuring done (1.3s)
-- Generating done (0.0s)
-- Build files have been written to: /home/ye/tool/kenlm/build
(base) ye@lst-gpu-3090:~/tool/kenlm/build$
```

Check number of CPU ...  

```
(base) ye@lst-gpu-3090:~/tool/kenlm/build$ lscpu | grep CPU
CPU op-mode(s):                     32-bit, 64-bit
CPU(s):                             24
On-line CPU(s) list:                0-23
CPU family:                         6
CPU max MHz:                        5100.0000
CPU min MHz:                        800.0000
NUMA node0 CPU(s):                  0-23
(base) ye@lst-gpu-3090:~/tool/kenlm/build$
```

Run make ...  

```
make -j 24
...
...
...
[ 93%] Building CXX object lm/builder/CMakeFiles/lmplz.dir/lmplz_main.cc.o
[ 95%] Building CXX object lm/builder/CMakeFiles/count_ngrams.dir/count_ngrams_main.cc.o
[ 96%] Linking CXX executable ../bin/kenlm_benchmark
[ 96%] Built target kenlm_benchmark
[ 97%] Linking CXX executable ../../bin/filter
[ 97%] Built target filter
[ 98%] Linking CXX executable ../../bin/lmplz
[ 98%] Built target lmplz
[100%] Linking CXX executable ../../bin/count_ngrams
[100%] Built target count_ngrams
(base) ye@lst-gpu-3090:~/tool/kenlm/build$ ls
bin             CMakeFiles           kenlmConfig.cmake  lm        util
CMakeCache.txt  cmake_install.cmake  lib                Makefile
(base) ye@lst-gpu-3090:~/tool/kenlm/build$ cd bin
(base) ye@lst-gpu-3090:~/tool/kenlm/build/bin$ ls
build_binary  filter    kenlm_benchmark  phrase_table_vocab            query
count_ngrams  fragment  lmplz            probing_hash_table_benchmark
(base) ye@lst-gpu-3090:~/tool/kenlm/build/bin$
```

## 5-gram Statistical LM Building

syllable segmented ဒေတာက 5-gram မော်ဒယ်လောက်ဆိုရင် အဆင်ပြေပါတယ်။  

```
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc$ time lmplz -o 5 < ./seg_hs_corpus
.txt > lm.5gram.arpa
=== 1/5 Counting and sorting n-grams ===
Reading /home/ye/exp/myHatespeech/eval/ppl_calc/seg_hs_corpus.txt
----5---10---15---20---25---30---35---40---45---50---55---60---65---70---75---80---85---90---95--100
****************************************************************************************************
Unigram tokens 7335893 types 6390
=== 2/5 Calculating and sorting adjusted counts ===
Chain sizes: 1:76680 2:5248165888 3:9840311296 4:15744497664 5:22960726016
Statistics:
1 6390 D1=0.647156 D2=0.938543 D3+=1.45863
2 371227 D1=0.638693 D2=1.06168 D3+=1.44861
3 1971935 D1=0.768907 D2=1.12922 D3+=1.37264
4 3771093 D1=0.859861 D2=1.2009 D3+=1.40137
5 4835909 D1=0.755941 D2=1.62412 D3+=1.60134
Memory estimate for binary LM:
type     MB
probing 223 assuming -p 1.5
probing 258 assuming -r models -p 1.5
trie     97 without quantization
trie     49 assuming -q 8 -b 8 quantization
trie     86 assuming -a 22 array pointer compression
trie     38 assuming -a 22 -q 8 -b 8 array pointer compression and quantization
=== 3/5 Calculating and sorting initial probabilities ===
Chain sizes: 1:76680 2:5939632 3:39438700 4:90506232 5:135405452
----5---10---15---20---25---30---35---40---45---50---55---60---65---70---75---80---85---90---95--100
------------------------------------------------------------------------------------------++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++******************************************************************************************####################################################################################################
=== 4/5 Calculating and writing order-interpolated probabilities ===
Chain sizes: 1:76680 2:5939632 3:39438700 4:90506232 5:135405452
----5---10---15---20---25---30---35---40---45---50---55---60---65---70---75---80---85---90---95--100
------------------------------------------------------------------------------------------++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++******************************************************************************************####################################################################################################
=== 5/5 Writing ARPA model ===
----5---10---15---20---25---30---35---40---45---50---55---60---65---70---75---80---85---90---95--100
------------------------------------------------------------------------------------------++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++****************************************************************************************************
Name:lmplz      VmPeak:52704960 kB      VmRSS:10980 kB  RSSMax:9423100 kB       user:4.88182      sys:2.9611      CPU:7.84296     real:6.59366

real    0m6.600s
user    0m4.883s
sys     0m2.962s
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc$
```

## Check the Statistical LM

Language model ကို ARPA format နဲ့ပဲ သိမ်းခဲ့တာမို့ ဖိုင်အထဲကို peek လုပ်ကြည့်ရတာ အဆင်ပြေပါတယ်။  

```
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc$ head -n 50 ./lm.5gram.arpa
\data\
ngram 1=6390
ngram 2=371227
ngram 3=1971935
ngram 4=3771093
ngram 5=4835909

\1-grams:
-5.525481       <unk>   0
0       <s>     -1.8698267
-2.220042       </s>    0
-3.1793256      လု      -0.5695411
-2.6307955      သာ      -0.8018073
-3.1199322      မောင်း  -0.6105088
-3.0450509      ပြိုင်  -0.7024183
-2.3082223      ကို     -1.2794439
-4.298998       ယ့်     -0.2666081
-2.7623425      ကိုယ်   -0.8561846
-2.9551132      ပိုင်   -0.65085495
-2.7556262      ကား     -0.7490673
-2.3018465      မ       -1.233987
-2.9216228      ဟုတ်    -0.6538618
-2.7101119      ပြ      -0.9647346
-3.7024763      ဿ       -0.32949388
-2.7523067      နာ      -0.72248787
-2.5004718      ဖြစ်    -1.1543733
-2.6782982      ရင်     -0.8826761
-2.81556        ထွက်    -0.9175844
-3.0502732      ပြေး    -0.7143059
-2.9625616      အေး     -0.7053375
-2.8941834      ဆေး     -0.74615747
-2.5275965      သွား    -1.2112159
-2.6788564      ပြန်    -0.967851
-3.2848742      သမ္မ    -1.4597393
-2.5221121      တ       -0.8386894
-2.6901717      ဦး      -0.88747036
-3.0463505      ထင်     -0.84865737
-2.9657936      ကျော်   -0.66401005
-3.1469703      အင်း    -0.5767914
-2.5045648      လေး     -0.9711726
-2.5794568      သူ      -1.0010203
-2.5094523      ဆို     -0.9702034
-2.5667617      လည်း    -0.9080558
-2.7335382      ကောင်း  -0.87234116
-2.5121071      တာ      -1.030593
-2.5347512      ပဲ      -0.9389109
-3.2565143      ကစ်     -0.62175095
-2.2774615      က       -1.2609818
-3.0944793      ဖြူ     -0.5175369
-3.502761       ဖွေး    -0.5039096
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc$
```

Language model ရဲ့ နောက်ဆုံး အပိုင်းကိုလည်း မျက်လုံးနဲ့ စစ်ကြည့်ပြီး confirmation လုပ်ခဲ့ ...  
တကယ်တမ်း က emoji တွေနဲ့ corpus အထဲမှာ ပါဝင်နေတဲ့ symbol တွေအားလုံးကိုပါ syllable ဖြတ်တဲ့အခါမှာ English စာလိုပဲ တစ်လုံးချင်းစီ ဖြတ်တာမျိုး၊ သို့မဟုတ် emoji တွေကို corpus ထဲကနေ remove လုပ်လိုက်တာမျိုး လုပ်ရင် ပို တိတိကျကျ measure လုပ်လို့ ရပါတယ်။ အချိန်က limit ဖြစ်တာနဲ့ အကြမ်းပဲ PPL တိုင်းကြည့်တာကို လုပ်ကြည့်မယ်။ လက်ရှိ အနေအထားကို ခန့်မှန်းလို့ ရတာမို့ ...  

```
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc$ tail -n 50 ./lm.5gram.arpa
-0.45228076     ရင် ဖင် ပါ လို -း
-1.0722371      နေ့ ရော ည ရော 👂🏻
-0.29612365     <s> ရိုင်း တယ် ​ ဆောက်​
-0.45452684     တ ရာို . . .း
-0.85684836     <s> လူ လိမ် မ ဖေ×ိုး
-0.36948365     ချင် တာ တဲ့ ကက် လန်​
-0.5769707      စား လို့ သာ ပဲ စောက်​
-1.48055        <s> တ ခါ တည်း နြူး
-1.9312932      သူ တွေ ကျ တော့ အ​
-0.29612365     မယ့် က လေး ​ တောင်​
-0.4201431      သူ့ အ ဖိုး လုပ် ရပ်​
-0.45505774     <s> အာ့ မ အေ လိုး​
-0.57081354     လို အ စား ထဲ ပဲ​
-1.1072607      အ ဖေ ကို သ x်
-0.4495237      ကို ရော ငါ သ x်
-0.3659513      သ တင်း လုပ် ​ ပြော​
-0.57687056     ကောက် ကို ဖင် ဝိုင်း Xိုး
-1.3425193      ရ တာ ကံ ကောင်း တ‌ာ
-1.2453475      ဖင် သာ ခံ လိုက် ​ေ
-0.2287815      သာ ခံ လိုက် ​ေ $ာက်
-0.90751475     ရ လာ တယ် ဆို တော့​
-0.57866645     ထင် နေ တဲ့ လ ပျွတ်
-0.5999915      တယ် ခွေး လေး တွေ 😭😭😭
-0.4497082      ယုတ် မာ တွေ နင် တို့​
-3.1098154      လဲ မ သိ ဘူး 🤫🤫🤫
-0.91051775     များ စု စည်း ရာ 🙂🖕
-0.45533326     အေ ဘေး တွေ ရ 😎🖕🖕
-0.45566383     ဂျိုး ရှီး လေး ပါ 😜😜😜😆😆😆
-0.5258407      ရ တာ ကြိုက် တဲ့ 🐮
-1.0829955      နင် လည်း ပါ တယ် 👌
-0.5955442      ယား ပြ ပါ နဲ့ 👌
-0.60018754     လ မ တစ် ကောင် …😡😡😡😡
-0.41162136     မ ယ့် ခေါင်း မျိုး 🤣🤣🤌
-0.8666703      လို့ သ နား မိ 😏🤌
-1.037431       ပြော မိ ပြန် ပြီ 🤭🤣
-1.5954549      ဟုတ် တာ တဲ့ လား 🤑🤑🤑😒😒
-0.5657399      သိုလ် က စ ပြီ 😏😏
-0.43753234     တွေ ချည်း ပဲ ဖြတ် -ိုက်
-0.5231397      လေ ‌ ဖ လ မ🖕🏿
-2.2860413      က န့် လ န့် ဖျဲ
-0.2854472      ရှိ ဘူး နော် 😞 🙌
-0.30083752     တွေ စ ဖု ပဲ 👉
-0.5127779      လိုက် ဖုန် ရှု လိုက် 🙂😎😎
-0.60587126     ကိုး ခံ လိုက် ပါ ✋
-0.45228755     မ နာ ခံ နဲ့ -ျင်
-0.39421624     က ဘူး ‌ေ - လာ်
-0.44281816     အား တန်း စောက် မ 🖕🖕🤬🤬
-0.60911703     ကြို ပြီး သား ပဲ 🦭

\end\
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc$
```

## Preparing Test Datasets

I already have 5 test outputs with GPT-2 Hatespeech Model. At first, I have to make syllable segmentation on these 5 files.   

Copying test data to the current PPL calculation folder as follows:   

```
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/script/sentence$ ls
Test-1  Test-2  Test-3  Test-4  Test-5
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/script/sentence$ cp * ../../ppl_calc/testdata/
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/script/sentence$
```

I need only 1st column of these files for evaluation with LM.   

```
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc/testdata$ head -n 3 Test-1
မနက် ၅ နာရီ ခု ထိ မ လာ ဘူး ၅ မိနစ် ၅ နာရီ ထိ ပျက် သွား အောင် ပေး တာ လား လီး ပဲ ဟေ့ မအေလိုး တွေပျက် သွား ပြီ ပြန် ဖျက် သလို ပဲောင် မ ပြည့် တော့ ဘူး မအေလိုး တွေ မီး နာရီ ပြန် ပျက် တယ် ဆို တော့ မ သိဝက် လည်း ပျက် ပြီ လီး ပဲ ဟေ့     ab
မအေလိုး တွေ မီတာခ ကျတော့ ပြည်သူ တွေ အကုန်လုံး ခု မီး လာ မယ့် အချိန် မှန် အိပ် ပေး ပြီ နော် မီး ပျက် နေ တာေ ရေ     ab
မအေလိုး တွေ တစ် နေကုန် ပျက် ၉ နာရီ လာ ပြီး ၉ နာရီ တော့ မှာ လာ ဖြတ် နေ တာ ပဲ     ab
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc/testdata$
```

PPL တွက်ဖို့အတွက် test data ကို ပြင်ဆင်တဲ့အခါမှာ hatespeech tag တွေက မလိုအပ်ပဲ မြန်မာစာ စာကြောင်းပဲ သီးသန့် လိုအပ်တာမို့လို့ ...  
Cut Column-1 only ...   

```
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc/testdata$ cut -f1 ./original/Test-
1 > ./Test-1
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc/testdata$ cut -f1 ./original/Test-2 > ./Test-2
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc/testdata$ cut -f1 ./original/Test-3 > ./Test-3
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc/testdata$ cut -f1 ./original/Test-4 > ./Test-4
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc/testdata$ cut -f1 ./original/Test-5 > ./Test-5
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc/testdata$
```

Check the file contents before syllable breaking ...   

```
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc/testdata$ head -n 3 Test-1
မနက် ၅ နာရီ ခု ထိ မ လာ ဘူး ၅ မိနစ် ၅ နာရီ ထိ ပျက် သွား အောင် ပေး တာ လား လီး ပဲ ဟေ့ မအေလိုး တွေပျက် သွား ပြီ ပြန် ဖျက် သလို ပဲောင် မ ပြည့် တော့ ဘူး မအေလိုး တွေ မီး နာရီ ပြန် ပျက် တယ် ဆို တော့ မ သိဝက် လည်း ပျက် ပြီ လီး ပဲ ဟေ့
မအေလိုး တွေ မီတာခ ကျတော့ ပြည်သူ တွေ အကုန်လုံး ခု မီး လာ မယ့် အချိန် မှန် အိပ် ပေး ပြီ နော် မီး ပျက် နေ တာေ ရေ
မအေလိုး တွေ တစ် နေကုန် ပျက် ၉ နာရီ လာ ပြီး ၉ နာရီ တော့ မှာ လာ ဖြတ် နေ တာ ပဲ
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc/testdata$ head -n 3 Test-5
မနက် ၅ နာရီ ခု ထိ မ လာ ဘူး ၅ မိနစ် ၅ နာရီ ထိ ပျက် သွား အောင် ပေး တာ လား လီး ပဲ ဟေ့ မအေလိုး တွေ
မီး ပျက် သွား ပြီ ပြန် ဖျက် သလို ပဲ
မီး လာ ရ မှာ မီး ပေး ပြီး ၅ မိနစ် တောင် မ ပြည့် တော့ ဘူး မအေလိုး တွေ မီး နာရီ ပြန် ပျက် တယ် ဆို တော့ မ သိ ရင် လည်း နာရီဝက် လည်း ပျက် ပြီ လီး ပဲ ဟေ့
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc/testdata$ tail -n 3 Test-4
ဘုန်းကြီး က တော့ မင်း တို့ က ဘယ်လို အဟုတ် မှာ လဲ ကျေနပ် မ ဆိုင် တာ နဲ့ တစ် ယောက် မှာ လေးစား ပါ တယ်
လူ က ရော နင် တို့ တစ် ယောက် က အစား ဖူး တုန်း က ကိုယ့် အများကြီး လို့ ရ တယ် ရှင်း ပေါ် က နေ မြန်မာ လူမျိုး တွေ က သူ တို့ နိုင်ငံ လေး တွေ က လုပ် ခဲ့ ရ လေ နေ လို့ အမေ မ ဟုတ် ဘူး တဲ့ သူ တွေ သူ တို့ အတွက် တောင် မ စား လို့ လား နော်
အခု မှ သန့် တာ ပဲ မြန်မာ ပြည် မှာ ပဲ လေ မအလ ကြီး ရာ ချင် စရာ
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc/testdata$
```

## Syllable Breaking on Testsets

separator ကို space ထားပြီး ဖြတ်ရပါမယ်။  

```
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc/testdata$ perl ../sylbreak.pl -i ./f1/Test-1 -s " " > Test-1.syl
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc/testdata$ perl ../sylbreak.pl -i ./f1/Test-2 -s " " > Test-2.syl
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc/testdata$ perl ../sylbreak.pl -i ./f1/Test-3 -s " " > Test-3.syl
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc/testdata$ perl ../sylbreak.pl -i ./f1/Test-4 -s " " > Test-4.syl
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc/testdata$ perl ../sylbreak.pl -i ./f1/Test-5 -s " " > Test-5.syl
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc/testdata$
```

Check the syllable breaked test data:   

```
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc/testdata$ ls
f1  original  Test-1.syl  Test-2.syl  Test-3.syl  Test-4.syl  Test-5.syl
```

```
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc/testdata$ head -n 3 ./Test-1.syl
မ နက် ၅ နာ ရီ ခု ထိ မ လာ ဘူး ၅ မိ နစ် ၅ နာ ရီ ထိ ပျက် သွား အောင် ပေး တာ လား လီး ပဲ ဟေ့ မ အေ လိုး တွေ ပျက် သွား ပြီ ပြန် ဖျက် သ လို ပဲောင် မ ပြ ည့် တော့ ဘူး မ အေ လိုး တွေ မီး နာ ရီ ပြန် ပျက် တယ် ဆို တော့ မ သိ ဝက် လည်း ပျက် ပြီ လီး ပဲ ဟေ့
မ အေ လိုး တွေ မီ တာ ခ ကျ တော့ ပြည် သူ တွေ အ ကုန် လုံး ခု မီး လာ မယ့် အ ချိန် မှန် အိပ် ပေး ပြီ နော် မီး ပျက် နေ တာေ ရေ
မ အေ လိုး တွေ တစ် နေ ကုန် ပျက် ၉ နာ ရီ လာ ပြီး ၉ နာ ရီ တော့ မှာ လာ ဖြတ် နေ တာ ပဲ
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc/testdata$ head -n 3 ./Test-3.syl
မ နက် ၅ နာ ရီ ခု ထိ မ လာ ဘူး ၅ မိ နစ် ၅ နာ ရီ ထိ ပျက် သွား အောင် ပေး တာ လား လီး ပဲ ဟေ့ မ အေ လိုး တွေ
မီး ပျက် သွား ပြီ ပြန် ဖျက် သ လို ပဲ
မီး လာ ရ မှာ မီး ပေး ပြီး ၅ မိ နစ် တောင် မ ပြ ည့် တော့ ဘူး မ အေ လိုး တွေ မီး နာ ရီ ပြန် ပျက် တယ် ဆို တော့ မ သိ ရင် လည်း နာ ရီ ဝက် လည်း ပျက် ပြီ လီး ပဲ ဟေ့
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc/testdata$ head -n 3 ./Test-5.syl
မ နက် ၅ နာ ရီ ခု ထိ မ လာ ဘူး ၅ မိ နစ် ၅ နာ ရီ ထိ ပျက် သွား အောင် ပေး တာ လား လီး ပဲ ဟေ့ မ အေ လိုး တွေ
မီး ပျက် သွား ပြီ ပြန် ဖျက် သ လို ပဲ
မီး လာ ရ မှာ မီး ပေး ပြီး ၅ မိ နစ် တောင် မ ပြ ည့် တော့ ဘူး မ အေ လိုး တွေ မီး နာ ရီ ပြန် ပျက် တယ် ဆို တော့ မ သိ ရင် လည်း နာ ရီ ဝက် လည်း ပျက် ပြီ လီး ပဲ ဟေ့
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc/testdata$ tail -n 3 ./Test-4.syl
ဘုန်း ကြီး က တော့ မင်း တို့ က ဘယ် လို အ ဟုတ် မှာ လဲ ကျေ နပ် မ ဆိုင် တာ နဲ့ တစ် ယောက် မှာ လေး စား ပါ တယ်
လူ က ရော နင် တို့ တစ် ယောက် က အ စား ဖူး တုန်း က ကိုယ့် အ များ ကြီး လို့ ရ တယ် ရှင်း ပေါ် က နေ မြန် မာ လူ မျိုး တွေ က သူ တို့ နိုင် ငံ လေး တွေ က လုပ် ခဲ့ ရ လေ နေ လို့ အ မေ မ ဟုတ် ဘူး တဲ့ သူ တွေ သူ တို့ အ တွက် တောင် မ စား လို့ လား နော်
အ ခု မှ သန့် တာ ပဲ မြန် မာ ပြည် မှာ ပဲ လေ မ အ လ ကြီး ရာ ချင် စ ရာ
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc/testdata$
```

## Writing a Bash Shell Script

shell script ရဲ့ ဖိုင်နာမည်ကို eval_with_ppl.sh ဆိုပြီး ပေးထားခဲ့တယ်။  

```bash
#!/bin/bash

## Written by Ye Kyaw Thu, LU Lab., Myanmar
## You have to install KenLM in advance.
## For evaluation with PPL on GPT-2 Hatespeech Model generated sentences
## Last updated: 23 Oct 2023

# Check if the folder name argument is provided
if [[ -z "$1" ]]; then
    echo "Error: No folder name provided."
    echo "Usage: $0 <folder-name>"
    exit 1
fi

# Ensure the folder exists
if [[ ! -d "$1" ]]; then
    echo "Error: Folder '$1' does not exist."
    exit 1
fi

# Loop through all .syl files in the specified folder, in alphabetical order
for file in $(find "$1" -name '*.syl' | sort); do
    echo "Evaluation on: $file"
    command="query -v summary ./lm.5gram.arpa < $file"
    echo "Running: $command"
    eval $command
    echo "==========";
    echo "";
done
```

## Evaluation with PPL

Perplexity နဲ့ evaluation ရလဒ်တွေက အောက်ပါအတိုင်းပါ။  

```
(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc$ ./eval_with_ppl.sh ./testdata/
Evaluation on: ./testdata/Test-1.syl
Running: query -v summary ./lm.5gram.arpa < ./testdata/Test-1.syl
Loading the LM will be faster if you build a binary file.
Reading ./lm.5gram.arpa
----5---10---15---20---25---30---35---40---45---50---55---60---65---70---75---80---85---90---95--100
****************************************************************************************************
Perplexity including OOVs:      55.28534226369465
Perplexity excluding OOVs:      53.14884888068335
OOVs:   3
Tokens: 997
Name:query      VmPeak:238648 kB        VmRSS:4144 kB   RSSMax:233052 kB        user:2.74644      sys:0.08795     CPU:2.83441     real:2.83355
==========

Evaluation on: ./testdata/Test-2.syl
Running: query -v summary ./lm.5gram.arpa < ./testdata/Test-2.syl
Loading the LM will be faster if you build a binary file.
Reading ./lm.5gram.arpa
----5---10---15---20---25---30---35---40---45---50---55---60---65---70---75---80---85---90---95--100
****************************************************************************************************
Perplexity including OOVs:      48.190194748201066
Perplexity excluding OOVs:      47.63006610357866
OOVs:   1
Tokens: 1130
Name:query      VmPeak:238648 kB        VmRSS:4212 kB   RSSMax:233188 kB        user:2.73601      sys:0.088       CPU:2.82403     real:2.82336
==========

Evaluation on: ./testdata/Test-3.syl
Running: query -v summary ./lm.5gram.arpa < ./testdata/Test-3.syl
Loading the LM will be faster if you build a binary file.
Reading ./lm.5gram.arpa
----5---10---15---20---25---30---35---40---45---50---55---60---65---70---75---80---85---90---95--100
****************************************************************************************************
Perplexity including OOVs:      48.190194748201066
Perplexity excluding OOVs:      47.63006610357866
OOVs:   1
Tokens: 1130
Name:query      VmPeak:238648 kB        VmRSS:4304 kB   RSSMax:233428 kB        user:2.85088      sys:0.071971    CPU:2.9229      real:2.92227
==========

Evaluation on: ./testdata/Test-4.syl
Running: query -v summary ./lm.5gram.arpa < ./testdata/Test-4.syl
Loading the LM will be faster if you build a binary file.
Reading ./lm.5gram.arpa
----5---10---15---20---25---30---35---40---45---50---55---60---65---70---75---80---85---90---95--100
****************************************************************************************************
Perplexity including OOVs:      48.190194748201066
Perplexity excluding OOVs:      47.63006610357866
OOVs:   1
Tokens: 1130
Name:query      VmPeak:238648 kB        VmRSS:3984 kB   RSSMax:233084 kB        user:2.73172      sys:0.087991    CPU:2.81975     real:2.81901
==========

Evaluation on: ./testdata/Test-5.syl
Running: query -v summary ./lm.5gram.arpa < ./testdata/Test-5.syl
Loading the LM will be faster if you build a binary file.
Reading ./lm.5gram.arpa
----5---10---15---20---25---30---35---40---45---50---55---60---65---70---75---80---85---90---95--100
****************************************************************************************************
Perplexity including OOVs:      48.190194748201066
Perplexity excluding OOVs:      47.63006610357866
OOVs:   1
Tokens: 1130
Name:query      VmPeak:238648 kB        VmRSS:4372 kB   RSSMax:233484 kB        user:2.72437      sys:0.100013    CPU:2.82442     real:2.82386
==========

(base) ye@lst-gpu-3090:~/exp/myHatespeech/eval/ppl_calc$
```

GPT-2 model နဲ့ hatespeech generation ကို ၅ခါ စမ်းလုပ်ခဲ့တာမို့လို ထွက်လာတဲ့ စာကြောင်းတွေကို LM သုံးပြီး PPL နဲ့ evaluation လုပ်တာတော့ ပြီးသွားပြီ။  

## To Do

- hatespeech corpus, in-hourse corpus ထဲက emoji နဲ့ symbol တွေကိုပါ တစ်လုံးချင်းစီ ဖြတ်ပြီး Language model ဆောက်ပြီး အဲဒီမော်ဒယ်နဲ့ evaluation လုပ်ကြည့်ရန်။

