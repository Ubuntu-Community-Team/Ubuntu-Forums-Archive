---
title: "After using Smart Boot Manager on the Xubunta dvd it still won't boot"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by mhpriest on 2008-03-19
I have a Compaq PII, 128MB RAM & 3.7GB HD.   I use to use it for a firewall using "Smoothwall," a linux platform which booted up fine.  I also use with "PartedMagic" which boots up fine, another linux PF.

I really wanted to try Ubuntu out and decided on the Xubunta-Alternate version because of hardware constraints.  The disk boots up from my laptop (XP/VISTA).

I read as many forums as I could over the last couple of weeks and thought I'd try the SmartBootManager.  When I boot up with the floppy and Xubunta CD in place, I get the screen with the CD option and save.  Then I try booting up with just the CD and it fails.

Does anyone have any other ideas I could try?

Thanks, much appreciated...

Mark

---

### Post by ajmorris on 2008-03-19
when you say it fails booting up the CD... what error do you get?

---

### Post by mhpriest on 2008-03-20
It boots into XP.  However, when boot up with another Linux dvd (parted magic), it boots up fine.

I have tried this with all the different Umbuntu iso's with no luck.  When I go into XP it reads the disk and lists all the directories/files.  Even when I boot up with straight DOS diskette it sees the directories/files.

Thanks, I really appreciate your response.  I am not exactly new with computer troubleshooting but am totally new with Ubuntu/Linux.

---

### Post by mk1w86 on 2008-03-20
> I read as many forums as I could over the last couple of weeks and thought I'd try the SmartBootManager. When I boot up with the floppy and Xubunta CD in place, I get the screen with the CD option and save.

In Smart Boot Manager select the save option then at the SBM menu choose to boot the CD again - if at first it does not work then try pressing enter a couple more times because sometimes it will eventually boot the CD.

---

### Post by mhpriest on 2008-04-25
I realized (embarassingly) that my DVD player is only RO, so the SBM won't work.  The only option I could think of was to fool around with the BIOS.

I discovered that setting up my secondary master showed CD but I had configure it as "CD" instead of "Auto." I changed it to "CD" rebooted and it immediatly went into the installation.

Thanks for all your help.

P.S. There was no option under Thread Tools to mark this as solved.

---

