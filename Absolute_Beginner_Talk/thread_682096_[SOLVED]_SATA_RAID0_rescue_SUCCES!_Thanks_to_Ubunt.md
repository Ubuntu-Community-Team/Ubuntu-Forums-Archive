---
title: "[SOLVED] SATA RAID0 rescue SUCCES! Thanks to Ubuntu and you guys"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by Desperate on 2008-01-29
Starting my XP pro and nothing goes anymore even the rescue from hard disk is not accessible.
BUT..... I had the Ubuntu live CD Gutsy 7.1 :lolflag:
It still took me over two weeks and lots of questions and reading to find out how it might be possible.
Then finally I could burn a few DVD's with my otherwise lost data

 I haven't tried Ubuntu yet, but when I rebooted, I had to pick the Windoze options just to see if..... and it did, now I'm two weeks behind in emails, but as soon as I'm done I'll study the how to install Ubuntu on this machine and post the steps I took to re activate my XP volume, so others might have this great feeling too :)

I'll have to change the name though, not true anymore!:lolflag:

Thank you all for the help and motivation when things looked dark and hopeless.

Happy camper here now, saved 12.7 gig of irreplaceable pictures this way.

**_Edit:_**
After loading/installing DMRAID I opened a terminal to type:
ubuntu@ubuntu:~$ sudo dmraid -ay
RAID set "isw_bccebhcagd_RAID0" already active
RAID set "isw_bccebhcagd_RAID01" already active
ubuntu@ubuntu:~$ sudo mkdir /media/windows
ubuntu@ubuntu:~$ sudo gedit /etc/fstab
** and added the line:
** /dev/mapper/isw_bccebhcagd_RAID01 /media/windows ntfs-3g defaults,force 0 0 
** and saved it of course
ubuntu@ubuntu:~$ sudo mount -av /dev/mapper/isw_bccebhcagd_RAID01
ubuntu@ubuntu:~$ 
** And there was my hard disk on the desktop :lolflag:

Simple, but I had to figure it out myself with help of the forum here what would happen and what would change. Nothing on the hard disk(s) and windows started up as always. 
**Now if you try this, read up on it first and check what you are doing. I can not accept responsibility for the result that you get on your system.**
Good luck
Richard

---

