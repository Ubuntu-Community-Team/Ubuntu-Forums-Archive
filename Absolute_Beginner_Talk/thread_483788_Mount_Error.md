---
title: "Mount Error"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by trottl on 2007-06-25
I mounted my external device, it was mounted automatically.

Then I changed in the properties dialog the mount options.

After removing and adding the device I no get alway invalid mount options.

How can I remove the mountoptions.
I cant found them in mtab and fstab

fstab
proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=5dc83eaa-91f6-435d-ae4e-48a1de4172a8 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=07928a0a-0ec0-4ce1-bb1f-5b6f5c7450a0 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0


mtab
/dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-16-generic/volatile tmpfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0

Thanx in advice

Chris

---

### Post by vanadium on 2007-06-25
Remove the options you set yourself first to be able to mount it again. then provide us specific info on what you wanted to change and how you did id. Then we might be able to give you specific advice and tell where the error was.

---

### Post by trottl on 2007-06-25
"Remove the options you set yourself first to be able to mount it again."

Thats the problem, how can I do that.
It must be somewhere saved but I cant find that.

Chris

---

