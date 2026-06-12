---
title: "Kubuntu live disc won't load on Macbook 5,2"
date: 2009-02-17
forum: Apple Hardware Users
---

### Post by darkkn1te on 2009-02-17
Hi, 

I'm fairly new to Linux (I started with Hardy Heron) and extremely new with Macs.  I just bought one of the new white Macbooks and its model id is 5,2.  I downloaded the kubuntu 8.10 live disc, and it won't load up.  I can get to the first screen where it says "Try Kubuntu without changing your computer". But when I hit enter, I get a line that looks like a memory address and Not Responding, then the screen goes blank.

I know the disc is fine because I used it to install Kubuntu on Virtual Box on the mac.  I also used to boot into a Windows computer.

I also tried a Fedora 10 KDE live disc, and it does the same thing.  Does anyone have any insight into my problem?  Is it because of KDE?  Is it because of my model of Mac?  Thanks.

---

### Post by cyberdork33 on 2009-02-17
> **darkkn1te said:**
> Hi, 

I'm fairly new to Linux (I started with Hardy Heron) and extremely new with Macs.  I just bought one of the new white Macbooks and its model id is 5,2.  I downloaded the kubuntu 8.10 live disc, and it won't load up.  I can get to the first screen where it says "Try Kubuntu without changing your computer". But when I hit enter, I get a line that looks like a memory address and Not Responding, then the screen goes blank.

I know the disc is fine because I used it to install Kubuntu on Virtual Box on the mac.  I also used to boot into a Windows computer.

I also tried a Fedora 10 KDE live disc, and it does the same thing.  Does anyone have any insight into my problem?  Is it because of KDE?  Is it because of my model of Mac?  Thanks.I believe you may be one of the first people to try Linux on a MacBook5,2. Unfortunately, it sounds like there is an issue... 

It may be the display that is having a problem. You could try a normal Ubuntu disc... and maybe a Jauntu alpha. there are some extra options available on the bootscreen that may force the display to cooperate.

---

### Post by eoldavix on 2009-02-18
Hello, in ubuntu 8.10 I had the same problem, the solution was mark the NOACPI option in the option's dialogue (F6 button)

Sorry for my poor english

Regards.

---

### Post by darkkn1te on 2009-02-20
That worked like a charm.  Thanks

---

### Post by MriG4 on 2009-03-28
I'm having the same issue: however, I used your advice to run the live disc but when I installed ubuntu (dual boot) I received the same message when i try to boot ubuntu

---

### Post by rshnike on 2009-03-28
> **eoldavix said:**
> Hello, in ubuntu 8.10 I had the same problem, the solution was mark the NOACPI option in the option's dialogue (F6 button)

Sorry for my poor english

Regards.

If this worked perhaps adding this to the wiki is in order though I don't have a 5,2 to test it out on.

---

### Post by eoldavix on 2009-03-31
You need to edit your grub menu. Put in the line "(K)ubuntu blah blah blah..." Press "e" key in the grub screen, put the cursor in the line begins with the word kernel, press the "e" key again and add "acpi off" at the very end of the line. Press enter key and then press the "b" key.

When the system boots, edit /boot/grub/menu.lst (opening a console and typing sudo gedit /boot/grub/menu.lst).

Search for the lines begins with #kopt and kernel and then add acpi=off

You will not need to edit this file anymore.

Regards.

---

### Post by cyberdork33 on 2009-03-31
bug report for this is here:
[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/341230](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/341230)

---

### Post by damage84 on 2009-04-18
I am having the same problem, just bought my MacBook 5,2 and I noticed the forms with documentation on how to do this are missing a section on 5,2 so I'm guessing this model is hot out of the oven. All of my CDs do the same thing, Ubuntu 8.04, 9.04 and Kubuntu 8.10. I will now try the NOACPI option and see if my luck changes. Thanks guys.

---

### Post by damage84 on 2009-04-18
Well turning off acpi worked for getting the CD to boot and I was able to install Ubuntu 9.04, however after restarting and using refit to boot the Linux partition grub loads and freezes immediately.  Oh well, at least I got the CD to boot and I know most/all of the hardware seems to work fine. Now if I could only get grub to load and not freeze :(

---

### Post by Tijs Zwinkels on 2009-07-21
A post on a forum over [here]("http://forum.notebookreview.com/showthread.php?p=4911326") seems to suggest that the hanging grub problem only surfaces on macbooks with 4 gb of memory. Can you confirm this?

---

### Post by damage84 on 2009-08-03
I do in fact have 4 GBs of memory... upgraded myself though not Apple memory.

---

