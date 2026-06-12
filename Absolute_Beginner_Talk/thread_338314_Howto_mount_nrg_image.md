---
title: "Howto mount nrg image"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by shareMenaPeace on 2007-01-14
Hello i found and used this nautilus script to mount iso files
[http://ubuntuforums.org/showthread.php?t=87369](http://ubuntuforums.org/showthread.php?t=87369)

Now i needed also nrg image mounting and tried the howto over here
[http://doc.gwos.org/index.php/Mount_ISO_script](http://doc.gwos.org/index.php/Mount_ISO_script)
I followed the steps and had problems during the install of cdemu (which i understand is only needed for bin files?).

I can still use iso mounting with the updated mount and unmount scripts for nautilus. 
But nrg is not working.

Any ideas or a howto for nrg script nautilus working for edgy?

thx

---

### Post by taurus on 2007-01-14
There's a program called nrg2iso that would allow you to convert .nrg to .iso and then you can mount it as you would with any other .iso file.  It's in the repos...

```
sudo aptitude update
sudo aptitude install nrg2iso
```

---

### Post by shareMenaPeace on 2007-01-14
Thank you taurus,
it works quiet fast with big filesizes too .

---

### Post by taurus on 2007-01-14
Well, have fun with it.  ;)

---

### Post by isenalim on 2007-05-14
Hi,
I have a bunch of nrg images of audio cd and nrg2iso doesn't work! It makes a corrupted file apparently.

Doing
```

sudo mount -o loop xyz.iso /media/xyz

```

it gives

```

mount: you must specify the filesystem type

```

So I did

```

sudo mount -o loop -t iso9660 xyz.iso /media/xyz

```

it gives

```

mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

The relevant output of dmesg | tail is

```

[21176.536000] loop: loaded (max 8 devices)
[21176.732000] cramfs: wrong magic
[21176.736000] VFS: Can't find ext3 filesystem on dev loop0.
[21176.736000] FAT: bogus number of reserved sectors
[21176.736000] VFS: Can't find a valid FAT filesystem on dev loop0.
[21253.596000] Unable to identify CD-ROM format.

```

I have also tried some script to mount directly the nrg images but it didn't work. Apparently the only workaround I found is to burn them with nerolinux to a RW disc and then extract the iso... but this is veeeeeery long!
Any idea?
Thanks a lot!
G

---

### Post by Stone123 on 2007-05-14
Try this : 

sudo mount  -o loop -t hfsplus  ~/file dmg  /mnt/point/

---

### Post by isenalim on 2007-05-14
Hi,
thank you for the quick reply!
Unfortunately it doesn't work :(

Maybe I didn't understand well the command. I gave

```

sudo mount -o loop -t hfsplus file path

```

What is the dmg you wrote? I if I put it between file and path mount complains it is not the right syntax or options.

Anyway, I tried both with the nrg and the converted iso images and I get the same error:

```

mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

This time dmesg says

```

[25143.784000] hfs: unable to find HFS+ superblock
[25149.536000] hfs: unable to find HFS+ superblock

```

Sadly,
G.

---

### Post by Stone123 on 2007-05-14
My bad , i thought it was a Mac OS X file . 

Can you type 

file file.nrg to see what is it ?

---

### Post by isenalim on 2007-05-14
file.nrg:data

---

### Post by fakie_flip on 2007-06-12
> **Stone123 said:**
> My bad , i thought it was a Mac OS X file . 

Can you type 

file file.nrg to see what is it ?

I also get the error from the dmg file.

```
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

dmesg:

```
[29679.785883] hfs: unable to find HFS+ superblock
```

file command:

```
VAX COFF executable - version 745
```

---

