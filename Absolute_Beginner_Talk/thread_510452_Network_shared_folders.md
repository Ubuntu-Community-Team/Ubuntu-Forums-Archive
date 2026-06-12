---
title: "Network shared folders"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by blop on 2007-07-26
Hey all, im having problems with my network shared folders for some reason when i try to open the workgroup it aks me for a password.....

which is weird...

i have 2 ubuntu pcs and 1 winxp....and i cant see any of the folders that i have enabled in gnome because of this login box....

"you must log in to access to guest@netplay"

username : matt
domain: netplay
password:

but i have not got a domain....cheers

---

### Post by UltraMathMan on 2007-07-26
I assume you're trying to access the Ubuntu PCs from XP. If that is the case you'll need samba - check out [SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba") specifically the "Configuring your computer as a server" section.

Hope this helps :)

---

### Post by xpod on 2007-07-26
nfs is better for the two Ubuntu machines i think.

---

### Post by blop on 2007-07-26
the thing is it was working....


when i connect from an Ubuntu pc to the workgroup it shows the workgroup but when i double click it to show the shares it gives me a login box......

when i connect from xp it actually show the computers but when i select a computer to see the shares it gives me a login box for that machine....and the logon does not work..

---

### Post by UltraMathMan on 2007-07-26
I got the same logon box on one of my XP machines when connecting to the Ubuntu box, where the correct username and password for an existing user on the Ubuntu machine failed. Doing```
sudo  smbpasswd -a username
``` for the existing username and setting home directories as browsable and writable in /etc/samba/smb.conf fixed it for me.

---

