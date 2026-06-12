---
title: "segmentation fault (core dumped)"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by jgrossm1 on 2008-03-02
hey everyone

so i just installed ubuntu last week, dual booting with vista more for compatibility issues than anything else, and i was trying to get an assembler to work under ubuntu (which can be found here: [http://flatassembler.net/](http://flatassembler.net/)) as I am working on learning assembly language. However, after I assemble a source file of one line in length to test the assembler:

move ax,3

and then run the output executable I get the error:

Segmentation fault (core dumped)

I've searched other forums and found several cases of the same error, though none with an assembler (seemed to be quite a few with Firefox though), and no one really explained exactly what the message means, though one forum mentioned that it might be due to overheated hardware (which I seriously doubt is the case here). Can anyone either explain what it is/how to fix it?

If you need any additional information please ask, wasn't really sure what to include with this post

Thank you in advance

---

### Post by jimbob on 2008-03-02
I haven't done any of this in many years but on entry to your program don't you have to use the push instruction to save the contents of all the registers so that they can be restored when you exit and Ubuntu can go along on it's merry way?

You are clobbering whatever is in the ax register with a 3 are you not?  That might be what is causing the segmentation fault.

---

