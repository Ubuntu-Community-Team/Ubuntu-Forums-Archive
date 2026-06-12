---
title: "Mounting stuff"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by Arwen on 2007-08-12
Hello to everyone!
I created a 100GB fat32 partition in my sata disc(I also have ubuntu on it) through disk manager of my Windows XP.Everytime I boot in ubuntu I have do right click on the icon of the disc and click on "mount volume".Do I have to do it everytime?Also I can't create any file in it.
Does anyone know what can I do about it?
Thank you!

---

### Post by felicity on 2007-08-12
You can add that  partition to your /etc/fstab file if you want it to mount each time you boot Ubuntu. You can also change permissions on it to be able to write to it from your Ubuntu account.

First you need to make a folder for the partition. You might use something like:
```
sudo mkdir /media/Storage
```

To add the partition to /etc/fstab:
```
sudo gedit /etc/fstab
```

You need to know which partition it is, if it's the second you can add this line: (changing /dev/sda<number> depending on which partition it is, i.e. /dev/sda3 for the third partition)
```
/dev/sda2 /media/Storage vfat defaults 0 0
```

Save the file. Then test if it works by typing:
```
sudo mount -a
```

To change permissions type:
```
sudo chmod -R a+rwx /media/Storage
```

---

### Post by Arwen on 2007-08-12
sudo mount -a gives this:
fusermount: mount failed: Device or resource busy
FUSE mount point creation failed
Unmounting /dev/disk/by-uuid/BA9C09ED9C09A4CB ()
fusermount: mount failed: Device or resource busy
FUSE mount point creation failed
Unmounting /dev/disk/by-uuid/8C90F17190F1625E (DATA)

It's the sda3 partition and its name is ARWEN,I added to fstab:
/dev/sda3 /media/sda3 vfat defaults 0 0
Is it OK?

Another vfat partition of mine in my hda:
# Entry for /dev/hda2 :
UUID=0807-8DF7 /media/hda2 vfat defaults,utf8,umask=007,gid=46 0 1

Maybe I should do it the same way?

---

### Post by felicity on 2007-08-12
Looks OK to me, as long as the folder you made in /media is also called sda3

---

### Post by Arwen on 2007-08-12
Here's my fstab now:
proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=0d19b503-6a2b-4b52-a838-9f2a96c2d23b / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda1 :
UUID=BA9C09ED9C09A4CB /media/hda1 ntfs-3g defaults,locale=el_GR.UTF-8 0 1
# Entry for /dev/hda2 :
UUID=0807-8DF7 /media/hda2 vfat defaults,utf8,umask=007,gid=46 0 1
# Entry for /dev/hda3 :
UUID=8C90F17190F1625E /media/hda3 ntfs-3g defaults,locale=el_GR.UTF-8 0 1
# Entry for /dev/sda2 :
UUID=faa1e6cc-aa1e-447e-8854-50e92f381f3f none swap sw 0 0
# Entry for /dev/sda3 named ARWEN :
/media/sda3 vfat defaults,utf8,umask=007,gid=46 0 1
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

It mounts to ARWEN hda2,Whatever is in hda2 is now in sda3 too.What's that UUID?

---

### Post by felicity on 2007-08-12
It's just a specific number given by the install, you shouldn't need one if you're adding to fstab. /dev/sda3 is fine.

But I notice on sda3 you haven't specificed where you want it mounted.

/media/sda3 vfat defaults,utf8,umask=007,gid=46 0 1

should be:
/media/sda3 /media/folder vfat defaults,utf8,umask=007,gid=46 0 1
(where /media/folder is the name of the folder you made to mount the partition in)

but you may just want:
/media/sda3 /media/folder vfat defaults 0 0
instead.. I'm not sure about the extra stuff, if you know what it is and want it fine, but it shouldn't be needed.

---

### Post by Arwen on 2007-08-12
I tried all:
/media/sda3 /media/sda3 vfat defaults,utf8,umask=007,gid=46 0 1
/media/sda3 /media/sda3 vfat defaults 0 0
/dev/sda3 /media/sda3 vfat defaults 0 0
/media/sda3 vfat defaults,utf8,umask=007,gid=46 0 1
but it does the same thing and sudo mount -a still gives:
fusermount: mount failed: Device or resource busy
FUSE mount point creation failed
Unmounting /dev/disk/by-uuid/BA9C09ED9C09A4CB ()
fusermount: mount failed: Device or resource busy
FUSE mount point creation failed
Unmounting /dev/disk/by-uuid/8C90F17190F1625E (DATA)

---

### Post by felicity on 2007-08-12
You did create a folder in /media called sda3 then? (since that's the folder you're trying to mount it into)

I'm not sure about that error you got. Are you sure it's an error relating to the drive you're mounting? I mean, have you manually checked the /media/sda3 folder after sudo mount -a to see if it's mounted?

---

### Post by Arwen on 2007-08-12
In "My computer" there's a disc icon named "ARWEN",I do right click and mount volume on it and I can see it in Desktop.I'm not changing anything in fstab.
In  /media there are hda1,hda2,hda3 and the sda3 that I created.
Should I named it ARWEN?What else should I do?

---

### Post by felicity on 2007-08-12
ARWEN is likely just the label of the partition. You shouldn't need to use that to mount it though. I'm not sure what the fuse error is that your receiving, perhaps someone with more knowledge of mounting can help you.

---

### Post by felicity on 2007-08-12
Not sure if this will help you, but here's the Ubuntu guide directions for mounting a FAT volume: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite")

---

### Post by Arwen on 2007-08-14
Felicity thank you a lot :)
The link you posted helped me out.I just had to add "/dev/sda3 /media/sda3 vfat  iocharset=utf8,umask=000  0    0" in fstab.
\\:D/
Cheers
Arwen

---

