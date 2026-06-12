---
title: "Installing on ASUS X45A"
date: 2013-01-23
forum: Asus Ubuntu Support (CLOSED)
---

### Post by davidnelson316 on 2013-01-23
Hello, everyone! I'm new to Ubuntu and I love it so far. I installed it on a 2005 Gateway laptop just to see if I would like it. I'm hooked, but I've ran into a problem. I have a new ASUS laptop that came pre-installed with Windows 8. I have tried all kinds of tricks to get Ubuntu installed and nothing has worked. I turned off secure boot, used Wubi, tried to get Windows to boot from my Ubuntu CD...nothing works. I want to get Windows 8 off of my laptop, so if anyone could help me, I would greatly appreciate it!

---

### Post by mörgæs on 2013-01-23
HI, welcome to the fora.

Before proceeding, how does it work in a live boot?

---

### Post by davidnelson316 on 2013-01-23
In a live boot, I get a warning saying there is some type of file missing and it takes me to the OS option screen where I can choose Ubuntu again(and get the same warning) or boot Windows 8. As to the second question, I chose Ubuntu because it was the first one I tried and I had read reviews on it and watched some walkthroughs and really liked it. I have read that others have had the same issues trying to replace Windows 8.

---

### Post by mörgæs on 2013-01-24
Please post the exact warning / error message.

---

### Post by audiomick on 2013-01-24
> **davidnelson316 said:**
> I have read that others have had the same issues trying to replace Windows 8.

Yes, I have been seeing a lot of posts about that. It seems to be tied up with the secure boot business, and whether or not you install EUFI/GPT or BIOS/MBR.

In particular, the moderator oldfred seems to have looked into this issue. Here are a couple of threads where he has posted on the subject. There may be some links there that could help you.

[http://ubuntuforums.org/showthread.php?t=2107873]("http://ubuntuforums.org/showthread.php?t=2107873)

[http://ubuntuforums.org/showthread.php?t=2105067]("http://ubuntuforums.org/showthread.php?t=2105067")

[ubuntuforums.org/showthread.php?t=2105622]("ubuntuforums.org/showthread.php?t=2105622")

---

### Post by prodigy_ on 2013-01-24
If you still can boot into Windows you can try using BCD (the Windows boot loader) instead of Gbub: [http://superuser.com/questions/499617/how-can-i-add-linux-to-the-new-windows-8-boot-manager](http://superuser.com/questions/499617/how-can-i-add-linux-to-the-new-windows-8-boot-manager)

And, like **mörgæs** said, it wouldn't hurt to know what kind of error messages you get.

---

### Post by davidnelson316 on 2013-01-24
Thanks for the replies! As soon as I get off of work, I am going to do a live boot again and get the exact error message and post it.

---

### Post by davidnelson316 on 2013-01-24
The error message I'm getting is:

Windows failed to start. A recent hardware or software change might be the cause. To fix the problem.

1. Insert your Windows installation disc and restart your computer.
2. Choose your language settings, and then click "Next".
3. Click "Repair your computer".

If you do not have this disc, contact your system administrator or computer manufacturer for assistance.

File: \ubuntu\winboot\\wuildr.mbr

Status: 0xc000007b

Info: The application or operating system couldn't be loaded because a required file is missing or contains errors.

---

### Post by monkeybrain2012 on 2013-01-24
There is a specialized Asus support subforum.

Maybe you would get more advice there. [http://ubuntuforums.org/forumdisplay.php?f=408](http://ubuntuforums.org/forumdisplay.php?f=408)

---

### Post by pqwoerituytrueiwoq on 2013-01-24
see if there is a uefi setting in the bios, my laptop has one i dont know exactly what it is for, but turning it off may help
i would guess it switch the bios to a old school version, if it is what i think it is it is disabled on my laptop
my laptop is in my sig

---

### Post by davidnelson316 on 2013-01-25
Yes, there are UEFI settings in the BIOS. I have been changing up these controls and attempting to boot Ubuntu, but to no avail.

---

### Post by mörgæs on 2013-01-25
Let's see if the Asus sub-forum gives more answers. Moved.

By the way, I guess people will soon be asking which model of Asus you are using. Better to post it right away.

---

### Post by davidnelson316 on 2013-01-26
It is an ASUS X45A.

---

### Post by davidnelson316 on 2013-01-26
Problem solved! Had to disable fast boot, launch CSM, enable Launch PXE OpRom in the BIOS settings. Then, I disabled Secure Boot Control and from there was able to boot from a USB and complete the install.  Thanks for your help!

---

### Post by mörgæs on 2013-01-26
Good, then please mark the thread 'solved' using 'thread tools'.

---

