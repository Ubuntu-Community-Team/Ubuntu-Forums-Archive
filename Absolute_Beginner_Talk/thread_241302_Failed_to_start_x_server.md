---
title: "Failed to start x server"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by Alien260 on 2006-08-22
hello, 
i was just posting on this website about another problem i had when ubuntu told me there where some updates to download. so i downloaded them after that it told me i should reboot. when loading the OS again (after the reboot) ubuntu doesnt start up it goes throught all the loading process at the beginning but then when the welcome login screen should pop up a horrible blue screen appears saying that ubuntu had "failed to start the x server" (which it says it has something to do with the graphical something). It the makes me login but not into the OS into a "DOS" type enviroment, asking me to fix the problem and reboot. 

??????????????????????????

i have no clue what to do. this happend 5 min ago 

HELP PLZ
ALien

---

### Post by Major_Stitch on 2006-08-22
Here from another post:

> **jlx said:**
> Solution:
When your Xserver crash and you are at text console type this:
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10

When finnish, reboot or just type startx. To reboot type:
sudo shutdown -r now

Now xserver-xorg-core is downgraded to prior working version. 

First I thought it was something wrong with XGL/Compiz Quinn's packages. But I upgraded xserver-xorg-core in my laptop that has no compiz installed and Xserver was broken too. So it has to be a problem with dapper packages. Hope Ubuntu boys will fix it soon.

Regards.

---

### Post by BitTorrentBuddha on 2006-08-22
[Known bug](http://www.ubuntuforums.org/showthread.php?t=241254). Simple fix is to run: ```
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10
sudo reboot
```

---

### Post by MaximB on 2006-08-22
[http://www.ubuntuforums.org/showthread.php?p=1408007#post1408007](http://www.ubuntuforums.org/showthread.php?p=1408007#post1408007)
how to

---

### Post by Harry Jensen on 2006-08-22
> **BitTorrentBuddha said:**
> [Known bug](http://www.ubuntuforums.org/showthread.php?t=241254). Simple fix is to run: ```
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10
sudo reboot
```

Yep, worked right away, thanks :cool:

---

### Post by Alien260 on 2006-08-22
thanks worked fine, just have to remember not to download that package in the future.

thanks 
Alien

---

### Post by tengil on 2006-08-22
Known bug and easy to fix if you know your way around. The problem is for all the "regular" straight-from-windows users (grand fathers, aunts and what not). They're either re-installing Ubuntu, or most likely going back to Windows. 

This is way more serious than the old obsolete and much complained about blue-screen.

Too bad for Ubuntu, Linux for human beings.

---

### Post by quad3d@work on 2006-08-22
> **tengil said:**
> The problem is for all the "regular" straight-from-windows users (grand fathers, aunts and what not). They're either re-installing Ubuntu, or most likely going back to Windows. 
This is way more serious than the old obsolete and much complained about blue-screen.

Too bad for Ubuntu, Linux for human beings.

[Read this too]("http://ubuntuforums.org/showthread.php?p=1407916#post1407916"). This level of frustration will drive a lot of new users away... and this is one of the major issues I continue to have with Linux as a desktop OS. I still use WinXP as main OS, simply I just get more things done in it than I do in Linux (perhaps I'm just more familar with it). I remember reading something few weeks ago about Unix/Linux's major problem not becoming mainstream is due to '**user hostility**'... too bad the wiki article is no longer available.

[This problem has been fixed]("http://ubuntuforums.org/showpost.php?p=1408166&postcount=40").

---

### Post by Christopher on 2006-08-22
> **BitTorrentBuddha said:**
> [Known bug](http://www.ubuntuforums.org/showthread.php?t=241254). Simple fix is to run: ```
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10
sudo reboot
```

Thank you very much, this worked great for me as well.  ;)

---

### Post by Ariam on 2006-08-22
Thank you all, it solved my problem as well

Ariam

---

