---
title: "What is compiling?"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by skhobotu on 2007-07-25
People on this forum talk a lot about compiling. What is it and how do you do it.
Words of one syllable ,please!

---

### Post by Mornedhel on 2007-07-25
Compiling is turning human-understandable code (example : C code) into machine-understandable code. If you heard about compiling here, it was likely something about compiling your own modules for your kernel, or compiling your own kernel, or compiling a third-party application not found in the Ubuntu package repositories. You'd compile by running your source files through a compiler program (in the case of C, gcc). These are mildly complicated tasks, do you need something in particular ?

(I'm leaving work in approx. 10 minutes and will not have access again till I get off the bus about 35 minutes later, but I'm subscribing to this thread so I'll keep an eye on it.)

---

### Post by Lord Illidan on 2007-07-25
Well, I'm lazy so...

[http://en.wikipedia.org/wiki/Compiler](http://en.wikipedia.org/wiki/Compiler)

---

### Post by Tomosaur on 2007-07-25
> **skhobotu said:**
> People on this forum talk a lot about compiling. What is it and how do you do it.
Words of one syllable ,please!

It means building a computer program from the source code. Source code is the code that programmers have to type to create a program. You can open source code in a text editor, but after compiling the source code, the finished program cannot be opened in a text editor (or it CAN, but it will just be a bunch of random characters).

If you need to compile something, you must first install the 'build-essential' package, then go into the folder where your source code files are, and **normally** you would then type './configure && make && sudo make install' to compile and install the software.

---

### Post by skhobotu on 2007-07-25
Thanks for that. I suspected it was something like that. I just wanted to understand what people were talking about. I have no need to carry out any compiling.I am still affected by Windows-itis where I want to point and click at everything!
Thanks again, hope this is helpful to other forum users.

---

### Post by andrew.46 on 2007-07-26
Hi,

 Saw your post about compiling:

> **skhobotu said:**
> People on this forum talk a lot about compiling. What is it and how do you do it.
Words of one syllable ,please!

 There is an excellent set of pages on compiling, apt, checkinstall etc starting at:

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

 It is beautifully written and well researched. Wish I had seen it before I started blundering through compiling :-)

                       Andrew

---

### Post by rich.bradshaw on 2007-07-26
You likely won't ever need to compile anything - I have only compiled my own code, but never any applications etc.

An advantage is that the compiled program is specific to your processor so it will run faster - though not by much.

Gentoo people like to compile everything from scratch in order to get that benefit.

---

### Post by andrew.46 on 2007-07-26
Hi,

 Can I cordially disagree with part of your post:

> **rich.bradshaw said:**
> You likely won't ever need to compile anything - I have only compiled my own code, but never any applications etc. An advantage is that the compiled program is specific to your processor so it will run faster - though not by much. Gentoo people like to compile everything from scratch in order to get that benefit.

 Certainly the Ubuntu repositories contain a wealth of material but there _will_ come a time that you will want software not in the repository, or you will want a different feature compiled into that software, or you will need a different version of that software.

 At that time the knowledge of how to compile will greatly extend the possibilities available to you.

                  Andrew

---

