---
title: "ubuntu not detecting blank cds"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by cosmoshell on 2007-05-28
whn i pop a blank cd in it dosnt detect it. however blank dvds are detected intill theres something burnt on them. can any one help?

---

### Post by Pragmatist on 2007-05-29
Go to this menu:
System-->Preferences-->Removable Drives and Media

---

### Post by cosmoshell on 2007-05-29
doesnt help

---

### Post by Pragmatist on 2007-05-29
This person solved the problem with Gnomebaker:
[http://ubuntuforums.org/showthread.php?t=454272&highlight=blank+cd](http://ubuntuforums.org/showthread.php?t=454272&highlight=blank+cd)

---

### Post by cosmoshell on 2007-06-02
> **Pragmatist said:**
> This person solved the problem with Gnomebaker:
[http://ubuntuforums.org/showthread.php?t=454272&highlight=blank+cd](http://ubuntuforums.org/showthread.php?t=454272&highlight=blank+cd)
my problem isent with the burning program its that the computer isent reading blank cds only some burnt ones and mosly pressed cds

---

### Post by ugm6hr on 2007-06-02
> **cosmoshell said:**
> my problem isent with the burning program its that the computer isent reading blank cds only some burnt ones and mosly pressed cds

Not entirely sure what you are expecting Ubuntu to recognise on a blank CD.  

Surely it's blank, so won't have anything on to recognise?  The only possible reason to have a blank CD would be to write to it, wouldn't it?  I think you will have to explain yourself if you want any more help.

---

### Post by cosmoshell on 2007-06-02
> **ugm6hr said:**
> Not entirely sure what you are expecting Ubuntu to recognise on a blank CD.  

Surely it's blank, so won't have anything on to recognise?  The only possible reason to have a blank CD would be to write to it, wouldn't it?  I think you will have to explain yourself if you want any more help.

it isent detecting it so i cant burn anything on it all the drive does is make gurgling noises

---

### Post by Pragmatist on 2007-06-02
First, some basic information:

1.) Make and model of the drive.

2.) Media format and brand (i.e. TDK CD-R)

3.) What happens if you try to manually mount the CD?
```
sudo mount /dev/hdc /media/cdrom
```
Now check if it mounted:
```
mount
```
look for a line containing /dev/hdc

---

### Post by cosmoshell on 2007-06-03
dont know how to make a model

devil@devil-laptop:~$ sudo mount /dev/hdc /media/cdrom
Password:
mount: No medium found
devil@devil-laptop:~$ mount
/dev/hda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/dev/hda5 on /boot type ext3 (rw)
/dev/hda2 on /media/hda2 type ext3 (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
devil@devil-laptop:~$

---

### Post by Lucifiel on 2007-06-03
LOL... when Pragmatist says "make and model of the drive", he means "what type of drive is it? What is the exact model number of the drive?"

---

### Post by hakimaki on 2007-06-03
Perhaps a hardware issue?  Have you other OS's on your computer where you can double check that issue?  The reason I ask is because I had a similar issue with my previous box, ended up being a faulty component.

---

### Post by pappapump on 2007-06-03
Pop in a written to CD with of the same size you are writing to (740meg 80 min) and make sure it can be read properly.
Then try right clicking and do a software eject instead of button pressing.
Now make sure your blank is spot free and close the drawer.
This assumes that you have blank CD's set to automount with a would you like to make a cd option selected.
Also make sure your removable drives screen looks like this.

---

### Post by Pragmatist on 2007-06-03
> **cosmoshell said:**
> dont know how to make a model

Make AND model refers to the manufacturer and the specific product.  So, for example, Make: SONY 
Model: CD-RW CRX300E

You can find this out using this command:
```
lshal -s | egrep '(CD|DVD)'
```

My second question was this:
[QUOTE=Pragmatist]
2.) Media format and brand (i.e. TDK CD-R)
[/QUOTE]
You can find this out by reading the box of CDs :)

---

### Post by nomad980 on 2007-12-26
I am having the same problem that he has. The ubuntu recognizes blank DVDRs but not CDRs.

storage_model_DVD_RW_DD0201
TDK CD-R 80min 700MB

nomad980@Heaven:~$ sudo mount /dev/scd0 /media/cdrom
[sudo] password for nomad980:
mount: No medium found
nomad980@Heaven:~$ sudo mount /dev/scd1 /media/cdrom
mount: No medium found

This started happening on fiesty after the last kernel update, and continues to happen now in gutsy.

---

