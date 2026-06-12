---
title: "Failed install? rookie mistake - Save me!"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by ordel on 2006-06-07
I realise related questions about this topic have been submitted but i hope that someone can give me more specific answers to my problem. 

After trying to install Ubuntu I am now getting a Grub loader error " Stage 1.5, error21". I cannot get into my windows XP now at all or get beyond this stage?

I used an external (formatted)hard drive and attempted to install ubuntu 5.10 on it. i already have (had??!) win XP on a desktop  pc and i thought that avoiding resizing or meddling with the internal Hard disk partitions would be safer. However i never took into account Grub being installed in the Mbr of the windows disk? Now grub comes back with this error?

:confused: 
Trust me i have searched the forums and come to the conclusion that FixMbr from the windows recovery concole is a choice. However would trying to install ubuntu to the internal hd also be possible? i.e. resize the hopefully untouched windows partition and make room for ubuntu?

This is my first step into linux and i would be ever so grateful of some helpful advice?

---

### Post by jimrz on 2006-06-07
[QUOTE=ordel]I realise related questions about this topic have been submitted but i hope that someone can give me more specific answers to my problem. 

After trying to install Ubuntu I am now getting a Grub loader error " Stage 1.5, error21". I cannot get into my windows XP now at all or get beyond this stage?

I used an external (formatted)hard drive and attempted to install ubuntu 5.10 on it. i already have (had??!) win XP on a desktop  pc and i thought that avoiding resizing or meddling with the internal Hard disk partitions would be safer. However i never took into account Grub being installed in the Mbr of the windows disk? Now grub comes back with this error?

:confused: 
Trust me i have searched the forums and come to the conclusion that FixMbr from the windows recovery concole is a choice. However would trying to install ubuntu to the internal hd also be possible? i.e. resize the hopefully untouched windows partition and make room for ubuntu?

This is my first step into linux and i would be ever so grateful of some helpful advice?[/QUOTE]

yes, you should be able to do just that. if you really do not want to touch your win partition, you could (assuming you have a place for one) add a 2nd internal hd and intall ubunto to it. this is how mine is set up and works like a charm.

---

### Post by catlett on 2006-06-07
You can definately install ubuntu to your xp hard drive. It is stable but you should have a backup before donig any partitioning.
That said there is a link to a dapper install guide in my signature that will walk you through it.
I think the problem is your motherboard might not support booting to an external hard drive and grub can't access it. Grub installs to the mbr (don't worry windows hasn't been touched) That partt of grub is minimal and only gets grub to the next stage. The error is grub can't find the next stage . The next stage is on your external hard drive in the boot folder.
If you boot to the install cd and resize your xp drive, after the install grub will be able to boot you to windows or ubuntu.

---

### Post by ordel on 2006-06-08
okay so I if understand correctly, i should begin a new ubuntu install to my internal hard disk. My fear is that i will do more damage and pass the point of no retrun as with the windows recovery utility i was able to get a dos prompt and 'see' some of my old windows files on the hard disk. 

A reinstall on the internal hard drive should (auto)partition the hd as needed resizing windows to make room for ubuntu and hopefully correctly putting grub in at the mbr?
Would i be correct in saying this?

Thanks for your advice guys

---

### Post by catlett on 2006-06-08
You don't have to reinstall to your hard drive. I thought you were asking if that was an option to get a working ubuntu install.
If you just want windows back, get to that dos prompt again and enter ```
fixmbr
```
The easiest way to install is to buy an old hard drive. (I get 15gb pulled ide drives from the local computer shop for $20) Put this drive as an internal slave drive and install ubuntu to that.

---

