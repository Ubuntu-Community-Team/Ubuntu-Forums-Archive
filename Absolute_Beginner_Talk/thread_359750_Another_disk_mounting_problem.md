---
title: "Another disk mounting problem"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by cybrkup on 2007-02-12
Long story not so short I updated my kernel to 17-11 and basically hosed my system completely. I have an nvidia video card.

I just installed Xubuntu on what used to be my WinXP drive and I'm now trying to access my data on HDA5, a pre-existing Kubuntu drive. For some reason Thunar won't see the drive at all. I have no FSTAB directory either. Please help!

> 
Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         638     5124703+  82  Linux swap / Solaris
/dev/hda2             639        3556    23438835   83  Linux
/dev/hda4            7038       17873    87040170    5  Extended
/dev/hda5            7038       17873    87040138+  83  Linux

Disk /dev/hdb: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9356    75152038+  83  Linux
/dev/hdb2            9357        9733     3028252+   5  Extended
/dev/hdb5            9357        9733     3028221   82  Linux swap / Solaris


> james@linux-home:/$ gksudo gedit /etc/fstab
sudo: gedit: command not found
james@linux-home:/$ gedit /etc/fstab
bash: gedit: command not found
james@linux-home:/$ sudo gedit /etc/fstab
sudo: gedit: command not found
james@linux-home:/$ cd /
james@linux-home:/$ dir
bin   cdrom  etc   initrd      lib         media  opt   root  srv  tmp  var
boot  dev    home  initrd.img  lost+found  mnt    proc  sbin  sys  usr  vmlinuz
james@linux-home:/$ cd /etc
james@linux-home:/etc$ cd /fstab
bash: cd: /fstab: No such file or directory


---

### Post by taurus on 2007-02-12
Since you are using Xubuntu, there is no gedit unless you install it by hand.  Therefore, try a text editor like nano.

```
sudo nano -Bw /etc/fstab
```

---

### Post by cybrkup on 2007-02-12
That did work. But what does it need to say? I'm sure you get this question a million times, but after having hosed my system despite the help of lots of friendly and knowledgeable folks I'm hesitant to just experiment as I might otherwise. 

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=c246bd02-4fb8-4232-9aff-76f89660f4ed /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=af95fb6b-8f21-4747-bc9f-d0463f661d27 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


---

### Post by taurus on 2007-02-12
Add these three lines to the end of it to mount the first harddrive.

```

/dev/hda1   none   swap   sw   0   0
/dev/hda2   /media/hda2   ext3   defaults   0   1
/dev/hda5   /media/hda5   ext3   defaults   0   1

```
Save it with <Ctrl>x, then Y, and then Return.

Now, you need to create the two new mount points and mount them, including the new swap partition.

```
sudo mkdir /media/hda2 /media/hda5
sudo mount -a
df -h
free
```

---

### Post by cybrkup on 2007-02-12
> **taurus said:**
> Add these three lines to the end of it to mount the first harddrive.

```

/dev/hda1   none   swap   sw   0   0
/dev/hda2   /media/hda2   ext3   defaults   0   1
/dev/hda5   /media/hda5   ext3   defaults   0   1

```
Save it with <Ctrl>x, then Y, and then Return.

Now, you need to create the two new mount points and mount them, including the new swap partition.

```
sudo mkdir /media/hda2 /media/hda5
sudo mount -a
df -h
free
```

Did all that twice but still no beans. 

Here is my fstab file:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=c246bd02-4fb8-4232-9aff-76f89660f4ed /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=af95fb6b-8f21-4747-bc9f-d0463f661d27 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1   none   swap   sw   0   0
/dev/hda2   /media/hda2   ext3   defaults   0   1
/dev/hda5   /media/hda5   ext3   defaults   0   1


Here is where I did the commands again after a reboot. 

> james@linux-home:/$ sudo mkdir /media/hda2 /media/hda5
mkdir: cannot create directory `/media/hda2': File exists
mkdir: cannot create directory `/media/hda5': File exists
james@linux-home:/$ sudo mount -a
james@linux-home:/$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb1              71G  1.7G   66G   3% /
varrun                505M   76K  505M   1% /var/run
varlock               505M     0  505M   0% /var/lock
procbususb             10M  140K  9.9M   2% /proc/bus/usb
udev                   10M  140K  9.9M   2% /dev
devshm                505M     0  505M   0% /dev/shm
lrm                   505M   18M  488M   4% /lib/modules/2.6.17-10-generic/volatile
/dev/hda2              23G  2.8G   19G  14% /media/hda2
/dev/hda5              82G   20G   59G  25% /media/hda5
james@linux-home:/$ free



BTW, I installed Gedit.

---

### Post by taurus on 2007-02-12
What do you mean no beans?  Both are mounted from the output!

```

/dev/hda2 23G 2.8G 19G 14% /media/hda2
/dev/hda5 82G 20G 59G 25% /media/hda5

```

---

### Post by cybrkup on 2007-02-12
> **taurus said:**
> What do you mean no beans?  Both are mounted from the output!

```

/dev/hda2 23G 2.8G 19G 14% /media/hda2
/dev/hda5 82G 20G 59G 25% /media/hda5

```

I'm not being clear in my explanation. I would like to use Thunar or another similar GUI app to access the files, and not have to do it via a command prompt. Nowhere in the file manager does it show this extra drive.

---

### Post by cybrkup on 2007-02-12
I'm not sure what happened, but they are showing up now after another reboot. Thank you very much for your help. I really appreciate it! 

:popcorn:

---

