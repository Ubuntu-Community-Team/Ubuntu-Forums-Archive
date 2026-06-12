---
title: "terminal newb needs help"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by ride1226 on 2007-01-21
ok so i go to applications then open the terminal...it opens with the following written in it...

chris@chris-desktop:

so im attempting to mount my windows partition so i can listen to music off of it and just make my life a little easier...but iv nvr used command line before as this is my second day on linux....

im following a guide and when i type the code i get this...

chris@chris-desktop:~$ sudo fdisk -l
Password:

it will not let me type my user name password in and actually wont let me type anything...what am i doing wrong any help would be greatly appreciated.

---

### Post by meng on 2007-01-21
The password does not echo to screen, not even as asterisks. Just type in your user password and press Enter

---

### Post by ride1226 on 2007-01-21
wow. that was easy...now i hope the rest of this goes as easy. thanks.

---

### Post by ride1226 on 2007-01-21
this is what im up to now...and i am tryin to follow the psychocats guide...im lost right here

  GNU nano 1.3.10             File: /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


any help? thanks.

---

### Post by meng on 2007-01-21
I can't help without some more information:
- where is your windows partition?
(sudo fdisk -l)
- are you happy with just read access, no write capability (please say yes, this makes life easier)?

---

### Post by ComplexNumber on 2007-01-21
**ride1226**
do you have a link to the psychocats guide? also, what are you hoping to achieve by editing the fstab file?
btw before you do anything with fstab, MAKE A BACKUP OF THE ORIGINAL FILE FIRST. call it something like fstab.bk.

---

### Post by ride1226 on 2007-01-21
i reopened terminal and typed the command and here is what is read out.

chris@chris-desktop:~$ sudo fdisk -l

Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       23110   185631043+   7  HPFS/NTFS
/dev/hda2           23111       24415    10482412+  83  Linux
/dev/hda3           24416       24792     3028252+   f  W95 Ext'd (LBA)
/dev/hda5           24416       24792     3028221   82  Linux swap / Solaris
chris@chris-desktop:~$


i would love to be able to write to it so when i find somethin cool i can throw it in the windows partition....my main concern is being able to access my itunes music folder and play the music with amarok...if u can help me be able to do that thatd be great...and if u can go a little further as to how to write to the windows partition thatd be great too. thanks again.

---

### Post by ride1226 on 2007-01-21
> **ComplexNumber said:**
> **ride1226**
do you have a link to the psychocats guide? also, what are you hoping to achieve by editing the fstab file?
btw before you do anything with fstab, MAKE A BACKUP OF THE ORIGINAL FILE FIRST. call it something like fstab.bk.


here is the link to the guide... [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

im tryin to be able tot access my windows partition so i can listen to the music off of it and write things to my documents on the windows partition....i have no idea how to make backups or even anything about this for that matter...im however greatful for the help here as id love to completly leave windows behind once i have a grip on linux.

---

### Post by meng on 2007-01-21
Your WIndows partition is /dev/hda1

Be warned that NTFS read-write access is still new, some (like me) would say experimental, so use at your own peril! (NTFS read-only access is quite safe though.)

Check out this guide:
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

but essentially, you need to do four things:
1. Enable universe repositories. [https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)
2. Install ntfs-3g (sudo aptitude install ntfs-3g)
3. Create a mount point for the windows partition (sudo mkdir /media/windows)
4. Add this line to your /etc/fstab:
/dev/hda1     /media/windows    ntfs-3g       defaults,locale=en_US.utf8       0       0

---

### Post by ComplexNumber on 2007-01-21
well, if its any consolation, i've installed all the relevant ntfs stuff, and i can't get write access to windows either. then again, i don't really need to.

---

### Post by ride1226 on 2007-01-21
that guide got me into my partition extremly easy...im actually excited now....first succesful use of linux. thank you. now this mean i can not write to it correct? only read? what would i need to do to be able to write to that partition?

---

### Post by meng on 2007-01-21
ntfs-3g will read and write
ntfs will only read

---

### Post by ride1226 on 2007-01-21
i tried the coding u left to install the ntfs-3g and it didnt install for w.e reason. any ideas? or would u like a readout of what i did in terminal to make it easier? thanks again.

---

### Post by meng on 2007-01-21
Did you enable new repositories? (universe)
then
sudo aptitude update [didn't mention that step, it helps to do this]
sudo aptitude install ntfs-3g

EDIT: Wait, are you running Dapper or Edgy? If you're running Dapper, I suggest you do yourself a favor and just stick to read access only.

---

### Post by ride1226 on 2007-01-21
i am runnin 6.06 as i heard 6.10 had many issues...is it worth it to do the upgrade to 6.10 or just stick here. i didnt understand that repositories thing. as i read it explained what they were but not how to enable them...maybe i missed that. friggin Colts game is very distracting sorry. lol. thanks again for the help.

---

### Post by meng on 2007-01-21
Yeah don't mess with your system while you're distracted, that's just asking for a catastrophe to happen. You could play around with 6.10, but I think with your level of experience you'd be better off just sticking with NTFS read access for now and seeing how it goes. There are other ways to achieve what you want, and in fact the best way might be to create a THIRD partition for both Windows and Ubuntu to share, and make it ext3 (you can install a Windows program that will give Windows read-write access to ext3).

---

### Post by ride1226 on 2007-01-21
thats a good idea...ill leave it as is...i have read access not what i rly need to do is figure out how to get all the multimedia stuff working on here...should i make a new post elsewhere for help wit that or can you help me with that here? thanks again.

---

### Post by Buck2348 on 2007-01-21
[This link]("http://www.ubuntuforums.org/showthread.php?t=217009&highlight=install+ntfs-3g+the+easy+way") will guide you through the process of installing write access to the ntfs partition.  I've used it on four installations and never had any problem at all with it.  They usually say after the disclaimer about experimental, etc. that you can use it with no worries.  But as Meng said, I wouldn't do it while watching football.  ;) 

Buck

---

### Post by meng on 2007-01-21
New post is safer, after all what if I can't help? (I'll try though)

---

### Post by ride1226 on 2007-01-21
haha alright...i guess ill put it in the multimedia section...that seems most fitting. thank you for the help. also if this becomes to tedious u could catch me on AIM at ride1226. thanks again.

---

