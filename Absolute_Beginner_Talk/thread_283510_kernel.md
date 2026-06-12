---
title: "kernel"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by yosef on 2006-10-24
how can I tell which kernel I have?  And if I don't have 2.6.18 how can I upgrade to it?

---

### Post by taurus on 2006-10-24
From a terminal, type

```
uname -a
```
And if you want to upgrade your kernel, the best way is to fire up synaptic and Search for it.  Then, highlight the latest and install it.

---

### Post by Kateikyoushi on 2006-10-24
uname -a will list which kernel you are using.
Edgy comes with a pathed 2.6.17 kernel which has most functions of .18

---

### Post by hw-tph on 2006-10-24
**uname -r** or **-a** will tell you what kernel you are running. Building a custom kernel is described [here](https://wiki.ubuntu.com/KernelCustomBuild) as well as on other pages in the wiki.


Håkan

---

### Post by TitusDalwards on 2006-10-24
uname -r  command  gives you the version of your kernel, if you don't have 2.6.18 you can download from [http://www.kernel.org](http://www.kernel.org) and after copiling for your system you can use it.

---

### Post by superprotta on 2006-10-24
type 
```
uname -r
``` in the terminal.to upgrade i think you should download and compile one..

---

### Post by furiousV on 2006-10-24
Just a quick question, in subject:

On the auto update, I noticed several options regarding the kernel.

There was simply Linux Kernel, Linux Kernel 2.6.xx and finally, Kernel *Image*.

Was just wondering what the difference between them all would be, and what I should install. I did install all of them though, system works fine.

---

### Post by Aberrix on 2006-10-24
[Picking the Kernel thats Right for You]("http://www.ubuntuforums.org/showthread.php?t=85917")

---

### Post by furiousV on 2006-10-24
> **Aberrix said:**
> [Picking the Kernel thats Right for You]("http://www.ubuntuforums.org/showthread.php?t=85917")

Thanks for the link, clears up what kernel to use with my AMD 64.

But it does not answer my question, what is the difference between the 'actual kernel' and a 'kernel image' ?

The post says not to install the kernel-image, but further down it says to run a quick search for such in Synaptic. Hmm

---

