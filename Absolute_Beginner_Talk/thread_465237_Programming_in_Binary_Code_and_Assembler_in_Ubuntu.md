---
title: "Programming in Binary Code and Assembler in Ubuntu?"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by willz06jw on 2007-06-05
Howdy,

I am trying to find the easiest way (AKA which programs do I use) to create a program in Binary Code that will run in Ubuntu.

Now I know this is a strange and eclectic question, but I have programmed a bit in my time and I am ready to try to further my understanding by trying this for fun. 

I am also interested in learning assembler (for device driver programming), so any help on what I could use for that would also be greatly appreciated.

Thanks Ubuntu guys/gals,
Will from Texas

btw: Is Binary Code faster than Assembly Language?

---

### Post by finer recliner on 2007-06-05
by binary code, i assume you mean 100101001010101010 etc...?
if so then stop right there. nobody, i repeat, nobody, programs using 0s and 1s (except maybe the insane). it is just too demanding to expect anyone to honestly write a program in just binary numbers (and be able to debug it too).

assemby on the other hand...is pretty much binary but in words that humans can understand. you can probably say they run at the same speed.

assembly is no walk in the park. its a low level language (meaning its easier for the computer to understand than a human). something like C++ is a higher level language (more natural human understanding). but the lower level you code at, the more effecient your program will execute.

---

### Post by willz06jw on 2007-06-06
The computers in the 1950's used punch cards marked with 1s and 0s to tell the computer what to do.  I thought that would be an interesting (also completely useless) experiment.  I heard you can use the jump instruction, when programming assembler, to a memory location with 0s and 1s to read binary code from that location.  But of course assembler is still not under my belt yet to try that.

What do you guys use to write assember, just vi?

Willz06jw

---

### Post by AnRa on 2007-06-06
You can learn using this book: [PC Assembly Language](http://www.drpaulcarter.com/pcasm/). As for the programs you may use NASM or GAS.

---

### Post by lazyart on 2007-06-06
I wanted to respond to this originally but I didn't want to take away it's "Unanswered Post" status because I didn't have an answer.

Assembly language is pretty much dead.  I used it in the 80s and early 90s and it's good for a static environment (for me it was the Commodore 64).  You have commands that translate directly into opcodes (binary/hex) and perhaps an argument:

```
LDA #255
```
translated to
```
$A9 $FF
```

which meant LoaD the Accumulator with the value 255.

You could certainly JuMP to other code (which was considered inelegant) or JSR -- Jump to SubRoutine (much prettier).  That is 6502 assembly-- I never took it up on any other platform.

If you still insist on abusing yourself, a better place to start would be [here]("http://www.drpaulcarter.com/pcasm/").  It takes a lot of discipline to work in assembly.  You have no real data structures other than simple counters.  You have to make *everything*.

---

### Post by Austin_KW on 2007-06-06
You do not want to write in binary/machine code unless you are a machine. The only time it is useful is when you hand patch a program.

The easiest way to create a program in binary code is to write it in a high level language and compile it.

You probably do not want to program in assembly language, It may be helpful to know assembly because knowing the fundamentals will make you a better programmer, but in general you would not want to use it. Be wary of people who tell you the advantages of writing in a assembly language, it often leads to what people in the business call 'write only code', impossible to understand, modify and maintain

If you a interested in low level programming, device drivers, etc you want to learn C. Even programming on bare hardware usually consists of a few assembly instructions to initialize the hardware and then a jump to the C code.

---

