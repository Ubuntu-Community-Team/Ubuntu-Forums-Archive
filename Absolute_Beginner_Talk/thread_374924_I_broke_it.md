---
title: "I broke it"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by 67GTA on 2007-03-03
I was trying to delete some files that belonged to VLC media player and must have deleted something important by mistake. Normally I would go to the trash and get it back, but the trash won't open. I tried to reboot and the splash screen did not finish loading. I had to click on it to make it go away. My desktop is not showing my folder that I created on the desktop for my personal stuff. When I try to open the computer or home folder from the panel nothing happens. Rebooted into recovery mode and file system check was forced, and said /dev/sda1 contains a file system with errors from whatever I deleted.Anyone have any ideas before I reinstall?

---

### Post by Kobalt on 2007-03-03
Have you trid reinstalling the ubuntu-desktop package ? 
When your comuter boots, press Ctrl+Alt+F1 to access a command line, then try reinstalling ubuntu-desktop with ```
sudo aptitude install ubuntu-desktop
```
You can also try to reinstall VLC the same way, but it's very likely you touched something that didn't belong to VLC.

---

### Post by 67GTA on 2007-03-03
I have reinstalled gnome...ubuntu-desktop....and nautilus. I think I killed it. It might be better to reinstall anyway. I am just now getting the hang of Linux. I have beat this first install up pretty bad over the past month. Is there any way to get to my personal folder from the command line to put on a disc before I wipe it out? I'm not that educated yet.

---

### Post by Kobalt on 2007-03-03
Yes, you can start a LiveCD session and mount your hard drive, then you can backup your data on CD or DVD very easily...

---

### Post by adam.tropics on 2007-03-03
If you're gonna reinstall, you might want to do a search here on partitioning. A separate /home partition will save you a world of hurt at times like this.

---

### Post by easyease on 2007-03-03
well said adam, i was just going to suggest that til i saw you got there, always a wise  move having a seperate home partition.

---

### Post by 67GTA on 2007-03-03
I can actually get to my home folder through gnomebaker. I am trying to pull the important stuff off right now. I will create a home partition this time. This was my first try at linux after 12 years of MS windows. It was a bloated mess after trying to find out what I wanted or needed, so I am looking forward to a fresh install. I'll be back...

---

