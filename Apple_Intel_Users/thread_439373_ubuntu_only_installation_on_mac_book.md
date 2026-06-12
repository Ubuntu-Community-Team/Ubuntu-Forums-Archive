---
title: "ubuntu only installation on mac book"
date: 2007-05-10
forum: Apple Intel Users
---

### Post by andrewbossie on 2007-05-10
i need help installing Ubuntu as my only os on my first gen 1.83 mac book, ive looked all over the place and have found nothing on it.

---

### Post by Lt_Data on 2007-05-10
I'm sure you already have the LiveCD, if not go to the Ubuntu main page and select whatever version you see fit. I recommend Xubuntu if your computer is lacking the needed power to carry out essential tasks or just be enjoyable. 

[http://forums.macrumors.com/archive/index.php/t-148617.html](http://forums.macrumors.com/archive/index.php/t-148617.html)

[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

Since you have a 1st Gen. macbook I've heard that you shouldn't have problems with WiFi because Atheros didn't change the chipset. I could be wrong, though, and if I am just scour the forum for topics relating to Ndiswrapper or MADWiFi.

Good luck.

---

### Post by benanzo on 2007-05-10
you wont have any problems with any boot issues if you did OS X updates past 10.4.6.  Apple released an EFI firmware update that does BIOS emulation without bootcamp.

So, as long as you updated OS X past 10.4.6 you can just install Ubuntu like normal and the EFI will find GRUB on the MBR and boot Ubuntu normally.  If not, I would recommend installing OS X and doing all the updates, or you'll need to install rEFIt to the protected EFI partition (which is still highly experimental if you want to use it without OS X.)

My advice, update OS X.  Run the Ubuntu LiveCD and do the install normally, formatting the whole disk (don't worry about the 200MB EFI partition if you're not using OS X, just delete it.)

---

