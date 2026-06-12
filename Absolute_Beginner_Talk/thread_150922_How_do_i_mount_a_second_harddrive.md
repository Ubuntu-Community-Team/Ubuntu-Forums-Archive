---
title: "How do i mount a second harddrive?"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by dermotti on 2006-03-26
How do i mount a second harddrive that is EXT3 formatted? The drive shows up in **DISKS **but it won mount

---

### Post by aysiu on 2006-03-26
[QUOTE=dermotti]How do i mount a second harddrive that is EXT3 formatted? The drive shows up in **DISKS **but it won mount[/QUOTE] Find out where it lives by typing ```
sudo fdisk -l
``` Let's assume it's /dev/hdb1, though, for the sake of this example. Then ```
sudo mkdir /second_harddrive
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
``` Add in this line: ```
/dev/hdb1 /second_harddrive ext3 defaults 0 0
``` Save (control-x), confirm (y), exit (Enter). ```
sudo mount -a
sudo chown -R dermotti:dermotti /second_harddrive
sudo chmod -R 755 /second_harddrive
```

---

### Post by Myndmelder on 2006-03-27
](*,)  <- This is really starting to hurt, but the dent in in me learning Ubuntu instead of my head.

Anyways,
I need the reverse. I installed my second hard drive, and then mounted it... Or so I beleived... I need a way to unmount it, nix any pathways that refered to this second drive, reformat it, and then set it up as a file that Azureus and my other downloading software can store on, and that I can rip DVD's to...

Currently, I beleive it is mounted as /media

This one has got me stumped, and I cannot find an answer. :confused: 

Thanks in advance.

---

### Post by tbresson on 2006-03-27
Look in the file /etc/fstab

---

### Post by Sutekh on 2006-03-27
Did you mount it with the command **mount**?

Or did you follow similar steps to aysiu's post, using the /etc/fstab?

First you need to determine the device location of the hard drive using
```
sudo fdisk -l
```

If the hard drive is /dev/hdb1 (for example), then to unmount it after using **mount** use
```
sudo umount /dev/hdb1
```

If you followed the steps to mount it the /etc/fstab use
```
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
```
and move down to the line that starts with /dev/hdb1 and either delete it fully or put comment it by adding a "#" to the beginning of the line.

Save the file (Ctrl+O) and exit (Ctrl+X) and refresh the mounting points
```
sudo mount -a
```

You should be done.  In future if you only want to mount this hard drive temporarily, use **mount**
```
sudo mount /dev/hdb1 /media/hdb1
```
and **umount**
```
sudo umount /dev/hdb1
```

---

### Post by Myndmelder on 2006-03-31
Okay,
I got to the final step in aysiu's example and when to put in the first comand, and this is what I got:

```
myndmelder@alpha-primus:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

I am using kubuntu instead of ubuntu...
When I did this with ubuntu it worked fine.
I tried using KDE's gui "disk and filesystem, but I got the same error...

Once again I'm in need of assistance. :-?

---

### Post by Mustard on 2006-03-31
[QUOTE=Myndmelder]Once again I'm in need of assistance. :-?[/QUOTE]

Paste the contents of your /etc/fstab file so we can look for errors.

---

### Post by Myndmelder on 2006-03-31
I beleive this is what you wanted:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1       /av_media       ext3    defaults        0       0

```

I'm starting to comprehend how some people curse out Ubuntu and return to Windows, but since I cannot afford to pay for windows I'm gonna stick with it ](*,) 

I'm stuborn like that.

Thanks again.

---

### Post by Alkine on 2006-12-09
Hi

I have some strange problem when following your guideline. Im on kubuntu and followed your steps to mount exactly.

But when I try to change permission with the chown command I get an error "changing ownership of '/320gb': Operation not permitted"

I do it with sudo and everything but to no avail :( Im trying to mount a vfat formatted drive (done this in kubuntu as well) How on earth can sudo not have permission?

Hope you can help
Thnx
Alkine

---

### Post by taurus on 2006-12-09
> **Alkine said:**
> Hi

I have some strange problem when following your guideline. Im on kubuntu and followed your steps to mount exactly.

But when I try to change permission with the chown command I get an error "changing ownership of '/320gb': Operation not permitted"

I do it with sudo and everything but to no avail :( Im trying to mount a vfat formatted drive (done this in kubuntu as well) How on earth can sudo not have permission?

Hope you can help
Thnx
Alkine
You cannot change permissions to ntfs or vfat filesystem!!!  You can set it in /etc/fstab...  Therefore, how do you mount it?  Paste the output of your /etc/fstab here then.

```
cat /etc/fstab
```

---

