---
title: "shortcut of hard drives"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by cmaranhao on 2006-10-01
i typed "sudo fdisk -l" in the terminal and i had this:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 1 2550 20482843+ 83 Linux
/dev/hda2 2551 9729 57665317+ 5 Extended
/dev/hda5 2551 9729 57665286 83 Linux

Disk /dev/hdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hdb1 132 24792 198089482+ 5 Extended
/dev/hdb5 132 24792 198089451 83 Linux

Disk /dev/hdd: 17.3 GB, 17340000256 bytes
255 heads, 63 sectors/track, 2108 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hdd1 1 261 2096451 82 Linux swap / Solaris
/dev/hdd2 262 2108 14836027+ 5 Extended
/dev/hdd5 262 2108 14835996 83 Linux


i want to have a shortcut (like a folder) of the hda5, hdb5 and the hdd5 inside my home folder. how can i do that?

i am a noob, don't know much so be kind with me :???:

---

### Post by cmaranhao on 2006-10-01
no replies?? i need to bump this topic :D

---

### Post by Kateikyoushi on 2006-10-01
You can create symlinks.

For example you have hda1 in /media then the next command will create a hda1 "shortcut" in the home folder. Replace USERNAME with the actual username.

```
ln -s /media/hda1 /home/USERNAME/hda1
```

---

### Post by cmaranhao on 2006-10-01
i have not tried those lines yet because it might not be what i want..

i want to name this partitions like 

hda5 will be backup
hdb5 will be multimedia
hdd5 will be incoming

and i want them to appear inside my home folder as folders, each folder for each partition..:???:

---

### Post by christhemonkey on 2006-10-01
You need to have them mounted.
(which they should be, all in /media)

And then you can type:
```
ln -s /media/hda5 ~/Desktop/backup & ln -s /media/hdb5 ~/Desktop/multimedia & ln -s /media/hdd5 ~/Desktop/incoming
```

---

### Post by cmaranhao on 2006-10-01
> ln -s /media/hda5 ~/Desktop/backupup

that will make it appear in desktop right (i really don't know much about this, sorry all these questions)?

can i do it like this to make the folder appear inside home??

ln -s /media/hda5 /home/backup

---

### Post by christhemonkey on 2006-10-01
O right yes you can.

Allthough in /home is not actually **your** home directory.

/home/cmaranhao is your home directory (replacing cmaranhao with actual username)

The bash shortcut for this is ~/
So you should do:
```
ln -s /media/hda5 ~/backup 
```

---

### Post by zaflaucich on 2006-10-01
you have understood, but remember that your "home" dir is located in
```
/home/username
```
or more easier just
```
~
```

ooops just not fast enough

---

### Post by cmaranhao on 2006-10-01
yeah, i read that (about the ~ thingy in terminal for noobies :) )

thanks guys for your input

well, just did it like this:

ln -s /media/hda5 ~/backup

an icon appeared but also with this following message:

The Link "backup" is Broken. Do you want to move it to the Garbage Bin?
This link can't be used, because its target "/media/hda5" doesn't exist.

what should i do now?

---

### Post by christhemonkey on 2006-10-01
That means that /dev/hda5 isnt mounted at /media/hda5 thats all.

If you type 
```
mount -l 
```
It should tell you all the mount points for your partitions.
Then you can replace /media/hda5 with its actual mount point.

---

### Post by cmaranhao on 2006-10-01
after doing the mount -l it showed me this:

/dev/hda5 on /home/backup type ext3 (rw)
/dev/hdd5 on /home/incoming type ext3 (rw)
/dev/hdb5 on /home/multimedia type ext3 (rw)

so, how should i make them appear inside my home folder? is it something like this??

ln -s /dev/hda5 ~/backup
ln -s /dev/hdb5 ~/multimedia
ln -s /dev/hdd5 ~/incoming

i am asking before doing because if i mess up i don't know how to correct it ](*,)

---

### Post by christhemonkey on 2006-10-01
No should be somethingn like this:

```
ln -s /home/backup ~/backup 
```

Allthough, i dont think your meant to mount drives in your home folder, bad form an all that.
They are meant to be mounted in /media or /mnt.
Just my £0.02

---

### Post by cmaranhao on 2006-10-01
lol

to let you know, i don't know much what i am doing.. i once had linux but it was configured by a friend of mine at my will.. then i deleted linux to go with windows again (but windows SUCKS SO MUCH ). now i want linux again and this time i am tweacking it all by myself..

maybe i am not asking the best way (but i don't know any better too ).. what i want to do is to have a shortcut to my hard drives inside my home folder.. i don't know where they are mounted.. this is sort of confusing :???:

---

### Post by cmaranhao on 2006-10-01
just tried and i already have the harddrives inside my home folder :D :D 

one last thing though.. my backup partition and incoming partition, both have a lock in its icon.. my multimedia folder is normal.. how can i remove the lock from those two folders and why is it there?

---

### Post by christhemonkey on 2006-10-01
That means it is owned by the root user.
To change this (using the GUI) do this:
Type:
```
gksudo nautilus 
```
Then go to these folders, double click on them.
Right click >> properties and select change  the permission so the folder is owned by your user and can be read modified an executed by everyone.

---

### Post by cmaranhao on 2006-10-01
the root - filebrowser only have a desktop folder.. the ones i added aren't there so i cannot edit them

---

### Post by christhemonkey on 2006-10-01
You need to navigate to /home/YOURUSERNAME/ in the new  nautilus file browser.

(replacing YOURUSERNAME with the username you use to logon)

---

### Post by cmaranhao on 2006-10-01
nice, i've done it (not without your help)

many thanks man 8)

---

### Post by christhemonkey on 2006-10-01
No problems.


(wow just noticed iv done 1001 posts?! wtf?! when did that happen...)

---

