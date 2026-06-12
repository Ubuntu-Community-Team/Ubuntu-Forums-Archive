---
title: "Xubuntu 7.04 install fails"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by gerry1936 on 2007-08-01
Trying to install Xubuntu fromthe Xubuntu-7.04-desktop-i386.iso download.

It seems to start off OK, but gets to a swirly blue screen with seven ikons down the left side, the bottom one being Install.

There is an arrow in the centre of the screen, but this will not move. Thinking that perhaps I need to wait, after about 15 minutes what look very like screen savers start to appear.

I've also tried the Safe mode- gets the same.

Machine is:

Intel Celeron, 600Mhz, 256M RAM, 25GB hard drive, with WIN98 occupying a partition of 12GB, the rest unallocated.

What's happening?

---

### Post by gerry1936 on 2007-08-01
I forgot: mouse is standard PS2 with scroll wheel.

---

### Post by Rocket2DMn on 2007-08-01
Sometimes the LiveCD doesn't work for people, so the alternate cd is the best option.  It doesn't have a live desktop session, but rather a text based install.
[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/) and choose the alternate cd for x86 architecture
Don't forget to check the md5sum
[HowTo]("https://help.ubuntu.com/community/HowToMD5SUM")
[Hashes]("http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/MD5SUMS") to check against (for Xubuntu)
Then burn at a slow speed, like 4x, to prevent write problems, and use quality media if possible.

---

### Post by gerry1936 on 2007-08-01
OK- so I downloaded the Alternate iso CD, and it installed perfectly- or so it seemed! At the end, it ejected the media and rebooted, and the desktop appeared. BUT the little arrow in the middle of the screen is fixed in place just as happened with the desktop CD.

The mouse works OK with WIN98 and with PupWin98 (Linux).

Any ideas?

Gerry

---

### Post by Rocket2DMn on 2007-08-01
What kind of mouse are you using?
You may need to reconfigure X (the GUI) to get the mouse to work.  Get to a terminal by hitting CTRL+ALT+F2
```
sudo dpkg-reconfigure xserver-xorg
```
This takes you through the process of reconfiguring X where you select hardware options, including mouse, keyboard, and display drivers.  Use TAB to move around and SPACEBAR to select/enable when necessary.
After you complete that, restart xdm
```
/etc/init.d/xdm restart
```

If this doesn't work, you might need some different drivers for your mouse (assuming it is actually functional).

---

### Post by ugm6hr on 2007-08-01
Bizarre - some else has the exact same problem:
[http://ubuntuforums.org/showthread.php?t=514892](http://ubuntuforums.org/showthread.php?t=514892)

---

### Post by gerry1936 on 2007-08-03
I tried what Rocket2DMn suggested- disaster! All that reconfiguring asked me questions that were complete gibberish to me, and my guesses completely screwed things up.

So it's back to good old trouble-free plug and go PUPPY for a while, until I work through the replies to the other thread.

Just a foot-note: I have two mice, both work on the machine that has XP installed, both work on the old machine that has WIN98 and Puppy installed, and on which I'm trying to install Xubuntu. Both also work with DSL.

Celeron 600MHz, 256M RAM, 13GB hard disk available.

Gerry

---

### Post by Rocket2DMn on 2007-08-03
Sorry that didn't work out.  When you run that configuration script, a backup is made of your old xorg.conf file in that directory in the form xorg.conf.YearMonthDayTime (a bunch of digits).  You can recover your old one by running
```
sudo cp /etc/X11/xorg.conf.123456 /etc/X11/xorg.conf
``` where xorg.conf.123456 is the backup file.  
With a computer like that, Puppy or DSL may function better, even though you have enough RAM.  Hope you'll join us again soon.

---

### Post by ugm6hr on 2007-08-07
Possible solution in other thread: [http://ubuntuforums.org/showpost.php?p=3146190&postcount=4](http://ubuntuforums.org/showpost.php?p=3146190&postcount=4)

---

### Post by pointyblue on 2007-08-19
Had the same problem, it was the kernel.

```
sudo apt-get install linux-image-generic
```

updated the kernel and solved the problem.

---

