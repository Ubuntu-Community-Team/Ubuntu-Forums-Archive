---
title: "PLEASE NEED HELP installing ubuntu/using live cd"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by bazooze28 on 2007-06-07
ok so i wanna give ubuntu a try.  i want  to dualboot vista and ubuntu.  I made 2 partitions.  I then put the live cd in the drive and restarted the computer, booted from the cd.  Then the ubuntu menu came up and i picked "Start/Install Ubuntu".  It loaded for a minute and then it showed a blue screen with a bunch of symbols and said "X Windows Server failed" or something to that extent.  Then it shows a command prompt.  I cant get into the live cd at all.  And i know that there is no problem with the CD itself because i checked for errors and i tried it on another computer. 

By the way, the computer im using has a ATI Radeon video card.  maybe the problem has something to do with that.

Someone please help

---

### Post by Inxsible on 2007-06-07
Right on. your ATI might be giving you problems. You should try the Alternate CD which does a text only install. Once you have installed Ubuntu you can go in and play around and change the xorg.conf to rectify the X server problem

---

### Post by bazooze28 on 2007-06-07
> **Inxsible said:**
> Right on. your ATI might be giving you problems. You should try the Alternate CD which does a text only install. Once you have installed Ubuntu you can go in and play around and change the xorg.conf to rectify the X server problem

alright thanks ill try the alternate cd.  but dont you need x server to run ubuntu? if you do, how is it going to install it?

---

### Post by NeoLithium on 2007-06-07
Xserver is just what you need to run the GUI interface. The Alternate install will install the x-server for you, though this way you don't need to run the liveCD environment, you can make it specifically for your computer once it's all installed.

---

### Post by bazooze28 on 2007-06-07
> **NeoLithium said:**
> Xserver is just what you need to run the GUI interface. The Alternate install will install the x-server for you, though this way you don't need to run the liveCD environment, you can make it specifically for your computer once it's all installed.

ok so after i install ubuntu with alternate cd, it should be configured with ati card?

---

### Post by Inxsible on 2007-06-07
> **bazooze28 said:**
> ok so after i install ubuntu with alternate cd, it should be configured with ati card?
once you install, you can see if it works. if not, you can go into recovery mode, make changes to your xorg.conf file and retry and eventually get a working machine :)

---

### Post by NeoLithium on 2007-06-07
Well, I'm not guaranteeing that part. Though you'll be able to easily get it to work with the proper ATI drivers.  Once you're done the install, it will run you through the XServer setup, and you can pick what works for you, then come back in the desktop environment and grab the proper stuff you need with one of the ATI guides on [http://www.ubuntuguide.org](http://www.ubuntuguide.org) or someone's advice here on the forums :)

---

### Post by bazooze28 on 2007-06-07
ok i installed using the ubuntu alternate cd.  when the computer boots up, it shows the grub menu.  i pick ubuntu and it loads up, and then it gives me the same screen as before.  "Failed to start X server. It is likely it is not set up correctly"  can someone please tell me how to get this working?

---

### Post by bazooze28 on 2007-06-07
bump

please need help

---

### Post by bazooze28 on 2007-06-07
bump

---

### Post by bazooze28 on 2007-06-09
> **bazooze28 said:**
> bump

...anyone...

---

### Post by bazooze28 on 2007-06-10
i guess not

---

### Post by mattva01 on 2007-06-10
You are going to need to get into recovery mode, should be right below regular Ubuntu in Grub.
Then you should open this file: /etc/X11/xorg.conf 
Find 
> Section "Device"
and tell me what it says for driver

---

