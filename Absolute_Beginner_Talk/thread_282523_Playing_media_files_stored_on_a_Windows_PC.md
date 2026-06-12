---
title: "Playing media files stored on a Windows PC"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by Contrast on 2006-10-22
I have about 60 GB worth of MP3's stored on my Windows desktop (I have Ubuntu on my laptop, and plan on putting on the desktop once I find a Linux replacement for all the Windows programs I use). I can view them without a problem through Samba, however, I'm unable to open them without copying and pasting them to the laptop. I tried adding the desktop's hard drive as a network folder using the Network Folder wizard and with just about every combination of the desktop's server's name (HOME), computer name (Desktop), and hard drive letter (C - I tried this with and without a colon and backslash) in the Server and Name fields, it said it was "unable to connect to server." I'd really like to be able to access and modify these files without having to copy and paste them to my laptop every time, as well as share them on P2P programs if this is possible. Lastly, please let me know if the files will become accessable through Samba once I switch the desktop over to Linux. I'm a relative Linux newbie, so any help this keeps that in mind would be greatly appreciated.

---

### Post by meng on 2006-10-22
If you can view them through Samba, VLC should be capable of playing them.

---

### Post by taurus on 2006-10-22
If you can view them, then any media player in Linux can play them.  Just tell the program where your source is...

---

### Post by BitTorrentBuddha on 2006-10-22
Try this if just playing it doesn't work:
Install smbfs ```
sudo aptitude install smbfs
```
Make a mount point and mount the windows share there *replace **hostname** and **sharename** with the hostname or IP of the windows computer and the name of the windows share repsectively*```
sudo mkdir /mnt/windows
sudo smbmount //**hostname**/**sharename** /mnt/windows
```
Then you should be able to play any media in that windows share in any media player you so choose (I tested rhythmbox and listen.)

---

### Post by meng on 2006-10-22
> **taurus said:**
> If you can view them, then any media player in Linux can play them.  Just tell the program where your source is...
This doesn't accord with my experience: without a proper mount, VLC will still play the files whereas Totem, Xine and Mplayer will not.

---

### Post by featherking on 2006-10-22
If you are looking for a more permanent solution you could add a line to your /etc/fstab file (be sure to back it up first). The line i use is

```
//RON/iTunes /mnt/iTunes smbfs username=**winuser**,password=**winpass**,umask 022 0 0
```

Just replace **winuser** and **winpass** with your windows logon info and you should have it mounted automatically upon boot as it mounts your hard drive in your computer. You will still have to install smbfs for this to work, but i play all my music from a windows desktop this way

---

