---
title: "Need help with fstab command."
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by uglowp on 2007-06-27
Hi,
 
I am a knew Ubuntu user recently switching my Vaio from Vista to Ubuntu.

Love Linux and the install went well.

Only problem is trying to access USB drives.

Read a lot of the posts and still can't get access.  I think I am putting in the wrong "mount Point"

Anyway here is the contents of my fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dv/sda1
UUID=a1b148ab-13c6-4d53-9106-e3442c68f190 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=5d72ad3a-4a4e-4b64-91f1-f78cacfb6da7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
# Acomdata USB Drive 111.7 GB
/dev/sdb5	/media	ext3	user	0	2

My problem is with the last line.  I want to mount this drive and have rw access to it.

The drive mounts but I can't rw to it.

Any idea how I can change the command to get me rw access?

( I have also tried the above command using " UUID=83c9bd71-373e-4e41-9fef-010098616cc5 " in place of dsb5 with the same results)

Thank you!

---

### Post by paradoxni on 2007-06-27
what filesystem has the usb drive been formated in? I had an external usb drive formated in NTFS, that was detected automatically when plugged in, but only in readonly. I installed the NTFS writable mounter with Automatix and enabled it for external drives.

---

### Post by Inxsible on 2007-06-27
> **uglowp said:**
> Hi,
 
I am a knew Ubuntu user recently switching my Vaio from Vista to Ubuntu.
 
Love Linux and the install went well.
 
Only problem is trying to access USB drives.
 
Read a lot of the posts and still can't get access. I think I am putting in the wrong "mount Point"
 
Anyway here is the contents of my fstab file:
 
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dv/sda1
UUID=a1b148ab-13c6-4d53-9106-e3442c68f190 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda5
UUID=5d72ad3a-4a4e-4b64-91f1-f78cacfb6da7 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto 0 0
# Acomdata USB Drive 111.7 GB
/dev/sdb5    /media    ext3    user    0    2
 
My problem is with the last line. I want to mount this drive and have rw access to it.
 
The drive mounts but I can't rw to it.
 
Any idea how I can change the command to get me rw access?
 
( I have also tried the above command using " UUID=83c9bd71-373e-4e41-9fef-010098616cc5 " in place of dsb5 with the same results)
 
Thank you!
 
You are right when you say its a problem with your mount_point. Your mount point needs to be /media/AcomData or something not just /media.
 
also since this is an external drive, you should use pmount to mount it. Pmount will mount it under /media and you do not need to have fstab entries. It will also auto-mount it the moment you connect your external drive.
 
If you need more info on how to mount external drives using pmount, post back and I will help you out.

---

### Post by moore.bryan on 2007-06-27
[I]you first need to have a directory IN /media in which to mount the usb drive.  you can name it anything.  to have your usbdrive mount in /media/xhd (short for external hard drive), you can do this:
```

sudo mkdir /media/xhd
sudo nano /etc/fstab

```
once in your fstab file, add the following line to replace your previouse /dev/sdb5 entry:
```

/dev/sdb5     /media/xhd     auto     defaults     0     0

```
that should work for you.  although it's not necessary, to keep things aligned in the fstab file, you might want to hit "tab" after each of the entries.
post if you have any problems.
[/I]

---

### Post by Inxsible on 2007-06-27
> **moore.bryan said:**
> *you first need to have a directory IN /media in which to mount the usb drive. you can name it anything. to have your usbdrive mount in /media/xhd (short for external hard drive), you can do this:*
```

*sudo mkdir /media/xhd*
*sudo nano /etc/fstab*

```
*once in your fstab file, add the following line to replace your previouse /dev/sdb5 entry:*
```

*/dev/sdb5     /media/xhd     [COLOR=red]auto[/COLOR]     defaults     0     0*

```
*that should work for you. although it's not necessary, to keep things aligned in the fstab file, you might want to hit "tab" after each of the entries.*
*post if you have any problems.*

 
The word auto should be ext3 actually

---

### Post by moore.bryan on 2007-06-27
> **Inxsible said:**
> The word auto should be ext3 actually
*i found on my machine, with a 180gb western digital external usb drive formatted ext3, fstab wouldn't mount it unless is was set to "auto."  in know, strange, but what can ya do...*

---

### Post by Inxsible on 2007-06-27
> **moore.bryan said:**
> *i found on my machine, with a 180gb western digital external usb drive formatted ext3, fstab wouldn't mount it unless is was set to "auto." in know, strange, but what can ya do...*
 
You are right, it happnes sometimes. When you have "auto" it automounts but you still need to specify the filesystem on that partition..
 
so the line should then have been
 
```
/dev/sdb5 /media/xhd ext3 defaults,auto 0 2
```

---

### Post by moore.bryan on 2007-06-27
> **Inxsible said:**
> You are right, it happnes sometimes. When you have "auto" it automounts but you still need to specify the filesystem on that partition..
[i]not necessarily.  my fstab mounts my external usb with the 
```
/dev/sdc1     /media/xhd     auto     defaults     0     0
```
line.
[/i]

---

### Post by Inxsible on 2007-06-27
> **moore.bryan said:**
> *not necessarily. my fstab mounts my external usb with the *
*```
/dev/sdc1     /media/xhd     auto     defaults     0     0
```*
*line.*

Does it also read the correct file system?
 
Anyway, if it works for you its great. I just have never seen a fstab entry without a file system specified and I dont know if there are any repercussions of not putting one there.
 
Again, I simply use pmount for my external drives. so I do not need fstab entries for them at all. Keeps my fstab quite neat and concise. :)

---

### Post by moore.bryan on 2007-06-27
*the file system is specified, it's the first entry.  do you mean type?  that's the "auto" command in the line.  fstab with automatically figure-out the file type and adjust accordingly.  the only reason i use fstab is because pmount (for whatever reason) never mounted it properly and since i never detach it, i figured fstab was the way to go.*

---

### Post by Inxsible on 2007-06-27
> **moore.bryan said:**
> *the file system is specified, it's the first entry. do you mean type? that's the "auto" command in the line. fstab with automatically figure-out the file type and adjust accordingly. the only reason i use fstab is because pmount (for whatever reason) never mounted it properly and since i never detach it, i figured fstab was the way to go.*
 
Here is a [link]("http://doc.gwos.org/index.php/Understanding_fstab#Fstab_Examples") that shows some fstab examples. They list vfat or ntfs-3g or ext3 as the file system on that particular partition.
 
But like you said, specifying the file system is optional. So it works both ways !!! :)

---

### Post by uglowp on 2007-06-27
> **paradoxni said:**
> what filesystem has the usb drive been formated in? I had an external usb drive formated in NTFS, that was detected automatically when plugged in, but only in readonly. I installed the NTFS writable mounter with Automatix and enabled it for external drives.

File system is ext3.  Drive is mounted when installed but I can't get rw access.

---

### Post by uglowp on 2007-06-27
> **Inxsible said:**
> You are right when you say its a problem with your mount_point. Your mount point needs to be /media/AcomData or something not just /media.
 
also since this is an external drive, you should use pmount to mount it. Pmount will mount it under /media and you do not need to have fstab entries. It will also auto-mount it the moment you connect your external drive.
 
If you need more info on how to mount external drives using pmount, post back and I will help you out.


Yes thank you.  Tried all the advice regarding fstab and nothing works, can't get ubuntu to even recognize the drive now.

So I'll give pmount a try.

Any advice on a command line?

Thank you.

---

### Post by uglowp on 2007-06-27
> **moore.bryan said:**
> *the file system is specified, it's the first entry.  do you mean type?  that's the "auto" command in the line.  fstab with automatically figure-out the file type and adjust accordingly.  the only reason i use fstab is because pmount (for whatever reason) never mounted it properly and since i never detach it, i figured fstab was the way to go.*

Thank you for your help.

I tried all your suggestions but now can't even get ubuntu to recognize the drive.  Even after a cold boot.

Here is my fstab file as it now stands:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dv/sda1
UUID=a1b148ab-13c6-4d53-9106-e3442c68f190 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=5d72ad3a-4a4e-4b64-91f1-f78cacfb6da7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
# Acomdata USB Drive 111.7 GB
/dev/sdb5	/media/xhd	ext3	defaults,auto	0	2

Any suggestions?

Thanks again.

Phil.

---

### Post by Inxsible on 2007-06-27
> **uglowp said:**
> Yes thank you.  Tried all the advice regarding fstab and nothing works, can't get ubuntu to even recognize the drive now.

So I'll give pmount a try.

Any advice on a command line?

Thank you.

If you dont have pmount already you can install it like this

```
sudo aptitude install pmount
```

Then use pmount to mount your external drive.
```
sudo pmount /dev/sdb5 MyExternalDrive
``` Make sure you dont have a folder called MyExternalDrive already under /media since pmount actually creates the folder for you. You can of course use any name you like instead of MyExternalDrive.

You also do not need entries in the fstab. So if you have entries for sdb5 then make sure you remove or comment them first..or it might create unnecessary problems

---

### Post by djchandler on 2007-06-27
I had an external drive with 2 partitions, formatted NTFS, and never had a problem mounting it through USB. When I took that drive out and ran dban and put it in my Ubuntu box, I switched out the old Ubuntu boot drive and put it in the USB box. Now I can't get Ubuntu to mount the old Ubuntu boot drive through the USB. I'm guessing the answer is in previous posts, so there's no need to reply. I just thought I had an interesting comment to make. Since I'm ill and taking a dozen prescription medications, this may not be too lucid, as part of my illness includes temporary (I hope) dementia. I just hope the thread starter gets an answer after the experts get things agreed upon as to the best course of action. Very confusing to me, but that's understandable. At least I haven't had any narcotics yet today.

DJ

---

### Post by bodhi.zazen on 2007-06-27
> **Inxsible said:**
> Here is a [link]("http://doc.gwos.org/index.php/Understanding_fstab#Fstab_Examples") that shows some fstab examples. They list vfat or ntfs-3g or ext3 as the file system on that particular partition.
 
But like you said, specifying the file system is optional. So it works both ways !!! :)

> **moore.bryan said:**
> *the file system is specified, it's the first entry.  do you mean type?  that's the "auto" command in the line.  fstab with automatically figure-out the file type and adjust accordingly.  the only reason i use fstab is because pmount (for whatever reason) never mounted it properly and since i never detach it, i figured fstab was the way to go.*

LOL you two ;)

It depends on which column the auto is placed in :

/dev/sdxy /mount/point auto auto 0 0

The first auto, in the third column = auto detect file system. It works fairly well and is helpful for removable media where the file system can change.

The second auto, in the 4th column = (auto) mount at boot.

For most USB devices (removable media in general) it is best not to have an entry in fstab. An entry in fstab can interfere with gnome-volume-manager and pmount. If you do not have an entry in fstab the removable device *should* be handled automatically.

If you need (or want) to sepcify a specific usb device in fstab, best to use either :

LABEL=<Label>
UUID=<xxx>

in the first column. You can then specify what mount options you want in the 5th column.

HTH

---

### Post by Inxsible on 2007-06-27
No wonder i got confused. I was unaware of the auto keyword for the filesystem. I knew about the auto for automounting of the drive :roll:#-o

---

### Post by uglowp on 2007-06-27
> **Inxsible said:**
> If you dont have pmount already you can install it like this

```
sudo aptitude install pmount
```

Then use pmount to mount your external drive.
```
sudo pmount /dev/sdb5 MyExternalDrive
``` Make sure you dont have a folder called MyExternalDrive already under /media since pmount actually creates the folder for you. You can of course use any name you like instead of MyExternalDrive.

You also do not need entries in the fstab. So if you have entries for sdb5 then make sure you remove or comment them first..or it might create unnecessary problems

Thank you.

I was able to get pmount to mount the drive, however I still can't rw to it.

Any other suggestions?

Phil.

---

### Post by Inxsible on 2007-06-27
> **uglowp said:**
> Thank you.
 
I was able to get pmount to mount the drive, however I still can't rw to it.
 
Any other suggestions?
 
Phil.
 
I am sorry if you mentioned this already, but do you have ntfs-3g installed ?
 
It could be a permissions/ownership issue. you can change ownership by
 
```
sudo chown -R <your username>:<your group> <path where you mounted the drive>
```
 
so assuming that you username and group is phil, and that you mounted the drive at MyExternalDrive
```
sudo chown -R phil:phil /media/MyExternalDrive
```

---

### Post by uglowp on 2007-06-27
> **Inxsible said:**
> I am sorry if you mentioned this already, but do you have ntfs-3g installed ?
 
It could be a permissions/ownership issue. you can change ownership by
 
```
sudo chown -R <your username>:<your group> <path where you mounted the drive>
```
 
so assuming that you username and group is phil, and that you mounted the drive at MyExternalDrive
```
sudo chown -R phil:phil /media/MyExternalDrive
```

Hmm?

No, I don't have ntfs-3g installed.  Drive is formated as ext3.

---

### Post by Inxsible on 2007-06-27
> **uglowp said:**
> Hmm?
 
No, I don't have ntfs-3g installed. Drive is formated as ext3.
 
Well then you dont need ntfs-3g...unless you get another ntfs drive. :) Try the ownership thing and see if that works.

---

### Post by uglowp on 2007-06-27
> **Inxsible said:**
> I am sorry if you mentioned this already, but do you have ntfs-3g installed ?
 
It could be a permissions/ownership issue. you can change ownership by
 
```
sudo chown -R <your username>:<your group> <path where you mounted the drive>
```
 
so assuming that you username and group is phil, and that you mounted the drive at MyExternalDrive
```
sudo chown -R phil:phil /media/MyExternalDrive
```

Thank you very very much!!

That worked.

The drive is mounted and rw.

Thank you again for all your help.

Phil

---

### Post by Inxsible on 2007-06-27
Glad to help out. Nice to see you got it working :)

---

