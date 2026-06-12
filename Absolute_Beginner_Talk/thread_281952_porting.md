---
title: "porting"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by saintj0n on 2006-10-21
I would like to take my c++ programs from college and get them to work on linux. Is it difficult to make them work? Is there anything grammatically different or fundamentally incompatible between a program written on anjuta IDE and a program with identical source written on visual studio?

---

### Post by localuser on 2006-10-22
Microsoft doesn't strictly adhere to standard C++ so you may run into problems, though probably nothing that you won't be able to fix.

Also, if you made any system calls or used sockets or threads, you may run into incompatibilities.

There's no better way to know than to fire up your Linux compiler and give it a try :)

---

### Post by slimdog360 on 2006-10-22
if its the same source code it should be alright. You may just have to compile it again.

---

### Post by saintj0n on 2006-10-22
Is there an FAQ somewhere that will get me started on building apps that will work within a window or produce dialog boxes, radio buttons, scroll bars, etc?

---

### Post by saintj0n on 2006-10-23
I am sure I will have to change the wording for displaying jpegs (ala slide show style), since that requires a system call. Unless there is a way of calling a jpeg from linux. Is there a c++ command for calling jpegs that works in Linux? another question I wondered was, if I want to distribute my programs as freeware, do I still have legal issues with using trademark logos in my program? Are you allowed to use brand names and trademarks (without paying royalties or fees?

---

### Post by n0dl on 2006-10-23
yeah all you have to do is compile it. You may want to look at the book "Programming in the unix/linux" environment and perhaps some Linux admin books to optimize and utilize your software to its full potential on the OS. 
If you wrote your programs in some kind of c++ dialect (such as the notrious borland) then you may have to do some maintainance before actually compiling your programs or youll end up with some weird syntax errors.

---

