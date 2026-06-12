---
title: "Problem with ubuntu install"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by -Morgoth- on 2007-08-05
Hi,
Today i decided to try a linux distro for the first time in my life. I chose ubuntu as i heard that was the easiest to use for beginners. I donwloaded and burned it to a cd and tried to install it on my laptop.
But once the installer has loaded for a minute or two, i get the following error: "Failed to start the X server (your graphical interface). It is likely that it is set up correctly. Would you like to view the X server output to diagnose the problem?  YES / NO"  I chose yes, then it showed a log, i clicked yes again, and then it said: " The X server is now disabled. Restart GDM when it is configured corectly."

As i am completely new with linux, I dont know whats wrong here so any help would be appreciated. 

My laptops specifications: Acer Aspire 5103WLMi
-AMD Turion 64 x2 Mobile technology TL-52 (1.6Ghz, 2 x 512KB L2 Cache)
-Up to 384MB ATI Mobility Radeon X1300
-160GB HDD
-2 GB DDR

---

### Post by Jimmyfj on 2007-08-05
First of all you could try to choose "Start Ubuntu in safe graphics mode" - If this doesn't help you need to try the alternate install cd. This Cd does not use a GUI but a text mode installer and are in my experience the best way to beat some ATI graphic cards

---

### Post by -Morgoth- on 2007-08-05
"Start Ubuntu in safe graphics mode" gave the same error :/
Downloading the alternate CD now, so will try as soon as its downloaded :)

---

### Post by proalan on 2007-08-05
i have similar problems installing ubuntu on low spec laptop sometimes

try the following in a terminal to configure the xserver manually

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by ugm6hr on 2007-08-05
ATI card help: [http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

---

