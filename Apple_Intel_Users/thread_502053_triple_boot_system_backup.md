---
title: "triple boot system backup?"
date: 2007-07-16
forum: Apple Intel Users
---

### Post by thefockinfury on 2007-07-16
i have my triple boot system (macbook pro, 2.16ghz, 2gb, 100gb; OSX, ubuntu studio, vista) working smoothly and everything is freshly installed and configured the way i want it. it is usually at this point when i start to get cocky and try to tweak things until i end up breaking something. here is my question:

would i be able to use either SuperDuper or the disk utility on the OSX DVD to back up each of the three partitions (plus the efi partition) to an image file on an external hard drive, and then restore them using disk utility on the OSX disc later if something should fail? would the file system and partitiion formats be maintained in the image file, or would i need to do some extra formatting before i did the restore? or would restoring the vista and linux partitions even work using disk utility? 

cheers

---

### Post by cyberdork33 on 2007-07-16
I would guess that each partition would have to have its own image file. IDK how it would go for windows, but linux ought to be OK.

---

### Post by thefockinfury on 2007-07-16
thanks for the reply. yeah, i figured each partition would need to be a separate image. good to know that it would work for linux. i guess the only way to see if it works for windows is to try it eh?

so would each partition need to be formatted to the appropriate file system before the image was restored to it, or would applying the image inherently restore the original file system as well?

---

### Post by cyberdork33 on 2007-07-16
> **thefockinfury said:**
> thanks for the reply. yeah, i figured each partition would need to be a separate image. good to know that it would work for linux. i guess the only way to see if it works for windows is to try it eh?

so would each partition need to be formatted to the appropriate file system before the image was restored to it, or would applying the image inherently restore the original file system as well?

I think the filesystem will be restored. You just have to make sure that they are identified correctly in the MBR.

---

### Post by thefockinfury on 2007-07-16
> You just have to make sure that they are identified correctly in the MBR.

i should probably know the answer to this, so pardon my ignorance... but how would i do that?

---

### Post by cyberdork33 on 2007-07-16
> **thefockinfury said:**
> i should probably know the answer to this, so pardon my ignorance... but how would i do that?

It's not something I would worry about too much. You would do that as a normal part of partitioning the disk. You would create a NTFS partition for windows, as opposed to creating a ext3 partition. Don't sweat it as most partitioners (especially graphical ones) will do this without you having to think about it.

---

### Post by benanzo on 2007-07-16
Even easier than cloning your partitions would be to just make a tarball out of each system.  That's what I do.  [Here's]("http://ubuntuforums.org/showthread.php?t=35087") a good tutorial on how to do that.  You can just boot to the Ubuntu LiveCD and do all the backups.

---

### Post by thefockinfury on 2007-07-17
that sounds like a good approach. i read the post, but i couldn't seem to find two elements i was looking for:

1) how would you back up an entire volume other than the linux partition?
2) how can you specify the destination of the tar file (ie, an external hard drive)

cheers

---

### Post by benanzo on 2007-07-19
> **thefockinfury said:**
> 1) how would you back up an entire volume other than the linux partition?
2) how can you specify the destination of the tar file (ie, an external hard drive)

You just mount the partitions that you want to backup (like OS X or Windows) and then make that the target of your backup.  It's not really a good idea to take a backup of the whole volume (Windows+Linux+OSX) in the same archive.  It is better to just tar up each system individually and then you can restore them individually as well.  For instance, you'd be able to restore only your Windows system instead of having to restore all three if something went wrong.

You can send the backup to where ever you like by just mounting your external disk in say **/media/usbdisk** and then setting that as the destination.

For instance, if you want to backup your Linux system you would run:
```
tar cvpzf /media/usbdisk/ubuntu_backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /
```

You can do this from within your Linux system or you can run it from a LiveCD (which is what I do.)  Just make sure that you adjust the backup command to backup your *installed* Ubuntu system, not the LiveCD environment.  If you just run the above command while booted in the LiveCD you'll just backup the LiveCD.  You need to mount the installed system in **/media/ubuntu** or something then set that as the target.

```
tar cvpzf /media/usbdisk/ubuntu_backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys **/media/ubuntu**
```

To backup Windows do (if your Windows system is mounted in /media/windows):
```
tar cvpzf /media/usbdisk/windows_backup.tgz /media/windows
```

The same for OS X.

```
tar cvpzf /media/usbdisk/osx_backup.tgz /media/osx
```

Good Luck!

---

### Post by thefockinfury on 2007-07-19
benanzo, thats great! thanks for the help. i was actually going to sit down this afternoon and try to slog through all the backups, so your post comes at the best of times! i realized that backing up the linux partition using diskutility would be a problem because OSX can't mount ext3 volumes and (to my knowledge) there's no working version of ext2fs for tiger. so i probably wouldn't be able to back up that volume without using your method. so this just sorts everything out. 

thanks again

---

### Post by cyberdork33 on 2007-07-19
> **thefockinfury said:**
>  ...OSX can't mount ext3 volumes and (to my knowledge) there's no working version of ext2fs for tiger.

Works just fine for me.

---

### Post by thefockinfury on 2007-07-19
i assume you're referring to ext2fs? hmm, i checked sourceforge and it said tiger support was added last year. i can't believe i missed that... everything else i read said that ext2fs wouldn't work in 10.4. i thought i had the latest version but maybe that's not the case. i can't check it out right now because i'm at work and away from my macbook but i will let you know if it works for me (or more like if it doesnt, because at that point i may have a question or two for you :p)

thanks for your help

EDIT: stupid, stupid, stupid. i downloaded version 1.3 and not 1.4d4. i guess i was thrown off by the '_dev' tag at the end of the filename. made me wonder what the difference was. ha, if i had just looked at the file information instead of going straight for the 'download' button i may have seen the field that stated that 1.3 was for PPC and 1.4d4 was for intel. bah. i'll sort this out when i get home.

---

### Post by thefockinfury on 2007-07-19
so here's what i learned for those who are interested:

1) disk utility worked fine making an image of the linux partition. i saved the volume to a read/write .dmg file.
2) disk utility failed at creating an image of the vista partition. for this i found a tool called winclone that supports imaging of both XP and vista installations, and it appears to be able to image the linux partition too, although i haven't yet tried this.
3) disk utility won't clone the OSX partition because it's the root file system and i havent tried booting into the dvd yet. instead i used superduper to create a .sparseimage clone of the volume. im not sure i trust the .sparseimage format as far as being able to restore it, though. i'll see if i can use winclone to clone the osx partition, or i'll just do it from the install dvd later.

i'll let you know what else i learn as it happens.

---

