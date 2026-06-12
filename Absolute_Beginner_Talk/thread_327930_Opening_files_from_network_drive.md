---
title: "Opening files from network drive"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by graficus on 2006-12-30
I have an ethernet network hard drive. 
How can I execute files directly from there without copying to internal disk?
(for example, all my music and video are on it. double clicking a song just doesn't work)
Is it possible to mount it instead of going smb:// way?

PS: I think the drive has NT system built into it, as it has its own IP and admin panel served in asp.

Thank you for suggestions!

---

### Post by lucky_chouhan on 2006-12-30
if you play your audio and video you need to vlc player.

---

### Post by graficus on 2006-12-30
I have 5 different players installed, including vlc. They just refuse to play from smb:// network links.

---

### Post by markba on 2006-12-30
> **graficus said:**
> They just refuse to play from smb:// network links.

Accessing file this way makes use of gnome-vfs, Virtual File System. The problem is that the native application (in your case, a music player) must understand this file system. In my experience, only a few applications do fully support vfs, most of them do not work very well or not at all.

Best is to mount a share through /etc/fstab or by adding a mount entry in /etc/rc.local. Then vfs is not used and almost all applications (including music players) can access these files.

---

### Post by graficus on 2007-01-01
I spent hours trying to figure out what you suggested. Too much for me as a beginner. 

If someone would just take time to walk me thru, or at least provide a link if it's already been done, it would be great.

---

### Post by markba on 2007-01-01
> **graficus said:**
> If someone would just take time to walk me thru, or at least provide a link if it's already been done, it would be great.

OK. This is what you have to do.

Open  a terminal

Install the samba file system libraries (you want to connect to a Windows share which uses Samba):
Enter in the terminal: sudo apt-get install smbfs <enter>

Create a mountpoint: the share will be mounted on this point and from there on accessible:
Enter in the terminal: sudo mkdir /media/win <enter>

Now you can do a test mount (assuming you have public access, so no login needed):
Enter in the terminal: sudo mount -t smbfs //<windows share> /media/win

An icon should appear on your desktop. Now you can browse (read-only currently) through your share.

To provide persistency, you must do a mount with each restart of your system. My preference is with /etc/rc/local, this file is executed everytime the system boots. The other is through /etc/fstab, but in practice, this isn't as stable as with /etc/rc/local.

Enter in the terminal: sudo nano /etc/rc.local
Add the following line: mount -t smbfs -o fmask=0777,dmask=0777 //<windows share> /media/win

Good luck.

---

### Post by bayvista on 2007-11-04
Typing in the Mount command gives me the following message:
david@david-laptop:~$ sudo mount -t smbfs  "//davidspc/My Pictures" /davidspc
mount: wrong fs type, bad option, bad superblock on //davidspc/My Pictures,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

The dmesg is:

david@david-laptop:~$ dmesg | tail
[17180334.692000]  CIFS VFS: No username specified
[17180334.692000]  CIFS VFS: cifs_mount failed w/return code = -22
[17181505.360000] smbfs: mount_data version 1935764838 is not supported
[17181564.452000] smbfs: mount_data version 1935764838 is not supported
[17181622.424000] CIFS: Unknown mount option fmask
[17181622.424000] CIFS: Unknown mount option dmask
[17181622.424000]  CIFS VFS: No username specified
[17181622.424000]  CIFS VFS: cifs_mount failed w/return code = -22
[17181666.728000]  CIFS VFS: cifs_mount failed w/return code = -22

Any help welcome.
[17182236.128000] smb_fill_super: missing data argument
david@david-laptop:~$

---

