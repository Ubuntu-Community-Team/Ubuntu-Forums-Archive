---
title: "newbie in a twist (CPU stuff)"
date: 2008-08-03
forum: Apple Hardware Users
---

### Post by orangep33l on 2008-08-03
Hello All, 
It is my hope that the following subject has not been brought up. I have successfully downloaded Ubuntu onto a cd on my Macbook. I have gotten it to boot up with Ubuntu only to reach a message telling me that it is unable to boot because I only have i686 CPU when what is needed is x86-64 CPU. I need to select the appropriate kernel for my CPU. It is now when I throw my hands up in the air and hope that one of you fine, experienced people will take some time to help me out. I appreciate it so much. 
From an Orangep33l.

---

### Post by lisati on 2008-08-03
It sounds like you downloaded the 64-bit version of Ubuntu. The 32-bit version will work on more CPUs - is this the one you actually downloaded, and if not, is downloading it an option? (I'm not familiar with what's "under the hood" on the MacBook range of machines)

---

### Post by orangep33l on 2008-08-03
32 bit? I don't recall being given a choice...:confused:

---

### Post by cyberdork33 on 2008-08-03
there is both a 32bit and 64bit version of Ubuntu. If you have an early Macbook (with a Core CPU, not a Core2 CPU) then you have a 32bit-only CPU. You should determine the version of your Macbook so that we know what hardware you have. See the "Before you post..." link in my signature.

---

### Post by orangep33l on 2008-08-03
I have a Mac OS X version 10.4.11

---

### Post by russo.mic on 2008-08-03
No, not the version of osx, but the hardware.  Is it a Core2Duo processor, or just a CoreDuo processor?  Or is it intel or ppc?

This is a question of hardware.  Go to the apple menu and about my mac in OS X for info.

Russo

---

### Post by tuxxy on 2008-08-03
Try the 32 bit install ISO as advised

---

### Post by orangep33l on 2008-08-03
Oh, sorry! Intel Core Duo

---

### Post by orangep33l on 2008-08-04
Anyway... I did install the 32 bit, considering there were 2 choices, I chose the first one. I feel like that part is covered, but about that message I was receiving, it seems like no one else experienced that problem.

---

### Post by cyberdork33 on 2008-08-04
> **orangep33l said:**
> Anyway... I did install the 32 bit, considering there were 2 choices, I chose the first one. I feel like that part is covered, but about that message I was receiving, it seems like no one else experienced that problem.

Yes, that is normal. Although, how you got it completely installed before that is beyond me... Usually, you encounter that message as soon as you select an option at the bootloader.

You have a Core CPU (as opposed to Core2), thus your machine is not capable of using 64bit binaries. That message is normal if you CPU is not capable of executing 64bit instructions.

Please read the "Before You Post..." link in my signature for basic information about hardware versions, and direction to the best install information for your hardware. BTW, you should have a MacBook1,1.

---

