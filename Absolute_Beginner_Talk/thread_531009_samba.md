---
title: "samba"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by mstrap123 on 2007-08-21
hello everyone. i cannot connect to the samba server from my xp machine. i m able to see the ubuntu machine in my workgroup but when i click on it, it return "you might not have permission to use this network resource. contact the administrator of this server to find out if you have access permission. The network path was not found." what is the problem and how to solve it.

---

### Post by will71110 on 2007-08-21
if you have NTFS installed on the XP drive then you'll have to log into it. Use "connect to server" under places, Drop down the service type and select Window Share and try using your admin name and password that is on your XP ( You only need to fill in the server field but if it requires a username and password then you'll need that too but as you can see it's optional).  By default, administrator with no password is installed on xp home.  Scarry huh?

---

### Post by luisromangz on 2007-08-21
Maybe you simple have to set permissions for the folder being shared. To be accessed through samba, it will need to be read or read/write for the "others" users.

---

### Post by mstrap123 on 2007-08-21
thanks for the help but i am trying to connect from xp to the ubuntu share. btw i m using the ubuntu 6.10 server and no gui installed.

---

### Post by hyper_ch on 2007-08-21
can you post your  /etc/samba/smb.conf ?

---

### Post by louieb on 2007-08-21
> **mstrap123 said:**
> thanks for the help but i am trying to connect from xp to the ubuntu share. btw i m using the ubuntu 6.10 server and no gui installed.
Just got a new PC put Linux on it and set up file sharing in about 30 min. using this. You'll just have to use nano or something else instead of gedit.
[HOWTO: Setup Samba peer-to-peer with Windows - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=202605")

---

### Post by mstrap123 on 2007-08-21
i setup the samba using HOWTO: Setup Samba peer-to-peer with Windows - Ubuntu Forums so the smb.conf is exactly the same as the 1 in there.

---

### Post by TeaSwigger on 2007-08-21
It shouldn't be. That's a template you're supposed to edit to suit your situation. The guide points out what parts to change in that file, then how to add users, then how to tell Windows to access it. So pour over the guide again and if you have any more questions post back.

---

### Post by mstrap123 on 2007-08-23
i look through the guide again and found out that the ip should be static and mine is dhcp from the router, did it cause me to unable to access the samba server?

---

