---
title: "editing boot.ini for proper start up"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by MEB202073 on 2007-11-18
I am having problems with my dell 1505 booting up right and instead ggoing into windows.


I checked the boot.ini  and this is what I have.

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

c:\wubildr.mbr="Ubuntu-Linux"


What I should have is a c: and an e: drive from a windows point of view.

I am using th cd unbuntu right now since the install of unbuntu, because of the boot up is working right.

What other files need some editing besides boot.ini?

---

### Post by MEB202073 on 2007-11-18
I am having problems with my dell 1505 booting up right and instead ggoing into windows.


I checked the boot.ini  and this is what I have.

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

c:\wubildr.mbr="Ubuntu-Linux"


What I should have is a c: and an e: drive from a windows point of view.

Two primary partitions of C: windows and E: Linux.

I am using th cd unbuntu right now since the install of unbuntu, because of the boot up isnt working right.

What other files need some editing besides boot.ini?

---

### Post by celticbhoy on 2007-11-18
When GRUB loads what options are available to you???

---

### Post by wydra on 2007-11-18
Have you tried repeatedly tapping the f8 key during startup? I think that will give you the option for the OS... I can't remember though.

---

### Post by oilchangeguy on 2007-11-18
> **wydra said:**
> Have you tried repeatedly tapping the f8 key during startup? I think that will give you the option for the OS... I can't remember though.

this will not give you an option to boot into ubuntu.

---

### Post by oilchangeguy on 2007-11-18
> **MEB202073 said:**
> I am having problems with my dell 1505 booting up right and instead ggoing into windows.


I checked the boot.ini  and this is what I have.

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

c:\wubildr.mbr="Ubuntu-Linux"


What I should have is a c: and an e: drive from a windows point of view.

Two primary partitions of C: windows and E: Linux.

I am using th cd unbuntu right now since the install of unbuntu, because of the boot up isnt working right.

What other files need some editing besides boot.ini?

you do not change the boot.ini file. please explain if you're trying to dual boot. and how you installed ubuntu. the ubuntu version. and your computers specs.

---

### Post by MEB202073 on 2007-11-18
Well, I do not know my computer specs other then dual intel processers, a large multi partitioned gigabyte hard drive, a screen, mouse and a keyboard with wifi internet.

Otherwise, I would of posted them.

What I did is installed 7.10 ubuntu by live cd on the free space I clear from media direct.


Okay, it seemed to install.


But when I reboot, some dell software give me grief about reboot, systems check, or systems setting, and no choice on what system to choose.

And using LIve CD doesn't find ubuntu on the hard drive either.

Could you please explain what is a dual boot is?

All I understand is that I do not have a menu on start giving me a choice on what system I would like to use.

And from looking at the boot.ini (which I have no idea how it works)  seems to be looking for the wrong OS in the wrong partition.

---

### Post by MEB202073 on 2007-11-18
I get a dell windows boot up instead.

Or at least, an attempt.

And I don't known almost anything about a laptop other then point move and tap.

Plus typing with one hand.

But that doesn't deal with grub then, does it?

WHat is grub by the way and how do I find it?

---

### Post by mike555 on 2007-11-18
It looks like you used Wubi to install Ubuntu , it installs to the c drive , inside Windows ......... can't you arrow down during boot , and boot into Linux ?    (you do need to do it fast -within 15 seconds)

---

### Post by MEB202073 on 2007-11-18
Could you please explain on what you mean by 'arrow down'?

Is that by using the down arrow key?
Also, what other files could I post that could help you figure out what is going on with my start up?

---

### Post by oilchangeguy on 2007-11-18
could you please explain why you've started another thread on the same subject!
[http://ubuntuforums.org/showthread.php?t=616742](http://ubuntuforums.org/showthread.php?t=616742)

---

### Post by MEB202073 on 2007-11-18
I don't know.

Must of been a double post.

---

### Post by mike555 on 2007-11-18
> **MEB202073 said:**
> Could you please explain on what you mean by 'arrow down'?

Is that by using the down arrow key?
Also, what other files could I post that could help you figure out what is going on with my start up?

  When you first start your computer you should get a choice of which to boot , Windows is default, so if you arrow down using the arrow down button , Linux will highlight , then hit the enter button (you must be quick, so be ready)

---

### Post by MEB202073 on 2007-11-19
okay, will do that.

I'll update you when I am done.

thanks.

---

### Post by dgray_from_dc on 2007-11-19
> **MEB202073 said:**
> 

. . .

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

. . .



You may also want to increase the number on timeout=xx

That's the amount of time the menu gives you until it goes to the default choice.  I find that on my Dual-Boot systems (By the way, Dual-Boot means booting two operating systems e.g. Windows and Linux) 30 seconds usually suffices.

> **MEB202073 said:**
> WHat is grub by the way and how do I find it?

Grub stands for **Gr**and **U**niversal **B**ootLoader.  It's a program that sits on the master boot record or MBR (the first thing that the PC looks at when it's trying to boot) and gives you a selection of which operating system to use.  If installed, it would sit in front of windows and Boot.ini would no longer control how your system boots.  I find that it's the better way to go.  However, I know nothing of Wubi.  It just seems better and cleaner to start Linux on its own rather than from within Windows.

---

### Post by tyggna1 on 2007-11-19
Best advice anyone could give at this point--I think, is to start over.

Run chkdsk /r in windows to make sure there are no errors on your hard drive, and then Download a live CD, boot from it (by pressing F12 at the Dell logo and using the arrow keys on your keyboard to select an option with CD-ROM or DVD in the name).

From there, just install Ubuntu where you want to, and then GRUB will take over the way the computer boots.   Grub is just a program that manages the way the computer boots, and will help you dual boot (i.e. have both windows and Ubuntu installed, and allow you chose which one you want to run everytime the computer boots).

---

### Post by Duck2006 on 2007-11-19
This is good reading.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

