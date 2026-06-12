---
title: "HELP!!!!! Backtrack 5 gaffe!!!"
date: 2013-05-12
forum: Any Other OS
---

### Post by digitalsmurf on 2013-05-12
Ive got a laptop with no cd drive . (just to make this clear when someone tells me to use the windows 7 install disk). So i've created a partition through the disk management, shrunk a 20gb section and then partitioned it as h: . Then i've installed a mythbuntu system on it and installed backtrack 5. Windows continued to work fine UNTIL I rebooted and now it boots straight into backtrack/mythbuntu. I've gone into the boot menu on startup and it only gives me the option to boot from Samsung hdd, not from individual volumes. REMEMBER, no cd drive, no start up disk, nothing. Please someone help.. as i've got tonnes of work from my business on there. Remember, no cd drive, no startup nothing

---

### Post by grahammechanical on 2013-05-12
There are a few things that I am not clear about. Ok, No CD drive. I got that :) But how is it possible to install 2 Linux distributions on one 20GB partition? It seems that you are saying that you did that. I am guessing that you used the Wubi.exe to install MythUbuntu. Correct? How else would you install a Ubuntu flavour without a CD drive. USB memory stick?

[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Regards.

---

### Post by mastablasta on 2013-05-12
> **digitalsmurf said:**
> Ive got a laptop with no cd drive . (just to make this clear when someone tells me to use the windows 7 install disk). So i've created a partition through the disk management, shrunk a 20gb section and then partitioned it as h: . 

There is no H:\in linux. what you should have done is create empty disk space (unformatted)

> 
Then i've installed a mythbuntu system on it and installed backtrack 5. Windows continued to work fine UNTIL I rebooted and now it boots straight into backtrack/mythbuntu. I've gone into the boot menu on startup and it only gives me the option to boot from Samsung hdd, not from individual volumes. REMEMBER, no cd drive, no start up disk, nothing. Please someone help.. as i've got tonnes of work from my business on there. Remember, no cd drive, no startup nothing

backtrack 5 is another linux distribution. if you installed one over the othe rthere are bound to be issues. however if you split the disk then 20 GB is enough to install both (e.g. if you split 20 GB ino 10GB + 10GB).

so how did you install? i suggest you run boot repair tool [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

and then run bootinfo summary in that tool. post the results here using code tags or on soem pastebin or something.


furthermore backtrack is OLD! use Kali linux instead (the new renamed backtrack). or Backbox.

---

### Post by oldos2er on 2013-05-12
Moved to Other OS/Distro Support.

---

### Post by kevdog on 2013-05-12
Ok -- here's what I would first do -- nothing to get in a panic about.  Boot to your linux install and make sure your have the ntfs-3g package installed.
Type at the command line:
sudo fdisk -l

There should be an entry listing System Type as NTFS
This command will list all mounted and unmounted partitions on the drive.  Hopefully your windows partition will be shown (cross your fingers!!).  If the partition exists it can always be mounted, and grub.cfg can be altered to choose which partition to use as the boot partition. I'm betting you just haven't set grub up correctly and your windows partition still exists.

---

