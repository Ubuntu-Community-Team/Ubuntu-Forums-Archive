---
title: "Thumb Drive Access Issues?"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by zombiepkx on 2007-02-24
I have a thumb drive which I use to move my band's music I record in the band room to my desktop in my room to edit and such,

And for some reason, I can't read/write in ubuntu with this drive at all on any of my PCs, it's 1GB, FAT, no RW protection set on it.

It works fine to write to in Windows just not Linux.

Mind helping?

---

### Post by yabbadabbadont on 2007-02-24
Does the drive get mounted automatically when you plug it in?

---

### Post by zombiepkx on 2007-02-24
Sure does!

---

### Post by yabbadabbadont on 2007-02-24
When the drive is plugged in and mounted, open a terminal window and run, "mount".  Please post the results back here.

---

### Post by zombiepkx on 2007-02-24
/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-11-generic/volatile type tmpfs (rw)
/dev/sda5 on /media/music type fuse (rw,nosuid,nodev,noatime,allow_other)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdb1 on /media/usbdisk type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=114,umask=077,iocharset=utf8)

---

### Post by yabbadabbadont on 2007-02-24
Open a terminal window and run, "id".  What is the output?

---

### Post by zombiepkx on 2007-02-24
uid=1002(jesse) gid=0(root) groups=0(root),4(adm),20(dialout),21(fax),24(cdrom),25(floppy),26(tape),29(audio),30(dip),46(plugdev),111(scanner),114(admin),115(fuse)


I see that the gids don't match now. I'm pretty new though, so I don't know how to fix that with a drive that isn't mounted and entered in fstab/mtab :X

---

### Post by zombiepkx on 2007-02-24
Oh wait, just add myself to group 112, or 102 or whatever.. XD


Thanks, you just helped me solve my own problem :)

Would it be

group: usbusers
id:       114

Then?

---

### Post by yabbadabbadont on 2007-02-24
Wow.  What did you do to create that user?

"gid=0(root) groups=0(root)"

---

### Post by zombiepkx on 2007-02-24
actually funny enough,
I did nothing of the sort.
I just used sudo admin-users
Went, created a user in my old accout (zombiepkx) which is no longer existant.

Then went into root and set it up so that "Jesse" was in it XD

---

### Post by zombiepkx on 2007-02-24
Fixed!

Thanks, I just had to be reminded that drives and mountables use groups and ids and such to spur me onwards to victory!

---

