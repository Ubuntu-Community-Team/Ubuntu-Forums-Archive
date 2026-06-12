---
title: "where are the kernel source?"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by jawa00 on 2006-09-19
I have a brand new standard dapper 6.06 lts on my laptop, I would like to
know if on my linuxbox does exist a directory which contains the kernel sources because I have as a target the optimisation of the hardware and I need to create a link in /usr/src which point to the kernel sources..if any!  
 
Thanks  Jawa00 - Italy -

---

### Post by Brunellus on 2006-09-19
your first step is to install the build-essential package

sudo aptitude install build-essential

A good kernel howto for ubuntu users:

[http://doc.gwos.org/index.php/Kernel_Compilation_Dapper](http://doc.gwos.org/index.php/Kernel_Compilation_Dapper)

---

### Post by lamego on 2006-09-19
You will need to install it.
Go to synaptic and search for "kernel-source" or just:
```
sudo apt-get install kernel-source
```

---

### Post by jawa00 on 2006-09-19
I already did it!

My question is I have to download the my kernel sources in /usr/src or Ican find them in my linux box and point to them from /usr/src?

---

### Post by Brunellus on 2006-09-19
> **jawa00 said:**
> I already did it!

My question is I have to download the my kernel sources in /usr/src or Ican find them in my linux box and point to them from /usr/src?
I don't understand the question.  

The kernel-source packages should already be in /usr/src

---

### Post by jawa00 on 2006-09-19
you said to install the kernel source ok my question is where I can find them?  I mean the directory.

---

### Post by Brunellus on 2006-09-19
cd /usr/src

and see what's there.

---

### Post by jawa00 on 2006-09-19
Thank you Brunellus....Great wine...

---

### Post by xyz on 2006-09-19
```
th@luser:/usr/src$ ls -l
total 0

```
Normal? Should do something about that?Thx.

---

### Post by Brunellus on 2006-09-19
> **xyz said:**
> ```
th@luser:/usr/src$ ls -l
total 0

```
Normal? Should do something about that?Thx.
I don't understand the question

---

### Post by xyz on 2006-09-19
I was led to believe that kernel sources belong in /usr/src and seeing nothing in there, I'm wondering what went wrong if anything at all?
Sorry if I wasn't clear.
Maybe it's 'normal' there's nothing in there. Don't know.

---

### Post by Brunellus on 2006-09-19
they are in /usr/src if and only if you download them.  Kernel sources are *available*, but not downloaded by default.

---

### Post by jawa00 on 2006-09-19
I did the download of the kernel source 2.6.15.tar.bz2  it goes automatically in /usr/src as you said, and decompressed.Now the point is: I have installed a linux-image 2.6.15-26-i386 on my linuxbox  if I want to compile the kernel source just installed in /usr/src/linux which has the version is 2.6.15 I will get after a compilation a new image upgraded like the 2.6.15-26 actually installed?

---

### Post by Brunellus on 2006-09-19
> **jawa00 said:**
> I did the download of the kernel source 2.6.15.tar.bz2  it goes automatically in /usr/src as you said, and decompressed.Now the point is: I have installed a linux-image 2.6.15-26-i386 on my linuxbox  if I want to compile the kernel source just installed in /usr/src/linux which has the version is 2.6.15 I will get after a compilation a new image upgraded like the 2.6.15-26 actually installed?
refer to the kernel howto I linked you earlier in this thread.

---

