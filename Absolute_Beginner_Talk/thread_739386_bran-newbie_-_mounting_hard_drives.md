---
title: "bran-newbie - mounting hard drives"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by ktronicon5 on 2008-03-29
Greetings! i just got rid of windows and installed ubuntu 7.10 and am having trouble mounting my 2nd internal hard drive, the one with all my files on it (which i would very much like to recover). seems like a comon problem; i have searched many posts but still can't figure it out. first i got the "cannot mount volume - unclean shutdown - NTFS is marked to be in use" message, then i installed NTFS-config, ran it, for some reason told it to write to both internal and external devices, then my device suddenly stopped appearing in "places - computer," i don't know why. anyway, here's where i am now:

ktron@ktronicon5:~$ sudo mount -t ntfs-3g /dev/sdb1 /media
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media ntfs-3g defaults,force 0 0
ktron@ktronicon5:~$ sudo -t ntfs-3g /dev/sdb1 /media -o force
sudo: illegal option `-t'
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
ktron@ktronicon5:~$ sudo mount -t ntfs-3g /dev/sdb1 /media -o force
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.

what does that mean? where'd my hard drive go?
thanks!

---

### Post by ktronicon5 on 2008-03-29
Whoa there, i just found all my files in the /media directory. so... i guess i need to mount my drive properly right?

---

### Post by Barrucadu on 2008-03-29
Don't mount things in the /media directory, make a subfolder. /media is where USB things and suchlike are mounted when connected, so having the contents of a disk in there makes it a bit messy, and I'm not sure if it would work properly.
Also, if the disk is permamently there, it is conventional to use a subfolder in /mnt for internal drives, leaving /media for removable ones.

---

