---
title: "Can I change my partition size after ubuntu install?"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by ianpallen on 2008-02-21
Ok so i decided to give ubuntu a go and it seems great and I'm having no issues with it currently (except for connecting my ipod touch without jailbreaking) the way i've got it setup is that ubuntu is running from an 8gb partition (shrunk from my windows vista partition)  on my Acer Aspirer 5710 laptop, now I'm thinking about getting rid of vista completly - is there a way to Increase my ubuntu partition to use all avalable space?

Thanks

---

### Post by NightwishFan on 2008-02-21
Please correct me if I am wrong, but I believe the ext3 can be resized from a gparted live cd. I will look into this and get back to you.

EDIT: Ok. Yes you can resize it. Use the live cd.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

### Post by kpkeerthi on 2008-02-21
Yes you can. Boot with ubuntu Live CD and run gparted from System -> Admin -> Partition editor. 

Click on the vista partion and choose delete from right-click menu. Now click on the ubuntu partition and choose resize. Drag the partition to fill the free space. Click Apply.

** Always make a backup if you are playing with your partitions**

To get rid of Window entry from grub,
1. Boot into ubuntu normally (not live cd)
2. Type in a terminal
```
gksudo gedit /boot/grub/menu.lst
```
3. Delete the windows boot options (lines that look like below) from the file and close gedit.
```
title Windows XP
hide (hd0,0)
hide (hd0,1)
unhide (hd0,2)
rootnoverify (hd0,2)
chainloader +1
makeactive

```
4. Type
```
sudo update-grub
```

---

### Post by NightwishFan on 2008-02-21
I had forgotten the Ubuntu live cd also had gparted. Thank you.

---

### Post by ianpallen on 2008-02-21
Excellent massive thanks guys, I'll do that tonight (currently at work)

---

### Post by housam on 2008-02-21
Also you can make a clean reinstall using the entire disk space.

---

### Post by ianpallen on 2008-02-21
Well I got into the partition editor using the ubuntu live cd - I can resize and delete the windows partitions but I cant do anything with the ext3 ubuntu partition any ideas besides reinstalling as it took me ages to get the sound working on my system lol

---

### Post by bodhi.zazen on 2008-02-21
What version of Ubuntu ? You need a newer version of gparted, so either Ubutu 7.10 or something like the gparted live CD or parted magic.

[http://www.digitalincursion.net/partedmagic/pmagic-2.0.iso](http://www.digitalincursion.net/partedmagic/pmagic-2.0.iso)

---

### Post by ianpallen on 2008-02-21
its ubuntu 7.10

---

### Post by bodhi.zazen on 2008-02-21
Can you give a better description of the problem then ? Is the partition mounted ? Is swap mounted ?

---

### Post by ianpallen on 2008-02-21
I've attached a screenshot of whats in partition editor

Basicly I want to remove ACER and PQSERVICE then resize etx3

---

### Post by bodhi.zazen on 2008-02-21
Delete the two partitions

Resize sda4 -> resize sda5

Gparted Documentation : [Documentation](http://gparted.sourceforge.net/documentation.php)

---

### Post by ianpallen on 2008-02-21
After deleting the partitions I right click on sda4 and theres no option to resize and with sda5 I can only make it smaller

sda4 says busy at least one logical partition is mounted 

sda5 is unmounted

---

### Post by bodhi.zazen on 2008-02-21
You need to unmount your swap partition.

sudo swapoff /dev/sda6

---

### Post by hammad1337 on 2008-02-21
you need to unmount the sda4 partition:
```

sudo umount /dev/sda4

```
or unmount it from the menu in Gparted.

---

### Post by ianpallen on 2008-02-21
hmm its still not letting me add more space are they locked or something?

---

### Post by bodhi.zazen on 2008-02-21
Locked = mounted

Post the output of :

```
mount
```

---

### Post by ianpallen on 2008-02-21
```
/dev/sda5 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

```

---

### Post by bodhi.zazen on 2008-02-21
You can not resize a mounted partition. This is why you need to do this with a live CD.

At the moment sda5 is mounted as root.

> /dev/sda5 on / type ext3 (rw,errors=remount-ro)

You will need to boot a live CD ;)

---

### Post by nikolas68 on 2008-02-21
warning: i did the same thing as you want to do a while ago....and after i couldn't boot into M$ any more. I would resize from M$ side....

---

### Post by ianpallen on 2008-02-21
I'm not gonna need to boot into the MS stuff after i'm done,

Well i'm booted into the ubuntu 7.10 live cd and I still can't do anything?

---

### Post by bodhi.zazen on 2008-02-21
My guess is your swap partition is mounted, if you have booted the live CD, post the output of ```
mount
```

---

### Post by ianpallen on 2008-02-21
```
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
```

---

### Post by bodhi.zazen on 2008-02-21
OK, now run :
```
gksu gparted
```

Problem ?

---

### Post by ianpallen on 2008-02-21
After doing that I get

```
ubuntu@ubuntu:~$ gksu gparted
======================
libparted : 1.7.1
======================
Unable to open /dev/scd0 read-write (Read-only file system).  /dev/scd0 has been opened read-only.
Unable to open /dev/scd0 - unrecognised disk label.
ubuntu@ubuntu:~$ 
```

And I still can't do what i want

---

### Post by bodhi.zazen on 2008-02-21
? why

---

### Post by ianpallen on 2008-02-21
not a clue, it's looking more and more like i'll need to do a reinstall.. is there a way of saving certain settings, so i can easily get my sound working quickly

---

### Post by bodhi.zazen on 2008-02-21
Resizing is much easier. What CD did you boot and can you give a description of the problem / screen shot ?

---

### Post by ve9gj on 2008-02-21
> **ianpallen said:**
> After doing that I get

```
ubuntu@ubuntu:~$ gksu gparted
======================
libparted : 1.7.1
======================
Unable to open /dev/scd0 read-write (Read-only file system).  /dev/scd0 has been opened read-only.
Unable to open /dev/scd0 - unrecognised disk label.
ubuntu@ubuntu:~$ 
```

And I still can't do what i want

I think /dev/scd0 is your cd so it is going to be read only.

try
```
sudo swapoff /dev/sda6
```
then
```
gksu gparted
```
if this doesn't get you anywhere try posting
```
sudo fdisk -l
```

---

### Post by ianpallen on 2008-02-21
Ok i'm using the ubuntu 7.10 live cd and i've also tried a gparted live cd i've got and it both cases i get the attached.

When I open a drive to resize it wont let me change it.

---

### Post by ve9gj on 2008-02-21
> **ianpallen said:**
> Ok i'm using the ubuntu 7.10 live cd and i've also tried a gparted live cd i've got and it both cases i get the attached.

When I open a drive to resize it wont let me change it.
Will it not let you apply the changes you have already requested (delete sda1 sda2)?

You will have to resize the extended partition sda4 ( to the left)  first before you can resize sda5

---

### Post by bodhi.zazen on 2008-02-21
First delete the partitions (your screen shot says operations pending).

The extend (enlarge) sda4 then sda5

---

### Post by johnn1949 on 2008-02-21
I've used the  gparted-livecd-0.3.4-11.iso  to succeesfully resize and move ext3 partions many times,

it's available here

  [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

just download and burn the iso.

---

### Post by ianpallen on 2008-02-21
Fantastic! it's currently in the process of growing now (fingers crossed) yep it seems I had to apply the deletion operation first, i just thought you could do it without applying.. thanks so much for the help!!!!

---

### Post by bodhi.zazen on 2008-02-21
> **johnn1949 said:**
> I've used the  gparted-livecd-0.3.4-11.iso  to succeesfully resize and move ext3 partions many times,

it's available here

  [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

just download and burn the iso.

Just a friendly FYI (it is hard to come in the middle of a long thread) he tried and the gparted CD did not boot. We did not trouble shoot this much, although we did discuss the safe graphic mode :)

Also although the gparted is a fine tool, the project has forked so Parted Magic may be better, I do not know yet.

Last, the ubuntu 7.10 desktop CD has an updated version of gparted, so really no "need" for downloading an alternate iso ;)

/end deep thought

---

### Post by ianpallen on 2008-02-21
Thanks very much bodhi.zazen  you've been a great help!

:guitar:

---

