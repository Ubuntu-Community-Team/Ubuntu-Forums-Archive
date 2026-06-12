---
title: "network problem"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by Demystification on 2007-07-24
I have a desktop and a laptop computer. I have installed windowsXP and ubuntu in both of them. When I run windowsXP  on one of them, the other running ubuntu can access properly the computer running WindowsXP. When I restart the computer and run ubuntu in both of them I cannot access the other.

Is there a kind of firewall running in ubuntu? Do I have to "share" a disk to be able to access the computers?

---

### Post by Orochi on 2007-07-24
Yeah, in Nautilius you can right click on a folder and choose Share to share the folder. Use Windows file sharing (Samba). It might say you need to download some new software, just say ok.

---

### Post by Rocket2DMn on 2007-07-24
It would be extremely insecure if you could just simply access the whole hard drive over the network without needing to set it up first.
If SSH is enabled on your box, you could always use the Connect to Server function from the other computer, select SSH, and then login with username and password and then have access to the full drive when the remote folder is mounted on your desktop.
That is one way to set up, but if you want open sharing between computers, use Samba so your windows can see the folders.

---

### Post by Demystification on 2007-07-24
hey if I wasn't an absolute beginner, I wouldn't be in that forum...

Why does the computers belong to MShome network??? I couldn't connect when I enter "UNIX network NFS" even when I entered the IP address of the desktop computer


where can I find "Samba"

---

### Post by Rocket2DMn on 2007-07-24
You can start here: [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

