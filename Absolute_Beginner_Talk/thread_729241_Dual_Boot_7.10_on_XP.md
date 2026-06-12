---
title: "Dual Boot 7.10 on XP?"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by n2oboost1 on 2008-03-19
Can someone give me a link to instructions on how to dual boot Ubuntu on my (HP DV6609wm) laptop with Windows XP?  Much appreciated.

---

### Post by donnyblaze1 on 2008-03-19
Assuming you already have XP installed on the drive, check this out [http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/]("http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/")

Good luck!

---

### Post by n2oboost1 on 2008-03-19
Yes, I currently have XP installed.

---

### Post by (((X))) on 2008-03-19
Hello

I recomend to create a backup in case ubuntu goes wild and wipes out windows.
Also, when you will be installing ubuntu, be carefull with partitioning, read everything what it    tells you.

Once you get ubuntu on your harddrive, reboot and don't panic, just press ESC,
There you will see section with other operating systems.
If it is your oem version of windows, boot to second os in that section, 1st one will be windows recovery.

Good luck.

---

### Post by jan quark on 2008-03-19
look here:

[http://apcmag.com/node/5162/](http://apcmag.com/node/5162/)

---

### Post by n2oboost1 on 2008-03-19
Well this is a fresh install of XP, so I won't be losing anything.  Just got rid of Vista.

---

### Post by bumanie on 2008-03-19
I would suggest using the apcmag article as a guide. However one thing guides rarely mention is that it is a good idea to manually partition and have a separate /home, therefore if anything happens to your file system, you only have to reinstall ubuntu to / All your saved data will be safe in /home.

---

### Post by Sef on 2008-03-19
Read [Installing by Psychocats]("http://www.psychocats.net/ubuntu/installing").

---

### Post by bro on 2008-03-19
Just boot ubuntu from live-cd. Choose install. Once asked do not choose the option 'erase entire disk' or 'use entire disk' or whatever it is called. Just let it automatically resize or partition yourself (choose manual partition). The latter is not that complicated as it brings up a nice graphical view of your partitions. 
After installation you reboot a menu will appear for some seconds (10 or 30 i forgot) and you can choose your OS. If you don't choose it will default to Ubuntu. The menu of course appears every time you reboot. You can later set the countdown to just 2 secs or so, so you don't have to wait each time...

---

### Post by n2oboost1 on 2008-03-19
On trying to install, I get this message:

Ubuntu running in low detail mode.
(Options:Configure, Shut Down, Continue)
I tried to configure, nothing, so I clicked continue and I get this:

```
*Running local boot scripts (/etc/rc.local)                                                    [  OK  ]
[  184.532000] bcm43xx:  Error:  microcode "bcm43xx_microcode5.fw"  Not available or load failed
[  207.752000] bcm43xx:  Error:  microcode "bcm43xx_microcode5.fw"  Not available or load failed
[  230.972000] bcm43xx:  Error:  microcode "bcm43xx_microcode5.fw"  Not available or load failed
[  254.192000] bcm43xx:  Error:  microcode "bcm43xx_microcode5.fw"  Not available or load failed

```

What's wrong?

---

### Post by tarin666 on 2008-03-20
this error is caused by the drivers of the wireless device (not yet working) i have the same laptop and you have to remove all the restricted drivers from ubuntu.

Then install the nvidia driver official, second for the wireless you have to use it with ndiswrapper.

---

### Post by n2oboost1 on 2008-03-20
I can't even install Ubuntu to remove the drivers from Ubuntu.

---

