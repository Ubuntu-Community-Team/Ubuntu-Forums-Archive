---
title: "Ubuntu sharing XP drive"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by TW3 on 2007-04-25
I have just installed ununtu Desktop on the 2nd drive in my PC.  The 1st drive has XP Hoime loaded.  I can now boot into either OS on startup.

I want to be able to access files on the XP drive from ubuntu, so I can load the software required to install my Speedtouch ADSL modem and share music files.  I can see both drives from ubuntu, but cannot access the drives.  Do I need to install Samba, and if so how?  Any help would be appreaciated :-)

---

### Post by Happy_Man on 2007-04-25
No... just put the following command into the terminal (Applications --> Accessories --> Terminal):

```
sudo apt-get install ntfs-3g ntfs-config
```

That gives you full read/write access to any NTFS partitions from Ubuntu.

---

### Post by TW3 on 2007-04-26
I could not get this commend to work, it appears that I do not have  NTFS-3g install.  I cannot get the package becaue I cannot get my Speedouch 330 working.  :-(

---

### Post by kagy on 2007-04-26
> **TW3 said:**
> 

I want to be able to access files on the XP drive from ubuntu, so I can load the software required to install my Speedtouch ADSL modem and share music files.  I can see both drives from ubuntu, but cannot access the drives.  

I'm sure you know this, but the drivers you had in XP won't work in Linux.

---

### Post by st33med on 2007-04-26
> **kagy said:**
> I'm sure you know this, but the drivers you had in XP won't work in Linux.

Ummmm.... Not particularly true. Ndiswrapper helps, but I have no knowledge on how to use it for your system.

---

### Post by zvacet on 2007-04-26
[https://help.ubuntu.com/community/UsbAdslModem]("https://help.ubuntu.com/community/UsbAdslModem")

---

### Post by TW3 on 2007-04-27
I have worked through the UK Speedtouch installation instructions, but still cannot access the Internet.  I get no messages or warning suggesting that anythng I have done has made any difference to the configuration of the system.

I am amazed that there is such poor support for the most previlent ADSL modem within the UK and that trying to set-up Ubuntu is such as nightmare.  If anybody has any suggestions on how this can be done I would be very grateful - if not I will return to Windows and a product that does work :-(

---

### Post by TW3 on 2007-04-27
I decided to start from scratch and reloaded ubuntu.  Based on what I had learnt and the guidance provided by the forum I loaded the correct drivers for my Speedtouch.  My first attempt to access the Internet worked perfectly and I am a happy bunny :-)

Thanks for your help, I'll be back with more questions later!!

---

