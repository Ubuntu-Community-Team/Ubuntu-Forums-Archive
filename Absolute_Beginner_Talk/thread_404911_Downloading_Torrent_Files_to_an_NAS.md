---
title: "Downloading Torrent Files to an NAS"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2007-04-09
Hello. I am using KTorrent. How can I have the torrent files download directly to a Network Attached Storage drive via Samba? If I try to do so on KTorrent, it does not give me an option. Thank you.

---

### Post by amitroy5 on 2007-04-11
Bump. I would like to clarify. How do I download a torrent directly to another computer via the samba file sharing.

---

### Post by devnulljp on 2007-04-11
Easy way is to mount the share, cd to the mount point, use screen to launch a virtual terminal and use btdownloadcurses to run the torrent session on the command line. You can also use this method to ssh into a remote linux machine and do the same thing that way -- downloadtorrent on the remote machine.

---

### Post by amitroy5 on 2007-04-20
I am not that advanced with Linux. Do you know of any tutorial of how to do this?

> **devnulljp said:**
> Easy way is to mount the share, cd to the mount point, use screen to launch a virtual terminal and use btdownloadcurses to run the torrent session on the command line. You can also use this method to ssh into a remote linux machine and do the same thing that way -- downloadtorrent on the remote machine.

---

### Post by amitroy5 on 2007-04-25
bump

How do I mount a samba share as a virtual drive or folder?

---

### Post by amitroy5 on 2007-11-03
Here is a guide to set up a Samba share to work with KTorrent. It will allow the samba share to act like a normal drive.

[http://ubuntuforums.org/showthread.php?t=280473](http://ubuntuforums.org/showthread.php?t=280473)

---

