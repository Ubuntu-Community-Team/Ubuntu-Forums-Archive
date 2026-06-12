---
title: "sudo apt-get install package"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by markpoole@ntlbusiness.com on 2006-12-19
Sorry about this its not my intention to over bear or get more attention than any other user.
Im a complete beginner at forums as well as ubuntu including terminal but thats why I want to use terminal to stop relying on softwares, capitalism, goverments and other wankers of the highest order.
i go in terminal 
mark@mark:~$
I add
sudo apt-get install package
it asks for a password
I put in my user password and it comes back with!
mark@mark:~$ 
mark@mark:~$ sudo apt-get install package
Password:
marine1mark@mark:~$ marine1
whats is wrong?
Ps is it an install config that I over looked for the uses of journal file?
ect
mark

---

### Post by meng on 2006-12-19
Well for starters I don't actually think there is a package CALLED package. What package are you trying to install? For example, if you wanted to install lyx, you would type

sudo aptitude install lyx
OR
sudo apt-get install lyx

(aptitude and apt-get have similar functionality)

I would try again - your screen log shows that you must have typed your password ("marine1" thanks for sharing it with the world!) AFTER you pressed enter, otherwise it would not have shown on the screen (the password does not echo to screen).

---

