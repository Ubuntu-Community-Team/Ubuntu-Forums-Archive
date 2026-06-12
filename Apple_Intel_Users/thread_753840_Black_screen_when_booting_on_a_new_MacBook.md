---
title: "Black screen when booting on a new MacBook"
date: 2008-04-13
forum: Apple Intel Users
---

### Post by toocsh on 2008-04-13
Hello there.
I got a new MacBook (normal one, not a Pro) and the first thing to do was to install Ubuntu :) I have to say this is my first Mac, and this is my first post on the forums, so I apologize for any stupid questions.

The problem is I can not boot from Ubuntu LiveCD. I googled, searched the forums but got no luck. I installed rEFIt, and when I choose to boot from the CD, it just gives me a black screen with a blinking cursor at the top left corner, no initial boot menu (Install or start, etc.) No response to keyboard or any sings of activity. I tried different Ubuntu isos, 32 and 64bit, 7.10 and 8.04beta, and even server edition (afaik it's got no GUI for installation, and I thought video cud be the cause). Same result everywhere.

Here is the configuration of the laptop:
Model Name:	MacBook
Model Identifier:	MacBook4,1
Processor Name:	Intel Core 2 Duo
Processor Speed:	2.4 GHz
Memory:	2 GB
Bus Speed:	800 MHz
Graphics: Intel GMA X3100
HDD: 250 Gb

Any help is appreciated!

---

### Post by cyberdork33 on 2008-04-13
make sure you verify the download, burn the disk very slowly, and if you still get the same issue, use the alt install cd. (the server install is not what you want.)

---

### Post by ronocdh on 2008-04-14
This sounds to me like a bad burn, as cyberdork hinted. In OS X I recommend using the program Burn, which you can grab at [Open Source Mac]("http://www.opensourcemac.org/"). It automatically verifies the disc post-burning.

---

### Post by salvat0r on 2008-04-15
Hi toocsh/guys,

First of all. Sorry Didn't mean to hijack thread. As I m another noobie fellow which having the same MacBook spec with yours. Just feel like asking for guidance over the forum without creating multiple same topics.

Here goes my situation, I got downloaded the 64bit Ubuntu 7.10. Managed to burn .iSO  using the Disk Utilities in Leo and installed rEIT. Everything goes well the installation. I've done create the partition manually like 20gb and swap size 4gb. I did key-in the Hostname/username/password when it prompt on the installation. Ok, Done. everything. But it failed at the installation grub. I tried LILO instead. Lazy guy lame didn't read exactly the instructions perhaps. So just enter . So restart it Mac back to the boot screen. I have selected Boot Ubuntu from Hdd. It prompt for the username and password. I been trying to key in according what I enter earlier on the installation but it just failed. Don't know why. Password: _ <--- seems to have a space from front part couldn't remove it. 

Any idea ? Please advise. Thank you. Regards,salvator.

---

### Post by cyberdork33 on 2008-04-15
> **salvat0r said:**
> Hi toocsh/guys,

First of all. Sorry Didn't mean to hijack thread. As I m another noobie fellow which having the same MacBook spec with yours. Just feel like asking for guidance over the forum without creating multiple same topics.

Here goes my situation, I got downloaded the 64bit Ubuntu 7.10. Managed to burn .iSO  using the Disk Utilities in Leo and installed rEIT. Everything goes well the installation. I've done create the partition manually like 20gb and swap size 4gb. I did key-in the Hostname/username/password when it prompt on the installation. Ok, Done. everything. But it failed at the installation grub. I tried LILO instead. Lazy guy lame didn't read exactly the instructions perhaps. So just enter . So restart it Mac back to the boot screen. I have selected Boot Ubuntu from Hdd. It prompt for the username and password. I been trying to key in according what I enter earlier on the installation but it just failed. Don't know why. Password: _ <--- seems to have a space from front part couldn't remove it. 

Any idea ? Please advise. Thank you. Regards,salvator.If you know what you are doing, you can boot from a live cd, mount the partition and chroot into it to create a new user or reset the password. Otherwise, you just have to reinstall.

---

### Post by mrsteveman1 on 2008-04-15
The disk utility in OS X can burn and verify ISO files pretty well.

Just make sure you don't try to use the Burn button in Finder, it just puts the files you select on a CD, it doesn't burn the ISO as an image

---

### Post by toocsh on 2008-04-16
Hey guys!
Solved the problem, but forgot to get back here, sorry!

The solution is quite unusual, but it works :) The thing is to Shutdown Mac OS, not Restart. If I do Restart, Ubuntu livecd just doesn't boot, no matter which ISO I use.

The same problem (and same solution) has been reported by my friend on his Toshiba P100-160 laptop and Vista. I don't know the actual difference between clean shutdown (and the start up) and just reboot, but my guess is that RAM still holds some garbage unless fully unpowered and that causes the problem. But maybe I'm wrong, it's better to ask some geeks out there :)

Cheers!

---

### Post by cyberdork33 on 2008-04-16
i noticed when choosing to reboot the Mac never actually reboots... with Leopard anyway.

---

### Post by tbirkeli on 2008-06-26
Ah, you're right! Thank you so much... In my case, I had to remove the battery as well, but then it worked.

---

