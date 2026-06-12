---
title: "[SOLVED] Can't shutdown properly"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by Skarjoko on 2007-11-27
I've been looking at a couple threads about this problem, and I can't seem to find any solutions.

The problem is that when I click 'shutdown' in Ubuntu, after closing all the running programs and everything, the screen goes black and the 'busy' light stays on. I have to use the power button to shut it down every time now. Also, it's gotten worse since I installed/uninstalled a new splash package (usplash-ubuntu-studio I think), as it *always* goes black when I try to shutdown, instead of once in a while.

I'm using a Dell Latitude D400 laptop.

---

### Post by master_kernel on 2007-11-27
Try removing the splash option from your /boot/grub/menu.lst and reboot and try to shutdown. When shutting down it will show you what's holding up.

---

### Post by cmnorton on 2007-11-27
I know this sounds lame, but... before you click on shutdown, go to a command line and see what is running 

ps -ef 

If you think you've shut everything down and processes are running that seem to be part of what you shut down, you could experiment by killing those processes one by one, and see if you can shutdown properly.

If you think this is due to a package uninstall/reinstall, then my guess would be to uninstall everything, after you save off data to a safe place. Then do a re-install.

---

### Post by Skarjoko on 2007-11-27
I already tried removing splash from the kernel line, and the problem still occured.

Also, I've only had Ubuntu for maybe a week (or less), and I haven't installed that many packages. This only started to occur when the screensaver stayed on for more than a minute, and I tried to shutdown/restart. After that splash package I installed (then promptly uninstalled), it just happens all the time.

And with the running processes, I don't really shutdown everything before a shutdown. Usually I have firefox and rhythmbox running, and I close those before shutdown.

---

### Post by cmnorton on 2007-11-27
What's your hardware config, especially RAM?

---

### Post by Skarjoko on 2007-11-27
Pentium M 1.60 GHz
1 GB of RAM
30.0 GB HDD
Intel 82852/855GM Integrated Graphics Card

---

### Post by Skarjoko on 2007-11-27
So any ideas on what I can do?

---

### Post by FreewheelinFrank on 2007-11-27
Welcome to the club!

> Since Microsoft was the first vendor to implement ACPI, many BIOSs are configured to meet Microsoft ACPI standards but may not be as effective when the computer has Linux installed on it.

[http://spidertools.com/ub_power.php](http://spidertools.com/ub_power.php)

[http://antitrust.slated.org/www.iowaconsumercase.org/011607/3000/PX03020.pdf](http://antitrust.slated.org/www.iowaconsumercase.org/011607/3000/PX03020.pdf)

There is a solution, for some laptops at least:

[http://ubuntuforums.org/showpost.php?p=3374952&postcount=5](http://ubuntuforums.org/showpost.php?p=3374952&postcount=5)

I have the same laptop as Viking777 and have to shut the damn thing off manually every time.

Cheers Bill!

---

### Post by Skarjoko on 2007-11-27
I noticed that one of the solutions involved "KLaptop". Is there a Gnome equivalent to this program?

---

### Post by Don DeGregori on 2007-11-27
7.04 has always shutdown properly on my  Fujitsu laptop. Now it will not with 7.10 installed. I have not changed any hardware. What was changed in 7.10?
I even see the same problem in gOS, the OS in the new Everex gPC, based on 7.10.  I don't have the gPC yet (on order), just the software I downloaded and burned to make a LiveCD. I've tried the gOS on 3 PC's. Same problem. Maybe when I get the gPC with gOS, the box will shutdown properly.

donde

---

### Post by RawMustard on 2007-11-28
Well Ubuntu has never shutdown one of my computers - Asus P5AD2-Deluxe Mobo.
I would dearly love to figure out a way of having shutdown work on this system as it's my daughters and it annoys me no end it sitting there with the Ubuntu logo and progress bar displayed all the time :(

I also have 2 Asus P5GPLs at work and they did shutdown with dapper, but stopped working with feisty and now gutsy.

Surely there is some way to make these things shutdown?

---

### Post by philinux on 2007-11-28
I had to put
 ```
acpi=force
```

at the end of the kernel line in menu.lst.

---

### Post by Skarjoko on 2007-11-30
I'm not sure what I did, but it seems to work now. I'm guessing that removing the splash screen, and rebooting after, fixed it for me.

Though if I decide to put the splash back on, I'll probably use what you did, philinux.

Thanks everyone, for all your help.

---

### Post by TeaSwigger on 2007-11-30
> **Skarjoko said:**
> I'm not sure what I did, but it seems to work now. I'm guessing that removing the splash screen, and rebooting after, fixed it for me.

Though if I decide to put the splash back on, I'll probably use what you did, philinux.

Thanks everyone, for all your help.

I had a sticky boot if I tried using usplash and had problems shutting down my 2nd PC, which also has an 8-series integrated Intel graphics. It's working now. Had to jump hoops; I installed the 915resolution package, the newer intel drivers, made sure xorg specified 'intel' for the driver, keep it to 16bit depth or it gets too sluggish, set the usplash / bootup resolution to only 8 bits (think I used vga=0x305 in the kernel line in menu.lst), put the usplash res to 1024x768, ran sudo update-initramfs -u -k `uname -r` and finally... it's working perfectly. Two days later Gutsy came out. I'm not hurrying to upgrade yet ;) and you can bet your beans I'm no fan of these integrated intel graphics cards. Anyway maybe that'll give you some ideas to go on.

---

### Post by RawMustard on 2007-12-01
Finally found a fix for all my shutdown problems thanks to a guy called Sander de Leeuw  on launchpad.  Thankyou so much dude, this was really starting to get on my nerves bigtime, to the point I was going to tell Ubuntu to go take a flying leap of a high cliff after 3 years of use.

Anyway, the fix for me went like so:

Make a script file called rmmod-all
```
gedit rmmod-all
```

Add this code.

```
#!/bin/sh

COUNT=1
while [ $COUNT -le 3 ]; do

	/sbin/lsmod | cut -d' ' -f1 | \
	while read MOD; do
		/sbin/rmmod $MOD
	done

COUNT=`expr $COUNT + 1`
done
```

Then:

```
sudo cp -v /path/to/rmmod-all /etc/init.d/
```
```
cd /etc/rc0.d
```
```
sudo ln -s ../init.d/rmmod-all S89rmmod-all
```

Reboot and then try to shutdown, viola, no more hanging at the splash screen - I'm soooooo happpppppy :) :)

To remove - just type in a terminal:
```
sudo rm /etc/init.d/rmmod-all /etc/rc0.d/S89rmmod-all
```

I hope this works for others as it did for me, I know how irritating a small bug like this can be :)

---

