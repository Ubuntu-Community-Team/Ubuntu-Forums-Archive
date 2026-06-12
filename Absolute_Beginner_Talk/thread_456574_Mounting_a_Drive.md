---
title: "Mounting a Drive"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by DarkAngel5745 on 2007-05-27
[CENTER][B][FONT="Comic Sans MS"][SIZE="1"][COLOR="DeepSkyBlue"]Would someone be able to tell me how to mount a drive/lead me through the steps? I need my files from Windows on Linux but I know know hoe to mount it. Plz Help. Thanks

~*_*~[/COLOR][/SIZE][/FONT][/B][/CENTER]

---

### Post by taurus on 2007-05-27
What partition it is and what filesystem is it?  What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by DarkAngel5745 on 2007-05-27
darkangel@kayla:~$ sudo fdisk -l
Password:

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3538    28418953+   7  HPFS/NTFS
/dev/hda2            3539        4803    10161112+  83  Linux
/dev/hda3            4804        4865      498015    5  Extended
/dev/hda5            4804        4865      497983+  82  Linux swap / Solaris

Disk /dev/sda: 127 MB, 127025152 bytes
16 heads, 32 sectors/track, 484 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         484      123888    e  W95 FAT16 (LBA)


~*_*~

---

### Post by taurus on 2007-05-27
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add these two lines to the end of it.

```
/dev/hda1   /media/hda1   ntfs   nls=utf8,umask=0222   0   0
/dev/sda1   /media/sda1   vfat   iocharset=utf8,umask=000   0   0
```
Save the changes.  Then, create two new mount points and mount them.

```
sudo mkdir /media/hda1 /media/sda1
sudo mount -a
df -h
```
Now, you can read your Windows partition on /media/hda1 and you can read and write to your other drive, /dev/sda1, on /media/sda1.

---

### Post by alienexplorers on 2007-05-28
This write up explains mounting all types of file systems.
> [http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

---

### Post by DarkAngel5745 on 2007-06-01
> **taurus said:**
> Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add these two lines to the end of it.

```
/dev/hda1   /media/hda1   ntfs   nls=utf8,umask=0222   0   0
/dev/sda1   /media/sda1   vfat   iocharset=utf8,umask=000   0   0
```
Save the changes.  Then, create two new mount points and mount them.

```
sudo mkdir /media/hda1 /media/sda1
sudo mount -a
df -h
```
Now, you can read your Windows partition on /media/hda1 and you can read and write to your other drive, /dev/sda1, on /media/sda1.
[FONT="Comic Sans MS"][CENTER][COLOR="DarkOrchid"]
The last part where do i type that in at the terminal or the other box?

~*_*~[/COLOR][/CENTER][/FONT]

---

### Post by Inxsible on 2007-06-01
> **DarkAngel5745 said:**
> [FONT="Comic Sans MS"][CENTER][COLOR="DarkOrchid"]
The last part where do i type that in at the terminal or the other box?

~*_*~[/COLOR][/CENTER][/FONT]

The last part should be again in the terminal, NOT in the fstab file. Those are commands that will make sure its mounted.

---

### Post by DarkAngel5745 on 2007-06-01
[B][CENTER][FONT="Comic Sans MS"][COLOR="Cyan"]Ok, But should i open a new one or in that some one?

~*_*~[/COLOR][/FONT][/CENTER][/B]

---

### Post by Inxsible on 2007-06-01
Doesnt matter ...once you save the /etc/fstab and close it you should be able to access the same terminal to enter the commands

---

### Post by DarkAngel5745 on 2007-06-01
darkangel@kayla:~$ sudo mkdir /media/hdal /media/sdal
Password:
mkdir: cannot create directory `/media/hdal': File exists
mkdir: cannot create directory `/media/sdal': File exists


[COLOR="Magenta"][B]That showed up. Now What?

~*_*~[/B][/COLOR]

---

### Post by drowner on 2007-06-01
it should be hda1 and sda1 not hdal and sdal 

and the last time you typed the command wrongly, it seems


you might need to do a bit of cleaning up, then we can start over

show us the output of these commands:
```

cat /etc/fstab
```

and
```

ls /media
```

---

### Post by Inxsible on 2007-06-01
> **DarkAngel5745 said:**
> [FONT="Comic Sans MS"]**[COLOR="Magenta"]That is what shows if i use the same box[/COLOR]**[/FONT]

darkangel@kayla:~$ gksudo gedit /etc/fstab
Launching a SCIM daemon with Socket FrontEnd...
Loading simple Config module ...
Creating backend ...
Loading socket FrontEnd module ...
Starting SCIM as daemon ...
GTK Panel of SCIM 1.4.4

sudo mkdir /media/hdal /media/sdal
sudo mount -a
df -h
[COLOR="Magenta"][FONT="Comic Sans MS"][B]
And that what shows is i type it in a new one.[/B][/FONT][/COLOR]

darkangel@kayla:~$ sudo mkdir /media/hdal /media/sdal
Password:
darkangel@kayla:~$ sudo mount -a
mount: mount point  does not exist
darkangel@kayla:~$ gf -h
bash: gf: command not found

[FONT="Comic Sans MS"][COLOR="Magenta"]**~*_*~**[/COLOR][/FONT]

When in doubt, Copy Paste.
The first command you have typed in l (Lowercase L) whereas it should be 1 (the digit one)
the last command is not gf ...its df

---

### Post by DarkAngel5745 on 2007-06-02
> **drowner said:**
> it should be hda1 and sda1 not hdal and sdal 

and the last time you typed the command wrongly, it seems


you might need to do a bit of cleaning up, then we can start over

show us the output of these commands:
```

cat /etc/fstab
```

and
```

ls /media
```



darkangel@kayla:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=8857f2d3-b7a3-48b7-ba4b-cd5e3cba8b7b /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5
UUID=8fcca32e-ecb9-4651-9496-9cf431cb6acd none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
darkangel@kayla:~$ ls /media
cdrom  cdrom0  DARK ANGEL  floppy  floppy0  hdal  sdal



~*_*~

---

### Post by DarkAngel5745 on 2007-06-02
darkangel@kayla:~$ sudo mkdir /media/hda1 /media/sda1
darkangel@kayla:~$ sudo mount -a
mount: mount point  does not exist
darkangel@kayla:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             9.6G  9.1G  7.4M 100% /
varrun                110M  116K  110M   1% /var/run
varlock               110M     0  110M   0% /var/lock
procbususb            110M  104K  110M   1% /proc/bus/usb
udev                  110M  104K  110M   1% /dev
devshm                110M     0  110M   0% /dev/shm
lrm                   110M   33M   77M  31% /lib/modules/2.6.20-16-generic/volatile


[B][CENTER][FONT="Comic Sans MS"][COLOR="Magenta"]
i don't think it worked.

~*_*~[/COLOR][/FONT][/CENTER][/B]

---

### Post by drowner on 2007-06-02
ok, so it doesn't appear you have edited your fstab yet.

Back up your fstab

```
sudo cp /etc/fstab /etc/fstab.bak
```

then edit the fstab file

```
gksudo gedit /etc/fstab
```

and add these 2 lines to the bottom
```

/dev/hda1   /media/hda1   ntfs   nls=utf8,umask=0222   0   0
/dev/sda1   /media/sda1   vfat   iocharset=utf8,umask=000   0   0
```

Save the changes and exit

then make proper directories:

```
sudo mkdir /media/hda1 /media/sda1

```
Remembering that these are 1 (the number) not L's!

then mount them and check
```

sudo mount -a
df -h
```

---

### Post by DarkAngel5745 on 2007-06-02
darkangel@kayla:~$ sudo mkdir /media/hda1 /media/sda1
mkdir: cannot create directory `/media/hda1': File exists
mkdir: cannot create directory `/media/sda1': File exists
darkangel@kayla:~$ sudo mount -a
mount: mount point  does not exist
mount: special device /dev/sda1 does not exist
darkangel@kayla:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             9.6G  9.1G  7.3M 100% /
varrun                110M  116K  110M   1% /var/run
varlock               110M     0  110M   0% /var/lock
procbususb            110M  104K  110M   1% /proc/bus/usb
udev                  110M  104K  110M   1% /dev
devshm                110M     0  110M   0% /dev/shm
lrm                   110M   33M   77M  31% /lib/modules/2.6.20-16-generic/volatile
/dev/hda1              28G   20G  8.0G  71% /media/hda1

[B][FONT="Comic Sans MS"][COLOR="Magenta"][CENTER]
What did i do wrong this time?

~*_*~[/CENTER][/COLOR][/FONT][/B]

---

### Post by drowner on 2007-06-02
> **DarkAngel5745 said:**
> 
mount: special device /dev/sda1 does not exist

[B][FONT="Comic Sans MS"][COLOR="Magenta"][CENTER]
What did i do wrong this time?

~*_*~[/CENTER][/COLOR][/FONT][/B]

I don't know. Something funny is going on here.

Show me 
```

sudo fdisk -l
```

---

### Post by DarkAngel5745 on 2007-06-02
darkangel@kayla:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3538    28418953+   7  HPFS/NTFS
/dev/hda2            3539        4803    10161112+  83  Linux
/dev/hda3            4804        4865      498015    5  Extended
/dev/hda5            4804        4865      497983+  82  Linux swap / Solaris


~*_*~

---

### Post by drowner on 2007-06-02
Your sda1 drive has gone missing.

Did you have a USB pendrive or something like that plugged in before? And now you don't, right?

---

### Post by DarkAngel5745 on 2007-06-02
[FONT="Comic Sans MS"][B][CENTER][COLOR="Orange"]Yah i have a flash drive, that isn't in right now.

~*_*~[/COLOR][/CENTER][/B][/FONT]

---

### Post by drowner on 2007-06-02
> **DarkAngel5745 said:**
> [FONT="Comic Sans MS"][B][CENTER][COLOR="Orange"]Yah i have a flash drive, that isn't in right now.

~*_*~[/COLOR][/CENTER][/B][/FONT]

Yep, ok, so earlier we put it in the fstab. It doesnt need to be there.

Make sure its not plugged in currently, and edit the fstab again
```

gksudo gedit /etc/fstab
``` 

and remove the line with the reference to /dev/sda1

save and exit.

I'm pretty sure you should be able to see all of your drives now. If you can't, let me know.

---

### Post by DarkAngel5745 on 2007-06-02
**[FONT="Comic Sans MS"][COLOR="Lime"]This?[/COLOR][/FONT]**

darkangel@kayla:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3538    28418953+   7  HPFS/NTFS
/dev/hda2            3539        4803    10161112+  83  Linux
/dev/hda3            4804        4865      498015    5  Extended
/dev/hda5            4804        4865      497983+  82  Linux swap / Solaris

**[CENTER][COLOR="Lime"]~*_*~[/COLOR][/CENTER]**

---

### Post by drowner on 2007-06-02
> **DarkAngel5745 said:**
> **[FONT="Comic Sans MS"][COLOR="Lime"]This?[/COLOR][/FONT]**

darkangel@kayla:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3538    28418953+   7  HPFS/NTFS
/dev/hda2            3539        4803    10161112+  83  Linux
/dev/hda3            4804        4865      498015    5  Extended
/dev/hda5            4804        4865      497983+  82  Linux swap / Solaris

**[CENTER][COLOR="Lime"]~*_*~[/COLOR][/CENTER]**

erm, no.

run the command to edit the fstab file again

```
gksudo gedit /etc/fstab
```

and remove this line:

/dev/sda1   /media/sda1   vfat   iocharset=utf8,umask=000   0   0

Save and Exit.

All your drives should be mounted, and accessible.
Let me know.

---

### Post by DarkAngel5745 on 2007-06-16
[CENTER][FONT="Comic Sans MS"][SIZE="3"][COLOR="Magenta"][B]Thanks for all your help,
and I'm sorry that it took me soo ling to reply to you.
My internet was down,
but it worked and i wanted to thank everyone for helping
^_^
~*_*~[/B][/COLOR][/SIZE][/FONT][/CENTER]

---

