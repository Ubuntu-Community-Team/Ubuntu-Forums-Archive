---
title: "Will ubuntu work on my old computer"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by afflusso on 2006-08-26
I'm hesitant to try to install it on my current Windows XP machine, but I have an old Gateway 2000 that I want to try it on. It has a 4 GB hard drive, with Windows 98 already installed on it. It runs Windows really really slowly, so I don't care about saving anything on it. Is it worth burning a CD to install ubuntu on this computer? I have no experience at all with Linux, but I like to think I'm good with Windows. 

So, simply, do you think I will get ubuntu running on this computer, and will it work quickly?

---

### Post by calvinthomas on 2006-08-26
Your best bet would be to use Xubuntu, its apparently much better on older machines!

Calv

---

### Post by Bachstelze on 2006-08-26
Maybe even XFCE will be a little heavy for a machine that old, I think Fluxbox will be better.

---

### Post by az on 2006-08-26
> **afflusso said:**
> I'm hesitant to try to install it on my current Windows XP machine, but I have an old Gateway 2000 that I want to try it on. It has a 4 GB hard drive, with Windows 98 already installed on it. It runs Windows really really slowly, so I don't care about saving anything on it. Is it worth burning a CD to install ubuntu on this computer? I have no experience at all with Linux, but I like to think I'm good with Windows. 

So, simply, do you think I will get ubuntu running on this computer, and will it work quickly?

You probably have a small amount of ram on it.  You will be best to have 128 megs or more for Xubuntu and 256 megs or more for the regular Ubuntu.

Don't use the Desktop cd, use the alternate cd for installation - you don't have enough ram and it will be terribly slow.

---

### Post by afflusso on 2006-08-26
What if I have less than 128 ram? I'm not sure exactly how much I have. I know the model can have from 96-128 mb ram. Is Xubuntu my best bet then? Also it's a pentium II.

---

### Post by Bachstelze on 2006-08-26
I think your best bet is Fluxbox. See [here](https://help.ubuntu.com/community/Fluxbox) for details on how to install it.

---

### Post by muep on 2006-08-26
96 might be tolerable, but luckily 128 is much more common.

If you have only 64 MBs, you might want to check Damn Small Linux. It is far away from Ubuntu in features, but it is quite easy to use and works very well even with as little as 32 MBs.

If you want to use Ubuntu, Xubuntu would work, but it would be slow. If you have 128 MBs, Xubuntu should work a lot better, it would be usable, at least.

---

### Post by afflusso on 2006-08-26
Thanks for your replies. I'll try to see which one might work best, but DSL looks like it might work. Is Fluxbox likely to work pretty fast as well? I probably just want to use it to at least surf the net and match small videos.

---

### Post by CREEPING DEATH on 2006-08-26
Xubuntu will work with 64 MB, but requires 128 MB for the graphical installer.

CD

---

### Post by Jerome36 on 2006-08-26
> **afflusso said:**
> What if I have less than 128 ram? I'm not sure exactly how much I have. I know the model can have from 96-128 mb ram. Is Xubuntu my best bet then? Also it's a pentium II.

My Linux box is a 350mhz Pentium II, with 192mb of RAM, and a 4gig hard drive (which is dying but I'm replacing once I get the new one).  You should be able to see how much RAM you have either via the BIOS or in Windows 98.  You'll probably want to go with Xubuntu, but there are some other great Linux Distros out there, for really low-end machines.

---

### Post by PrawnEater on 2006-08-26
> **Jerome36 said:**
> ...  You'll probably want to go with Xubuntu, but there are some other great Linux Distros out there, for really low-end machines.

What other distros are suitable for low-end machines? I too have an old gateway 2000 heap.

---

### Post by Jerome36 on 2006-08-26
Well [Damn Small Linux](http://www.damnsmalllinux.org/) (DSL) immediately comes to mind.  There's also [Puppy Linux.](http://www.puppyos.com/)  Here's [an article](http://distrocenter.linux.com/article.pl?sid=06/02/13/1854251&tid=127&pagenum=1) on Linux for older hardware.

---

### Post by afflusso on 2006-08-26
I checked on startup and it looks like my computer is 32MB ram. A lot lower than I thought. But I did get DSL loaded onto it, and it was working pretty well for a while (a little slow maybe) but now the screen is frozen. Does anyone know if I have to have the CD and floppy in all of the time when I use DSL?

---

### Post by uph0ria on 2006-08-26
My computer is lightning fast, here's my specs:

-Pentium 3 Processor
-360MB RAM
-Blackbox GUI
-Netgear Wireless-G

I installed Ubuntu "Dapper Drake LTS" and then followed this guide [http://www.ubuntuforums.org/showthread.php?t=125084](http://www.ubuntuforums.org/showthread.php?t=125084) to install the Blackbox GUI. Good luck!

---

### Post by shamrock_uk on 2006-08-26
> **afflusso said:**
> I checked on startup and it looks like my computer is 32MB ram. A lot lower than I thought. But I did get DSL loaded onto it, and it was working pretty well for a while (a little slow maybe) but now the screen is frozen. Does anyone know if I have to have the CD and floppy in all of the time when I use DSL?

DSL is a little thin on the ground for a full-time distro in my opinion, but no, once you do the hard drive install you effectively have a tiny Debian distro and can remove the livecd. You can also use the Debian repositories to add applications easily.

You could try [Zenwalk](http://zenwalk.org) which flies on my slow laptop. It does use xfce so maybe 32MB is too little, but might be worth a try if you have bandwidth to burn. 

I'm always surprised that we really have to resort to fluxbox on older computers. I remember running Windows 95 on 8MB with no problems, but getting a graphical interface with equivalent functionality under Linux is apparently not possible.

---

### Post by afflusso on 2006-08-26
When I take out the CD it just loads regular Windows, so I think I am using the wrong type of CD maybe. It works OK when I load it, but **after 5-10 minutes it always freezes** and I have to pull out the power cord, which I hate doing. I think it is running directly off of the CD, because that might explain it. 

Does anyone know where I can go to get the right CD and what my problem might be?

---

### Post by shamrock_uk on 2006-08-26
> **afflusso said:**
> When I take out the CD it just loads regular Windows, so I think I am using the wrong type of CD maybe. It works OK when I load it, but **after 5-10 minutes it always freezes** and I have to pull out the power cord, which I hate doing. I think it is running directly off of the CD, because that might explain it. 

Does anyone know where I can go to get the right CD and what my problem might be?

:confused: Surely you can just use the power button at the front? Yanking out the cord is always a last resort...I hate that little 'gzzzt' sound.

It sounds to me like you haven't actually installed DSL on your hard drive. The livecd you boot off is just running from RAM and you need to actually install it like you would Ubuntu. Then, when the CD is out, you would get a bootloader screen.

Why it's freezing after 10 mins is a separate issue.

I'm almost tempted to say start with Debian Sarge and do a very small install of that. You can then just apt-get install fluxbox and let it do the work. Can't help feeling that you'll encounter less problems this way than you would with DSL.

---

### Post by afflusso on 2006-08-26
> **shamrock_uk said:**
> :confused: Surely you can just use the power button at the front? Yanking out the cord is always a last resort...I hate that little 'gzzzt' sound.

I'm almost tempted to say start with Debian Sarge and do a very small install of that. You can then just apt-get install fluxbox and let it do the work. 

The power button doesn't do a thing. I hate to pull the plug, but there was no other way. The CD drive wouldn't open either.

I don't have many CD-R's, so I am going to wait until I figure out which one should work before I try burning the iso. (Can I write over/reuse a previously burnt CD?)

Anyone have an idea of what I should try? Thanks so much for your replies.

---

### Post by pollenmail on 2006-08-26
I'm trying to run/install Ubuntu on a Compaq Armada E500 with 128 meg of RAM and a 10 gig HD (I think.)


I'm using the disk out of the back of The Official Guide to Ubuntu book. 

I make it to the Ubuntu logo and while Nautilus is installing, the machine hangs. I let it continue to hang--you can hear the HD or DVD trying to read/write--but after a few minutes the screen goes black](*,) . I've tried the first install option and the safe graphics install mode. 

Suggestions?

---

