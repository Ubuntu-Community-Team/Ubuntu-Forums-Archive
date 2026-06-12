---
title: "Xubuntu 6.10 LiveCD install problem"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by HumusSmurf on 2007-03-14
Hi!

I have tried to start Xubuntu 6.10 LiveCD on a computer that for the moment are running Win98, 128 M RAM. But I have not made it so far, already on my first attempt I’m asked for my username and password, direct after I chose ‘Start or install Xubuntu’. I have tried xubuntu, ubuntu, Edgy, Eft, live, root, blank, 6.10. etc as username and passwords, and in all possible combinations without luck. I have checked the CD and memory, and they are all OK. I downloaded the iso-file and burn it myself from the official ubuntu website. I have tried to log in using: safe graphic mode, Xfce session, standard session, Failsafe GNOME session and Failsafe Terminal session. When starting Win98 I’m not asked for user name or password.

I’m grateful for any help!

---

### Post by benfindlay on 2007-03-14
If I understand you correctly, it installed successfully?

Have you installed the OEM version by any chance?

If so your username is ```
oem
``` and your password is whatever you picked during the installation.

---

### Post by benfindlay on 2007-03-14
Also with those system specs I would suggest you download the alternate cd and install that instead. Since the system is fairly low spec it is more likely to install without a hitch!

Hope this helps!

---

### Post by HumusSmurf on 2007-03-14
I have not been able to come so far in the process so that I could install it! As I understand the alternative-iso version of Xubuntu is that you can not start it as a LiveCD, so you must install it (dual boot possible?). I would like to check if Xubuntu can deal with my hardware before wiping out Win98.

---

### Post by benfindlay on 2007-03-14
Yes you can dual boot from the alternate cd, you simply set up your partitions manually and make sure the install won't format the windows partition!

As for whether your system will be compatible, I would suggest posting your specifications here and hopefully there will be someone who has that system, so can confirm whether it will work or not!

---

### Post by loanrangie on 2007-03-14
> **HumusSmurf said:**
> I have not been able to come so far in the process so that I could install it! As I understand the alternative-iso version of Xubuntu is that you can not start it as a LiveCD, so you must install it (dual boot possible?). I would like to check if Xubuntu can deal with my hardware before wiping out Win98.

 Dual boot works well, i run it on my pc and laptop.

---

### Post by HumusSmurf on 2007-03-15
Now I have tried the alternative xubuntu 6.10 version, but I was a little bit confused which install alternative I should choose. Before burning the iso-file I looked for which options to install at [http://ubuntu-cdimage.datahop.it/xubuntu/releases/6.10/release/](http://ubuntu-cdimage.datahop.it/xubuntu/releases/6.10/release/)

"Alternate install CD

The alternate install CD allows you to perform certain specialist installations of Xubuntu. It provides for the following situations:

creating pre-configured OEM systems;
setting up automated deployments;
upgrading from older installations without network access;
LVM and/or RAID partitioning;
installing GRUB to a location other than the Master Boot Record;
installs on systems with less than about 128MB of RAM."

But the options that actually are on the alternative xubuntu 6.10 were these:
Install in text mode
Install in OEM mode
Install in command-line system
Install an LSTP-server
Check CD for defects
Rescue a broken system
Memory test
Boot from first hard drive

What is the difference between text mode and command-line system??
How to get Xfce desktop environment, when you are new to linux??
How to install without download many packages, since I only have a slow telephone connection?

Thank you all help!

---

### Post by benfindlay on 2007-03-15
A command line system is the server install: it has no GUI unless you add it manually

I suspect you want a text install so you will have the GUI present!
Also, xubuntu comes with xfce ready to use!
Several packages are already included on the cd/dvd. All you need do is make sure the cd is present in your package repository list (etc/apt/sources.list) and it will be used instead of your internet connection!

hope this helps!

---

### Post by HumusSmurf on 2007-03-15
Thank you benfindlay!

---

