---
title: "Need help giving WinXP users on network access to hde1"
date: 2006-06-14
forum: Absolute Beginner Talk
---

### Post by Triad773 on 2006-06-14
Hi everyone- need help mounting a FAT32 drive so other Windows users can access/modify that drive, that is on the same machine as I have Ubuntu on. The machine was originally run on Win2k, but when that OS was corrupted, I refused to give in to BGates and the dark side (again). I have 3 physical drives on the machine, each about 20GB. One is dedicated to Ubuntu, but the other two were old FAT32 drives I was using for data backups from another 3 WinXP machines.

I have only had Ubuntu on there for a few days, but have Samba and file sharing working (can see WinXP machines from Ubuntu, can see the Home directories from WinXP machines for respective shares in Samba on the Ubuntu drive).

My question is: is there a way I can share the other FAT32 drives that are also on the Ubuntu machine with the (3) other WinXP machines?

*General comment: thanks for those who posted on getting Samba started- very informative and it works great! Already I am doing more with this distro then any other I have had (including Mandrake, Yellow Dog, and Redhat).*

Thanks in advance, and I look forward to any of your responses.

Regards

Triad773

---

### Post by Triad773 on 2006-06-14
Hi again- just a little bumpage hoping to get a response on this. I understand patience is not only a virtue but required when learning an OS.

Any thoughts or opinions welcome also.

Thanks again

Triad773

---

### Post by rbgCODE on 2006-06-14
you just need to goto system > administration > shared folders and add what you want to share, and just make sure that you setup the smb.conf correctly

---

### Post by Triad773 on 2006-06-14
Cool beans (no pun intended :)) rgbCode! Will try it when I get home.

Thanks

:D 

Triad773

---

### Post by Triad773 on 2006-06-15
Well that hadn't worked as well as I had hoped. I saw another thread where it will help ( [http://ubuntuforums.org/showthread.php?t=195148](http://ubuntuforums.org/showthread.php?t=195148) ) but I am not understanding where these disks reside in the system. Is it in /media/windows/name of drive?

When I used Mandrake it seemed like it was a little easier (but it was some time ago) as this could be set up in the graphical interface, but here using the command line is proving a challenge :confused: 

Any help/opinions welcome, and again thanks.

Triad773

---

### Post by pt4117 on 2006-06-15
I'm a total noob, but I just did this very thing.  I ran into a couple of problems.  The first was that my drives weren't mounting.  I would go into Places> computer, and see the drive but it wasn't mounted.  I went to 
[http://easylinux.info/wiki/Ubuntu#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite](http://easylinux.info/wiki/Ubuntu#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite)
That got my fstab right, but I still had to run 
sudo mount -a
in order to mount the drive.  

If you copy and paste make sure you change the hd* I forgot to do that, and it caused me a headache.  I also fogot that everything is case sensitive, and that was another little headache.  Like I said I am a total noob.  

After I got the drive mounted I still had a problem.  I ended up having to adjust my smb.conf.

---

### Post by Triad773 on 2006-06-15
Thanks pt4117- I am feeling really new myself despite some experience. Ubuntu is new to me so I guess that makes me start over in some ways. Will try when I get home tonight and hope for the best.

:D 

Cheers

Triad773

---

