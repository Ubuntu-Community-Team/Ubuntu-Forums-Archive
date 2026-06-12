---
title: "Newbie seeking advice..."
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by alba1314 on 2008-03-07
Hi, I am about to delve into Linux for the first time and wondered if anyone would be so kind as to advise me on how best to set it up on my WinXP PC?

I currently have two hard drives, one 160Gb (C) drive containing WinXP and a smaller separate 20Gb (D) drive which I would like to install Ubuntu 7.10 desktop onto.  I have downloaded ubuntu-7.10-desktop-amd64 for my PC which is running a 900 megahertz AMD Sempron processor - I think this is the correct version of Ubuntu to install, but would appreciate advice on this...

Can anyone please explain, in easy steps, my best way to proceed with installing Ubuntu to my D drive?

Thanks in advance,

alba.

---

### Post by Joeb454 on 2008-03-07
Actually no, that isn't the correct version, you need the Intel x86 version (that is for AMD as well)

amd64 is the version for 64 bit processors :)

---

### Post by forestpixie on 2008-03-07
this page should be of some help 

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by PinkFloyd102489 on 2008-03-07
You might want to use the Alternate CD, since the PC is slower.

---

### Post by alba1314 on 2008-03-07
Thanks to Joeb454, forestpixie and PinkFloyd102489 for your replies - They're very much appreciated.  :KS

Joeb, I'll download the Intel x86 version as you suggest and try my luck with it.

Pixie, thanks for the link - I've printed hard copy of the details and will have some interesting reading tonight, I'm sure?!  

Floyd, can I ask why you suggest using the Alternate CD?  Is this the same as using a 'live' CD??

Already, I feel as if the big step away from M$ is not going to be as scary as I thought it might be - Thank you all!!

---

### Post by Joeb454 on 2008-03-07
It's no problem :)

And the 'Alternate CD' is for lower spec systems :) It doesn't contain the 'Live' desktop environment that you can boot into and use before installing.

So basically the 'alternate' install CD, **only** installs the system with a text based interface :)

---

### Post by alba1314 on 2008-03-07
What is the difference in a text based interface and a standard install, Joeb?

Sorry to ask, but Ubuntu and Linux is all new to me and I know that I've a fair bit to learn....

---

### Post by Joeb454 on 2008-03-07
Text based install is harder to use if you need to be careful of the drives you use, whereas the standard install is a normal desktop loaded into RAM.

However if your processor is only 900Mhz, and you don't have much RAM, I would recommend the Alternate CD, just be careful you don't overwrite your Windows partition (unless that's what you want ;))

---

### Post by alba1314 on 2008-03-07
Thanks, Joeb.  

I've been able to get some info from **[http://releases.ubuntu.com/7.10](http://releases.ubuntu.com/7.10)** about the various forms of Ubuntu and it is quite informative.  Though it's always good to hear the opinion of the informed!

As far as memory goes, I have 1216Mb memory onboard, though (admittedly) the processor is a little on the slow side.  Will this make any difference to the version of Ubuntu I should use??

Also, I will be installing to my smaller separate 20Gb (D) hard drive, so will this impact on my main 160Gb (C) drive where WinXP is installed??


Thanks, again...

---

### Post by Joeb454 on 2008-03-07
It shouldn't, as long as you make sure you install to the correct drive. :) Back-up important data on the XP drive just to be safe (good practice when installing/upgrading an OS).

And the processor might make a difference....if Ubuntu does not run quick enough for you, I'd recommend Xubuntu :)

---

### Post by Ecclesia on 2008-03-07
You should be fine with the memory.  Linux will run fine on fairly low memory.  If you had less than 256mb I would suggest Xubuntu - which you may like better if you find that Ubuntu runs too slowly on your machine.

Ubuntu won't conflict with XP as long as it's on a separate drive, but you will have to install grub on this drive in order to dual boot.  I would recommend reading up on dual booting before installation, just to make sure that it goes smoothly.

Also, I'd recommend partitioning your drive with a separate root and /home partition.  This way when Hardy hits an a couple of months you'll have an easier time upgrading.  So when you install, you're going to choose the 20gb drive, and partition it into three sections.  One is going to be your swap partition (the text installer should kind of set this up as a base for you anyway, you'll see it), the next will be your root folder or "/" that's going to contain all of your system files, the third will have your settings and personal files.  In the text installer you're going to have to tell it to mount the partition as "/home".  You should see how to do this when you select the partition.

Let me know if that's not clear enough, I'll try to elaborate.

You aren't going to need a lot of space for Ubuntu if you already have a larger drive with Windows on it, you should be able to play your mp3s/videos/etc directly off of the XP drive.

---

### Post by alba1314 on 2008-03-07
Thanks, Joeb - much appreciated!

\\:D/

---

### Post by Sef on 2008-03-07
> Text based install is harder to use if you need to be careful of the drives you use, whereas the standard install is a normal desktop loaded into RAM.

It is not hard to install using the alternate cd.   The only tricky part is partioning.  An excellent tutorial is the [Illustrated Dual Boot]("http://users.bigpond.net.au/hermanzone/").

---

### Post by Joeb454 on 2008-03-07
That's what I was trying to imply Sef ;)

---

### Post by alba1314 on 2008-03-07
Thanks Ecclesia.

I knew that installing Linux was going to be a learning curve, but I didn't realise that it would be so technical?!  I'd sure appreciate it if you could elaborate a little more and help me with a hopefully painless installation process.

Also, you mentioned that I will have to install "grub" on the D drive in order to dual boot..  I understand dual booting, but am at a loss as to what "grub" is?  Could you please explain it for me??  I assume that it is a procedure/option to boot directly into WinXP on my C drive OR Ubuntu on my D drive - is this correct?  :confused:

---

### Post by Sef on 2008-03-07
> Also, you mentioned that I will have to install "grub" on the D drive in order to dual boot.. I understand dual booting, but am at a loss as to what "grub" is? Could you please explain it for me?? I assume that it is a procedure/option to boot directly into WinXP on my C drive OR Ubuntu on my D drive - is this correct? 

GRUB stands for Grand Unified Bootloader.   It allows you to boot into either Windows or Ubuntu on a dual boot with both.  The default will be Ubuntu.  For more information on [GRUB]("http://www.gnu.org/software/grub/").

---

### Post by alba1314 on 2008-03-07
Thanks for the links, Sef!  I now have some extra reading to do tonight - looks like it's gonna be a late one for reading?!  :lolflag:

As that's the case, I'm gonna close down for the night and see how far I get with my homework...   But I'll be back soon to keep everyone posted on how I'm getting on?...

Good night, folks - and thanks for the help!!

---

### Post by Ecclesia on 2008-03-07
That's exactly what Grub does.  If you didn't have it your machine would only boot to Windows even with Ubuntu installed to your second drive.

You're right, it's a little more technical now during the installation - it's much easier if you're not trying to keep your Windows partition.  Since I don't have a lot of experience with dual booting, I'm probably not the person to ask.  Just want you to make sure you know what you're getting into.  There are a lot people who panic after having grub issues.  Since you're installing to a different drive you should be able to recover from it without much of a hitch if there is an issue. 

Hopefully your installation will run fine and you won't need to tweak it much to get things working.  Some people have issues with sound, wireless, or video.  If you do, just come back here and ask, chances are someone's gone through the same thing.  I've found the solutions to each of my issues by searching the forums. 

Enjoy your new OS!

---

