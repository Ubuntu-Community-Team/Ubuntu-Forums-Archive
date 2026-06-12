---
title: "What kernel should i be using?"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by WalmartSniperLX on 2006-08-09
Hey Im getting a lot of problems with the terminal and certain files/directories not being there. Im wondering if this has to do with what kernel im using? But jw what version should I be using?

---

### Post by GuitarHero on 2006-08-09
What kind of processor do you have?

---

### Post by WalmartSniperLX on 2006-08-09
> **GuitarHero said:**
> What kind of processor do you have?

AMD sempron 64 3100+

---

### Post by kpkeerthi on 2006-08-09
Your problem definition is very vague. What exactly is the problem you've got with the terminal? What folders and files do you find missing? Have you ever changed your kernel? Was it fine before you 'upgraded' your kernel? And give us some info about the hardware you are running?

---

### Post by GuitarHero on 2006-08-09
I think Linux kernel image for version 2.4.27 on AMD K7 should do it.  Go to the synaptic package manager, search for kernel, and see which one you are using.

And yes I should have asked if you had made changes to your kernel, ubuntu should have installed the right one.

---

### Post by WalmartSniperLX on 2006-08-09
> **kpkeerthi said:**
> Your problem definition is very vague. What exactly is the problem you've got with the terminal? What folders and files do you find missing? Have you ever changed your kernel? Was it fine before you 'upgraded' your kernel? And give us some info about the hardware you are running?

First off my prob with the terminal is that when i follow instructions to install something it ends up giving me such outputs saying that there is no file or directory. Heres and example pasted off of a thread on the forum for installing bcm43xx-fwcutter:


Install bcm43xx-fwcutter
Open a terminal (dont worry) and type the following:
Code:
sudo apt-get install bcm43xx-fwcutter



I typed it in and heres the output:


[I]patrick@patrick-desktop:~$ sudo apt-get install bcm43xx-fwcutter
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package bcm43xx-fwcutter
patrick@patrick-desktop:~$
[/I]


I dont remember doing any updates to the kernel all thought I may have inorder to install my ATI driver. Im running 2.6.15-26-386.


My hardware is this:

AMD Sempron 64 3100+ at 1.8ghz x86-64
1GB of Patriot Memory (SC)
28GB partition for ubuntu 
ATI Radeon x1600Pro 256mb DDR2
onboard audio


I hope that is enough :S Thanks for helping me

---

### Post by GuitarHero on 2006-08-09
That means you probably need to enable the extra repositories.  Theres a guide in the wiki.

---

### Post by WalmartSniperLX on 2006-08-09
> **GuitarHero said:**
> That means you probably need to enable the extra repositories.  Theres a guide in the wiki.

Ok thanks :)

---

