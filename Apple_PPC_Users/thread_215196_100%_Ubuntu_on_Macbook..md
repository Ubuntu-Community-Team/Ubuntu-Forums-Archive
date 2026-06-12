---
title: "100% Ubuntu on Macbook."
date: 2006-07-13
forum: Apple PPC Users
---

### Post by cowboydan on 2006-07-13
I have a core duo macbook.  I've looked through all of the threads and I'm unable to come across someone that only wants unbuntu installed on their machine.  I'm trying to go 100% Open Source so that I have a necessity to learn it.  I'm running into many problems.  I've tried the step by step walk throughs for installing this as a dual boot, ignoring what I think is unimportant information to make this machine 100% ubuntu.  On my sucessful installs, the computer hangs up when it's loading GRUB.  Honestly, I really don't know what I'm doing.  Can anyone help with a walk through on how to just install this without all of the unnecessary partitions?

---

### Post by n00bWillingToLearn on 2006-07-13
Forgive me if I am misunderstanding your question.
The default for the Ubuntu installer is actually to erase everything and just install Ubuntu alone. When you boot the 'Desktop' cd and run the install program from the desktop it should ask you if you want to erase the drive completely or manually edit the partition table. Just select the option to erase the entire drive ( it should be selected by default if I remember correctly ) and continue with the install following the directions given ( enter you username / password / timezone... ). That really should be it if I am not forgetting anything. [edit] I guess I was wrong see comments below, sorry.[/edit]

FYI, to get your airport card working you will need to follow these directions after you install [http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174).

Just curious, do you plan on not using anything prorietary ( Flash, ATI drivers...) or just nothing non-Linux?

---

### Post by cowboydan on 2006-07-13
I've done that a few times now, when I restart the machine all I get is GRUB loading, please wait... and it just sits there.  I've let it do this for about an hour, but I get nothing.

I'm planning on using linux only.

---

### Post by chasisaac on 2006-07-13
> **cowboydan said:**
> I have a core duo macbook.  I've looked through all of the threads and I'm unable to come across someone that only wants unbuntu installed on their machine.  I'm trying to go 100% Open Source so that I have a necessity to learn it.  I'm running into many problems.  I've tried the step by step walk throughs for installing this as a dual boot, ignoring what I think is unimportant information to make this machine 100% ubuntu.  On my sucessful installs, the computer hangs up when it's loading GRUB.  Honestly, I really don't know what I'm doing.  Can anyone help with a walk through on how to just install this without all of the unnecessary partitions?

I hate to say this . . . I am not to sure you can or even want to do this. 
First reason: You need the MacOSX to get updates (firmware) for the computer. Keep a really small partition (3GB) and run make that way. 

Second you need LILO to boot Linux. This will require a very small parition on the HD. 

Read instructions on [http://www.planetisaac.com/articles/ubuntuinstall.html](http://www.planetisaac.com/articles/ubuntuinstall.html)

The installer WILL ALWAYS die at GRUB.


CI

---

### Post by phico on 2006-07-14
> **cowboydan said:**
> .  I'm trying to go 100% Open Source

Should be possible with elilo but I kept a minimum OSX partition to 
be able to ugrade firmware easily (though it could be possible with 
firewire)  but also to check my hardware in case of problem.

It takes 7Gb of  HD but still you can mount that partition to 
share read-only data.

---

