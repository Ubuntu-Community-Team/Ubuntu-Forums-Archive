---
title: "Unable to relocate &quot;Documents dir to ntfs"
date: 2011-04-12
forum: Any Other OS
---

### Post by gc2712 on 2011-04-12
I want to share "My Documents", "My Pictures" etc folders with a dual boot of XP and linux mint 10. I have created a data partition and edited the user-dirs.dir file to point to the new location on the ntfs partition (It is mounted at startup). eg 

XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOWNLOAD_DIR="/media/GCDATA-LENOVO/Downloads"
XDG_MUSIC_DIR="/media/GCDATA-LENOVO/My Documents/My Music"
XDG_VIDEOS_DIR="/media/GCDATA-LENOVO/My Documents/My Videos"
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOCUMENTS_DIR="/media/GCDATA-LENOVO/My Documents"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PICTURES_DIR="/media/GCDATA-LENOVO/My Documents/My Pictures"

I then logged out and in again.

Fstab entry for the ntfs data partition is:

#Entry for /dev/sda6 :
UUID=2889219B1F6E4B74    /media/GCDATA-LENOVO    ntfs-3g defaults,nosuid,nodev,locale=en_US.utf8    0    0

The problem is the new locations are not implemented and the default folders remain located in my home directory on the root partition. I already understand that I should not try and change my home dir to ntfs so I only want to change location of My Documents folders.

Can anyone give me a solution to this. As several posts I have read indicate that the above should work.

---

### Post by Perfect Storm on 2011-04-12
Moved to Other OS/Distro Talk forum.

---

