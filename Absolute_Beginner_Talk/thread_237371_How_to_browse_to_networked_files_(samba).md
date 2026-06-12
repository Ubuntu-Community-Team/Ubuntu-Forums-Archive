---
title: "How to browse to networked files? (samba)"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by crash331 on 2006-08-16
When I am in a media player like VLC or something, where are the network shares located?  In windows, they were under My Computer and then network neighborhood or something like that, but I can't find the folder in linux.  The only place I see is if I go to places and then Network Servers.

---

### Post by andb on 2006-08-16
Depends on the type of network shares. Can I assume these are windows or Samba shares? If yes, then samba will connect you, either smbclient or mount with '-t smbfs'. the smbmount info page has all the options.

for example:
```
sudo mount -t smbfs //192.168.1.1/SHARE_NAME /media/MOUNTPOINT/ -o uid=1000,username=USERNAME,password=PASSWORD
```

The mountpoint can be anywhere of course.

---

### Post by crash331 on 2006-08-16
What would SHARE_NAME be?  


MSHOME/WINDOWS_COMPUTERNAME/FOLDER?

---

### Post by scxtt on 2006-08-16
SHARE_NAME is the name of the share in windows (or whatever is using samba) ... so if you share C:\Documents and Settings\default_user\My Documents as **windows_MyDocuments** (via right clicking in windows and sharing it), then you'd have \\192.168.1.100\windows_MyDocuments as the path to the samba share ...

---

### Post by crash331 on 2006-08-16
Ah, so I have to mount each folder that is shared in windows?  I have several folders shared on my windows machine:

Business Docs
Personal Docs
Videos
Pictures
Music
Azureus
DVD

So I would have to do all of those seperate?  Or can I make it so I have 1 folder that has all those shared folders in it?

---

### Post by scxtt on 2006-08-16
well, you can always share your "C:\" drive in its entirety ...

---

### Post by andb on 2006-08-16
Please, dont share the whole c:\ drive. Scxtt, as a joke, its hilarious, but someone might actually believe you!

Crash331, yes, the best way is to put it into a single folder, then share that folder, so its all under. Each share requires system resources to track, so it makes sense to minimize them. Usually you seperate a share when you need different access rights.

I have a short script that connects all my network shares, and I often have it run at login. I've never tried, but it ought to be possible to mount it automaticaly with /etc/fstab, though I wouldnt do this as the share isnt always there.

---

### Post by scxtt on 2006-08-16
andb, your policy isn't "bad" - but not entirely necessary for a home network (using a router) ...

what i said WAS NOT a joke - it's the easiest way to share mult. folders w/o the need to create ~7 separate shares ... and having it so you have to enter a password keeps it "secure" in as much as anyone w/ physical access to you box needs said password ...

---

### Post by jelly on 2006-08-16
crash, if you just want to browse shares you can do this easily in Gnome.. just go to Places / Network Servers.  Or type smb://server_name_here/ in the location bar.  You can then right-click on any of the share names and click 'Connect to server' which will place an icon on your desktop and list the location as a volume in Gnome.

However, this is only useful for Gnome-aware media players - such as the default movie player (Totem).  For some others, such as VLC and MPlayer, I don't know where (or if) the mount points are created - so I can't access the shares from these applications using this method (doesn't mean you can't - I just don't know how to).

Anyway, just thought I'd mention the simple no-fuss method.  Editting fstab is still the way to go if you want perm shares that can be accessed by all applications.

- Jelly.

---

