---
title: "not so new to Ubuntu"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by smacintyre569 on 2007-08-15
I have been using Ububtu Desktop Edition for some time now, but now I want to use Server Edition at work as a simple file server. I know some very basic commands, but what I am looking for is some infor on setting up a windows share file, the group name, and file permissions in samba. 

I made a copy of the smb.conf file and I tried to edit it. I tried:
cat < smb.cont
then xedit
and elvis

any help would be greatly appreciated from this command line newb.

---

### Post by ukripper on 2007-08-15
> **smacintyre569 said:**
> I have been using Ububtu Desktop Edition for some time now, but now I want to use Server Edition at work as a simple file server. I know some very basic commands, but what I am looking for is some infor on setting up a windows share file, the group name, and file permissions in samba. 

I made a copy of the smb.conf file and I tried to edit it. I tried:
cat < smb.cont
then xedit
and elvis

any help would be greatly appreciated from this command line newb.

go to terminal and type follwoing command:

```
sudo gedit /etc/samba/smb.conf
```

then you will be able to edit conf file

---

### Post by p_quarles on 2007-08-15
Much easier way:
```
sudo nano /etc/smb.conf
```

The link below is a good tutorial on setting up Samba. Try it, and if you don't understand something or need further help, ask here.
[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

---

### Post by HereInOz on 2007-08-15
Why do you not just use the desktop version as a file server.  Works well.  

All you need to do is to enable the samba share by going to System > Administration > Shared folders and enabling the samba share.  If samba is not installed, you will be prompted to install it.

Then you set a samba username and password in a terminal:

sudo smbpasswd -a username
enter your sudo password, then the samba user password.

After that, you need to open the SMB ports in the firewall (use firestarter for an easy way to do this) and you should be fine.

---

### Post by ukripper on 2007-08-15
Here is samba guide will help you configure it:

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

Goodluck

EDIT:
If you are looking for PEER to PEER networking with your windows machines folwo the below link:
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

