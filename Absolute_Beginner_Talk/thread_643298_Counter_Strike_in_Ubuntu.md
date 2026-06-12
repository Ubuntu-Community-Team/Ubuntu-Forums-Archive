---
title: "Counter Strike in Ubuntu"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by LinuxIsInnovation on 2007-12-17
I have installed CS1.6.. When I start the game, It goes well until the game starts.. Theres a point in which the map is displayed and we have to press OK on a translucent windows to start the game.. 
My cs1.6 freezes at that point. The translucent windows usually has some text on it, but it doesnt have in this case. I have copied all windows fonts into the wine fonts folder, after which, I could see all main menu fonts.. How do I run cs1.6 (valve hl launcher)
Please help :(

---

### Post by nowshining on 2007-12-17
i didn't know spiders eat beans :P

nah j/k with ya

do u have compiz turned on, if so turn that off and try again.

---

### Post by LinuxIsInnovation on 2007-12-18
I realized that and switched to metacity temporarily.. But still it freezes at the same point.

---

### Post by LinuxIsInnovation on 2007-12-18
Also, my CPU usage goes 100% for one core and 84% for the other when I start CS1.6

---

### Post by nowshining on 2007-12-18
wine is still in development and many programs and games don't simply work at all or do work some in wine. Did u download from synaptic/repoes or did u download directly from the winehq site?

---

### Post by LinuxIsInnovation on 2007-12-18
I downloaded it from synaptic repositories.

glade@Muzic-Jukebox:~$ wine --version
wine-0.9.46
glade@Muzic-Jukebox:~$

---

### Post by LinuxIsInnovation on 2007-12-18
DOes it mean that I won't be able to play CS???

---

### Post by Rocket2DMn on 2007-12-18
I get wine directly from winehq, here's the directions - [http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)
It tells you how to add the repository.  Also, they are on version 0.9.51
I run cs1.6 ok under wine - i always make sure metacity is running (not compiz), and you might need to run "winecfg" from a terminal and check your sound settings.  Some people have problems with ALSA and others have problems with OSS.  I think the suggestion is to enable OSS and disable ALSA to prevent that freezing problem, though I use ALSA because OSS doesn't work for me.

---

### Post by LinuxIsInnovation on 2007-12-18
Ok.. I'll try out and post the results :)

---

### Post by LinuxIsInnovation on 2007-12-18
Dint work :(
I downloaded the new Wine, but it still freezes at the same point...
How can I generate specific error codes to explain the exact situation?
By the way, I just copied the Windows TTF fonts to /.wine/drive_c/windows/fonts folder..
I bulk renamed the TTF to ttf.. though that it might help..
Is it a fonts related issue?

---

### Post by hyper_ch on 2007-12-18
did you have a look at the wine appDB? Maybe there is some solution to your problem.

---

### Post by LinuxIsInnovation on 2007-12-18
Yes I did. Here it shows that CS1.6 can install/run on ubuntu:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3507](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3507)

Here it shows that it crashes..
[http://appdb.winehq.org/viewbugs.php?bug_id=6534](http://appdb.winehq.org/viewbugs.php?bug_id=6534)

But I think some users have run CS1.6 succesfully...:|

---

### Post by LinuxIsInnovation on 2007-12-21
Bump.

---

### Post by Rocket2DMn on 2007-12-21
Did you change your sound settings in winecfg?  This is the only reason I've ever heard of for freezing when you join a game, I had the problem myself.  Change to the OSS sound drivers and disabled ALSA from winecfg.

---

### Post by new2*buntu on 2007-12-21
I have ran it before, but I had to change the Windows version in winecfg to Windows XP for it to work right.

---

### Post by LinuxIsInnovation on 2007-12-22
> **Rocket2DMn said:**
> Did you change your sound settings in winecfg?  This is the only reason I've ever heard of for freezing when you join a game, I had the problem myself.  Change to the OSS sound drivers and disabled ALSA from winecfg.

Disabled ALSA and enabled OSS but still facing the same problem :(

---

### Post by LinuxIsInnovation on 2007-12-22
> **new2*buntu said:**
> I have ran it before, but I had to change the Windows version in winecfg to Windows XP for it to work right.

It is already set to Win XP..

---

