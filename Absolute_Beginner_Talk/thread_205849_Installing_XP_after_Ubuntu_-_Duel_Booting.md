---
title: "Installing XP after Ubuntu - Duel Booting"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by Pavilion on 2006-06-29
Perhaps there may be others who are curious as to wheather or not it's possible install XP after Ubuntu, simply by first installing Ubuntu then installing XP.:-\" 

Well I tried it and are the results:

I was curious, and since I was going to upgrade this machine to dapper, I popped in the XP CD and gave it ago.  XP went through all the motions for the install, but when it got to the point where it had to decide where it was going on the hard drive it complained that it didn't reconize the Linux [0X83] partition.  It the gave me the option of deleating the Linux [0X83] partition [Breezy] or exit, I took the exit.  No harm done.:-\"   

Thought you might like to know.:):-\"

---

### Post by lamego on 2006-06-29
Your post is a bit misleading. What you have tried to do has nothing to do with dual boot.
Dual boot requires that you have at least 2 different partitions, one for each system. What you have tried was to install Windows XP over a disk which is dedicated to Linux. On such case the only option from the Windows install is to delete your existing partition.

---

### Post by cotcot on 2006-06-29
Once you made a partition available for XP install XP. This will override the MBR and give you direct XP on boot. You can afterwards install the Grub bootloader with the liveCD. Here are a couple of methods : [http://www.ubuntuforums.org/showthread.php?t=24113]("http://www.ubuntuforums.org/showthread.php?t=24113")

You further might need this trick [http://http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows]("http://http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows")

---

### Post by Apple 101 on 2006-06-29
I prefer this method for installing Windows after Linux: 
1. Save the grub MBR into a file using *dd*.
2. Install Windows.
3. Copy the Grub MBR file onto C:\.
4. Edit the boot.ini file to show something like: C:\ubuntu.lnx="Ubuntu Linux 6.06" (Save the boot.ini file).

Now you can load Ubuntu and other Linux distributions from the XP/Windows boot loader.

---

### Post by Pavilion on 2006-06-29
[QUOTE=cotcot]Once you made a partition available for XP install XP. This will override the MBR and give you direct XP on boot. You can afterwards install the Grub bootloader with the liveCD. Here are a couple of methods : [http://www.ubuntuforums.org/showthread.php?t=24113]("http://www.ubuntuforums.org/showthread.php?t=24113")

You further might need this trick [http://http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows]("http://http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows")[/QUOTE]

Thanks cotcot:  I simply wanted to pass along my experience in trying the process  as I described it in my post, nothing more.   However, the information you have offered is simply... awsome:cool:  I'll keep your info in a safe place:)

---

### Post by Pavilion on 2006-06-29
[QUOTE=Apple 101]I prefer this method for installing Windows after Linux: 
1. Save the grub MBR into a file using *dd*.
2. Install Windows.
3. Copy the Grub MBR file onto C:\.
4. Edit the boot.ini file to show something like: C:\ubuntu.lnx="Ubuntu Linux 6.06" (Save the boot.ini file).

Now you can load Ubuntu and other Linux distributions from the XP/Windows boot loader.[/QUOTE]

Thanks Apple 101:  I have one 6 gig machine I use as a test bed in an attempt to increase my Linux understanding, and no configuration remains for long on its hard drive.  You and cotcot have provided me an two very excellent reasons why I keep the machine available as a tinker toy:cool:

---

### Post by Pavilion on 2006-06-29
[QUOTE=lamego]Your post is a bit misleading. What you have tried to do has nothing to do with dual boot.
Dual boot requires that you have at least 2 different partitions, one for each system. What you have tried was to install Windows XP over a disk which is dedicated to Linux. On such case the only option from the Windows install is to delete your existing partition.[/QUOTE]

You are correct:cool:

---

