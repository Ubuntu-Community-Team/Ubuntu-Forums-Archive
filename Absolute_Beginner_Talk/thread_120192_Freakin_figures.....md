---
title: "Freakin figures...."
date: 2006-01-21
forum: Absolute Beginner Talk
---

### Post by Heretic Monkey on 2006-01-21
Ok, installed Ubuntu, got all the partitions the way i like them, set up most of the hardware configuration, blah blah.... Now it seems that the majority of the programs i want to run can't properly be utilized on the 64-bit OS i installed....

I have an AMD 64 processor, so i figured "Hey, make use of what i got!".... i'm guessing that was a newb mistake.... **As of now, is there any major advantage of installing the 64-bit distro over the x86?**

So, a big question i have is, when i go to install the x86 version of Ubuntu, do i have to run through and install all of Ubuntu 64-bit, or will formatting the partition it's on when installing the x86 distro?

I promise i won't have TOO many more noob questions....

---

### Post by tokyovigilante on 2006-01-21
[QUOTE=Heretic Monkey]As of now, is there any major advantage of installing the 64-bit distro over the x86?[/QUOTE]
Performance in processor and memory intensive applications, ie DV-editing, encoding etc, and to physically address more than 4GB of RAM.

General desktop use is only marginally faster. However even 32-bit code runs better on a 64-bit processor.

What specifically can you not run? Most problems can be solved either with the 32-bit compatibility libraries or with a chroot.

[QUOTE=Heretic Monkey]
So, a big question i have is, when i go to install the x86 version of Ubuntu, do i have to run through and install all of Ubuntu 64-bit, or will formatting the partition it's on when installing the x86 distro?[/QUOTE]

You need to remove the 64 bit partition and install from scratch. I suggest creating a separate /home partition so your data is not lost.

---

### Post by Heretic Monkey on 2006-01-21
[QUOTE=tokyovigilante]
What specifically can you not run? Most problems can be solved either with the 32-bit compatibility libraries or with a chroot.[/quote]
I tried installing Macromedia Flash (a major plugin i need for a large number of sites i frequent), and the **Automatix** app i've seen around these boards.  I've also been seeing threads on the incompatibility of other programs, no specifics off the top of my head.

> You need to remove the 64 bit partition and install from scratch. I suggest creating a separate /home partition so your data is not lost.
I've only had the 64-bit Ubuntu installed for like 12 hours, and haven't really saved any data or information onto it.  Is the possible loss of information the only downside of just re-formatting using the Ubuntu-install disc partitioner?

*Sig comment: You're correct, emo sux*

---

