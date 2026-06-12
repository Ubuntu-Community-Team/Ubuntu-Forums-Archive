---
title: "Make has gone missing"
date: 2005-10-27
forum: Absolute Beginner Talk
---

### Post by dustyub on 2005-10-27
./configure
Make
Make Install 

These are the steps to compiling and installing software from source right? 

I ./configure without errors, but in every case, whether it's 'Anjuta' building my executable or I'm trying to compile software fresh from the net I get a: '''''bash: make: command not found'''' upon running the 'make' command. Note that packages and software install from synaptic and from the applications menu. 

My question is, what could be causing failure in the make command? 
Can 'make' be missing? Broken? Is there a way to fix this? Am I just doing something stupid (seems likely)? 

Thanks in advance for any help you can offer.

---

### Post by Ampersand on 2005-10-27
first thing to check, did you get the build-essential package from synaptic? That contains the programs required to compile programs.

---

### Post by dustyub on 2005-10-27
Well, I'll be damned. Thank you for your help, everything works like a charm now that I have the build-essentials installed. 

I feel stupid, though I don't think I had to do this in the past (pre-installed perhaps?). Oh well. Thanks again.

---

