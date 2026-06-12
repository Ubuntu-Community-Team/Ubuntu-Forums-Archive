---
title: "Asus U56E Continually Rebooting"
date: 2012-07-07
forum: Asus Ubuntu Support (CLOSED)
---

### Post by cjsmall on 2012-07-07
I have an Asus U56E laptop that is configured for dual boot.  Windows 7 is installed on the sda2 partition (111 GB) and Xubuntu 12.04 is installed on sda3 (460 GB).  GRUB2, version 1.99 is the boot loader.

This machine came with Windows 7 pre-installed.  Originally I did a Ubuntu 11.10 installation and let Ubuntu repartition the drive.  I then installed xfce4 and other Xubuntu components.  Everything worked fine and the machine ran for a few months without problems, booting into either OS.  Later, I upgraded to Ubuntu 12.04, and the machine continued to properly boot into either OS.  I generally run Ubuntu and the laptop sits on my desk 99% of the time, continuously plugged into power.

A few months ago I noticed that the system was automatically rebooting itself at random intervals, usually when it was just sitting there not being actively used.  This could occur whether or not the screensaver was running.  I will hear a little click (sounds like a relay), the screen goes blank, and then it reboots. The frequency of these reboots has been increasing, but it is still very random.  Sometimes it will sit there for half a day before rebooting while other times it will reboot every 30 minutes or so.  What I have discovered is that it makes no difference whether it is Ubuntu or Windows 7 running.  The machine will reboot with about the same random frequency.

My initial thought was that this was a hardware problem -- possibly with an internal heat sensor that was shutting the system down.  This was further reinforced by the fact that it seems to be OS independent.  I took it in for service and after three weeks, it was returned with a report of no problem found.  I put it back on my desk and it rebooted withing 30 minutes!

Before I take it back in, I wanted to be sure that it wasn't something software related.  I have made sure that hibernate/sleep modes are off for both OSes.  The only thing that I can imaging both OSes sharing is the GRUB2 boot loader.  However, after boot is completed, I do not see how GRUB could be playing any further role.  A search of the web shows that other people have certain types of booting/rebooting problems with dual-boot Ubuntu configurations, but I have found nothing quite like my problem.

So my question is whether anyone has any ideas as to what may be responsible for this constant rebooting other than a hardware problem?  Any insights or suggestion you can offer would be greatly appreciated.  Thanks.

---

### Post by andyw8 on 2012-07-27
I am not running Ubuntu, just WIndows 7, but am having the same random powering off issue mid task. 

If you get anywhere in finding the solution I'd be grateful if you could let me know!

---

### Post by Kirboosy on 2012-07-27
Sounds heat related to me but I don't know for sure. Have you tried taking compressed air and blowing out the vents of the laptop? Maybe a dust bunny is caught in their sideways.


I was going to suggest a BIOS flash but I looked at the change log and nothing seems related to random power off issues. Its still worth a shot if your willing to try it.

Sorry I can't be of more help

---

### Post by cjsmall on 2012-07-27
Following up to my previous posts:

Since I was able to show that the problem was hardware and not software related (due to being OS independent), I took the unit back in.  They finally saw the problem and replaced the motherboard.  I got it back a couple of days ago and it is running like a champ once again.

Thanks for all the suggestions.  They were much appreciated.

Regards,
--
Jeff

---

### Post by ohyeah180 on 2012-08-07
hey csjmall

ive been having your exact problem for almost a year and i sent it twice and they said it was fixed but it wasnt

exactly what did you tell them that convinced them that it was a hardware problem?

im not good with computers at all so please tell me what to do. i have basically your exact problem.

thank you

---

