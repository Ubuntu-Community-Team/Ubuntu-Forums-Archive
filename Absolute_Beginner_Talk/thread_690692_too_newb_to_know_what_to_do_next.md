---
title: "too newb to know what to do next"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by Onompoly on 2008-02-07
So i installed ubuntu everything was great. eventually i wanted windows back for some games that i play, well i repartitioned through a live cd of xubuntu cause it was the only way i could get the drive partintioned for some reason. i installed windows xp essential edition and now when i boot up it goes straight to windows no option for choosing, i went back into xubuntu and saw that the original ubunutu partition was flagged boot now the windows is flagged boot and lba so i tried switching those back , and it says it cannot load the operating system. ,.,.. arg what have i done!

---

### Post by taurus on 2008-02-07
When you reinstalled windows, it overwrote GRUB from MBR so you need to reinstall GRUB to MBR to be able to boot Ubuntu and windows again.

[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles)

---

### Post by Onompoly on 2008-02-11
having troubles actually. I did easyBSD on windows and restarted. gave me some os error. I had the xp i installed right there so installed that on another partition. Now i have the option to choose out of the three operating systems. ubuntu doesn't work. Could i simply have installed ubuntu onto that partition or on another partition and both linux partitions would work?

---

### Post by HappyFeet on 2008-02-11
> Could i simply have installed ubuntu onto that partition or on another partition and both linux partitions would work?
yes, basically. if ubuntu is the last OS to install, it will see all OS's and put all in GRUB.

---

