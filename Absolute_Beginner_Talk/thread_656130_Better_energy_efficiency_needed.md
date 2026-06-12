---
title: "Better energy efficiency needed"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by johnleonard on 2008-01-02
I have read a number of articles in which the power consumption of various OSs running on a standard PC or laptop are compared. Sad to say Ubuntu generally does poorly in comparison with XP as well as other linux desktops. I have been unable to find out why it is so hungry for power, but the sooner it is sorted, or tools provided to allow the average user to tweak their system to reduce the wattage the better.

As well as issues with laptop battery life, the prevailing interest in green computing as well as the general open source ethos means Ubuntu is really missing a trick if this is not improved. It will not be too long before the wolves are at the door.

Does anyone know why Gutsy uses more power than say Fedora and how consumption can be reduced?

---

### Post by kwacka on 2008-01-02
[http://www.lesswatts.org/projects/powertop/](http://www.lesswatts.org/projects/powertop/)

"PowerTOP is a Linux tool that helps you find those programs that are misbehaving while your computer is idle. The application that misbehaved the most was the Linux kernel. However, as of version 2.6.21, the Linux kernel went tickless, and no longer has a fixed 1000Hz timer tick. The result (in theory) is huge power savings because the CPU stays in low power mode for longer periods during system idle. "


The important word there is 'tickless'.  

Unfortunately as the kernel gets more bloated the effect of this is reduced.

---

### Post by johnleonard on 2008-01-02
Thanks for that, I will have a look at PowerTOP. However, this seems only to deal with the situation of idling rather than when the PC is in use. A few posts have noted reduced battery life in Gutsy in particular (eg [http://ubuntuforums.org/showthread.php?t=600810](http://ubuntuforums.org/showthread.php?t=600810) ), and this article seems to demonstrate that Ubuntu uses more power in use as well as while idling.

[http://www.phoronix.com/scan.php?page=article&item=880&num=2](http://www.phoronix.com/scan.php?page=article&item=880&num=2)

---

### Post by dogeatery on 2008-01-02
Yeah, Powertop does nothing to help this problem at all.  I have just upgraded from Feisty to Gutsy, hoping the problem would have been solved or improved, at least.  So far, I am loving Gutsy, but this power situation is simply unacceptable.  Upgrading to Feisty reduced my laptop's battery life from three hours to one hour, this recent upgrade has reduced the battery to roughly 20 minutes of life.  It's REALLY a letdown.

---

### Post by LowSky on 2008-01-02
im not having any issue with my battery life, and its an 7 year old dell. I had it on for over an hour and a half last night  and it started with less than 50% battery. I would check your BIOS settings  to see if it has stepping turned on, and also you should do a few complete battery drains so that ubunut can gauge out the battery life.

make sure you have ubuntu-laptop-mode installed

---

### Post by dogeatery on 2008-03-12
LowSky, what would I need to look at in my BIOS settings, exactly?    I do have laptop-mode and it has made no difference

---

### Post by Sam Lars on 2008-06-04
> **LowSky said:**
> make sure you have ubuntu-laptop-mode installed

This conflicts with laptop-mode-tools.
ubuntu-laptop-mode says that it only controls hard drive spindown, while laptop-mode-tools does other things too, so wouldn't it be preferred to the ubuntu-laptop-mode?

---

### Post by dogeatery on 2008-06-04
As per the instructions in your signature:

How do I access the options enabled by laptop-mode-tools ?  I'm running Linux Mint and it's included in the distro.  Will they be in my BIOS settings now?  :confused:

---

### Post by Sam Lars on 2008-06-04
You can enable laptop mode in /etc/default/acpi-support.
```
ENABLE_LAPTOP_MODE=true
```
You can configure it in /etc/laptop-mode/laptop-mode.conf

---

### Post by dogeatery on 2008-06-09
> **Sam Lars said:**
> You can enable laptop mode in /etc/default/acpi-support.
```
ENABLE_LAPTOP_MODE=true
```You can configure it in /etc/laptop-mode/laptop-mode.conf

Wow, great, it actually worked a bit.  I've stretched it out to 50 minutes.  Unfortunately, I don't really want to mess with many of the settings in that file ... is there anything in particular that anyone would say it's safe to change or that I SHOULD change?

---

### Post by Raistlin82 on 2008-06-10
> **Sam Lars said:**
> You can enable laptop mode in /etc/default/acpi-support.
```
ENABLE_LAPTOP_MODE=true
```
You can configure it in /etc/laptop-mode/laptop-mode.conf

Hi there, when i edit acpi-support to ENABLE_LAPTOP_MODE=true 
i get the following error 

You do not have the necessary permissions to save the file. Please, check that you typed the location correctly and try again

any suggestions?

---

### Post by tomlinas on 2008-06-10
I believe you will need to open the file for editing in your editor of choice using sudo in order to prevent this error message.

---

### Post by dogeatery on 2008-06-11
Okay, since I made those changes to the file and posted the other day, I have been keeping an eye on my battery life.  It's very strange.  It will say I have as many as 55 minutes left with 95% battery life, but then minutes later it says I have 44% (25 minutes) left.  The good news is that it never used to get as high as 55 minutes before I altered the file, but the bad news is it seems to drain just as quickly as before.  Any tips on what changes I can make in the config file?  Can anyone else post what they've got in theirs?

---

