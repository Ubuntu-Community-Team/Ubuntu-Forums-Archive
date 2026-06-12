---
title: "Problems with Wubi installations"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by vigiu_76 on 2007-11-30
Hi all,

I instaled wubi on my pc, Dellatitude d630 with windows Xp professional,

When the system reboots and load graphical interface gives me this message:

Failed to start the X server (your graphical interface). It0s likely that it's not set up correctly. Would u like to view the x server output?

I chose yesbut this message is an enigmatic one.

how can i solve?

---

### Post by quandary on 2007-11-30
> **vigiu_76 said:**
> 
When the system reboots and load graphical interface gives me this message:

Failed to start the X server (your graphical interface). It0s likely that it's not set up correctly.



on the command line, try this:
dpkg-reconfigure xserver-xorg

---

### Post by vigiu_76 on 2007-11-30
> **quandary said:**
> on the command line, try this:
dpkg-reconfigure xserver-xorg

which command line ? are u talking about in windows enviroment?

ubuntu doesn't load

---

### Post by jrharvey on 2007-11-30
hmmm WUBI is tricky but it should boot into text mode after the message you recieved. That message is the most dreaded thing about 7.04 but they fixed it in 7.10 so if you are new to linux then I would use the WUBI 7.10 alpha. I know it is alpha but it works great on both my friends computers and I think 7.10 is alot more user friendly. The only problem is that when 8.04 comes out you cannont upgrade. 

Check out this thread for the alpha. You WILL have to do some maintenance in Windows before you install so dont freak out if it doesnt seem to work right away. Just go to the thread.

[http://ubuntuforums.org/showthread.php?t=572147&highlight=wubi+beta](http://ubuntuforums.org/showthread.php?t=572147&highlight=wubi+beta)

---

### Post by vigiu_76 on 2007-11-30
> **jrharvey said:**
> hmmm WUBI is tricky but it should boot into text mode after the message you recieved. That message is the most dreaded thing about 7.04 but they fixed it in 7.10 so if you are new to linux then I would use the WUBI 7.10 alpha. I know it is alpha but it works great on both my friends computers and I think 7.10 is alot more user friendly. The only problem is that when 8.04 comes out you cannont upgrade. 

Check out this thread for the alpha. You WILL have to do some maintenance in Windows before you install so dont freak out if it doesnt seem to work right away. Just go to the thread.

[http://ubuntuforums.org/showthread.php?t=572147&highlight=wubi+beta](http://ubuntuforums.org/showthread.php?t=572147&highlight=wubi+beta)

I don't know what i have to do... I dowonloaded different reviosion of wubi 7.10, but with all of them after the reboot the installazion check frozes at 46% in copyng file.

I tried to repeat the installation changing the size of virtual drive tryng 30,15,9 but without result.

Is it so complicated? HELPPPPPPPPPPP

I want to learn LINUXXXXXXX......

---

### Post by jrharvey on 2007-11-30
did you do a check disk in windows? You have to do this b4 installing WUBI. You could always try a dual boot. Go to this section right here to search for WUBI stuff.   [http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)

---

### Post by jrharvey on 2007-11-30
Oh and also if you have a desktop cd of Ubuntu 7.10 then use that instead of downloading the ISO. Its ALOT faster. All you have to do is burn a cd and then have it in the drive when you start WUBI. It automatically uses the CD ISO. Did you know that you can try linux from the CD without installing it?

---

### Post by quandary on 2007-12-02
> **vigiu_76 said:**
> which command line ? are u talking about in windows enviroment?

ubuntu doesn't load

Hm, i'm talking about the normal linux console.
If wubi is installed in a windows folder, there might be a file called xorg.conf
on the real ubuntu in /etc/X11/xorg.conf

It's a textfile, you have to edit it to adjust your configuration, as the message said.

You could also shrink your windows partition and install a proper linux instead.
Or you could use cygwin or the live-cd as a alternative.

---

