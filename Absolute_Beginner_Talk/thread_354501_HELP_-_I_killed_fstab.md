---
title: "HELP - I killed fstab"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by mulligan.can on 2007-02-06
Help!!, ok i managed to accidently overwrite fstab with an empty file and i have no idea what i am supposed to rewrite it with.

hda1 = ext2 and is /boot
hda2 = swap
hda3 = jfs and is /

hdc = dvd

i can do basic fstab editing and i think i can get it right again but not perfectly sure.

anyway, any help would be mot appreciated

---

### Post by Rui Pais on 2007-02-06
you have a simple setup should be easy.

But fstab use is different from dapper to edgy. 
Which one are you using?

---

### Post by mulligan.can on 2007-02-06
sorry, ok, im using edgy.

i also am going to add a few extra nfs shares into fstab but i just wanna make sure i end up with the correct base. i have the system booting with the following just not sure if im missing something or have the wrong options specified

# <device>      <mountpoint>    <filesystemtype><options>  <dump> <fsckorder>

/dev/hda1       /boot           ext2            defaults        1       2
/dev/hda2       swap          swap           defaults        0       0
/dev/hda3       /                 jfs               defaults        1       1
/dev/hdc        /media/cdrom   auto           defaults        0       0

none            /proc           proc            defaults

---

### Post by Rui Pais on 2007-02-07
it seems ok.

i have extra:
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

my cdrom options are:
 udf,iso9660 user,noauto     0       0

my options for root (/) are:
defaults,errors=remount-ro,noatime 0  1

and for /boot:
defaults,noatime 0  0

but that should be of no importance...

note that in edgy the references to devices change (and the ones you use will be deprecated in the future).
Now is:
UUID=xxxx-x-xxx-xxxxxx-xxx
instead of /dev/hdxx

You can get the UUIDs using:
```
sudo vol_id /dev/hdxx
```

---

### Post by bodhi.zazen on 2007-02-07
FYI you can also get a listing of your uuid with:

```
blkid
```

Also, not to ask the obvious, but how did you edit fstab ?

If you opened an editor without root powers you will get an empty file.

If you opened with gedit you will have an automatic backup as /etc/fstab~

Also, in the future, you can always:

```
sudo nano -B <file>
```

the -B flag creates a backup, again as file_name~

also ```
gksudo gedit <file_name>
```Also makes a backup ....

HTH

EDIT: Fixed typos, thanks Rui Pais

---

### Post by Rui Pais on 2007-02-07
...


*edited: not need anymore...*

---

### Post by bodhi.zazen on 2007-02-07
> **Rui Pais said:**
> since **mulligan.can** says on his/her last post
"i have the system booting with the following..."
we can assume that he/she already manage to create a fstab ;)

Thanks for the editorials, I think I fixed that stuff.

It is getting late here :(

The point of my question is that perhaps mulligan.can has a full backup and his work can be finished with a single 

```
sudo cp /etc/fstab~ /etc/fstab
```

rather then adding additional devices or network shares by hand ;)

also a little advice on how to automate backups in the future can never hurt :rolleyes:

---

### Post by Rui Pais on 2007-02-07
> **bodhi.zazen said:**
> 

```
sudo cp /etc/fstab~ /etc/fstab
```

rather then adding additional devices or network shares by hand ;)

also a little advice on how to automate backups in the future can never hurt :rolleyes:

You can said that again. Backups are never too much.

I forget to ask if mulligan.can have an /etc/fstab~ 
If so that would be the fastest way for sure :)

---

### Post by mulligan.can on 2007-02-08
uhhhh kinda silly actually. i had customised my fstab a bit by adding a fair few nfs shares and getting rid of the uuid's (i prefer to see the device names and i never change my disk config so why not?)

anyway, i had to reformat my pc and reinstall kubuntu (somehow the filesystem got heavily corrupted and fsck.jfs wouldn't help at all and it was beyond my ability to fix) so i backed up my customised configuration and files etc except something went wrong with the fstab backup.

i then copied the fstab across from the backups and overwrote the original fstab without looking at its contents.....turns out it was an empty file... (was using cli for all this btw, i prefer using nano and didnt know about the -B switch...)

anyway thanks for the help guys :)

---

### Post by bodhi.zazen on 2007-02-08
> **mulligan.can said:**
> i then copied the fstab across from the backups and overwrote the original fstab without looking at its contents.....turns out it was an empty file... (was using cli for all this btw, i prefer using nano and didnt know about the -B switch...)

anyway thanks for the help guys :)

:lolflag:

Backups. Make sure they are working before you need them :D

---

