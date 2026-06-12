---
title: "Lightscribe load did not complete or something"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by trugreg on 2007-12-28
Beginner Using Hardy 8.04. I downloaded and installed Lightscribe from Lightscribe.com. It downloaded and the manager installed it BUT now I can't find it in Applications. Is there something else I have to do?

---

### Post by Jerry N on 2007-12-28
Did you just install the LSS program (lightscribe-1.10.27.1-linux-2.6-intel.deb) or are you talking about the Simple Labler?  Other than changing from standard to high density writing, I don't think you explicitly run the LSS program.  You need to install a label writer program AFTER LSS is installed.  I think I just screwed that up in a new install of 7.10 by getting them in the wrong order although I got it to work fine in LinuxMint 4.0 and an earlier install of 7.10.  You can download a fairly good label writing program at lacie.com (look for software, Lightscribe).  

After LSS is installed, you can change the writing density by running 'sudo /usr/lib/lightscribe/elcu.sh' in a terminal.

Jerry

---

### Post by Jerry N on 2007-12-28
By the way, if you are a Linux newby, why are you trying to run a potentially unstable alpha release like 8.04?  If you are, on the other hand, already a die hard Linux user and just new to Ubuntu or this forum, forget what I just said.  

Have you previously used lightscribe?  Although I use it all the time and have a bunch of lightscribe disks around, the results are less than spectacular and write times are in the range 8 to 24 minutes, depending on how much of the disk surface is being written.  I also find that writing lightscribe disks in Linux takes about 50% longer using Lacie's 4L writing program than writing equivalent disks in Windows XP using Nero.  (Nero Linux does not do lightscribe, unfortunately).

Jerry

---

### Post by trugreg on 2007-12-28
I am totally new to Linux. When I decided to start I picked Ubuntu from reading on the Internet. I just got 8.04 thinking I should start with the newest system. What version should I use? What can I do now I have installed on my system. Any ideas

---

### Post by Afkpuz on 2007-12-29
Just download version 7.10, put in the disc and reboot.  Click the install icon and tell it to use whole disc.  As for light scribe, the application is installed in /opt/lightscribe

To add to your launch menu, Right click on "applications" and select edit menus.  Click on accessories (or wherever you want it) and select "new item". 

Name it something like "lightscribe labeler" and browse to the program in /opt.  That should do it

---

