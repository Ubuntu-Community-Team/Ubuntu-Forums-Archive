---
title: "Changing the permissions for different partitions"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by Metaphor on 2007-09-26
Hi.

I'm starting to get in touch with the Ubuntu world, I've installed it hours ago.

But I'm having a problem related to permissions. I've searched and read many posts related to that but couldn't find the solution...

I have three partitions - one for the system and two other for data storage. What happens is I can't create folders in any of the partitions because it says I'm not the owner. When I right-click them and check permissions it says that the owner username is "root", and i can't change nothing.

How can I change this situation? It's very annoying...

Thx in advance.

---

### Post by reckless2k2 on 2007-09-26
please post the results from this terminal command


```
sudo cat /etc/fstab
```

this will tell us mount points and permissions..yadda..yadda

---

### Post by mikewhatever on 2007-09-26
Here you go [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_change_files.2Ffolders_permissions](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_change_files.2Ffolders_permissions)

---

### Post by Majorix on 2007-09-26
If that all confuses you, type
```
gksudo nautilus
```

And then you can right click any file/folder to change the owner. BUT! Changing the owner is generally not a good idea as some files or folders MUST be owned by root or the user on Linux systems. So while you are using gksudo nautilus, copy and paste those files in necessary places and don't try to change the owner. Thats what I would do in your situation.

---

### Post by Metaphor on 2007-09-26
This is what i get:

/etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=d758cfea-5f71-4941-a089-7ed7ad01f1de /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=6CE43C69E43C3822 /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=24A0A6B8A0A68FBA /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda4
UUID=9e0cf44f-320c-4f6a-8153-b10b7bb563f9 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
tiago@Tiago-Quarto:~$ 


And when i use the code sudo chown system_username /location_of_files_or_folders   it says : "changing the ownership of ... : file system - read-only

thx

---

### Post by Metaphor on 2007-09-26
> **Majorix said:**
> If that all confuses you, type
```
gksudo nautilus
```

And then you can right click any file/folder to change the owner. BUT! Changing the owner is generally not a good idea as some files or folders MUST be owned by root or the user on Linux systems. So while you are using gksudo nautilus, copy and paste those files in necessary places and don't try to change the owner. Thats what I would do in your situation.

when i do that it takes me only to the system partition, so i can't get to the file storage partition, where i have my stuff...:(

---

### Post by Terl on 2007-09-26
> **Metaphor said:**
> This is what i get:

/etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=d758cfea-5f71-4941-a089-7ed7ad01f1de /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=6CE43C69E43C3822 /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=24A0A6B8A0A68FBA /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda4
UUID=9e0cf44f-320c-4f6a-8153-b10b7bb563f9 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
tiago@Tiago-Quarto:~$ 


And when i use the code sudo chown system_username /location_of_files_or_folders   it says : "changing the ownership of ... : file system - read-only

thx

I assume you are asking about the media partitions (hda2 and hda5)?  If so, install (using synaptic) ntfs-3g and ntfs-config.  Use the config tool to allow write and read access and you should be set.  If I guessed the wrong partitions let me know.

---

### Post by Metaphor on 2007-09-26
> **Terl said:**
> I assume you are asking about the media partitions (hda2 and hda5)?  If so, install (using synaptic) ntfs-3g and ntfs-config.  Use the config tool to allow write and read access and you should be set.  If I guessed the wrong partitions let me know.

You're right! 

But when i start to run it it says it'll remount the hdd. Won't it erase any data? sorry about the ignorance!

---

### Post by Terl on 2007-09-26
> **Metaphor said:**
> You're right! 

But when i start to run it it says it'll remount the hdd. Won't it erase any data? sorry about the ignorance!

Nope, mounting is what you want.  Mount makes the drive available for you.  It works like a charm.  Remember ntfs-3g is not guaranteed to be 100% safe.  For sensitive things I make backups...just in case.

Don't apologize for questions we all have them

---

### Post by bodhi.zazen on 2007-09-26
> **Terl said:**
> Nope, mounting is what you want.  Mount makes the drive available for you.  It works like a charm.  Remember ntfs-3g is not guaranteed to be 100% safe.  For sensitive things I make backups...just in case.

Don't apologize for questions we all have them

First, ntfs-3g is out of beta and is considered stable or safe (this is a recent change from beta testing).

See this link to review testing/quality of ntfs-3g : [http://www.ntfs-3g.org/quality.html](http://www.ntfs-3g.org/quality.html)

Second, to run ntfs-config use :

```
sudo ntfs-config
```

Works like a charm.

---

### Post by Metaphor on 2007-09-26
Ok thx a lot for the help i'll try that things now.

---

### Post by Metaphor on 2007-09-26
It worked!

thx a lot for the help! :)

---

### Post by pitseleh on 2007-09-27
I'm actually in a similar situation! I have a separate internal hard drive with an NTFS partition that had been used just as a media storage for XP (never had an OS on it) in the past, and still currently a media storage, but now for Ubuntu.

My boyfriend wants to dual-boot XP and Ubuntu, so we need to move/back up some stuff onto this secondary drive before I reformat his primary drive. The problem, of course is that I do not have permission to write to this drive.

I latched onto the NTFS-Config thing because it worked for Metaphor. I installed the only NTFS package that showed up in my Add/Remove thing, "NTFS Configuration Tool." I mounted the drive through the config tool, but it only gave an error that had this to say:

Mounting /media/Spenelli failed.

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/hdb1': Operation not supported
Mount is denied because NTFS logfile is unclean. Choose one action:
   Boot Windows and shutdown it cleanly, or if you have a removable
   device then click the 'Safely Remove Hardware' icon in the Windows
   taskbar notification area before disconnecting it.
Or
   Run ntfsfix version 1.13.1 on Linux unless you have Vista.
Or
   Mount the NTFS volume with the 'ro' option in read-only mode.

And now I can't umount this drive, even if I enable or disable what I did in the config. I would assume on restart that it will be able to mount and unmount again, but I have not tried this. This stuff is beyond me, so if any of you can help that would be awesome!

---

### Post by Metaphor on 2007-09-28
Sorry to answer just now!

has you've seen i'm a newbie in ubuntu so i can't help you try to post a new thread with your problem sorry!

Good luck :)

---

