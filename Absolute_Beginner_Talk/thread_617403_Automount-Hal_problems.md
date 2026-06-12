---
title: "Automount-Hal problems"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by iopo on 2007-11-19
Hi,
I'm having issues automounting cdroms and dvds. I can manually mount them and access them with k3b, kaffeine or any other application so it's not a -mounting issue but rather an auto- one.
I tried debugging the problem following this instructions:

[https://wiki.ubuntu.com/DebuggingRemovableDevices](https://wiki.ubuntu.com/DebuggingRemovableDevices)

In particular, when I write:

```
sudo killall hald
sudo hald --daemon=no --verbose=yes 2>&1 | tee hal.log
```

I get a neverending output message where the block:

[6446]: 10:33:20.297 [E] addon-storage.c:394: open failed for /dev/scd0: Permission denied
[6446]: 10:33:22.297 [E] addon-storage.c:394: open failed for /dev/scd0: Permission denied
[6446]: 10:33:24.297 [E] addon-storage.c:394: open failed for /dev/scd0: Permission denied
[6446]: 10:33:26.297 [E] addon-storage.c:394: open failed for /dev/scd0: Permission denied
[6446]: 10:33:28.303 [E] addon-storage.c:394: open failed for /dev/scd0: Permission denied
[6446]: 10:33:30.305 [E] addon-storage.c:394: open failed for /dev/scd0: Permission denied
[6446]: 10:33:32.305 [E] addon-storage.c:394: open failed for /dev/scd0: Permission denied
[6446]: 10:33:34.305 [E] addon-storage.c:394: open failed for /dev/scd0: Permission denied
[6446]: 10:33:36.305 [E] addon-storage.c:394: open failed for /dev/scd0: Permission denied
[6446]: 10:33:38.305 [E] addon-storage.c:394: open failed for /dev/scd0: Permission denied
[6446]: 10:33:40.305 [E] addon-storage.c:394: open failed for /dev/scd0: Permission denied
[6446]: 10:33:42.306 [E] addon-storage.c:394: open failed for /dev/scd0: Permission denied
[6446]: 10:33:44.305 [E] addon-storage.c:394: open failed for /dev/scd0: Permission denied
[6446]: 10:33:46.305 [E] addon-storage.c:394: open failed for /dev/scd0: Permission denied
[6446]: 10:33:48.305 [E] addon-storage.c:394: open failed for /dev/scd0: Permission denied
10:33:48.920 [D] acpi.c:176: Current voltage is unknown, smaller than 50% or greater than design

is repeated infinetly many times (meaning, for about 5 min, then I closed the terminal).

Any idea on what can be the problem?

Thanks!

p.s. I also tried to execute the two commands above with a cdrom in the driver. The output gets stuck in the same way but the cdrom will get mounted.

---

### Post by Arthur Archnix on 2007-11-20
What's you fstab look like?
```
cat /etc/fstab
```

---

### Post by iopo on 2007-11-26
Hi!
here is my fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6276d1ee-454a-415c-8c72-9dfa2c0a9d8f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=aea79556-b948-a4b4-ef98-6db9c64414ea none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

sorry for the late reply, I was away for thanksgiving.

Thanks!

---

### Post by Arthur Archnix on 2007-11-26
Yeah.. the fstabs fine. Ok, well what about the groups your user belongs to?
```
groups username
```
Compare this with mine. 
```
username : username adm dialout cdrom floppy audio dip video plugdev scanner lpadmin admin netdev powerdev
```
If you're missing one, go to >system >administration >users and groups  Click on your account and then properties, and then the privileges tab. Put a check mark beside the ones your missing. ok. You will need to log out and log back in.

Note, this is just for a default install. But depending on how you're handling security on this computer you may just want to make sure that cdrom and plugdev are checked, as I think that those are the two responsible for HAL.

---

### Post by iopo on 2007-11-26
Hi Arthur Archnix,

```
andrea@andrea-laptop:~$ groups andrea
andrea : andrea adm dialout cdrom floppy audio dip video plugdev scanner lpadmin                                              admin netdev powerdev mythtv

```

it is exactly the same as yours! 

One more thing: if I have K3b or K9copy open, the cdrom tray does not open when I press the tray button. I have first to close the application and then I can get the cdrom.

Anyway, are you on gnome or kde? I'm on KDE and I'm starting thinking is a KDE related issue.

Thank you!

---

### Post by iopo on 2007-11-26
Also, does this make any sense to you?

[HTML]andrea@andrea-laptop:~$ groups fuse
id: fuse: No such user
andrea@andrea-laptop:~$ groups haldaemon
haldaemon : cdrom floppy plugdev haldaemon powerdev
[/HTML]

how is yours?

Thanks

---

