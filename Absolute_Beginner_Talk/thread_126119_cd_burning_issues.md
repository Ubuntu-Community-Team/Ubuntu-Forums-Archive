---
title: "cd burning issues"
date: 2006-02-05
forum: Absolute Beginner Talk
---

### Post by RaiSuli on 2006-02-05
Hi,

I've installed k3b on my new system, but it just dies on me every time I try to load it. It gets to the point "scanning cd drives" and that's it. No error message, it just stops working.

When I try to mount the drive in the terminal, I get the following error:

mount: block device /dev/hdd is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdd,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

This can't be good, right?

---

### Post by el3ktro on 2006-02-05
Please start K3b from a konsole window, then you'll have some interesting output which may help your (or me ;-) ) to find your problem.

Tom

---

### Post by RaiSuli on 2006-02-05
Thanks for the quick reply. This is what I get from the terminal.

kernforce@RIPPER:~$ k3b
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
Link points to "/tmp/ksocket-kernforce"
Link points to "/tmp/kde-kernforce"
kbuildsycoca running...
kernforce@RIPPER:~$ find: /dev/.static: Permission denied
k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
k3b: WARNING: Can't open /home/kernforce/.kde/share/apps/konqueror/bookmarks.xml

EDIT: k3b started this time and even burned a cd. Here are some more messages from the terminal after the launch:

Launched ok, pid = 9639
OggS-SEEK: at 0 want 78328 got 68160 (diff-requested 78328)
OggS-SEEK: at 78400 want 520 got 0 (diff-requested -77880)
kio (KDirWatch): WARNING: KDirWatch::removeDir can't handle '/etc/samba/smb.conf'
kio (KDirWatch): WARNING: KDirWatch::removeDir can't handle '/etc/security/fileshare.conf'
ICE default IO error handler doing an exit(), pid = 9636, errno = 0

I downloaded k3b with apt-get and am using it under Gnome.

---

### Post by taurus on 2006-02-05
Try

sudo k3b

Otherwise, you can always try graveman or xcdroast to see if your CD-RW is working or not!

---

### Post by RaiSuli on 2006-02-05
[QUOTE=taurus]Try

sudo k3b

Otherwise, you can always try graveman or xcdroast to see if your CD-RW is working or not![/QUOTE]

sudo k3b resulted in an ICEauthority error that prevented me from logging into the system. I read that some people have the same problem with KDE apps on Gnome. Is this a permission problem and is there a way around it?

The CD_RW works fine, burns cds with Gnomebaker and Graveman. I only need k3b for burning video dvds because none of the other applications seem to be able to handle this. I'd happily step away from k3b, if someone could point out another burning software with this function.

---

### Post by RaiSuli on 2006-02-06
New idea: would it help to install the kubuntu desktop on my system? Would that make a difference?

---

### Post by annsachd on 2006-02-06
I just burned a bunch of data CDs with Graveman. Worked like a charm, fast too.

You might want to give Graveman a try.

---

### Post by RaiSuli on 2006-02-06
Graveman is fine for data cds and other stuff, but I don't think there's an option for burning video dvds, which means dvds where the burning software creates a file structure that is supported by stand-alone dvd players. I need to burn these a lot, and I really don't want to boot into Windows just for that. :(

---

### Post by newuser111 on 2006-02-06
you can safely delete Iceauthority files as well as Xauthority Xauth

---

