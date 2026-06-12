---
title: "Help"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by Squeaky G on 2006-07-13
Ok Ubuntu's managed to intrigue me and I want to try it, the problem is I only have on computer, which is running Windows XP, this computer is rather valuable to me because it has all of my personal files, schoolwork etc... I'm not willing to uninstall windows to install Ubuntu. I have a friend who is a bit more knowledgeable with computers (I would say i know a fair bit about them so if someone gives me a hand I shouldn't have too much difficulty) and he says that there shouldn't be too much trouble in running the two operating systems on the same computer. Can anyone tell me how I would do this? If it helps I'm running XP SP2 on a Dell Dimension 4550 (2.66GHZ P4, 512mb Ram, 60GB HDD)

---

### Post by Jagot on 2006-07-13
Have a look at these guides:

[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)
[http://psychocats.net/ubuntu/installing.html](http://psychocats.net/ubuntu/installing.html)

---

### Post by T700 on 2006-07-13
Let me suggest, nay, beg you--back up your data before attempting to dual boot.  99% of the time, there is no problem at all, but that's cold comfort if you're in the 1%.

A safer way to make your initial test drive might be to run Ubuntu off the Live CD.  You pop it in, reboot, and you're in Linux.  Take it out.  Reboot, and you're back to the flat, gray, sad, world of Windows.  :-)

Good luck and welcome!

Paul

---

### Post by Rumor on 2006-07-13
Using the 6.06 live CD, you can set up a dual boot system pretty easily. The part you want to watch for is the partitioning of your hard drive. You would want to use the option to resize the disk and use the free space for ubuntu. 

The install routine will detect your Windows installation and set up Grub so that both ubuntu and windows show in your list of boot options.

As was already mentioned, you will want to back up your critical files in windows in case you are in the 1% where something goes wrong. I have a dual booting Dell at my office. The install correctly identified my WinXP install and set up so that I can boot into Windows or Ubuntu without any problems.

Good luck! Let us know how it turns out for you.

---

### Post by bschmiduk on 2006-07-13
I'm a recent convert myself - here was my plan of attack:

I went and bought a bargain Hard Drive, and cloned my old drive.  Then I installed the dual-boot Ubuntu to the clone (with the original drive safely disconnected and put into storage).

No worries.  Even if it went completely bad (that 1%) I could just pop the original drive back in and I'm golden.  I could even re-clone the cloned drive and start over.  It was an $80 insurance policy - well worth my peace of mind.

BTW - install on the cloned drive was quick and painless.  I've not even started XP for the past 2 weeks.

---

### Post by Squeaky G on 2006-07-14
> **Rumor said:**
> Using the 6.06 live CD, you can set up a dual boot system pretty easily. The part you want to watch for is the partitioning of your hard drive. You would want to use the option to resize the disk and use the free space for ubuntu. 

The install routine will detect your Windows installation and set up Grub so that both ubuntu and windows show in your list of boot options.


Ok I just about get that and i'm using the live CD to run ubuntu atm, however how do i partition the hard drive - is there an easy way of doing it on the ubuntu end of things, because doing it in XP seems just about complicated. When you say "The install routine will detect your Windows installation" do you mean i can just install ubuntu straight off the CD and it does it for me? Also what's Grub. Sorry about all the questions but I've never done this before.

---

### Post by bschmiduk on 2006-07-14
I've only done this once, so I'm far from expert.... but here is how it went for me (on the COPY of my main drive, remember??  Insurance policy??)

I booted from the LiveCD, clicked on the "install" desktop icon, and followed the prompts.  It walked me through the GPARTED Linux partition manager that let me resize my XP partition to make room for:
(1) Main Linux partition (ext3)
(2) Small Linux swap partition (ext3)
(3) XP-Linux shared partition (FAT32)

Then it partitioned/formatted my choices, copied files, rebooted and.... that was it.  It was an order of magnitude more simple than installing XP (either from scratch or as an upgrade).

GRUB is the boot loader program that gives you a startup choice to go to XP, Ubuntu, or any other operating system you may have installed.

---

### Post by Rumor on 2006-07-14
> **Squeaky G said:**
> Ok I just about get that and i'm using the live CD to run ubuntu atm, however how do i partition the hard drive - is there an easy way of doing it on the ubuntu end of things, because doing it in XP seems just about complicated. When you say "The install routine will detect your Windows installation" do you mean i can just install ubuntu straight off the CD and it does it for me?

What I would recommend is firing up the installer. It will start by asking you some very basic questions:
1. Your language
2. Your time zone
3. Your keyboard layout
4. Your personal data
Then the partitioner will load. You'll be given up to three choices (if memory serves). The choices will be (in no particular order) 
(A) Erase the entire disk and use it. 
(B) Resize the partition and use the freed space.
(C) Manually edit the partition table.

You DO NOT want to erase your whole hard drive, so don't choose that option. You should either choose to resize the partition and use the free space or manually edit the table. The easier option is to let Ubuntu resize it automatically for you. In my experience, it splits the space about in half so you'd have 30 gigs (roughly) for Ubuntu and 30 gigs for Windows.

Load up the installer and get to this step. COme back and tell us what your menu options are for partitioning if you don't feel comfortable proceeding. To this point in the install, you have not changed anything on your computer. You've just answered questions.

If you choose to proceed, you'll be given a summary screen that tells you what the installer is going to do and then you can do it. During the install, Ubuntu will look for other operating systems on your computer. It will find Windows and set it up so that you can boot into Ubuntu or Windows using Grub.

> **Squeaky G said:**
> Also what's Grub. Sorry about all the questions but I've never done this before.

Grub stands for Grand Universal Boot loader if I am not mistaken. It is a text menu at your start up that shows all your operating systems/boot options. By default, if you do nothing, you'll boot into your Ubuntu install. Windows will be located at the bottom of the list. You can select any option using your cursor keys and pressing enter at the desired boot option.

---

