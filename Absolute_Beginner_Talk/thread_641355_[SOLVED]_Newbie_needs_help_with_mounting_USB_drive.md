---
title: "[SOLVED] Newbie needs help with mounting USB drive"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by brett611 on 2007-12-15
I have no experience with Terminal & its commands.  Fstab, etc are a mystery to me...

I just installed Ubuntu 7.10, cleaning out XP.  Everything has worked above my expectations except for when I've tried to connect my 2 external USB hard drives.

The first is a WD 500gig "My Book".  The first time I plugged it in it worked fine but after a reboot it is unaccessable.  It appears as an icon on the panel, stating "unmounted".  If I click it and select mount I get the following error: Unable to mount the volume 'My Book'.  details:  mount_point cannot contain the following characters:  newline, G_DIR_SEPARATOR (usually /)?

The 2nd is a Maxtor III Onetouch, which requires its own software as it does backup and synch stuff.  I installed Wine and have run the Maxtor setup software a few times but it fails right at the end with an error of: Feature Transfer error.  Error:  -1627 ERROR_FUNCTION_FAILED

I've read beaucoup "instructions" on mounting but they all assume I have a clue.  I cannot specify what these drives are called when typing a mount command as I have no idea what the system thinks they're called.

Help is most appreciated as I thought I was being smart by not dealing with a dual boot system and moving all files to these USB drives.  Now it appears the jokes on me.

Thanks!!

---

### Post by PmDematagoda on 2007-12-15
Do this:-

1) Open the file manager in Root mode using:-
```

gksudo nautilus
```

2) Navigate to the /media directory and create a new folder(It is better if there are no spaces).

3) Then do:-

```
sudo ntfs-3g /dev/sdg1 /media/nameofnewfolder -o force
```

That should fix the problem.

---

### Post by Pumalite on 2007-12-15
Too late...

---

### Post by brett611 on 2007-12-15
Ok.  Here's what happened:

brett@brett-desktop:~$ sudo ntfs-3g /dev/sdg1 /media/WDMyBook -o force
[sudo] password for brett:
Failed to access '/dev/sdg1': No such file or directory

---

### Post by PmDematagoda on 2007-12-15
Post the result of:-

```
sudo fdisk -l
```

---

### Post by Josh1 on 2007-12-15
Just a note, the Maxtor III One Touch apparently **does not** work with Ubuntu.

Have you tried rsync? I use it on my laptop to backup to my backup drive, it only backs up files that have been changed.

Have a look at:
[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)

---

### Post by brett611 on 2007-12-15
brett@brett-desktop:~$ sudo fdisk -lu

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   385078049   192538993+  83  Linux
/dev/sda2       385078050   390716864     2819407+   5  Extended
/dev/sda5       385078113   390716864     2819376   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf49c60bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768064   488384001    c  W95 FAT32 (LBA)
brett@brett-desktop:~$ sudo mount -t ext3/dev/sdb/media/WDMyBook
brett@brett-desktop:~$ 

Also - I launched Synaptic for the first time and got this:
Starting without Administrative privileges.  you will not be able to apply any changes.  But you can still expor tthe marked changes or create a download script for them.

That I really don't get as I am the only user on the machine and have confirmed that my password works when having to enter it for other 'admin' tasks

---

### Post by Pumalite on 2007-12-15
I think MyBook comes with Microsoft software included.

---

### Post by SunnyRabbiera on 2007-12-15
yeh those western digital ones are unreliable... maybe you can get a seagate to replace it

---

### Post by brett611 on 2007-12-15
The WD My Book has 400gigs of pictures and music so I can't toss it

---

### Post by PmDematagoda on 2007-12-15
Try using Gparted to really find out what is really in your HDD, install it using:-

```
sudo apt-get install gparted
```

When you open it could you post a screenshot of the external drive as Gparted sees it?

---

### Post by brett611 on 2007-12-16
Sorry for the delay...life got in the way.:)

Attached is screenshot of what I get when I try to run gparted.  I am the only user on the machine so I don't get why I get this message

thx

---

### Post by Pumalite on 2007-12-16
sudo gparted

---

### Post by MrSpiffdifilous on 2007-12-16
not so much a technical Terminal command based answer here but...when i switched of from XP my eSATA drive wouldnt work because ubuntu didnt recognize the hardware required for it so I just canibalised the drive and installed it internally. works beautifully now. Of course this is only an option if 1. you have the guts to tear apart your hardware 2. you have a desktop and not a laptop and 3. you have open spots/connections. Just some food for thought.

---

### Post by brett611 on 2007-12-16
d'oh...right. thx  :confused:

---

