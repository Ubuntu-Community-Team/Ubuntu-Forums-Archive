---
title: "Grub in MBR or not?"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by kilou on 2006-11-28
Hi,

the question of where to place Grub has been asked several times but I still cannot find the right answer to my concern. It seems that by default Grub is installed in the Master Boot Record (MBR) but most people advise againt this when using a dualboot system.

I'd like to dualboot Ubuntu and XP. Ubuntu will be my primary OS and in the future I want to get rid of XP. I understand that when dualbooting it's OK and probably good to have Grub not installed in the MBR so that I may reinstall windows without breaking Grub (windows install rebuild the MBR I think). However when I will want to definitely get rid of XP on my system, what will happen if Grub is not in the MBR?? In a non-dualboot system, Grub is in the MBR anyway, right?

So:
- Why not place GRUB in the MBR? Even if I reinstall XP I can always rebuild the MBR for Grub.

- If I place Grub on the Ubuntu partition (not in MBR), what happens when I format my XP partition to get rid of it?

- If I install Grub in MBR and for some very unlikely reason want to remove Ubuntu from my system and only use XP, is there any drawback in using "format /mbr" command? Some people say it's risky....but why?

Thanks

---

### Post by Bachstelze on 2006-11-28
Go with GRUB in the MBR, it will work just fine.

---

### Post by anaconda on 2006-11-28
HymnToLife is right!

The command is fdisk /mbr and it is safe. You can also restore the orginal mbr by booting with windows CD and going to recovery console and typing fixmbr and fixboot..

And if you get rid of your winXP it wont affect your grub or mbr...

---

### Post by kilou on 2006-11-28
Yes the command is fdisk /mbr. But why do some people warn against using it?? What is the potential damage this command can do? And finally what is the advantage of having Grub not installed in the MBR?? I can't understand why this would be better...or safer.

---

### Post by bodhi.zazen on 2006-11-28
> **kilou said:**
> Yes the command is fdisk /mbr. But why do some people warn against using it?? What is the potential damage this command can do? And finally what is the advantage of having Grub not installed in the MBR?? I can't understand why this would be better...or safer.

I am glad to see this thread.

I come on the side of installing grub into the MBR.

Grub will not harm your hard drive or the MBR in any way. Grub is a one of the most versatile boot loaders and can boot Linux, Unix, and ahemm..  {cough....} wind{akk}ows.

I think the primary reasons some people advocate against this is likely due to multiple reasons and hopefully we will here from them soon ....

My first impression is choice. That is what is so wonderful about Linux, you almost have too many choices. Some prefer alternate boot loaders including LILO and the Microsoft boot leader.

Part of it may also be "fear". If GRUB is unfamiliar to you and you want to preserve your ability to boot windows, well GRUB may not seem like such a good idea. And yes, you will find examples on the forums where people have trouble with GRUB. so why take a chance? Why "fix something that is not broken" if you will.

I would echo what has been said by HymnToLife and anaconda, there is no need to fear GRUB will damage your system or leave your system un-bootable. The vast majority of problems are rapidly resolved, wither by configuring GRUB or re-installing the windows boot loader as has been explained by anaconda.

I have no problems with GRUB in the MBR and am currently configured to boot 13 OS. I no longer boot windows, but when I did GRUB gave me no problems.

With that said, I think the **most important advice** is to 


**[size=2]BACK UP your windows system and data !**[/size]

At the end of the day I think it all will come down to personal choice and not a matter of "safety".

---

### Post by xpod on 2006-11-28
> I think the primary reasons some people advocate against this is likely due to multiple reasons and hopefully we will here from them soon ....


The primary reason i reckon is most probably because they themselves have had\caused some issues with it then spent all sorts of time trying to suss it out that first time round???

The warnings i`ve seen about "fdisk \mbr" are just down to the "fdisk" command itself i think as i was given those same warnings when first learning about re-installing windows with my dusty i386 cd and a bootdisk all those months ago.

You get plenty warnings about what your doing using fdisk etc so it`s pretty hard to mess up when using it.

Just MHO.

---

### Post by kilou on 2006-11-28
OK guys you convinced me in installing Grub in the MBR. It appears to me there is no valuable reason not to do so because the MBR can be restored:
1) to "windows standards" with fdisk /mbr
2) to Grub with Booting from Ubuntu LiveCD and running some commands in the terminal to reinstall Grub.

I once installed Linux Mandrake + XP and after removing Mandrake from the system, I had a problem to boot the computer (don't really remember why though). Put fdisk /mbr out of a startup floppy and everything was cured! 

I'll probably just do a backup of the MBR (with MBRTool) before installing Ubuntu just to be safe.

Thanks for your great help !

---

### Post by kilou on 2006-11-28
Oh just another question probably related to GRUB in the MBR:

Now I have XP installed. I want to install Ubuntu and dualboot with XP but I'd prefer having Ubuntu on the first partition of my disk since XP will be secondary OS and I will get rid of it anytime in the future. Therefore Ubuntu would be best placed on the first partition and XP on the second (rather than the opposite in most dualboot systems) since I will be able to remove the XP partition without affecting the Ubuntu partition this way (otherwise Ubuntu would have been moved to be placed first after removal of XP).

So what I planned to do was to create a partition before my actual XP partition, moving XP to partition 2 (I can do that with Norton Ghost probably) and install Ubuntu on partition 1. But then does GRUB automatically detects that XP is on partition 2???

---

### Post by Bachstelze on 2006-11-28
Yas, why wouldn't it ? GRUB doesn't care which partition the OS is installed on.

And you don't need Ghost to move your Windows, GParted can copy partitions and it works pretty well.

---

### Post by kilou on 2006-11-28
Great! Thanks ALOT!!!!

---

### Post by Ben Sprinkle on 2006-11-28
I use LILO, I have had no problems dual booting either.
If you do want dual boot add these two lines to lilo.conf in /etc:
```

other = /dev/hda2
label = WindowsXP

```
May have no spaces between the = signs, I forget. :)

---

### Post by kilou on 2006-11-28
What's the difference between Lilo and Grub? Lilo is graphical and Grub is text?

---

### Post by Ben Sprinkle on 2006-11-28
Actually you have it backwards. LILO is ONLY text I believe as GRUB can be text OR graphical.

---

### Post by kilou on 2006-11-28
Oh OK, then I prefer going graphical -> Grub! Thanks.

---

### Post by Bachstelze on 2006-11-28
"Graphical" is a big word, you can just put a nice background picture if you want.

---

### Post by Ben Sprinkle on 2006-11-28
I prefer the ol' console text and mash setting. :)

---

### Post by steve.horsley on 2006-11-28
If I can wade in with another reason to put GRUB on the MBR: The Ubuntu installer is incapable of putting GRUB in the superblock of the root partition, which is what you would want to do if not installing it to the MBR. The alternate installer offers the option to do it, but it screws up royally, and leaves Ubuntu unbootable.

---

### Post by gn2 on 2006-11-28
Grub in MBR if it suits you, and you are fully up to speed with editing it and recovery methods.

Grub in the MBR of the Windows drive isn't essential, other options are available.

One of which is remarkably simple: [http://ubuntuforums.org/showthread.php?t=275728](http://ubuntuforums.org/showthread.php?t=275728)

Another is the option of installing PCLinuxOS direct to a USB hard drive with the (point-and-click) Draklive Installer.

Since I started the dual-boot on two drives thread, I have moved on from dual-booting on my main PC, I now use virtualisation with XP as guest in a Linux host.

Booted with a graphical LiLo.

---

### Post by Ben Sprinkle on 2006-11-29
Yeah, kilou, LILO can be graphical to some extent also.

SLAX for example has a bitmap.

---

### Post by jerrylamos on 2006-12-05
Xubuntu install onto 2G USB pen drive does not seem to have installed MBR correctly, after trying lots of things for the last couple weeks.

Some of the entries above suggest:

fdisk /mbr

which on my 6.06.1 LTS CDLive gets:

fdisk /mbr
unable to open /mbr

With ubuntu CDLive, what are the keystrokes to put an MBR on a USB pen drive?

By the way, I'm having no luck on putting CDLive on a 1G pen drive as suggested in WIKI, there's apparently no MBR on that one either.

And yes I've tried SuperGrub both the windows options and manual page suggestions.  I must be missing something.

Thanks much for anyone with any ideas to try.  Jerry

---

### Post by bodhi.zazen on 2006-12-05
> **jerrylamos said:**
> Xubuntu install onto 2G USB pen drive does not seem to have installed MBR correctly, after trying lots of things for the last couple weeks.

Some of the entries above suggest:

fdisk /mbr

which on my 6.06.1 LTS CDLive gets:

fdisk /mbr
unable to open /mbr

With ubuntu CDLive, what are the keystrokes to put an MBR on a USB pen drive?

By the way, I'm having no luck on putting CDLive on a 1G pen drive as suggested in WIKI, there's apparently no MBR on that one either.

And yes I've tried SuperGrub both the windows options and manual page suggestions.  I must be missing something.

Thanks much for anyone with any ideas to try.  Jerry

What is you are trying to do?

Install grub? If so, to the MRB or USB drive?

Or are you trying to restore you MBR to the windows boot loader?

---

