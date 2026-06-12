---
title: "howto revive broken pen drive?"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by nab on 2008-03-31
Hi all,

today i did something really stupid: While Windows was updating I reformeted a usb stick. GUess what happend windows restarted itself before finishing the formatting (No I didn't answer the question to reboot with yes).

Now back home I try to revive the stick.

With "fidisk -l" and gparted! I get only my local drive but no usb drive. "lsusb" doesn't show any devices.

What could I do next?
TIA,
Niko

---

### Post by lswest on 2008-03-31
you might need to stick it in a windows machine again, i know it sounds silly, but i've found...what windows breaks, usually only windows can fix :P  Otherwise, what filesystem were you formatting it to? if it was ntfs make sure you have ntfs-config installed.

---

### Post by nab on 2008-04-01
I tried formating it with windows and linux. Under windows xp i tried different data recovery tools without any success.

Both systems don't "see" the stick.

I tried formating it to fat.

---

### Post by lswest on 2008-04-01
Then sorry, looks to me like it's not coming back :S  At least, nothing i know of will recognize it if the programs you listed above and windows don't.  Maybe someone else has a genius idea :P

---

### Post by bumanie on 2008-04-01
If you have access to a windows machine, you could try this site. Got no idea whether it will work.
[http://3d2f.com/download/41-460-usb-drive-files-recovery-software-free-download.shtml](http://3d2f.com/download/41-460-usb-drive-files-recovery-software-free-download.shtml)
Unfortunately, I think it's past help however.

---

### Post by mick8985 on 2008-04-01
Sounds pretty broken to me, if it doesn't show up in lsusb, its not gonna show up as /dev/sd**, if it doesnt show up in /dev no tools with do anything. On the other hand if you find it has showed up in /dev/, just do

```
 sudo apt-get install [ntfs-progs]("apt:ntfsprogs")

sudo mkfs.ntfs /dev/sd*1
```

replacing * with the drive letter for your usb pendrive.

---

