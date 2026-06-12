---
title: "Network help (yep another one...)?"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by sourjax on 2007-08-16
Okay I've looked and looked and I can't find a HOWTO on how to network two PCs running Ubuntu. I have a 1 PC that's a Vista/Feisty dual boot and another that is Feisty only. I only use Vista for things that I can't do in Linux (iTunes, Anime Studio Pro, U3..) so Networking wuth Windows is pointless. I want to network and share folders/files on the two PC's like I could with a standard Windows Network. 

So how can I do this, do I need Samba (I wouldn't think so but I'm still really new at this)?

---

### Post by mikeyphi on 2007-08-16
> **sourjax said:**
> Okay I've looked and looked and I can't find a HOWTO on how to network two PCs running Ubuntu. I have a 1 PC that's a Vista/Feisty dual boot and another that is Feisty only. I only use Vista for things that I can't do in Linux (iTunes, Anime Studio Pro, U3..) so Networking wuth Windows is pointless. I want to network and share folders/files on the two PC's like I could with a standard Windows Network. 

So how can I do this, do I need Samba (I wouldn't think so but I'm still really new at this)?

You need Samba - check under System/Administration/Services to see if you have it - if not - download.
Then again under System/Administration/ Shared Folders.....select General tab ...make sure same Workgroup name on both computers...select Folders tab...Add which folders to share (/home/username) perhaps?
Also make sure the link between computers is set up.

---

### Post by jspangler on 2007-08-16
You also have to make sure samba is set up with a username password. After following the instructions above, activate a new samba username:

```
sudo smbpasswd -a username
```
Then type in the password of your choice (remember this username and password, it's only for networking. Then:
```
sudo smbpasswd -e username
```

Use this username and password if prompted by windows.


ADDITION: If you are using GNOME, an easy way to add Samba is to right click a folder you want to share and go to "Share Folder". If Samba is not installed, it will ask if you want to install it. Then choose SMB (Windows Networking). After you do this, follow the other instructions from mikeyphi to make sure you have the workgroup set up correctly.

---

### Post by sourjax on 2007-08-16
I'll try it out, but why do I need Samba since I'm not going to use it for Windows? Do I need to install Samba on both PCs or just one?

---

### Post by jspangler on 2007-08-16
Well, you need Samba if you want to be able to browse a shared computer (like in Windows). With Samba, you can go to "Network" in GNOME and see which computers are online and then browse their shared folders.

Another option is to use NFS. However, with NFS each shared folder must be specifically mounted using the mount command (or automounted in /etc/fstab).

Hope that helps.

---

### Post by jspangler on 2007-08-16
You need to install Samba on both PCs.

---

### Post by sourjax on 2007-08-16
I have an external Drive I want to use as a network storage drive can I do that with Samba or NFS. I can do it in Windows so I know it has to be possible in Linux, or at least I think...

Any ideas on how to do this?

---

### Post by jspangler on 2007-08-16
You can do that with either Samba or NFS. You just need to share the folder where the drive is mounted. So, if the drive is mounted at /media/USBDrive, then you need to share /media/USBDrive.

---

### Post by sourjax on 2007-08-16
Okay I can "see" everything but it won't let me do anything but browse the folder/drive that I shared I tried to chmod the folder/drive...

```

sudo chmod -R 0777 /media/Storage

```

it doesn't do anything all I get is this...

```

chmod: changing permissions of `/media/Storage': Read-only file system
chmod: changing permissions of `/media/Storage/$RECYCLE.BIN': Read-only file system
chmod: changing permissions of `/media/Storage/$RECYCLE.BIN/S-1-5-21-944347005-1020124143-4272399934-1000': Read-only file system
chmod: changing permissions of `/media/Storage/$RECYCLE.BIN/S-1-5-21-944347005-1020124143-4272399934-1000/desktop.ini': Read-only file system
chmod: changing permissions of `/media/Storage/System Volume Information': Read-only file system
chmod: changing permissions of `/media/Storage/System Volume Information/tracking.log': Read-only file system

```

Any idea how I can change the permissions?

Note: I'd like to delete the "$RECYCLE.BIN" and everything else currently on the disk but 

```

sudo rm -R /media/Storage/*

```

doesn't do it, any ideas on how I can do that?

---

### Post by sourjax on 2007-08-17
Okay I figured out how to delete the files I wanted to delete. How do I properly add this disk to fstab?

---

