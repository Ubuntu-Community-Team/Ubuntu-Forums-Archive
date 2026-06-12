---
title: "Samba"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by rifazmohamme on 2007-05-06
I can connect see my windows shared files of my desktop in ubuntu(in my laptop) also the vice-versa. i've networked my pcs using a switch. Please help me on how to share files frm my linux to windows. i use ubuntu 7.04 n windows xp professional

---

### Post by viciouslime on 2007-05-06
System/Administration/Shared Folders I'm sure you'll figure it out from there, it is pretty simple. You can also right click any folder and select share folder. Any problems, post below :)

---

### Post by rifazmohamme on 2007-05-06
ya i did that. but when i access from windows its askin for a username n pass. i gave the one which i use in linux. but i can't log in

---

### Post by Fitzy_oz on 2007-05-06
> **rifazmohamme said:**
> ya i did that. but when i access from windows its askin for a username n pass. i gave the one which i use in linux. but i can't log in

You;ll need to use one that is on the windows computer, easiest way is to create an account on the windows box called ubuntu or linux or something to that effect, give it a password and when you get prompted use those credentials.

---

### Post by viciouslime on 2007-05-06
Actually you will have to create a samba password. The best thing to do is to run "gksudo gedit /etc/samba/smb.conf" then find the line ;security = user and delete the semi-colon. Save the file and then type "smdpasswd -a <your username>" to set a password for samba. You can then enter your username and the password you set in the last step on the windows side.

---

