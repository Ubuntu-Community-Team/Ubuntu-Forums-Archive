---
title: "connecting NFS mount . . .permission denied"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by castingflame on 2007-09-15
I have set up a small NAS box and can connect with SMB and FTP ok. I would prefer to connect with NFS on my newly installed Ubuntu Lappy but I just get the following error message.  . .

sudo mount 192.168.1.64:/public /home/castingflame/nas
mount: 192.168.1.64:/public failed, reason given by server: Permission denied

I have proven that the nas box is running nfs by turning it on and off and port scanning. 

How does the nas under NFS know who I am? What user and password. IMy laptop is using the same account name and password as a user on the nas box but im confused.

---

### Post by aJayRoo on 2007-09-15
To access an NFS share you need to be using a machine that the NFS server has been told is allowed to connect. What operating system is your server running? Is it Ubuntu (and if so is it desktop or server)?
You must setup the NFS server to allow connections from you machine/network. If you are running a Gnome desktop on the server this can be fairly straight forward, just right click on the folder you are sharing and click 'Share Folder'. Then select NFS and make sure to add your laptop/network to the allowed hosts. If this does not apply then you will need to edit the '/etc/exports' file. I am no expert on this topic but I have setup NFS shares in the past with some help from [this](http://ubuntuforums.org/showthread.php?t=249889) post so I suggest you have a read. Good luck!

---

