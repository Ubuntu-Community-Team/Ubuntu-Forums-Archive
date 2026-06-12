---
title: "Compiling RainbowCrack - Unknown Register"
date: 2006-07-29
forum: Apple PPC Users
---

### Post by aboutblank on 2006-07-29
Hey all,

I'm attemping to compile the official rainbowcrack 1.2 from [here]("http://www.antsight.com/zsl/rainbowcrack/"). I get the following error:

```
aboutblank@ServerG5:~/RainbowCrack/rainbowcrack-1.2-src/src$ make -f makefile.linux
g++ Public.cpp ChainWalkContext.cpp HashAlgorithm.cpp HashRoutine.cpp RainbowTableGenerate.cpp -lssl -O3 -o rtgen
ChainWalkContext.cpp: In member function ‘void CChainWalkContext::IndexToPlain()’:
ChainWalkContext.cpp:425: error: unknown register name ‘%edx’ in ‘asm’
ChainWalkContext.cpp:425: error: unknown register name ‘%eax’ in ‘asm’
make: *** [rtgen] Error 1
```

I think the error occurs because the PowerPC processor doesn't have those registers. So, is there any hope of me fixing this?

PowerMac G5 64 bit

---

### Post by chansiuming on 2006-07-29
> **aboutblank said:**
> Hey all,

I'm attemping to compile the official rainbowcrack 1.2 from [here]("http://www.antsight.com/zsl/rainbowcrack/"). I get the following error:

```
aboutblank@ServerG5:~/RainbowCrack/rainbowcrack-1.2-src/src$ make -f makefile.linux
g++ Public.cpp ChainWalkContext.cpp HashAlgorithm.cpp HashRoutine.cpp RainbowTableGenerate.cpp -lssl -O3 -o rtgen
ChainWalkContext.cpp: In member function ‘void CChainWalkContext::IndexToPlain()’:
ChainWalkContext.cpp:425: error: unknown register name ‘%edx’ in ‘asm’
ChainWalkContext.cpp:425: error: unknown register name ‘%eax’ in ‘asm’
make: *** [rtgen] Error 1
```

I think the error occurs because the PowerPC processor doesn't have those registers. So, is there any hope of me fixing this?

PowerMac G5 64 bit

It's x86 assembler, so if you cannot edit source code, no hope. If you look at the file in question, theres a "slow version" of the same loop above the faulting instructions. You might want to comment out the faulting loop and try to slow version instead.

---

### Post by aboutblank on 2006-07-29
> **chansiuming said:**
> You might want to comment out the faulting loop and try to slow version instead.

Whoo hoo! This worked. Thanks a bunch! I didn't look at the source because I thought it would be a fruitless effort. Thanks again :KS :KS

---

