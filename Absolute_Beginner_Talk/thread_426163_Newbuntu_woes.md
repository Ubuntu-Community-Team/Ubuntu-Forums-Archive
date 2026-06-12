---
title: "Newbuntu woes"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by Lew8 on 2007-04-28
I've been a long time debian unstable user (7yrs).  I've dabbled with ubuntu here n there and as I was having some issues with a mythtv frontend system after a recent update, thought I'd take the opportunity to take a look at feisty.  A long story short, I tried 3 different cd images and had to pull some 'not for novice'  tricks out to get installed onto a std p4 gigabyte system.' .  Nothing crazy with the install, just swap & root on a single drive.  The MD5's were correct but the CD self examination gave the thumbs down, all 3 were the same, eventually command line install was the only way (5-6 hrs later)
The end result was very pleasing. Following the new feisty guide for mythtv frontend install, I had a system that is the best I've seen.  The boot time was incredible at around 35 sec's and shutdown even better.  No need for suspend2 here.  The NVIDIA drivers were also easier to install than SID. 
My mythtv backend has been in action for some 3 years and was getting a little unstable, I suspected the database was suffering from a few too many version upgrades and amateur hacks. With the install woes behind me, I thought I'd tray to rehash my 1TB backend system with feisty.   
I know this is absolute beginner, but as I more or less am with Ubuntu I could not find a more appropriate forum listing. I backed up the olde system to a new NAS server, testing it at the same time and embarked on a 7yr itch to a new distro for my main box.  Part of the reason for the upgrade was also that I'd been running software raid5 on the root partition for many years and wanted to use lvm ontop to better manage the storage.
Desktop The install of a raid5 with lvm root with raid1 boot was a little bumpy.  Lilo would not install, and grub did after some manual intervention from a console, but could not even load the initrd. A rescue and chrooted lilo install worked well (at least for a while...) .  Installed the rest if the mythtv backend and used tasksel for kde etc, but had trouble getting lock with a dvb card.  I know sometimes these cards need a cold start to initialize properly, so I cold started the machine and discovered it would not start, something to the tune of no rtc, failed to initialize console... kernel panic.  Recovered again using the server install CD and midfied the lilo append to read append="root=/dev/mapper/r5lvm-root pci=nomsi " ... nomsi being the addition. Yay back up again..Looks like a bug with 2.6.20, not necessarily an Ubuntu issue I suspect.  Twice now with 2.6.20 I've had systems that work & then mysteriously stop during initrd pre pivot root phase...
Anyway, I have the backend up, stole some stuff from debain to get the programme guide for mythtv automated, only to find I could'nt remotely connect to it!  I grant all on mythconverg.* to [email]mythtv@xxx.xxx.xxx.xxx[/email] but no banana.  Hmmm try phpmyadmin installs OK, but can't login as mysql root cycles.  Hmm... cookie problem? no the cookie lists in konq & ffox =>: seek documentation => 0.  Suspect bug  => investigate bug reporting & help  => well maybe if I spend some considerable time as an experienced user can I figure out how to use the bug report system => as novice newbie == too hard!  

So the report card from me is... (expecting one back on this post from someone... he he!)
OS looks good. B+
installer (does not get along well with newbie's) D
Installer handles lvm & raid5 root (almost) A (for almost)
phpmyadmin doesn't work with no way out D

This may be the last text ever written from my feisty main machine, before I return to the dark side (debian sid).
I came, I saw, I almost conquerred
P.S. what  happenned to the kde logon screen?  It's gdm, but without gdm installed.  I have kids who like to see their user icons and click.  Could not get this to work either.
I'll definitely keep the mythtv frontend  running  Ubuntu ;=)
Lew

PS PS
Just got session time out before submit => newbie == too hard again....

---

### Post by vanadium on 2007-04-28
Where you download the Newbuntu image (joke :lolflag: )

A newbie that for 7 years has been using Debian unstable ??? :lolflag: :lolflag: :lolflag: 

Anyway, your post isn't too clear for me and I don't see where exactly you have to stop using Ubuntu and return to the much more "user friendly" Windo... Debian.

One thing I can help you is the nice login screen with face browser. As a (real) newbie, I managed to install a nice face browser from Gnome art: a matter of downloading the tar and dragging the tar on the System - Administration - Login window tool. Anyway, I am with you: it is a bit strange that a nice themed face browser does not come with Ubuntu by default (I do not consider Gnome face browser "nice").

Concerning the install, I haven had any issue with a Dell Latitude laptop and a "generic" (and venerable in the mean time) pentium desktop with 256 K ram. Very strange you couldn't get phpadmin to work, with your experience.

---

