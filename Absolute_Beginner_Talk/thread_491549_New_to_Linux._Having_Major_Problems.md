---
title: "New to Linux. Having Major Problems"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by Andy_Drainz on 2007-07-03
well i recently got a ubuntu disk in the mail and was super excited. i have been useing a windows pc all my life and have always wanted to learn linux and when a friend referred me to ubuntu as a good way to learn i was excited, especially since i have been useing Windows vista and having problems with it. so i found a computer from a friend that they were not useing and they let me have it. 

so i cleaned the hard drive, it was running windows 95. deleted the partitions and all the good stuff like that. then i put the ubuntu disk in. the main screen loads up and i am excited.  then i click install and it loads and does its thing. it boots for about 2 minutes on the ubuntu "loading" bar then the screen goes blank and i get a whole mess of messages that look similar to this

"[173.52263] Buffer I/O error on device hdc, Logical block 0 (sometimes its a 1 or a 2)
  hdc: error code: 0x70 sense_key: -x-3 asc: 0x11 ascq: 0x00"

it does a whole heap of those messages with number variations in the begining... then i get this message after about 4 or 5 minutes of thos emessages that says 

"Busy Box v1.1.3 ( Debian 1:1.1.3-3ubuntu3) Built in shell (ash)
  Enter 'help' for a list of built in commands

  /bin/sh: can't access tty; Job control turned off

 (initramfs)_ "

it prompts me to type commands from "(initramfs)" what is that? why wont it install? 

so i tried to boot without any disks in my drives and i get this

"3com pxe, version 0.99j.03
 Compright blablabla..............

 PXE-E61: Media Test Failure, check cable.
 PXE-MOF: Exiting PXE"

would that have anything to do with why i cant install linux? what does it mean? any help with this would begreatly appreciated... i want to break free from the chains of microsoft and the horrible vista. 

Here is all the info i can get from this pc:

System: Dell Optiplex GX1 450MTbr+

Pentium III Processor- 450 mhz
Level 2 cache: 512 kb Intigrated
System Memory: 256mb ECC SDRAM
almost a 10gb HD
CD Drive
Floppy Drive
USB ports

Please help this noob

---

### Post by Moop on 2007-07-03
I think that message just means it can't find anything to boot from and it tries a network boot as a last resort. 

I'm not sure what your other problem is. Did your cd come with memtest on it? Have you tried running that? Is it a live cd your trying to boot from?

---

### Post by lemonseed on 2007-07-03
Maybe since it is an older machine, try Xubuntu? I'm still fairly green to Ubuntu but I think that is meant for older machines..

Also, your friend gave away his old computer to you maybe because it was broken to begin with and they just dumped it off onto you?

---

### Post by Jimmyfj on 2007-07-03
To me it looks like you have a faulty hdd - The numbers you get with reference to hdc shows that something went wrong at the disk. Second the PXE error you get could be from a network card set to boot from a network server. The first you should do is to alter the BIOS and load factory default BIOS setup. If the system runs well on the live disk it indicates that the disk might be faulty.

---

### Post by bsell on 2007-07-03
> **lemonseed said:**
> Maybe since it is an older machine, try Xubuntu? I'm still fairly green to Ubuntu but I think that is meant for older machines..

Also, your friend gave away his old computer to you maybe because it was broken to begin with and they just dumped it off onto you?
 
You probably need to use the alternate install CD. The LiveCD install uses more system resources

---

### Post by dwanders on 2007-07-03
With the new Ubuntu disks (and I would agree XUbuntu might be better for the older hardware & low RAM) you should be able to completely boot into the Ubuntu Desktop prior to installing anything. Then clicking the Install Icon on your desktop should install it. Tha first boot into the live CD is a very good test to see if your Hardware is going to be problematic. 

Do you know what version of Ubuntu your trying to install? And if you have a high speed Internet access (or can get to one), it might be worth your while to download and try the XUbuntu 7

[http://xubuntu.org/get](http://xubuntu.org/get) 

While Ubuntu seems to work on less RAM (like 512), I prefer to run at least a Gig and a P4 for full Gnome/KDE. I use Xubuntu to build Linux Kiosk's on really old hardware PII or better with minimal RAM 128-256.

---

### Post by popch on 2007-07-14
I had the same messages (Busy box) when I tried to install ubuntu linux 7.04 on a dell optiplex sx260. However, installing ubuntu linux 6.10 worked flawlessly.  Upgrading to ubuntu linux 7.04 posed no problem thanks to fast internet access.

---

### Post by randytuggle on 2007-07-14
I has this sort of problem (on my laptop) and found out that I was overheating the system in a short time. Let it cool off and once you can log in, change the power management settings to run at a slower speed (conserve energy) and see if that helps.

---

### Post by popch on 2007-07-14
After some more experimentation using elderly hardware, here's my two cents of opinion:
- It is somewhat possible that your CD drive does work but is not supported by Feisty.
- Indeed, this appears to be the problem with my own Dell PC, which is, however, a somewhat more recent vintage than yours is.
- The message 'can't access tty; Job control turned off' seems to be the salient part of your problem description. There appears to be a largish number of users who have encountered this message, albeit for different reasons. As far as I can make out, the message seems to be written when the first part of Linux (the Kernel) has been loaded off the CD, and this part wants to read more files off the CD. The first part is read using the functions of the Bios built into the PC, and then the Kernel tries to read the rest using its own software.
In my case, ubuntu 6.10 works fine, while 7.04 does not, quite.

---

