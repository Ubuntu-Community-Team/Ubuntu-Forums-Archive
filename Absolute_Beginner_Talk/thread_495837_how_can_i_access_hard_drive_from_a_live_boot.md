---
title: "how can i access hard drive from a live boot?"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by 5trawberry on 2007-07-08
hello there.
I've just booted up with the live option and wouldn't like to install ubuntu just yet....
even though accessing the hard drive is disabled, can someone tell me what to type to access it?

thanks in advance

---

### Post by taurus on 2007-07-08
You just have to mount it before you can access it.  What filesystem are you trying to access here?  What's the output of this command from a terminal from the LiveCD?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by nitro_n2o on 2007-07-08
If you are using 7.04 just go to places->computer or any hard driver icon... and it should mount them automatically... Ubuntu is great :)

---

### Post by 5trawberry on 2007-07-09
> **taurus said:**
> You just have to mount it before you can access it.  What filesystem are you trying to access here?  What's the output of this command from a terminal from the LiveCD?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

The file system is NTFS, and the original OS installed on it is XP home edition.
After typing in sudo fdisk -l , i get:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device        [COLOR="DarkOrange"]Boot[/COLOR]      [COLOR="Lime"]Start[/COLOR]    [COLOR="MediumTurquoise"]End[/COLOR]     [COLOR="Blue"]Blocks[/COLOR]         [COLOR="Red"]Id[/COLOR]    System
/dev/hda1    [COLOR="DarkOrange"]*[/COLOR]           [COLOR="Lime"]1[/COLOR]        [COLOR="MediumTurquoise"]7295[/COLOR]    [COLOR="Blue"]58597056[/COLOR]    [COLOR="Red"]7[/COLOR]     HPFS/NTFS


> **nitro_n2o said:**
> If you are using 7.04 just go to places->computer or any hard driver icon... and it should mount them automatically... Ubuntu is great :)

Ermmm, I am using version 6.06 LTS, if that makes any difference. 
When i click on places->computer-> three things come up:
DVD drive
412010
Filesystem

When i double click on 412010 or right click it and click on Mount Volume, it comes up with an error message saying 

[COLOR="Blue"]"Unable to mount the selected volume

error: device /dev/hda1 is not removable
error: could not execute pmount"[/COLOR]

any ideas?

---

### Post by 5trawberry on 2007-07-09
> **nitro_n2o said:**
> If you are using 7.04 just go to places->computer or any hard driver icon... and it should mount them automatically... Ubuntu is great :)

Can someone please confirm that the hard drive can be accessed by live booting with ubuntu version 7.04 please?
thanks

---

### Post by gloatse on 2007-07-09
> **5trawberry said:**
> Can someone please confirm that the hard drive can be accessed by live booting with ubuntu version 7.04 please?
thanks

I'm hoping this is possible as well. 

A corrupted Windows startup directory is my issue, and I'd like to use a livecd to copy files from the current HD to an external HD via USB2 before formatting and reinstalling Windows and dual-booting with proper Ubuntu.

Is this plan feasible or is there a better livecd for the job?

---

### Post by louistan3 on 2007-07-09
yes this is possible.. i have done it before... about a couple of months ago...

but i do not remember exactly what i did... i think i mounted it through the command line

using the "mount" command... to copy from a partition.. you only need read permissions..

so this makes it easier....  try reading through the man pages of mount using ...

```
man mount
```

il try to remember what i did.. and get back to you guys..


hope this helps :)

---

### Post by bodhi.zazen on 2007-07-09
Yes you can, but I think the problem is with ntfs. I do not think the 6.06 live CD supports ntfs.

You can try :

```
sudo mount -t ntfs /dev/hda1 /mnt
```

If that fails you can try to install ntfs-3g :

*You may need to enable your repositories first

```
sudo apt-get install ntfs-3g
sudo mount -t ntfs-3g /dev/hda1 /mnt
```

If you want rw access, use -o umask=000

Lilke this : ```
sudo mount -t ntfs-3g /dev/hda1 /mnt -o umask=000
```

---

### Post by 5trawberry on 2007-07-10
hello there.
I'd just like to thank all those who contributed to this thread, you've solved the problem!

7.04 only does a maximum LIVE resolution of 800X600 which is a bit annoying.
You can access the hard drive like a piece of cake with ver 7.04

Some advice: Burn the ISO of the new ubuntu 7.04 at the **slowest** speed possible.

thanks once again!



Now, does anyone know why when i put the ISO file onto my USB and tell the computer to boot from thatt, the computer said (in DOS style writting)  "Disk error, Press any key to restart"

I tried the same thing but with unpacking all the files within the ISO using WinRar. The same thing happened.
Any ideas?

---

### Post by geirha on 2007-07-10
> **5trawberry said:**
> 
Now, does anyone know why when i put the ISO file onto my USB and tell the computer to boot from thatt, the computer said (in DOS style writting)  "Disk error, Press any key to restart"

I tried the same thing but with unpacking all the files within the ISO using WinRar. The same thing happened.
Any ideas?

You just copied the ISO to the USB-drive? that won't work, and neither will unpacking it.

Why not simply install ubuntu on the USB-drive? When the drive is inserted, start the installer, and it should detect the USB-drive and give you some options of how to install it. The default will be to install to your /dev/hda, so make sure you change it to your USB-drive (probably /dev/sda)

---

### Post by bodhi.zazen on 2007-07-10
Try these links :

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

[http://doc.gwos.org/index.php/Ubuntuliveusb](http://doc.gwos.org/index.php/Ubuntuliveusb)

This will not work with Feisty (7.04) as there is a bug, but it works with Edgy (6.10)

---

