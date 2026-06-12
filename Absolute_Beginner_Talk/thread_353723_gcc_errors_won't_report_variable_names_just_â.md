---
title: "gcc errors won't report variable names just â"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by siddharth.dawara on 2007-02-05
I'm using Xubuntu. I've installed the build-essentials package using Synaptic and my gcc won't report any symbolic names, like function names or variable names.

All it show's me is:

maintry.l: In function â:
maintry.l:447: error: â was not declared in this scope
maintry.l:514: error: â was not declared in this scope
maintry.l:546: error: â was not declared in this scope
maintry.l:552: error: â was not declared in this scope
maintry.l:565: error: â was not declared in this scope
maintry.l:631: error: â was not declared in this scope
maintry.l:646: error: â was not declared in this scope
maintry.l:658: error: â was not declared in this scope
maintry.l:690: error: â was not declared in this scope
maintry.l:701: error: â was not declared in this scope

I've tried installing the locales package for the installed gcc versions, still doesn't work.

Thanks in advance!

---

### Post by jblebrun on 2007-02-05
It looks like your terminal program is choking on multichar output from gcc. Try a different terminal program, that properly supports multichar encodings (or enable it on the terminal program that you're using). 

Multichar means that a single character is actually encoded using multiple bytes. GCC is giving you an error message, and it puts special quote characters around variable names. If your terminal program doesn't know how to interpret the multi-byte quote characters, you see weird output like you've pasted here.

---

### Post by siddharth.dawara on 2007-02-05
I was using xterm instead of the default terminal!!!!

I should have written in that in the post, terribly sorry about that.

But what you said was right, I switched back to the default terminal and it shows me the names, only demarcated with three question marks. It works quite fine for me though :) Thanks a zillion for your help!

Still ... how do you change the perferences for xterm to allow interpretation of multi-byte quote characters?

---

