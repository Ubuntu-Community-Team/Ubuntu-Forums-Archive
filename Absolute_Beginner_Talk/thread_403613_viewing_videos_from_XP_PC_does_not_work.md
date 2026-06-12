---
title: "viewing videos from XP PC does not work"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by pognonec on 2007-04-07
On my Ubuntus edgy PCs, I can navigate to an XP computer on my network, and listen to mp3 files localized on that remote PC by simply double clicking on it. Totem handles everything OK.
Great.
However, if I do the same with a video file (.avi), Totem also opens up, but nothing happens, and the movie is not played. When the same movie file is first transfered to the Ubuntu machine, it can then be played with no problem.
Transferring a 100Mo on my network takes a little less than 1 min, and the same movie can also be displayed from an XP PC to another XP PC. So it does not look like a bandwidth problem.
What could be wrong with my Ubuntu edgy settings?

---

### Post by xopher on 2007-04-07
Weird, haven't tried this myself though.

Have you tried alternative players? Eg. VLC, mplayer? The other backend for totem? (gstreamer/xine)

---

### Post by pognonec on 2007-04-07
Yep, I tried with VLC, and it gives the same result.

---

### Post by chocbar31 on 2007-04-07
You need to mount the network folder(s).

[http://ubuntuguide.org/wiki/Dapper#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite]("http://ubuntuguide.org/wiki/Dapper#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite")

This should help

---

### Post by chocbar31 on 2007-04-07
> **chocbar31 said:**
> You need to mount the network folder(s).

[http://ubuntuguide.org/wiki/Dapper#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite]("http://ubuntuguide.org/wiki/Dapper#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite")

This should help


Or a quick fix!
[http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read.2Fwrite]("http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read.2Fwrite")

---

### Post by pognonec on 2007-04-07
Thanx Chocbar,
but the files I cannot play are on an XP PC, and are perfectly accessible (shared). Proof is I can LISTEN to mp3 files, but not VIEW avi files, that are in the same exact folder on this networked windoz machine :confused:

---

### Post by vpiff on 2007-04-07
I have the same idential problem, if I copy the avi file there are no problem, if I double clik on it the player open, but nothing is shown...

---

### Post by pognonec on 2007-04-08
Two more pieces of information:

1- As suggested by chocbar31, I mounted the folder from the XP machine containing the avi file before trying to view the avi file: it does not help;
2- I tried the other way around, that is: the avi file is on the Ubuntu Edgy machine, and I open it from the XP machine: it works flawlessly.

So there clearly is a problem, at least with my config, for viewing an avi file through the LAN with Ubuntu. 

Any idea?

---

