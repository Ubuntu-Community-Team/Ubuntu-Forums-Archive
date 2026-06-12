---
title: "Accessing Multiple OS X shared volumes with Ubuntu"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by 72Devilz on 2007-03-10
This issue has been a thorn in my side for a long while. OS X allows you to Windows File share in sharing options to allow windows/linux (ubuntu) machines share files, however you can only access a user directory, which means you will not have access to any other volume connected to the machine you have connected via Windows file sharing to. The secret is modifying the smb.conf file on the OS X machine that you wish to fileshare with. This is accomplished as follows:


Open Terminal and type;

cd /etc 
sudo pico smb.conf 
----------------------------------------------------------
You'll be prompted for the password.
You should see the following with the exception of the lines in bold which I added for my system. 
-------------------------------------------------------------
[global]
client code page = 437
coding system = utf8
guest account = unknown
encrypt passwords = yes

[homes]
comment = User Home Directories
browseable = no
read only = no
create mode = 0750


[B][volumes]
comment = CDs, disk images and network volumes
path = /Volumes
writable = yes[/B]

;[public]
; path = /tmp
; public = yes
; only guest = yes 
; writable = yes
; printable = no

;[printers]
; comment = All Printers
; browseable = no
; printable = yes
; public = no
; writable = no
; create mode = 0700
-------------------------------------------------------------

When done making your changes, hit Control-O to write changes to disk and press Return when prompted for a file name. The hit Control-X to quit pico and close the Terminal window.


This information was found at: [http://macosx.com/forums/networking-compatibility/29906-how-do-i-share-non-osx-volume.html](http://macosx.com/forums/networking-compatibility/29906-how-do-i-share-non-osx-volume.html)

After making the above modifications to the smb.conf file you will have acess to any shared/connected volume on the OS X machine you connect to via Windows File Sharing.

Use this guide at your own risk, I wont take resposibility if you break your Samba sharing.


~Devilz

---

