---
title: "Linux Mint does not appear in the bootloader"
date: 2013-03-23
forum: Any Other OS
---

### Post by nikhilbhartiya on 2013-03-23
Hi , I downloaded the linux mint 6 from its official website , then mounted the iso file and installed inside windowsnow after reboot mint doesnot appear and windows boots automatically i tried to check the boot menu by pressing ESC key and there i found only windows.I am having Windows 7 on my HP pavillion DV5 laptop.It is having an AMD processor.Please Help

---

### Post by oldfred on 2013-03-23
Mint does not install inside Windows, it has to be in another partition. Did you create a partition for it to install into?

Post this from terminal in live mode of your installer:

 sudo parted /dev/sda unit s print

---

### Post by Perfect Storm on 2013-03-24
Moved to Other OS/Distro Talk.

---

### Post by Virtuality314 on 2013-03-24
oldfred - I think he means that LinuxMint was installed using wubi. 

Check if there is a LinuxMint folder in your C:/ dirve (or the drive with windows on it)

---

### Post by nikhilbhartiya on 2013-03-24
Hey oldfred,
Thanx for your reply.

What I meant to say is :

I mounted the iso file, then 
i clicked on "lmmenu.exe" inside it.
a window appeared, i went for "Install inside windows" option.
i choosed the my f drive. then choosed 8 gb for installation size. and gave the password.
after it I clicked on install. it installed like an application. took some 2 minutes.
then asked for reboot.
i was expecting a linux mint option after the reboot to go into , but windows opened up directly.

this is the whole story .
please help. I am a newbie to LINUX.

Thank you.

---

### Post by oldfred on 2013-03-24
I thought only Ubuntu had wubi, but since Mint is Ubuntu based it may. 

Wubi adds an entry into the Windows boot.ini if XP or BCD if Vista/7.

       [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)


 bcdEdit - bcbc
[http://ubuntuforums.org/showpost.php?p=11927905&postcount=5](http://ubuntuforums.org/showpost.php?p=11927905&postcount=5)

---

### Post by deadflowr on 2013-03-24
Are you really trying to install linux mint 6?

That's a five years old, and most likely no longer supported, distro.

If that is the case, then I could see a WUBI install being somewhat buggy.
It would be using a very early version.

---

### Post by MadmanRB on 2013-03-24
Yes dont use mint 6, its very out of date.

The latest version is 14

[http://www.linuxmint.com/index.php](http://www.linuxmint.com/index.php)

---

### Post by nikhilbhartiya on 2013-03-24
Thanks oldfred, got it :)

---

