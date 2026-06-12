---
title: "Partition help"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by Trebuchet on 2007-01-21
I have decided to install Ubuntu 6.06 (used the LiveCD and was pretty impressed. It recognized all of my hardware and I even did a bit of web browsing and word processing) onto my desktop alongside my XP at least until I'm up to speed, and I need some help.

I need to partition off part of my 120 GB HDD for Linux, and figured 20 GB (including Linux swap file) should be enough? I've got plenty of room; the drive is new and has over 100 GB still free. Since I can't afford Partition Magic 8, how should I go about partitioning the drive? I can use DOS, but that won't establish the correct file format for Linux.

---

### Post by Pobega on 2007-01-21
20 GB should definitley be enough: I have my whole hard drive in use for Linux and I only use 9 GB, including all of the (2GB) of music I have stored.

Also, for partitioning the drive, the easiest method is to go into the Ubuntu LiveCD and run "gksudo gparted". GParted is probably the next best progrm next to cfdisk for partitioning (cfdisk sometimes doesn't recognize partitions correctly, so I really do prefer gparted whenever I can use it)

---

### Post by shoaibi on 2007-01-21
Just leave it to the Installation, Start the Install and from there you should be able to understand.
or check this link:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Paerez on 2007-01-21
Boot the live CD, Click on System (in the panel) then Administration, then GNOME Partition Editor (aka gparted).

There you can right click your windows partition and click "Resize" (you may have to click unmount first).

Then when you install, choose "partition the free space on the drive" (may not be exact wording).

---

### Post by Trebuchet on 2007-01-21
Thanks for the replies! :D 

OK, next dumb question: I've downloaded and burned the 6.10 .iso file onto a CD, but I get the impression it's not "ready for prime time" and would be better reserved for more experienced Ubuntu users. If that's so, how difficult will it be to upgrade if and when 6.10 "goes gold" assuming it's the next stable release? I've upgraded Windows numerous times, but never a Linux distro.

I'll be trying out Kubuntu 6.06 also.

---

### Post by Paerez on 2007-01-21
6.10 is stable. The current unstable is 7.04. 6.06 is called Long Term Support because patches will be released for it for a long time.

The upgrade from 6.06 to 6.10 was painless for me, I used the ubuntu updater to do it. You basically tell it to do a distribution upgrade and it handles the rest.

Unless this is going on a server, install 6.10. I use it on my laptop every day and it never crashes.

---

### Post by freebeer on 2007-01-21
Well, with 6.06 you get LTS - Long Term Support that basically means the version will continue to have support (upgrades, fixes, etc.) for 5 years from it's release.  I haven't tried 6.10, myself, so I can't really comment.

If you're thinking/planning ahead, you could try something that I did:

I resized my Windows partition to 20 Gigs on an 80 drive.  I then created 3 partitions on the remaining space.  Once partition for / (20 Gigs), 1 partition for swap (512 megs which is 2x the memory), and the balance for /home.

With this setup I could, theoretically, change/upgrade OS on the / partition without affecting the data on my /home partition.  (It's still recommended to back up, of course, before an upgrade/change.)

You might even want to consider a fourth partition, formatted as FAT32, thus allowing Windows and Unbuntu to share file space.  Lots of options.  :D

Another thing you might want to consider: Kubuntu is basically Ubuntu with the KDE GUI, whereas Ubuntu uses Gnome.  You can install KDE on regular Ubuntu and then have the option of booting into whatever GUI you want at the time.  I haven't tried this myself, so I don't have first-hand experience, but I've seen it posted on these forums often enough to think that its a stable and viable option.  If anyone has had different experiences, or has a better suggestion for partitioning, I'm all ears.  :D

---

### Post by Trebuchet on 2007-01-21
I've got 512 Mb RAM and the stuff I've read suggests the swap file should be 2 - 3X the RAM amount, but no larger than 500 Mb. So I guess I'll just use 500 Mb.

This was a pretty good system (PIII 1 GHz overclocked to 1.13) when I built it in January 2000, but it's really showing its age now. 512 Mb of RAM was a lot back when the dinosaurs ruled the Earth and most desktops had 64 or 128 Mb. While it runs XP just fine, a leaner OS like Linux might get me a few more good years out of it as a backup/work system. Microsoft will discontinue support for XP in about 2010.

---

### Post by CroEragon on 2007-01-21
It is wry stable, currently i have 5 Windows managers (including KDE) installed on what was just ubuntu, no problems with it. It is not experimental product, it is final relese that have as much chance to work as ubuntu. If you wanna do it there is no any danger in installing KDE. To do it run each line separately in terminal:
```
sudo apt-get update
sudo apt-get install ubuntu-desktop

```
After that restart x server wit CTRL + Alt + Backspace (save all unsaved documents). Then it will show login screen, there chose your windows manager you want and it will ask you to choose default and thats it.
Note: download is 250mb big and kubuntu-desktop is not just kde, it is kde, bunch of kde programs and kde settings together optimized for ubuntu.

---

### Post by Trebuchet on 2007-01-21
I've DL'd both the Ubuntu 6.10 and Kubuntu 6.10 .iso, although I haven't burned Kubuntu onto a CD yet. But since Ubuntu 6.10 is solid, I'll use that instead of the 6.06.

---

### Post by Paerez on 2007-01-21
Definitely do the 3 partition scheme with /home on a separate partition!

As for firefox bookmarks, File->Export then find bookmarks.

---

### Post by Trebuchet on 2007-01-21
Well, my install attempt failed - not sure why. And my 6.10 image was apparently flawed; my system couldn't even see the CD. Back to the drawing board... :(

My Firefox has only an Import under File, no Export. I finally found the bookmarks and moved a copy of the file to a flash drive; I might be able to Import from that.

---

### Post by Paerez on 2007-01-21
you can always install 6.06 (takes 20min) then instead of doing a regular upgrade to update your system, tell it to jump straight to 6.10.

---

### Post by Trebuchet on 2007-01-21
It was my 6.06 install that failed.

Maybe I misunderstood - Should I run gparted from the LiveCD to partition the drive prior to beginning the full install? I thought the install process took care of that?

---

### Post by houstonbofh on 2007-01-21
I have a few points for you.

6.06 vs 6.10 - Several defaults changed so a 6.06 upgraded will be different from a 6.10 clean install.  6.10 has Firefox 2.0 which is reason enough to get it. :-)  I have several systems (including a few servers) and I have upgraded (or installed) to 6.10 on all but 2.  Those 2 are headless servers.  I have found it rock solid.

Gnome vs KDE - Ubuntu is developed and tested primarily in Gnome.  Gnome has the most GUI administrative tools.  KDE has had some bugs not found in the Gnome version. (Like the Upgrade to 6.10, and WLan Assistant)

Partitions - Everyone says different things, But I just split the hard drive in half.  I do not use "a fat32 partition to transfer files" because it further fragments my hard drive.  I use the tools in [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html) and [http://ubuntuforums.org/showthread.php?t=142481](http://ubuntuforums.org/showthread.php?t=142481) to read and write NTFS from Ubuntu, and ext3 fs from Windows.  As to swap, if you want to suspend properly, you swap must be bigger than your memory.  I would make it a gig.

Installs - I have to defer to the cat. [http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

