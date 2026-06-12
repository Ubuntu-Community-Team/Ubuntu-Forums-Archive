---
title: "filesystem"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by phantalon on 2007-12-08
Hello... I am a complete novice at ubuntu, and I'm having a problem mounting my second drive...I'm coming from XP and of course the file system is ntfs...obviously I need to change this, but how and to what...is it ext3 or is it something else? Can someone help me?

---

### Post by lbthrice on 2007-12-08
i don't know if i understand what you are asking....are you trying to mount a windows partition on your ubuntu partition?

---

### Post by lamalex on 2007-12-08
You don't necessarily need to change the file system. Exactly what problems are you having mounting it? Ubuntu has NTFS read/write on by default if I recall correctly. So, what's it not doing right?

---

### Post by Thulemanden on 2007-12-08
You could use qtparted to format the disk to ext3.

---

### Post by phantalon on 2007-12-08
ive just installed ubuntu and im trying get into my second drive and it says cannot mount wrong file system

---

### Post by lamalex on 2007-12-08
What way are you trying to mount it? Just by plugging it in? Or with the command line mount. Also, what version of Ubuntu are you running? 7.10?

---

### Post by phantalon on 2007-12-08
Im running the latest ubuntu 'Gutsy' And im simply clicking on the drive as i would the system drive and it will not mount...i tried to force it but it wouldn't let me

---

### Post by lamalex on 2007-12-08
try mounting it via the command line
```

sudo mkdir /media/disk
sudo mount -t ntfs-3g /dev/hdXY /media/disk

```
you'll need to figure out what disk your windows one is. ls -l /dev/disk/by-path and you should be able to figure out which is which.

---

### Post by phantalon on 2007-12-08
Ok   its telling me mount is denied because ntfs is marked in use

---

### Post by phantalon on 2007-12-08
ok im mounted   ... do i now have to change the type of file system? after i save all my data of course?

---

### Post by Sef on 2007-12-08
> ok im mounted ... do i now have to change the type of file system? after i save all my data of course?

If you are using only Ubuntu, it would be best to change it to ext3, the default.   Yes, refomatting will overwrite all of your information.

---

### Post by GGLucas on 2007-12-08
There's no need to change the filesystem to ext3, ntfs will work fine with ubuntu (well, you can't really use custom unix permissions, but that isn't that big a problem, most of the time), the problem you had was most likely caused because windows "forgot" to mark the drive as being usable and left it in the "in use" state, I had the same problem a couple of times when I was dual booting between windows and linux, you should be able to fix it by mounting it manually, which you already did. Though, you don't have to switch filesystems, it's a bit of a hassle.

---

### Post by Orbital75 on 2007-12-08
Yep..... No need to format your drive to ext3, it will preform just fine in NTFS.
If I'm correct, you should even be able to write to the drive with Gusty.

---

### Post by phantalon on 2007-12-08
Ok Ok Ok........I've transfered my files and I've reformatted the drive and then it doesn't show up...you know click on places, computer, and no drive. So I followed the steps to mount from terminal and then it surfaces,  so I now want to transfer the files back to the drive BUT it says, and I quote, "you do not have permission to write to this location"???????????
At this point I am lost.......

---

### Post by lamalex on 2007-12-08
you can use sudo to transfer the files, OR, you can modify the permissions of the folder to make it writable for you. To do this, unmount the drive, and then
```

sudo chown <your user name>:users /media/<folder where you mount the drive>
sudo chmod 775 <folder where you mount the drive>

```
then remount it.

---

### Post by phantalon on 2007-12-09
I'm sorry for being such an idiot here...and I thank you immensly for your assistance...But..."folder where I mount the drive"?    I go to places - computer - and double click on the drive....?

---

