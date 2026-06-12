---
title: "[Antergos] SMB stall to 0kb/sec when receiving data"
date: 2019-11-21
forum: Arch and derivatives
---

### Post by ryan.fitzsimmons on 2019-11-21
SMB for some reason has started to stall to no data transfer when sending data to it for my plex server, usually after about 1GB but not always a guarentee at that point.

Downloading from the server still fine at a stable 112MB/sec.

tried adjusting MTU to no avail, tested SMART of all 12 drives in both and they all come back as passing (on system in question and on a Windows system).

What should i try next?

EDIT: would post on Antergos forums but they are no more, and Arch registration is snobby and forces OS verification... dont want to have to take time to reinstall if i dont have to.

---

### Post by TheFu on 2019-11-22
What to the samba logs say?
Check the client and server logs.

---

### Post by ajgreeny on 2019-11-22
It might be worth seeing if the Arcolinux forums can help as they have a section specifically to assist ex-Antergos users at [https://arcolinuxforum.com/viewforum.php?f=135&sid=269366c40c4026be5e43ab53581b8841](https://arcolinuxforum.com/viewforum.php?f=135&sid=269366c40c4026be5e43ab53581b8841)

---

### Post by SeijiSensei on 2019-11-22
Any chance you could add support for NFS? I use both NFS and Samba on my server, the latter for the occasional time I need a Windows client. But *nix-to-*nix file sharing works best over NFS.

---

### Post by ryan.fitzsimmons on 2019-11-22
> **TheFu said:**
> What to the samba logs say?
Check the client and server logs.

apparently i have no logs...

Nov 22 16:41:02 Templar-Archives smbd[641211]: [2019/11/22 16:41:02.606765,  0] ../../lib/util/debug.c:1090(reopen_one_log)
Nov 22 16:41:02 Templar-Archives smbd[641211]:   reopen_one_log: Unable to open new log file '/usr/local/samba/var/log.archon': No such file or directory

> **ajgreeny said:**
> It might be worth seeing if the Arcolinux  forums can help as they have a section specifically to assist  ex-Antergos users at [https://arcolinuxforum.com/viewforum.php?f=135&sid=269366c40c4026be5e43ab53581b8841](https://arcolinuxforum.com/viewforum.php?f=135&sid=269366c40c4026be5e43ab53581b8841)

Thanks for the info. Will check out.

> **SeijiSensei said:**
> Any chance you could add support for NFS? I  use both NFS and Samba on my server, the latter for the occasional time I  need a Windows client. But *nix-to-*nix file sharing works best over  NFS.

Will look into this

---

### Post by TheFu on 2019-11-22
+1 on using NFS for unix-to-unix needs.

---

