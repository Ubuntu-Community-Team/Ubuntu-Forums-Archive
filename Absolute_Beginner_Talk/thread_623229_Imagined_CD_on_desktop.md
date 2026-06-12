---
title: "Imagined CD on desktop?"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by rumpyhw on 2007-11-25
Hi, I am a total newbie to this forum and Ubuntu. Finally, decided to give it a try with an old Acer Travelmate 202T my school has had in storage for some time. New drive and some ram and I am running Ubuntu. Please forgive this posting if it as been addressed before but I am still getting my feet wet.

my computer will all of a sudden mount an Audio CD on my desktop and i get an error window stating that sound juicer could not find a CD to extract music from. I cannot eject the CD icon unless 
I reboot my machine. It happens when I do nothing or if I am doing anything but I cannot find a pattern to this. 
tried a brand new install and still the problem exists.

I just installed the newest of updates for 7.10 and well I had hoped it would be fixed but not so far. 

Any suggestions would be most appreciated. if it regards the terminal please be gentle.

thanks in advance.
 rumpy

---

### Post by marinesrock.1990 on 2007-11-25
My first reaction is that Ubuntu may not support your CD drive.  However, if the audio CD mounts...hmmm.

---

### Post by annda on 2007-11-25
so does the CD get mounted? do you see it on your desktop?

also, what is the output of this command AFTER you have inserted an audio cd:

```
mount
```

---

### Post by jken146 on 2007-11-25
To eject a CD you  first have to unmount it.  Right-click on the appearing desktop icon and click on the option that says 'Unmount Volume' or 'Eject', I forget which it says.

---

### Post by rumpyhw on 2007-11-25
That is just it a CD mounts onto my desktop, sound juice opens and tells me it cannot read the disk..but......there is no disc in my cd drive. and i cannot eject the imagined CD out of the drive not by right click eject, dragging the icon to the trash bin, or even pressing the eject button on the drive.

when i go to the terminal and type mount i get a bunch of stuff.

/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode-0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

I tried to insert a store bought audio cd to see what happens but nothing happens.

Oh and thanks for the fast replies. BTW i am on two systems one with internet is not using Ubuntu. Still cannot get the wireless to wrk with it.

---

### Post by annda on 2007-11-25
sorry, i didn't read your post carefully enough. i understand now there is NO cd that gets mounted.

one thing is to check the contents of fstab - it might have a cdrom entry:

```
cat /etc/fstab
```

also, can you right-click on the non-existing cd on the desktop and check the volume tab in properties? what is hte mount point? this might be something that needs to removed from the configuration in fstab...

---

### Post by rumpyhw on 2007-11-25
Annda  thanks for the reply


when i did cat /etc/fstab

i see what looks like an entry for the cdrom

/dev/hdc    /media/cdrom0  udf,iso9660 user noauto, exec 0   0

when i right click the icon and go into volume i see
mount point not mounted
file system not mounted
mount option not mounted

my settings are all blank. I have to find another laptop cd drive and see if its an old one. i know this drive is just a plain old cd drive not built for burning.

---

### Post by rumpyhw on 2007-11-25
Okay I decided to shut down the machine and remove the entire cd rom drive from my laptop. restarting the machine. If I do not get the same error then it should be a hardware problem. Keeping my fingers crossed.:confused:

---

### Post by annda on 2007-11-25
i'm not sure what is happening because i can't replicate it but you might try modifying fstab to avoid random mounting of the cdrom drive.

```
gksudo gedit /etc/fstab
```

and remove the cdrom line. it's mounted automatically on cd load, so you don't need the fstab entry. reboot. i hope it helps a bit.

---

### Post by annda on 2007-11-25
> **rumpyhw said:**
> Okay I decided to shut down the machine and remove the entire cd rom drive from my laptop. restarting the machine. If I do not get the same error then it should be a hardware problem. Keeping my fingers crossed.:confused:

DO remove the fstab entry anyway. maybe i'm panicking but it might confuse the booting-mointing process.

---

### Post by rumpyhw on 2007-11-25
Well without the CD drive i did not get an error. I restarted the machine and commented out the CD rom line where you suggested. Still no error...

but when i went to play a music cd it could not find the drive. I am puzzled. Maybe the drive is just too old to be recognized.

I still have to find a newer drive and swap it in maybe it will help.

---

### Post by rumpyhw on 2007-11-25
shut down the machine completely and then restarted it. Put in the same CD and now it can mount and red a real cd and sound juicer is playing it. I still have to see if the computer mounts an imaginary cd yet. But maybe this problem is fixed.

Sorry to bug you like this.

---

### Post by rumpyhw on 2007-11-25
the problem continues.

---

### Post by rumpyhw on 2007-11-27
okay i guess no one is biting on this one. though i did notice one thing once the cd icon appears on my desktop if I physically pop out the drive and replug it back in the icon goes away and the problem does not seem to happen. I am guessing the drive is just too old. SO far 2 days with this os and i am starting to like it. Back to learning. 

Oh and what are the major differences between edubuntu and ubuntu can they be mixed an matched because some application I like in edubuntu.

---

