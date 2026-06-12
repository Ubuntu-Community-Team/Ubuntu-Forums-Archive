---
title: "Just installed alongside windows and now neither works ](*,)"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by Marlow on 2006-04-18
Okay I'm 100% new to Linux, and am typical in the sense that I know Windows and in the last few months have learnt mac.  I wanted to add Linux to that mix but I'm experiencing some setbacks.  

Short background.

My desktop PC was crashing (freezing) and had been neglected for years while I used laptops.  I just reformated it and freshly installed XP on the main drive.  It was working fine (for windows at least).  I then installed Ubuntu on a partition on the slave drive (9 gb plus 500 mb for swap).  The installation went fine and GRUB installed as planned.  The only hiccup were the network settings, but I get free wireless which I knew I'd have to play with so I skipped that step.

When I rebooted, Ubuntu launched and conitinued and finished the intsallation.  I then rebooted again and the dual boot option came up, but when I tried ubuntu it would start to load and then my screen would enter standby, like when you don't touch for x-number of minutes in XP (LED on moniter changes from green to orange).  I tried twice but both times got the same result.  I knew this would not be too easy so i figured I'd go into XP just to check a few things out but I got  "Error 13, Invalid or unsupported executable format" after it tried to boot XP.

So my question is where to I start?

I don't mind reinstalling xp and ubuntu but given the time it takes I'd like to know what might have happened.  My XP pro wasn't fully updated ( I ran autopatcher but only selected some of the updates) but that seems unlikely to be a problem, and as far as ubuntu goes I'm clueless.

I'm thinking of maybe trying a fresh ubuntu only install if that could perhaps limit potential problems.  This is a redundant second (third maybe even) PC so I really just want to play with Linux - ubuntu as well as some other distros.

Any help would be great, keeping in mind that I'm a newby with limited programming abilities (none).

Thanks,

Marlow

---

### Post by htinn on 2006-04-18
One thing you can do is boot Ubuntu and then press Ctrl+Alt+F1 to go to a terminal. If you can log in and run some commands, that would be very helpful.

sudo fdisk -l

The above command would be helpful for understanding how your system is set up. It would also be nice to see the result of this:

sudo cat /boot/grub/menu.lst
sudo cat /etc/X11/xorg.conf

As for not having video with Ubuntu, that could be a matter of having not set up your video correctly, so it would be helpful to know what kind of video card you have and what type of monitor you have.

---

### Post by Marlow on 2006-04-18
I have two HD's /dev/hda1 has XP on it in FAT32

hdb1 (8.9 gb) has linux
and hdb6 has a swap partition

(hdb5 has some old files)

I couldn't get the other two commands to run.

the first said no such file or directory the other said command not found.

I'm lost.

Marlow

---

### Post by Marlow on 2006-04-18
Sorry and I have an ATI rage 128 card from around 1999, I cant get the specifics as I can't get windows to run and am clueless in linux.  Graphics seem to work however after teh ctrl+alt+F1 trick.

Cheers,

Marlow

---

### Post by htinn on 2006-04-18
Weird. If you could navigate around and describe what you're seeing in the console, that would be nice. For example:

cd /etc/X11
ls
cd /boot/grub
ls

Maybe we can nail down part of the problem that way.

---

### Post by Marlow on 2006-04-18
here's a little update

Having done the ctrl+alt+F1 trick linux boots up fine (I think).  I was able to try and play around with my rt2500 wireless card (still not working).  I just want to check something basic - you want me to type these commands in terminal right?  Sorry for the noob question but this is a new world for me.  I'm not quite sure what you want me to describe and I can't get those commands to produce anything.

Thanks

---

### Post by htinn on 2006-04-18
Right after you login, you should get a prompt like this

user@ubuntu:~$

And probably a blinking cursor. Just type in commands and look at what the result is. For example "ls" gives you a directory listing and "cd" changes to a different directory.

The rt2500 will probably have to wait till you can get the desktop going. :)

---

### Post by sxtz on 2006-04-18
which version are you trying to install from, marlow?

---

### Post by Marlow on 2006-04-18
I've got the desktop going now.  For whatever reason ctrl+atl+F1 booted differently that one time and now it works (couldn't tell you why).  I'm using a fresh download of 5.10 that I just got two days ago from a torrent link at ubuntu.org.

htinn... when I open terminal I can check the fdisk command which shows all the other partitions, but the others all get errors.  ls just says [COLOR="Red"]DESKTOP[/COLOR] [COLOR="Black"]

Anyways, ubuntu seems to be working from what I can tell, but I still have the XP issue (error 13) and can't seem to get the above commands running.  Are there any other things I could do to diagnose?  I don't have internet on the computer, but can burn RW's iso's and what not from my mac.  

I this point I just like to try and fix the XP thing and play around with linux (hopefully get the wireless going) and any other cool tricks I can find [/COLOR]

---

### Post by htinn on 2006-04-18
Good idea. You can always just nuke Ubuntu and reinstall it later.

---

