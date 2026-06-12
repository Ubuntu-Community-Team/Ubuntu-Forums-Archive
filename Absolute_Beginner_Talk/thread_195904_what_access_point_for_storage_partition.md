---
title: "what access point for storage partition?"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by johnthejack on 2006-06-13
I have a 60GB drive. I have partitioned with 9+ for ubuntu, 730 for swap. I have formatted 46+ as FAT32. I want to enable. I have several times tried this and afterward found myself locked out and forced to do a fresh install. What access point should I use please?

---

### Post by uzi09 on 2006-06-13
[QUOTE=johnthejack]I have a 60GB drive. I have partitioned with 9+ for ubuntu, 730 for swap. I have formatted 46+ as FAT32. I want to enable. I have several times tried this and afterward found myself locked out and forced to do a fresh install. What access point should I use please?[/QUOTE]

i'm sorry, but this is ***VERY*** hard to understand!

what do you mean you want to enable??? what would you like to enable? where are you locked out from??

if you're looking for help in installing ubuntu please see this guide:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

otherwise, please rephrase and post.

---

### Post by johnthejack on 2006-06-13
My apologies for the lack of clarity. I go system/Administration/Disks. The disks manager comes up. I select the Partitions tab. Listed as partition3 is device /dev/hda/3. Access path is currently none. Status is inaccesible. The option available is "enable". I presume to gain access to this "46.15GB (free space not available)" I need to type in an access path and then enable. I have done this  a few times. Each time I have selected e.g. /home I return to my screen and can access absolutely nothing. It is as though the system is on one partition and I'm stuck on the new blank one and can't do anything. The only solution I could come up with is another fresh install, so I don't want that to happen again.

---

### Post by glinsvad on 2006-06-13
I have an identical setup, well with a larger swap and a tiny ntfs for winxp - don't know why really ;)

During install I simply went with /media/storage for my FAT32 and afterwards edited fstab
```

sudo gedit /etc/fstab

```
Just edit the line looking like this (might not be hda3, just alter that part):
/dev/hda3 /media/storage vfat defaults 0 0
Into:
/dev/hda3 /media/storage vfat umask=000 0 0

There are plenty of other setting that might work with FAT32, but "umask=000 0 0" is recomended in the Ubuntu Help...

EDIT: Oh yearh, mounting in /home is kind of a no-no since it's a special "system-folder". You can always mount in /media/something and then create a symbolic link in home like this
```

ln -s /media/storage /home/storage

```

---

### Post by steve.horsley on 2006-06-13
You do NOT want a FAT partition as your home partition - FAT doesn't support the unix file permissions flags. Ubuntu seems to want to put everything in /media, so perhaps /media/hda3 or /media/fat would be a good choice. 

You may need to create the directory that you will mount to with the command:
**sudo mkdir /media/fat**

You may also need to tinker with the fstab entry so that all users can access the drive. See this web page:
[http://www.krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide#Windows](http://www.krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide#Windows)

---

### Post by johnthejack on 2006-06-13
Ok thanks for the replies. I set the access point as /media/fat and enabled, and that seems to have worked. (Now if I could only get my wireless to work, but that's another problem.)

---

### Post by uzi09 on 2006-06-13
try this:
[http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)
and its wiki....
[https://wiki.ubuntu.com/WifiDocs/NetworkManager?action=show&redirect=NetworkManager](https://wiki.ubuntu.com/WifiDocs/NetworkManager?action=show&redirect=NetworkManager)

---

