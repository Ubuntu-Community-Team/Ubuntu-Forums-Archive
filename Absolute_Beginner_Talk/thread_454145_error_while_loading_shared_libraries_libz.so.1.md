---
title: "error while loading shared libraries: libz.so.1"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by Sysco Kid on 2007-05-25
I'm trying to run a program but I get this message.

error while loading shared libraries: libz.so.1

Can anyone tell me what libraries I'm missing, and what package I need to install?

Current system
ubuntu 7.04 AMD64 server
with 
apt-get install build-essential

---

### Post by Skrynesaver on 2007-05-25
apt-cache search libz.so should answer your question

---

### Post by JesterGr on 2007-05-28
i had same problem with another lib. it asked for libcurl.so.6 (or something like that, found a workaround) and went i did apt-cache search libcurl, it found some results. 

What is this .so.6 supposed to mean, and how i install this particular library? Didn't find it on Synaptic either. Just curious what to do if equivallent problem happens again.

---

