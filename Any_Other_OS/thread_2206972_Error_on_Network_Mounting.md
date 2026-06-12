---
title: "Error on Network Mounting"
date: 2014-02-21
forum: Any Other OS
---

### Post by benjamin15 on 2014-02-21
Using Linux Mint 15:
(line14)
from the fstab I have inserted this to setup a shared folder for a home network. However, when doing "mount -a" it gives me a "[mntent]: line 14 in /etc/fstab is bad"
[B]
# Mapping A Network
//192.***.*.*/benjamin /media/winshare01 cifs uid=1000,gid=1000,credentials=/home/benjamin/.winshare01credentials,iocharset=utf8,sec=ntlm 0 0
[/B]

---

### Post by benjamin15 on 2014-02-21
Fixed most of the problem by a spacing error (dummy stuff). However now I get this on "mount -a"

mount error(115): Operation now in progress
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

---

### Post by howefield on 2014-02-21
Thread moved to the "*Other OS/Distro Support*" forum.

---

### Post by benjamin15 on 2014-02-21
Gracias

---

