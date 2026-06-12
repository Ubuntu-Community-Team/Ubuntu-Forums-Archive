---
title: "Pre-install questions..."
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by User X on 2007-07-06
Hey Everybody!  I am going to try Ubuntu on my computer at home.  This will be my first real attempt at a Linux OS so please be easy on me if I don't understand some of the chat around here.  Here are my questions (lots of em'!):

I have a VIA KT890/VT8232 chipset on my motherboard, and it has a SATA Raid1 Array - will Ubuntu support this?

How about my Realtek AC97' Audio?

There are Linux audio drivers on the manufacturers website, these should work in Ubuntu?

If I install the 64bit version of Ubuntu am I limited to 64bit software, or will 32bit software work as well?

I have one of the dreaded ATI X... video cards, and the FAQ says to use the alternate install disk for Ubuntu - whats that?

Thanks for any help on my initial questions.  I look forward to visiting this forum more often!


** EDIT **   Yay!  I got a bean!

---

### Post by Lolicon on 2007-07-06
Try the LiveCD and see how well it works.

---

### Post by overdrank on 2007-07-06
> **User X said:**
> Hey Everybody!  I am going to try Ubuntu on my computer at home.  This will be my first real attempt at a Linux OS so please be easy on me if I don't understand some of the chat around here.  Here are my questions (lots of em'!):

I have a VIA KT890/VT8232 chipset on my motherboard, and it has a SATA Raid1 Array - will Ubuntu support this?

How about my Realtek AC97' Audio?

There are Linux audio drivers on the manufacturers website, these should work in Ubuntu?

If I install the 64bit version of Ubuntu am I limited to 64bit software, or will 32bit software work as well?

I have one of the dreaded ATI X... video cards, and the FAQ says to use the alternate install disk for Ubuntu - whats that?

Thanks for any help on my initial questions.  I look forward to visiting this forum more often!


** EDIT **   Yay!  I got a bean!

Hi and welcome, I have installed ubuntu on sata raid system and it was no problem, this link may help
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
As for you sound this thread may help also
[http://ubuntuforums.org/showthread.php?t=32020](http://ubuntuforums.org/showthread.php?t=32020)
I would say stick with the 32bit it works just fine.
What ati card do you have, you could search the forum here and see what pops up.

---

### Post by User X on 2007-07-06
Lolicon, thanks for the response - is that the 700Mb file @ Ubuntu.com?  I have downloaded that and burnt it to a disk.  I even booted to it, and played a bit.  Is this what you are referring to?  

You call it the "Live CD" - Do you know what the "Alternate CD" is?

Thanks in Advance!

I have the X1600 Pro installed, and a spare X700 Pro

The computer is an:
AMD Athalon 64 4000
ATI X1600 Pro Video Card
Onboard AC97' Audio
DVD DL Burner     -     Hey is there support for DL disks?
DVD Rom
2x 200gb SATA WD Caviar drives in raid1
1x 60gb. ATA100 IBM Deskstar drive (I had it laying around)
3.5" floppy
Conextant DV/TV tuner card (I am not heck bent on getting this to work - although Video Capture would be nice)

---

### Post by twiceasworn on 2007-07-06
the alternate cd is merely a text based installer.  I installed ubuntu on my desktop with an ATI X1300 card and went flawlessly.  If the LiveCD is working for you fine, go ahead and install.  You shouldn't run into any problems.  Once you get the OS installed, thats really when the fun begins.

---

### Post by User X on 2007-07-06
Not to doubt your knowlege but you only have 13 beans (just kidding)!  You think it will work?  I may just give it a go this evening.  Where do I get this text based installer?

---

### Post by az on 2007-07-06
> **User X said:**
> Not to doubt your knowlege but you only have 13 beans (just kidding)!  You think it will work?  I may just give it a go this evening.  Where do I get this text based installer?

I don't know what you mean by needing the alternate installed because of an ATI card.  If the live cd boots and you see the desktop, there is no problem.  The text installer is slower and will not install anything different.

---

### Post by twiceasworn on 2007-07-06
> **az said:**
> I don't know what you mean by needing the alternate installed because of an ATI card.  If the live cd boots and you see the desktop, there is no problem.  The text installer is slower and will not install anything different.

exactly.  But if he wants to play it safe with the alternate, let him.  It certainly wont hurt anything.

---

### Post by djchandler on 2007-07-06
Your motherboard and audio chipsets will be fine. I go along with az. If you can see the desktop with the trial/installer CD, you should be able to install from it just fine. If you are needing support for 3D graphics, that may be another matter. Make it easy on yourself and ease into Ubuntu. You can solve any other problems once you are up and running. Just come back to the forums for help before you can't get into the GUI if you are not comfortable with fixing things from the command line interface (text only). It is my understanding that ATI has a proprietary driver, i.e., not licensed under any of the FOSS approved licensing standards or Canonical, that you can download after Ubuntu is running. Pay attention to discussions involving ATI (now owned by AMD) and Xorg. ;)

DJ

---

### Post by az on 2007-07-06
> **twiceasworn said:**
> exactly.  But if he wants to play it safe with the alternate, let him.  It certainly wont hurt anything.

Live cd = 30 minutes to a full install.

Alternate cd (in this case) = a few hours to download plus a few hours to install.


> **djchandler said:**
>  It is my understanding that ATI has a proprietary driver, i.e., not licensed under any of the FOSS approved licensing standards or Canonical, that you can download after Ubuntu is running. Pay attention to discussions involving ATI (now owned by AMD) and Xorg. ;)

DJ

ATI cards are supported by the kernel.  Some newer cards require a proprietary driver that ships with Ubuntu, but is not installed by default.  A bleeding-edge card may require a download to use the most advanced features, but those cards are not common.

---

### Post by User X on 2007-07-06
Thanks for all the help guys!  This is a good fast moving forum!  Ok well I will be back I'm sure!

---

