---
title: "CD Rom"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by the beak on 2008-03-05
Hi I'm a newbie so please excuse the dumb question.

I'm strugglying to play a cd or look at a cd on my damn small linux.

Should the etc/fstab file do this automatically? - bearing in mind I've played around with this.

If not what mount command should I use or do I need to? Am I looking in the wrong directory for it?

---

### Post by mali2297 on 2008-03-05
According to your fstab that you posted earlier, you should be able to mount it with
```

mount /mnt/auto/cdrom

```
Auto-mount can be enabled with gnome or thunar volume managers.

---

### Post by the beak on 2008-03-05
I get the error:

mount:fs type noauto not supported by kernel

any ideas?

---

### Post by mali2297 on 2008-03-05
Do you still have this line in /etc/fstab:
```

/dev/scd0    /mnt/auto/cdrom    udf,iso9660    ro,owner,noexec,noauto   0   0

```
...or have you changed it?

---

### Post by the beak on 2008-03-05
Yep that's on the 4th line.   ???

---

### Post by mali2297 on 2008-03-05
Can you post your entire /etc/fstab? Copy/paste the exact content.

---

### Post by the beak on 2008-03-05
Yep here it's. Thanks for looking at this

/dev/hda2  /  ext3  defaults,errors=remount-ro  0  1
proc  /proc  proc  defaults  0  0
/dev/fd0  /mnt/auto/floppy  vfat  defaults,owner,noauto,showexec  0  0
/dev/scd0  /mnt/auto/cdrom udf,iso9660,ro,owner,noexec,noauto  0  0
# Added by KNOPPIX
/dev/hda1 none swap defaults 0 0

---

### Post by mali2297 on 2008-03-05
> **the beak said:**
> Yep here it's. Thanks for looking at this

/dev/hda2  /  ext3  defaults,errors=remount-ro  0  1
proc  /proc  proc  defaults  0  0
/dev/fd0  /mnt/auto/floppy  vfat  defaults,owner,noauto,showexec  0  0
/dev/scd0  /mnt/auto/cdrom udf,iso9660**[COLOR="Red"],[/COLOR]**ro,owner,noexec,noauto  0  0
# Added by KNOPPIX
/dev/hda1 none swap defaults 0 0

Change the marked "**[COLOR="Red"],[/COLOR]**" into a space. Then reboot.

---

### Post by the beak on 2008-03-05
Brilliant, thanks! I'm well impressed with how helpful everyone is on this

---

### Post by the beak on 2008-03-05
sorry me again.

I now get the following:

wrong fs type, bad option, bad superblock on /dev/scd0,
or too many mounted file systems

???????????????

---

### Post by the beak on 2008-03-05
Any ideas???

---

### Post by mali2297 on 2008-03-05
Try changing the line to
```

/dev/scd0    /mnt/auto/cdrom    udf,iso9660    user,noauto   0   0

```

Note that there should be six columns separated by spaces but no spaces next to the commas.

You can reload fstab without rebooting, just run
```

mount -a

```

---

