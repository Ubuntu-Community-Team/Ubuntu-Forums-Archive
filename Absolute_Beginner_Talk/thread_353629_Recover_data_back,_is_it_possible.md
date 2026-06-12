---
title: "Recover data back, is it possible?"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by sankarv on 2007-02-04
I have tried to install a flavour of linux on my hard disk . Unfortunately i accidently erased my harddisk during installation. My original file system of 80 GB harddisk was 


20 GB WinXP fat32
4 GB fat32 
4 GB fat32 
4 GB fat32 
4 GB fat32
10 GB Ubuntu linux.


After installing that linux (not fully that too, i restarted suspecting that it was erasing my hard disk at that time it was completed inode structure) i booted the system and just a blank screen appeared and nothing was happening. i dint see any of these partitions booting from any live cd linux.


So i installed ubutu again for 8GB size.(i badly need OS for my machine)


Now my query is is it possible to recover the data from the fat partitions. I dont think my reinstallation operation was sensible. But still is there a way or are there any softwares (possibly freewares linux based) with which i can recover the data from my fat partitions (i dont think think there are any partitions except the new ext3 FS for 8GB).


Any suggestion would help me a lot.

---

### Post by scrooge_74 on 2007-02-04
Did you erase each partition?  Did you mount those partitions? 

Maybe some of this could help, but I am not sure of it

[http://trinityhome.org/Home/index.php?wpid=1&front_id=12](http://trinityhome.org/Home/index.php?wpid=1&front_id=12)

or this 

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by jml on 2007-02-04
If you have access to a computer with an Internet connection.  (dumb comment, if you didn't, you would not be posting.)  Check out this link.

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

This is a live Linux distro designed retrieve data and restore a broken system.  I would suggest that you concentrate on your data files.  How much you can recover will depend on how much of your hard drive was overwritten by the install.  Focus on your data.  After you recover as much as you can, then do a clean install of first Windows if you still need it, then Ubuntu.  Pay particular attention to the dialog boxes.  If I am correct, the default choice is to install Ubuntu onto your entire hard drive.  Don't choose this option, or you will be going through this exercise again.  Good luck.

Joe

---

### Post by sankarv on 2007-02-05
Thanks a lot for the help. I will try that.

---

### Post by sankarv on 2007-02-05
With testdisk i could recover major part of my data since there was no rewriting over those cylinders (sda5, sda6, sda7 and sda8 deleted partitions of fat32 format) i suppose. Atleast partly(almost 75%) i recovered my data (i could not recover from sda1 since i installed again linux over it (testdisk reported those areas as bad sections) ). Thanks a lot for the help.

---

### Post by scrooge_74 on 2007-02-05
Good to know that you at least manage to get some of it back

---

