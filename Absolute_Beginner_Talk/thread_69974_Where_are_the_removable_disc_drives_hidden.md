---
title: "Where are the removable disc drives hidden?"
date: 2005-09-28
forum: Absolute Beginner Talk
---

### Post by commodore on 2005-09-28
I can see cdrom on the desktop and in nautilus (or whatever it is) but I can't see my floppy disk drive nor my cd-r/rw. Where are they hidden? I even saw them on the device manager but not in nautilus or file browser.

---

### Post by invalid on 2005-09-28
I can't vouch for the icon placement, but they should be in the /media folder
/media/floppy and /media/cdrom1 (or similar)

Cheers,
Cb

---

### Post by greenstar on 2005-09-28
So when you click Places/Computer, you don't see them in the Computer window?

Sounds like they are probably not mounted at startup. Run this command:
```
sudo gedit /etc/fstab
``` and see if all your devices are listed. If you don't know, then post contents of fstab here, and I'll check it out.

greenstar

---

### Post by Kyral on 2005-09-28
Kinda a stupid question, but is there any media in them? The icons don't show up in Nautilus or on the Desktop unless there is actually a CD/Floppy in them

---

### Post by commodore on 2005-09-29
I got this message:
(gedit:21795): GnomeUI-WARNING **:While connecting to session manager: Authentication Rejected, reason: None of the authentication protocols specified are supported and host-based authentication failed.

And gedit had this written in it:
/dev/mapper/casper-snapshot/auto noatime 00
tmpfs/tmp tmpfs nosuids, nodev 00

NOTE: The zeros in gedit's message had dots in them
          I'm currently running ubuntu on Live CD.

---

### Post by wmcbrine on 2005-09-29
Floppy: /dev/fd0
CD Drives: /dev/hdc, /dev/hdd, etc., depending on how they're connected.

Those are the "real" devices. The entries in /media are mount points.

---

### Post by commodore on 2005-09-30
Thank ya. I'll try it out soon.

---

