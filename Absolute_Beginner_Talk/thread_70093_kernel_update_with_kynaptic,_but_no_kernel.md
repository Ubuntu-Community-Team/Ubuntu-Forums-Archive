---
title: "kernel update with kynaptic, but no kernel"
date: 2005-09-28
forum: Absolute Beginner Talk
---

### Post by stoeptegel on 2005-09-28
*Long version:*
I did some updates with kynaptic some days back, noticed that it installed the new 2.6.10.7 kernel, and i assumed that it was good to go.   But today conky showed me that the running kernel was still 2.6.10.5. 
So i did a reboot for looking what grub was willing to show me. I was kind of surprised not seeing the new kernel listed there, so i did a ls on /boot and the whole kernel appears to be missing. :confused: 

*short:*
Kynaptic says i've installed the new 2.6.10.7 kernel, but grub and ls /boot says otherwise.


Someone knows what i did wrong?
TIA

---

### Post by stoeptegel on 2005-09-29
Is there something i can investigate? It's propably  my newbieness which made me doing something wrong. Please help me.

---

### Post by stoeptegel on 2005-09-30
Better someone has an idea, this it total crap.

---

### Post by stoeptegel on 2005-09-30
I've installed another kernel: 2.6.10.7-k7. This one also shows up as a wrong numer 2.6.10.5-k7 in system.

---

### Post by nitricacid on 2005-09-30
are you useing the search that is on the Synaptic? 
I.e. Search 'Kernel' ?

Cuz i just search for 'Kernel' and only found patches.
There were no actual kernel updates

---

### Post by stoeptegel on 2005-09-30
No but when i search for: "linux-"  a new version is listed, as far i know.

---

### Post by nitricacid on 2005-09-30
What exactly did you install that you think\it says its a kernel?

---

### Post by nitricacid on 2005-09-30
BTW, you might want to try this site for latest kernel version [http://www.kernel.org/](http://www.kernel.org/)

---

### Post by stoeptegel on 2005-09-30
I installed linux-386 and later linux-k7, both listed in kynaptic as installed, but i can't find them,

EDit
kernel.org and then compiling from source? no i've seen enough dependencies hell, sorry that doesn't work for me.

---

### Post by nitricacid on 2005-09-30
Here is what they both say in the description.
I am not sure but i think the 386 is for intel processors and the other is for AMD.
Which one are you running?

The only ones i have marked is the 386.
It also sounds to me that they only depend on the Completed Linux Kernel.

Complete Linux kernel on 386.
This package will always depend on the latest complete Linux kernel available
for 386..

Complete Linux kernel on AMD K7.
This package will always depend on the latest complete Linux kernel available
for AMD Duron/Athlon.

Your guess is as good as mine, i am still a noober at this stuff myself.

I anything just wait till the full version of Breezy comes out. It should update then (hopefully).

---

### Post by stoeptegel on 2005-09-30
I am running neither of both, as uname -a says: 
Linux Jupiter 2.6.10-5-386 #1 Fri Sep 23 14:13:55 UTC 2005 i686 GNU/Linux
(i have an amd64, both i386 and k7 should work.)

Yeah descriptions if what kynaptic lacks of. (or it's very very hard to find)

No problem nitricacid, more people more knowledge.;)

---

