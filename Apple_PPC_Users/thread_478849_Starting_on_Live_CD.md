---
title: "Starting on Live CD?"
date: 2007-06-19
forum: Apple PPC Users
---

### Post by DSFAN#1 on 2007-06-19
Hello, everyone I'm fairly new to Linux, and Ubuntu. By that I mean I've NEVER ran any linux before, but I have learned quite a bit on Ubuntu. So I want to run it on my G3 PPC iMac.

So i got downloaded 7.0.4 Feisty Fawn, I got the special low RAM version (can someone explain what the difference in this version is please) because I do have a G3 mac and those are quite aged now. (i only got 192Mb's of RAM :( ) 

So after downloading Ubuntu I opened up disk utility and burnt the file onto a disk. Just as the instructions said.

Next I restart my computer on the disk. It brings me to a screen saying stuff like (paraphrased) default option is install. When in doubt press enter. Most common error is a white screen. 

I press enter and it brings me to a blue page asking what language I'd like. I later find out this is the install procedures.

MY question is, I don't want to quite install yet, right now i just want to boot up on Live CD to see what Ubuntu is like. Is there a special command I must type in to boot on live CD?

---

### Post by Auria on 2007-06-19
> **DSFAN#1 said:**
> Hello, everyone I'm fairly new to Linux, and Ubuntu. By that I mean I've NEVER ran any linux before, but I have learned quite a bit on Ubuntu. So I want to run it on my G3 PPC iMac.

So i got downloaded 7.0.4 Feisty Fawn, I got the special low RAM version (can someone explain what the difference in this version is please) because I do have a G3 mac and those are quite aged now. (i only got 192Mb's of RAM :( ) 

So after downloading Ubuntu I opened up disk utility and burnt the file onto a disk. Just as the instructions said.

Next I restart my computer on the disk. It brings me to a screen saying stuff like (paraphrased) default option is install. When in doubt press enter. Most common error is a white screen. 

I press enter and it brings me to a blue page asking what language I'd like. I later find out this is the install procedures.

MY question is, I don't want to quite install yet, right now i just want to boot up on Live CD to see what Ubuntu is like. Is there a special command I must type in to boot on live CD?


the version you downlaoded (the one you call the low-ram one) is not a LiveCD and cannot be used this way - LiveCDs take more memory.

Basically the LiveCD is nicer, the alternate disk is leaner.

---

### Post by DSFAN#1 on 2007-06-19
> **Auria said:**
> the version you downlaoded (the one you call the low-ram one) is not a LiveCD and cannot be used this way - LiveCDs take more memory.

Basically the LiveCD is nicer, the alternate disk is leaner.

Ok thank you... My new question is. Would my computer be fast enouhg to run the full/normal version of Ubuntu?

it's 400Mhz procoessor
192Mb SDRAM

---

### Post by tcrroadie on 2007-06-19
> **DSFAN#1 said:**
> Ok thank you... My new question is. Would my computer be fast enouhg to run the full/normal version of Ubuntu?

it's 400Mhz procoessor
192Mb SDRAM

Yes, your machine is fast enough to run Ubuntu after installation.  The disk that you downloaded and burned is the Alternate install cd.  I would recommend finishing the installation process on the Alternate installation cd that you already have.  

After you have Ubuntu installed and up and running, we can help you trim down some of the system services that automatically start up at system boot.  This will help free up some extra ram for you.

---

### Post by DSFAN#1 on 2007-06-19
> **tcrroadie said:**
> Yes, your machine is fast enough to run Ubuntu after installation.  The disk that you downloaded and burned is the Alternate install cd.  I would recommend finishing the installation process on the Alternate installation cd that you already have.  

After you have Ubuntu installed and up and running, we can help you trim down some of the system services that automatically start up at system boot.  This will help free up some extra ram for you.


Ok thank-you, but what if I get the normal version of Ubuntu, will i be able to install it, THEN trim down on some thing to make it faster?

So far you've been a HUGE help thouhg. I thank you :)

---

### Post by tcrroadie on 2007-06-20
> **DSFAN#1 said:**
> Ok thank-you, but what if I get the normal version of Ubuntu, will i be able to install it, THEN trim down on some thing to make it faster?

So far you've been a HUGE help thouhg. I thank you :)

What I meant from my previous post, was not the removal of software, but disabling any programs (services/daemons) running in the background on your machine.  Such as ssh, acron, atd, cups (you do need to have cups running if you want to print), hplip, bluetooth.  

You can disable any services that you do not need, to help free up some RAM for other memory hungry applications such as Firefox.  

You can easily disable any unwanted services/daemons through your Gnome menu.  

System -> Administration -> Services.  

Simply uncheck any unwanted services in the list.

---

### Post by ssam on 2007-06-21
ram for those iMacs is very cheep. i strongly recommend that you buy a 256mb chip, which would give you 384mb (assuming that you currently have 128+64, and take the 64mb out)

---

### Post by 3rdalbum on 2007-06-22
> **ssam said:**
> ram for those iMacs is very cheep. i strongly recommend that you buy a 256mb chip, which would give you 384mb (assuming that you currently have 128+64, and take the 64mb out)

Easier said than done - one of the memory chips is stored underneath the CPU, so you need to go to an Applecentre and get it done. They charge a lot for the RAM, and would probably charge you a lot for the installation if you didn't buy the RAM from them.

To the OP: I'd recommend installing Ubuntu from the CD you already have. The Live CD contains a bug that stops your system's monitor from being recognised properly.

If you want to see if Ubuntu is compatible with your hardware before you install it, you could try the Xubuntu Live CD or even give my Copland distribution a go as it is based on Ubuntu.

---

