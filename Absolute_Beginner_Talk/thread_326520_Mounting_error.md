---
title: "Mounting error"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by KrayzeKaliber on 2006-12-27
Howdy fellow ubunters...

Currently running Edgy Xubuntu while I encountered a mounting problem. I went to accessories>computer to mount my 'CD-ROM/DVD-ROM Drive' and I got the following message: 

> mount: block device /dev/hdc is write-protected, mounting read-only
mount: /dev/hdc already mounted or /media/dvd busy
[mntent]: line 11 in /etc/mtab is bad
mount: according to mtab, /dev/hdc is already mounted on /media/dvd

I currently own two drives: the dvd drive and a CD-RW drive. I've never played a dvd on my xubuntu box because of my mounting issue. Totem is constantly giving me the message

> Failed to mount /dev/hdc... 'failing to find mountpoint', and messages of similiar nature.

Something with fstab? mstab? I'm wishing could explain this whole /media/cdrom, cdrom0, cdrom1, dvd deal, along with how it's incorporated with /dev/hdc.

Sorry for the long request...some guidance is appreciated. :D

---

### Post by taurus on 2006-12-27
Look in /etc/fstab.  Make sure you have two entries, one for each CD drive and they are not supposed to share the same mount point...

Applications -> Accessories -> Terminal
```
cat /etc/fstab
```

---

### Post by KrayzeKaliber on 2006-12-27
Unfortunately, those mounts are fine:

> johnnyo@Toybox:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=0df8f6c0-0cc8-40a2-ab67-2636024de237 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb2
UUID=6c76e282-9a87-42c2-a4c5-280870ab77ac /home           ext3    defaults        0       2
# /dev/hdb1
UUID=3db9a8bb-6bb2-4ffd-bb3a-e6c398401ec0 none            swap    sw              0       0
/dev/hdc        /media/dvd      iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


I'm not sure if /dev/hdc (dvd drive) is supposed to have the udf before the iso9660 user...just noticed that.

---

### Post by taurus on 2006-12-27
Go ahead and add it in there...

```
gksudo gedit /etc/fstab
```

---

### Post by KrayzeKaliber on 2006-12-27
We're making some progress...slightly shorter error line (just one line missing)
> mount: block device /dev/hdc is write-protected, mounting read-only
mount: /dev/hdc already mounted or /media/dvd busy
mount: according to mtab, /dev/hdc is already mounted on /media/dvd

I kno reboots aren't as necessary as they are in windows, but should I reboot just in case? Better safe than sorry right? ;)

---

### Post by taurus on 2006-12-27
What's the output of this command from a terminal then?

```
df -h
```
And yes, sometimes rebooting will cure the illness...

---

### Post by KrayzeKaliber on 2006-12-27
Sorry about the long response time...the output is as follows:

> Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              56G  2.5G   50G   5% /
varrun                122M   76K  121M   1% /var/run
varlock               122M     0  122M   0% /var/lock
procbususb             10M  112K  9.9M   2% /proc/bus/usb
udev                   10M  112K  9.9M   2% /dev
devshm                122M     0  122M   0% /dev/shm
/dev/hdb2              12G  639M   11G   6% /home
/dev/hdc              6.9G  6.9G     0 100% /media/dvd


So now my cd-drive's missing (hdd?) The cd-rw is functioning flawless tho. Uh-oh... :-?

---

### Post by taurus on 2006-12-27
Your DVD is already mounted, **/dev/hdc 6.9G 6.9G 0 100% /media/dvd**, so you can't mount it again!!!  

So what exactly are you trying to do here?

---

### Post by KrayzeKaliber on 2006-12-28
Sorry, all this mounting and such is an attempt to watch my dvd. I can't choose in "computer" because it has that mounting error, and when I choose to watch it in Totem media player, it responds with the error > Failed to mount /dev/hdc If mounting the drive isn't the source of the problem, I'm not exactly sure what is...:-k

Does it fail to mount /dev/hdc because it's already mounted at /media/dvd?

---

### Post by KrayzeKaliber on 2006-12-28
Sorry about the double post, but I was wondering there would be any way to alter how Totem mounts the dvd drive.

---

