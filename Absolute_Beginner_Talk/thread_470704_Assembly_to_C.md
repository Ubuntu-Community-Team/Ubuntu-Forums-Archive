---
title: "Assembly to C"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by boschow on 2007-06-11
Hi all,
i have a piece of program written in assembly. I have to rewrite it to C, but i dont know how, can somebody help me with it ?

```

unsigned int iz32prvi(                //read word from nonvolatile data buffer
    TNVVar *nvv,                      // pointer to nonvolatile memory
    UINT16 dat)                       // address of doulbe word in nonvolatile memory
{
  UINT16 vh1 = dat;
  unsigned int bla=0;
  asm {
    LDD 7,SP
    ADDD 2,SP
    TFR D,X
    LDD 0,X
    STD 0,SP
 }
 
 return bla;
}

```

Thx and best regards,
BoSCHoW.

---

### Post by rich.bradshaw on 2007-06-11
Why do you need it in C? You can call assembly from within C if you google it.

---

