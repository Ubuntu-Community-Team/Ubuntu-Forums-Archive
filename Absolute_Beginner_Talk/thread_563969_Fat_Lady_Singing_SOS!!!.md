---
title: "Fat Lady Singing?? SOS!!!"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by berZirker on 2007-09-30
The basics: I am dual-booting an almost 4 year old stock emachines m6809 laptop with windows XP and ubuntu feisty fawn.  While running windows (I do recognize this as my first mistake) my laptop started making bad noises (sort of a popping sound), and was running unusually/unacceptably slow, though not quite frozen.  I did a hard reboot to get it started again, and it came up with the big "e" and the option to get into the BIOS settings, but the grub stage didn't load and all it said "operating system not found."  I rebooted again, and this time the grub manager came up.  Trying to select any of the operating systems produces  "error 29: disk write error".  All the hardware that is easily accessable (HD, ram, battery) seems to be seated correctly.   The noises are getting worse every time I reboot.  Rebooting will randomly give the operating system not found error, or the GRUB manager.  

Extra information (possibly applicable):  I had been running windows in fairly vulnerable mode, with just the SP2 firewall, and an illegitemate copy of Panda 2008 (is this just bad karma comming back to get me?)  I had been downloading a few torrents, so I will concede that it is possible that I have gotten a mother of a virus.  Due to the sounds, I am inclined to think that something serious is going on with the hardware however.  Also: I had been changing the xorg.conf file on the linux side, which may or may not be applicable.  see this thread [http://ubuntuforums.org/showthread.php?t=562276](http://ubuntuforums.org/showthread.php?t=562276)

I have access to the BIOS setup, as well as ubuntu memtest86+ but I am unfamiliiar with using them, and I don't want to go poking around without some ideas.

I could try doing a fresh install, but I would really like to figure out wtf happened first.

PLEASE HELP!!!

---

### Post by FuturePilot on 2007-09-30
Sounds like you hard drive crashed.
```
error 29: disk write error
```
Definitely sounds like a hard drive failure.

---

### Post by floke on 2007-09-30
You could run a live rescue disk that has the smarmontools app on it - this will report any damage to your hard drive. Best google smartmontools for more info. One such rescue disk is at [http://trinityhome.org/Home/blog.php?front_id=15](http://trinityhome.org/Home/blog.php?front_id=15)

A useful piece on smartmontools is here: [http://www.linuxjournal.com/article/6983](http://www.linuxjournal.com/article/6983)

---

### Post by jfinkels on 2007-09-30
First thing you could try is booting into the liveCD environment and running 'fsck' on the the drive.

You may also want to take a look at the Ultimate Boot CD [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) . It has a lot of useful disk utilities, etc.

---

### Post by berZirker on 2007-09-30
Crash mid session?  Would this simply be a cheap components (ie nothing to do but buy a new hd)?  The warranty is definitely out of date, but I'd hate to lose a functioning laptop if I can help it, or buy a new hd (if that's even possible without knowing of alternatives.)  Thanks for the quick response.

---

### Post by berZirker on 2007-09-30
Running the trinity rescue kit, the only failed checks are the ip aadress and "system logger: /etc/rc.d/rc3.d/S12syslog: line 41: 2618 Terminated   $*"  From my limited research, it seems like smartmontools is a better tool for prevention than recovery.  Is there something I am missing?

When I try to load ubuntu from the disk it takes me to a command line busybox interface which does not recognize the fsck command.  I don't know really what busybox is or what I can do with it.  I have only a limited familiarity with the command line anyway.

Thanks for helping me work through this.

---

