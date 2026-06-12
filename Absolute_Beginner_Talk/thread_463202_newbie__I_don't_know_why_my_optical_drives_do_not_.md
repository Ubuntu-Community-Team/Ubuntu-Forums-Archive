---
title: "newbie:  I don't know why my optical drives do not work"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by mgh on 2007-06-03
HI All,

Very new to Linux.  Used Ubuntu 6.10 for a couple of weeks, then did a clean install from CD to Ubuntu 7.04.  Very happy with the new version, though I have a few problems.

The first one I want to work on is getting my DVD drives to work.

I can burn a data DVD when I insert a blank DVD, but can not read the data DVD after it is burned.  If I put in a movie DVD, Totem opens, but will not play the movie.  The first time I put a movie in, I was prompted to install codecs, which I did.

When I browse folder "computer", and double click on what is listed as cdrom, I get message  

Unable to mount the selected volume
mount: special device /dev/scd1 does not exist

I do not know what I am doing with the command line, but managed after reading a bit to display this:

mike@mike-desktop:~$ mount
/dev/hdb2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/dev/hdb5 on /home type ext3 (rw)
/dev/hda1 on /media/sda1 type vfat (rw,utf8,umask=007,gid=46)
/dev/hda2 on /media/sda2 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/hda5 on /media/sda5 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/hda6 on /media/sda6 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/hda7 on /media/sda7 type ntfs (rw,nls=utf8,umask=007,gid=46)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda1 on /media/SimpleDrive type ntfs (rw,nosuid,nodev,umask=222,utf8)

and this:

mike@mike-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=890ae9a2-9ce7-477f-8038-cdcc8d31b59f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=9b663705-8a60-43f1-bd72-dd0345b00bce /home           ext3    defaults        0       2
# /dev/sda1
UUID=07D4-0203  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=40E8E421E8E41746 /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=7AA48CF7A48CB763 /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=8E40396B40395B63 /media/sda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=861CB7F01CB7D97F /media/sda7     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb1
UUID=725d89cc-15e0-4a98-ba92-56832bd13e85 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0

I just do not know what to do next.

BTW, V6.10 had no problems with optical drives, I was able to play anything I had.  I absolutely do not want to go back to V6.10, as 7.04 fixed some other major issues I had.

Thanks for any help.

---

### Post by annda on 2007-06-03
can you read any cds in those drives? if so, put any cd in the tray, wait until it's mounted and check the output of the mount command to make sure that the devices scd0 and scd1 are correct.

---

### Post by mgh on 2007-06-03
Thanks.

I inserted an audio CD, and started it playing, paused it and did the cat /etc/fstab again.  

results:  
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0

Again, unfortunately for me, I do not know what the results mean.

Thanks for the help.

---

### Post by annda on 2007-06-03
hi!

fstab has static configuration, so it says how drives should be mounted, not what actually happens. please type 'mount' in the terminal to see what device file (/dev/something) is mounted as your drive (/media/cdrom0 or something)

---

### Post by mgh on 2007-06-03
Sorry,

here are the "mount" results

mike@mike-desktop:~$ mount
/dev/hdb2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/dev/hdb5 on /home type ext3 (rw)
/dev/hda1 on /media/sda1 type vfat (rw,utf8,umask=007,gid=46)
/dev/hda2 on /media/sda2 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/hda5 on /media/sda5 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/hda6 on /media/sda6 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/hda7 on /media/sda7 type ntfs (rw,nls=utf8,umask=007,gid=46)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda1 on /media/SimpleDrive type ntfs (rw,nosuid,nodev,umask=222,utf8)

I can see all the ntfs partitions on my other hard drive, and see a couple of the ext3 partitions, but can not see anything for cdrom.

Thanks for the help.

---

### Post by annda on 2007-06-03
can you try the same thing with a dvd? or doesn't it automount at all?

can you mount it manually?

```
sudo mount /dev/scd0 /media/cdrom0
```

or for the second drive

```
sudo mount /dev/scd1 /media/cdrom1
```

that way we can see it the device names are wrong or it automounting dvds is not working - in that case you will need some more qualified help, i have no idea how to fix the automounting problem.

---

### Post by mgh on 2007-06-03
here are those results:

mike@mike-desktop:~$ sudo mount /dev/scd0 /media/cdrom0
Password:
mount: special device /dev/scd0 does not exist
mike@mike-desktop:~$ sudo mount /dev/scd1 /media/cdrom1
mount: special device /dev/scd1 does not exist

Thanks again.

---

### Post by annda on 2007-06-03
ok, the device file names are wrong - in your fstab, too. i have no idea how that happened, but you need to correct that.

can you get any dvd to open automatically? movie or data? if so, try the mount command while the system recognizes a disk.

---

### Post by annda on 2007-06-03
oh, i just discovered that you can use gnomebaker to easily check the right device names. go to preferences>devices and see what the appropriate names are - mine are sr0 and sr1.  then edit your fstab accordingly:
```

sudo gedit /etc/fstab
```

creating symbolic links should help too. if you get sr0 and sr1 you can use those lines instead of changing fstab:
```

sudo ln -s /dev/sr0 /dev/scd0
```

```
sudo ln -s /dev/sr1 /dev/scd1
```

---

### Post by mgh on 2007-06-03
Earlier today the DVD would try to load, totem would open, but not do anything, and I would have an icon on the desktop for the DVD.  Now I do not even get that.  I can see the activity light come on the DVD, but nothing happens.

Any suggestions on how to find help for these mounting or naming Issues?

Thanks a lot for the help.

---

### Post by mgh on 2007-06-03
Hmmm, I do not see a "devices".  I have a "hardware information", and I can see the names of my drives, that is NEC 2500A, but not the scd0 or scd1.

fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=890ae9a2-9ce7-477f-8038-cdcc8d31b59f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=9b663705-8a60-43f1-bd72-dd0345b00bce /home           ext3    defaults        0       2
# /dev/sda1
UUID=07D4-0203  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=40E8E421E8E41746 /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=7AA48CF7A48CB763 /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=8E40396B40395B63 /media/sda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=861CB7F01CB7D97F /media/sda7     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb1
UUID=725d89cc-15e0-4a98-ba92-56832bd13e85 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0

Thanks

---

### Post by annda on 2007-06-03
in gnomebaker you should have a column 'Node' - this is what you need. 

if for some reason you don't see it. try any other burning program like k3b to show you what the available drives are.

---

### Post by mgh on 2007-06-03
I got another DVD to load, just not start and play.  Now "mount" shows this also:

/dev/hdc on /media/LEBOWSKI type udf (ro,nosuid,nodev,uid=1000)

Under "node" in gnomebaker, I have /dev/hdd, and /dev/hdc.  The hdd is out of service (a LliteOn drive), the hdc is my NEC.
Thanks

---

### Post by annda on 2007-06-03
great, now change your fstab and substitute /dev/scd0 with /dev/hdc

everything should be fine after reboot.

---

### Post by mgh on 2007-06-03
Well I am making progress, and I thank you for that.

Now my cdrom0 is /dev/hdc.  It shows up with a mount point in gnomebaker, and it will no read a data DVD I made earlier as a test.  I still am unable to play a DVD.  Totem opens automatically, but will not play.

Could it now be a problem with Totem?  Would it be worth installing a different player to see what happens?

Also, before the drives were mounted, I would see cdrom0 and cdrom1 when I browsed "computer".  They are now gone from there.

Thanks for helping me along here.

---

### Post by ivesjd on 2007-06-03
does sound work? If sound works when you play a disc, and you have desktop effects on, turn them off. (and Beryl or Compiz) There seems to be a bug that won't let video play, at least with a standerd set-up.

---

### Post by mgh on 2007-06-03
No, I get no sound.  Totem opens, and shows that it is playing, but the time counter does not move.

Thanks

---

### Post by ivesjd on 2007-06-03
You could try using VLC. type ```
sudo apt-get install vlc
``` in a terminal window.

---

### Post by ivesjd on 2007-06-03
[QUOTE=annda;2775484]oh, i just discovered that you can use gnomebaker to easily check the right device names. go to preferences>devices and see what the appropriate names are - mine are sr0 and sr1.  then edit your fstab accordingly:


Just realized my disc drive wasnt working right, turns out it was mounting as hda!

---

### Post by mgh on 2007-06-06
Thanks to Annda I can now read my data DVDs.

My DVD drives show as dev/hdd and dev/hdc.

I still can not get a DVD to play.  I installed VLC, but it does not even see the DVD.  I will get an icon on my desktop with the name of the DVD, but can not play it.  Totem will open automatically, but can do nothing.

When I right click and open the DVD, the file path is media/cdrom0.

Any ideas?

Thanks

---

