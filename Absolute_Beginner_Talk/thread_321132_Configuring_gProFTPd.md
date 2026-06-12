---
title: "Configuring gProFTPd"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2006-12-18
I am not able to get this working for some reason. How do I get FTP working on Ubuntu? I prefer gproftpd because it has a GUI.

I tried configuring. After I did so, I try logging in and it doesn't work. Thanks!

---

### Post by Pobega on 2006-12-18
It should work unless you have a router firewall on. Check your router (Found at [http://192.168.1.1/](http://192.168.1.1/) 75% of the time) and make sure your firewall isn't on. If it is, try to forward port 21 (FTP's port).

For a user friendly GUI, I would recommend gFTP.

---

### Post by amitroy5 on 2006-12-18
The problem is with the server. I can't get it to say "online." I'm trying to configure an FTP server.

---

### Post by Pobega on 2006-12-18
Oh, FTP Server. I know nothing about those, I thought you were asking about a GUI FTP Client, sorry.

---

### Post by amitroy5 on 2006-12-18
Thanks for your help. Does anyone else knwo how to configure the gproftpd FTP server? Thanks!

---

### Post by amitroy5 on 2006-12-18
I still cannot figure out. Even when I connect from within the local network, it does not connect to the FTP server.

---

### Post by amitroy5 on 2006-12-18
Does anyone at least have a guide to how to configure an FTP server for Ubuntu. I really don't want to be forced to go back to Windows over this. Please help me! I really need an FTP server up and running. Thanks! :)

---

### Post by NumberOne on 2006-12-18
I just installed Pure-FTPD.  It works right out of the box with standard Linux user accounts.  It is just a little more complicated if you want to use "virtual users".  This is what I have set up.  It has a GUI- PureAdmin.  If you want to give this a try, I might be able to help.  I am kind of a Linux newbie, but have 25+ years of windows and network experience.

---

### Post by atnishry on 2006-12-18
try those guides:
[http://www.howtoforge.com/perfect_setup_ubuntu_6.10]("http://www.howtoforge.com/perfect_setup_ubuntu_6.10")
[http://www.howtoforge.com/taxonomy_menu/1/35]("http://www.howtoforge.com/taxonomy_menu/1/35")

---

### Post by Almighty on 2006-12-19
What error messages if any do you get when trying to start the FTP with gproftpd?

---

