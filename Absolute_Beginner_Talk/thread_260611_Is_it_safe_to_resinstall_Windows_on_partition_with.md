---
title: "Is it safe to resinstall Windows on partition without messing up Ubuntu?"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by Rizla on 2006-09-19
Latest problem, thankfully not Ubuntu related, but still a major hassle.  When i first built this new pc, i installed WinXp first on my primary hard drive and partitioned the dirve to dual boot.  As to be expected, I infected the hell out of windows by using some bad programs. ie. cracked/hacked programs I downloaded from Bittorrent.  I guess one of the programs i must have installed was spyware/trojan riddled and my XP OS is pretty much shot.  I ran antivirus on it, rootkit, detectors you name it i did it, but to no avail. Now i cant even log into the box, its automatically loggin me out.

Obviously I want to format that partition and reinstall it.  My question is, will it mess up my ubuntu parition or grub?  The last thing i want to do is not be able to boot into ubuntu.  I'm a full convert from XP at this point, the only reason I ever boot back into it is to use a program called Fruity Loops (music sequencer/tracker prog.)

Any advice on reinstalling Xp without messing my current ubtuntu setup?

---

### Post by tommcd on 2006-09-19
If you reinstall windows, it will overwrite grub and you will not be able to boot ubuntu. It is possible to reinstall grub if this happens. I'm not sure how to do that though, but see this thread:
[http://ubuntuforums.org/showthread.php?t=228690&highlight=reinstall+grub](http://ubuntuforums.org/showthread.php?t=228690&highlight=reinstall+grub)

---

### Post by tommcd on 2006-09-19
Here's a better source of info:
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

---

### Post by indytim on 2006-09-19
Rizla,

I just did exactly what you are seeking to do this last Saturday.  The only difference is that the Windows OPS was 2000Pro.  Here's the sequence of my re-building efforts:

1.  Run the necessary backups from your Window partition.
2.  Using GParted Live, I re-formatted my NTFS partition containing the Windows op system.
3.  Insert the Windows Install CD and go through the complete Windows installation.  (Note : obviously pay CLOSE attention to the  patition selection BEFORE initiating the installation.
4.  Load the hours-upon-hours of drivers etc.

I found through the entire process, that my Grub loader remained intact.  I did have a copy of Super Grub handy (burned to a CD - just in case).

Hope this helps.

IndyTim

---

