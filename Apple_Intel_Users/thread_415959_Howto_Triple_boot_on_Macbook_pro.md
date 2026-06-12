---
title: "Howto: Triple boot on Macbook pro"
date: 2007-04-20
forum: Apple Intel Users
---

### Post by michaels on 2007-04-20
Hi , guys!

This is my mini howto about triple boot (OS X, Feisty & WinXP) on my Macbook pro, in which I include the solutions working for me and some of my successful experience. As a not so professional user, I understand the feeling when something gets in a mass. So I try my best to write these instructions as simple as possible.

[[COLOR="Blue"]This link is here[/COLOR].]("http://www.cs.helsinki.fi/u/jzshen/install_feisty.html")

I hope it would help you or give you a good reference!

Thanks all here ! & Cheers for Ubuntu!
:guitar:

---

### Post by ronocdh on 2007-04-20
Very valuable!! I haven't been able to start gdm either, and it's been driving me nuts. Rebooting now to try your method of installing fglrx before even getting into the GUI.

Durr, should have thought of that myself. ;)

---

### Post by ronocdh on 2007-04-20
It works. I'm booted into 64-bit 7.04 right now, on my MacBook Pro! Thank you, sir, for the simplest, most insightful fix I've seen in a while!

:guitar:

---

### Post by stickboy3k on 2007-04-20
Thank you for taking the time to type that up :) That's almost exactly how I got my triple boot working and I was going to write my first howto but you've saved me the typing :)

Wish I wouldn't known about installing grub to the hd0,2 before, I ended up getting it on the mbr, then installing on hd0,2, then using Vista's bootrec /fixmbr to remove grub from the mbr.

Thanks again, that's awesome :)

---

### Post by michaels on 2007-04-22
One more thing to mention, during the first time of file system checking, there maybe some error. However, it will be fixed automatically and won't appear any more.

Good Luck Everybody!

:popcorn:

---

### Post by rjc on 2007-04-22
Does this also work somehow if windows with bootcamp is already installed?

---

### Post by ronocdh on 2007-04-22
> **rjc said:**
> Does this also work somehow if windows with bootcamp is already installed?
It's been awhile since I set up my triple boot configuration, but I believe the Boot Camp partition utility only supports creation of one additional partition. This means that to create a third for Ubuntu, you'd have to partition using the terminal in OS X, a process which would likely destroy your existing XP partition.

The way I did it was partition via terminal in OS X, then install Windows on the fourth partition, update it using the drivers CD burned in Boot Camp, then I installed Ubuntu on the third partition. (First should be occupied by [rEFIt]("http://refit.sf.net"), I think.)

---

### Post by michaels on 2007-04-22
It depends on your current partition table. 

If you have one free partition on which no operating system is installed, you could install Linux directly! Nothing special you need, just follow the instruction.

And If you don't have it, the problem is quite complex. Because I haven't tried it, what I can give you is some suggestion. First you should resize one of the current partition with the OS X build-in diskutil command, (read its  manual to learn how to do it), personally, I advise to resize the OS X partition. Then you can try to follow this howto. Remember! The most important thing is the balance of MBR and GPT! Though I don't use rEFIt to finally synchronize them, these two things are still synchronized! You could do some googling to get the explanation of them and understand how bootcamp works.

Good Luck!  :KS

---

### Post by skwid on 2007-04-22
Maybe I am just slow but when I bootup off the Fiesty CD I get stuck on the F6 Part.  No keyboard input is working?

---

### Post by michaels on 2007-04-22
Have you check the md5 sum of your CD?

Try to download a new one and burn it with a relatively slow speed.

---

### Post by ronocdh on 2007-04-22
> **skwid said:**
> Maybe I am just slow but when I bootup off the Fiesty CD I get stuck on the F6 Part.  No keyboard input is working?
What is the F6 part? Is that something to change the settings before you boot into the Live CD? Personally I rarely have keyboard response during the live CD, same goes for GRUB, I suspect it's an issue with EFI instead of BIOS, but I'm not certain.

If you are booting the live CD, it should count down from 30 seconds and take you right into "Install Ubuntu," and your keyboard should respond in the GUI installer.

---

### Post by michaels on 2007-04-23
Could some one tell me his keyboard mapping situation? My Fn key isn't detected, but the function keys works really well, which means at a cost, I can't use F!1-- F10 and I can't switch to the console mode!

Is there some way to fix it?

---

### Post by ronocdh on 2007-04-23
> **michaels said:**
> Could some one tell me his keyboard mapping situation? My Fn key isn't detected, but the function keys works really well, which means at a cost, I can't use F!1-- F10 and I can't switch to the console mode!

Is there some way to fix it?
Yes, I too am irritated that the F keys don't behave as F keys, rather they only have the specialized context of brightness (which doesn't even work for me, though it displays a cute little box onscreen) or volume. I know that by reconfiguring xserver-xorg, one can choose a keyboard layout, and among the choices are "Mac" and "Mac laptop." (Maybe it's "Apple" and "Apple laptop," I don't remember.) Perhaps this would cure what ails us?

---

### Post by michaels on 2007-04-23
Thank you for you reply. However, I've one more serious problem that today I notice that my macbook pro start to whine again!!! You know, it even doesn't whine in OS X. 

Do you have the same problem? or do you do how to fix it? Is it the problem of the Ubuntu kernel?

---

### Post by ronocdh on 2007-04-23
> **michaels said:**
> Thank you for you reply. However, I've one more serious problem that today I notice that my macbook pro start to whine again!!! You know, it even doesn't whine in OS X. 

Do you have the same problem? or do you do how to fix it? Is it the problem of the Ubuntu kernel?
That's very interesting! I notice on your blog you say you have a Core Duo, which were the ones with the whining problem back in the day. I guess the fix Apple released was a software thing in the OS, and not any kind of firmware update (which should carry over to hardware behavior in Linux).

=/ Don't know what to tell you. I've never had a whine on my C2D, although I do recall the fans screaming at me as I tried to run Beryl with errors filling up the terminal. ;)

---

### Post by Mattybook on 2007-04-24
i don't have an internet connection when installing this linux so the part in the tutorial where you ave to apt-get the driver won't work so i can't continue ... 

i tried with wired and wireless, both had no succes
any ideas how to fix this?

---

