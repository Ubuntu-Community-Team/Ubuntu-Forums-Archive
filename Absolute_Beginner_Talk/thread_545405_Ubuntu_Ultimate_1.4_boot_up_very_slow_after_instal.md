---
title: "Ubuntu Ultimate 1.4 boot up very slow after install"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by rkever on 2007-09-07
Greetings

I've resently installed Ubuntu Ultimate 1.4 from the DVD iso file ([http://ubuntusoftware.info/Ubuntu_Ultimate_1.4/](http://ubuntusoftware.info/Ubuntu_Ultimate_1.4/)).  The live DVD version worked perfectly.  I successfully installed it from the DVD and the first boot screen (with ubuntu logo and progression bar) loads just as fast as with the DVD.  Once past that, when the mouse shows up, it seems to take forever.  I let it run for over 10 minutes just to make it to the startup screen where you enter user and pass.  After entering user and pass it continues to run so slow that I finally gave up.  I've tried installing twice.
[B]
My specs[/B]

    * HP X2100 workstation
    * Pentium 4 2.2 GHZ
    * 1.5GB Rambus RAM
    * 2 - 34GB Ultrawide 160 SCSI drives (no RAID setup)
          o C: drive - My main drive with Windows XP Pro installed
          o D: drive - partitioned (using Ubuntu installation) 25.5GB NTFS Primary, 8GB Linux EXT3 Primary, and 424MB Linux Swap Logical
    * NVidia Quadro4 900 XGL w/128MB (dual monitor setup)

I'm a multimedia developer and have used Mac and PC all my life.  I'm very interested in trying out Linux as I see there are many programing applications out there now for linux.Any help would be much appreciated.

~~~Rob

---

### Post by tyggna1 on 2007-09-07
I don't personally use Ubuntu Ultimate--If you can boot up into it, try checking preferences->sessions and see what is trying to start up when your computer boots.  If there are more than ~14 things here, too much is trying to start up.

The other possibility is that it's a driver conflict or problem.  If such is the case--then you're gonna need a huge shot of Ubuntu and using the Command Line to get it to work.

Try to edit the start-up items.  If that doesn't work, we'll see what's going on with your drivers and make sure there aren't any conflicts.  Also--you may want to try installing just a regular Ubuntu distro--and see if you have any problems.

---

### Post by bone2006 on 2007-09-07
It's hard to tell what's causing it since your not using the standard ubuntu.  You might want to try the standard ubuntu to see if it's something that the ultimate version added, since the ultimate version isn't supported by ubuntu themselves.

since your into multimedia, you might take a look at ubuntu studio [http://ubuntustudio.org/](http://ubuntustudio.org/)

---

### Post by LowSky on 2007-09-07
UU is actually an off shoot of ubuntu and was created by someone who like ubuntu but wanted more functions right off the bat...

try Linux Mint another ubuntu based distro

---

