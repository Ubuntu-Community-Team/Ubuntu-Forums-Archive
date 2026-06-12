---
title: "'Device not ready' halts startup"
date: 2006-04-06
forum: Absolute Beginner Talk
---

### Post by klichev on 2006-04-06
Hello!

Sometimes, when I try to load Kubuntu I get error message 'Device not ready: dev/hdc/' (that is my CD-ROM) and then the startup stops on command prompt. Is Kubuntu trying to mount it at startup and something goes wrong or what? And if it does, how can I prevent it?

It might be a problem with my device, though, because occasionally under WinXP it will stick closed/open and will disappear from the System (when computer is restarted with disk inside) or after Nero burn, but with Kubuntu it happens on fresh system start with no disk inside.

Thanx!!!

---

### Post by towsonu2003 on 2006-04-06
check out your /etc/fstab file (or post it here). in the line where it says /dev/hdc, there should be something that says "noauto"... uhm, just post the file here :) to post the file here, use ```
cat /etc/fstab
``` in a terminal and copy paste output here (don't copy paste your username by mistake -I'm paranoid)

A quick workaround would be to comment out the /dev/hdc line from fstab altoghether and manually mount cdrom (or write a ~script for that) when you insert a disc... manually mounting without the fstab entry requires a long command (see man mount) that should include the filesystem (ISO96something), /dev/hdc, and the place as part of command arguments to mount it...  

if you decide to change your fstab, make sure you keep a backup of the previous one, just in case...

---

### Post by klichev on 2006-04-12
OK, here's the /etc/fstab. I pasted it the whole, thought the CD-ROM is the hdc device. Just today it took me 4-5 restarts to make it work. At the end I put a CD and managed to boot. As I said, it happens to me in Windows mainly when the disk is auto-ejected after burn. Sometimes it would happen when after spinning the CD slows and stops. Then it just disappears, the eject button is not working and the CPU gets at 100% on Windows. In Ubuntu so far, the problem is at startup (not that I use it for long and can tell for sure, thought)...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/WinC     ntfs    nls=utf8,umask=0222 0       0
/dev/hda5       /media/WinD     ntfs    nls=utf8,umask=0222 0       0
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by towsonu2003 on 2006-04-12
[QUOTE=klichev]
/dev/hdc        /media/cdrom0   udf,iso9660 user,**noauto**     0       0
[/QUOTE]
hmm, I thought "noauto" wasn't there, but it is (it's supposed to be there :) )

try rebooting with the following fstab (hdc commented out) and see what happens
```

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda7 / ext3 defaults,errors=remount-ro 0 1
/dev/hda1 /media/WinC ntfs nls=utf8,umask=0222 0 0
/dev/hda5 /media/WinD ntfs nls=utf8,umask=0222 0 0
/dev/hda6 none swap sw 0 0
# /dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

```

if still hangs, uncomment the line (back to its original state) and next time it does this, try to pass it with ctrl+c. check out the file /var/log/messages for errors too. and do ```

dmesg >> ~/Desktop/dmesg1.txt
``` and check out the information in dmesg1.txt (on your desktop). you will be looking for errors as well as anything that seems to be related to hdc/cdrom/iso/mount/filesystem...

---

