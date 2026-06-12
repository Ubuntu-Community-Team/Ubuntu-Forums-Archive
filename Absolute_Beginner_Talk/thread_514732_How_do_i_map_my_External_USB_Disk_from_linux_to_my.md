---
title: "How do i map my External USB Disk from linux to my XP drives????"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by highlevelthinker on 2007-08-01
I am trying to network my external USB disk through samba on my development server to my XP laptop for storage.... 

I had enough trouble figuring out how to mount the usb drive... now when i try to connect to it from windows... it asks me for a user name and password... and wont accept the user and pass i think i have set for it. I have a feeling i have not set proper permissions for the mounted disk.

This has given me headaches for weeks, so finally decided to join a blog.

Can anybody help me please????

Here is the share information in smb.conf:

[WebDevelopment]
comment=Development Sharing Folder
path=/var/www
browseable=yes
read only=No
guest ok=Yes
public=yes

[Storage]
comment=USB storage Device
path=/media/usbdisk
browseable=yes
writeable=yes
guest ok=yes

The webdevelopment mount works fine... i cant figure out what to change in the storage drive.

---

### Post by Austin_KW on 2007-08-01
The password it is asking for is the samba password (not the user password)

To add a samba password for your ***username*** use the following command in a terminal
sudo smbpasswd -a ***username***
Password:*YourSudoPassword*
New SMB password:***newSambaPassword***

You will then have to restart samba
sudo /etc/init.d/samba restart

Then use your ***username*** and ***newSambaPassword*** to access your shares

Alternatively (not recommended) you can remove user passwords by removing the default "security = user" and adding "security = share" to the Authentication section of /etc/samba/smb.conf
Then restart samba services as above.

---

