---
title: "[SOLVED] network/interfaces file issue"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by opie102 on 2008-01-25
hey guys,

 Now this could be attributed to my ignorance and the fact that im teaching my self as i go, but I seem to have run into a frustrating issue.
 
 I attempting to set up a LAMP server with Gusty 7.10 server. I had gone through and set the Ip to static in the etc/network/interfaces/file and had just about everything configured with the drives and shares using webmin and the console together. 

 After not being able to map a drive from my XP box to the file server I was poking around and found that the etc/network/interfaces file was blank and that i could not restart the network using "etc/init.d/networking restart" said no such file or directory. I still had connectivity to the router and internet so figuring I did something stupid i ripped it all out and reinstalled the Server OS. Figuring that the fiel would be restored on the reimaging. 

 Loaded up the OS and did the updates and then went to set the IP and file was still blank. this is after a format and reinstall.

Any ideas? or is there any way to recreate that file or download it. Cause if i open that blank file in PICO and type it out it wont let me save it saying no such file exists. Just wierd cause the file was there at one point.

Hopefully I explained it all correctly.

I am getting an IP if i run IFCONFIG ETH0


Thanks in advanced for any help.

---

### Post by Bachstelze on 2008-01-25
```
cat /etc/network/interfaces
```

**Copy and paste** (do not copy manually) that into a terminal, press Enter and tell us what you get.

---

### Post by opie102 on 2008-01-25
#This file describes the network interfaces available on your system 
#and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback 

# The primary network interface
auto eth0
iface eth0 inet dhcp


***
now i know you said not to put it in manually but i didnt see anyother way as the server is running in terminal mode and i havent installed a GUI as it is just going to be a file, web, etc. with no monitor and using PUTTY and WEBMIN to administer it. I dont believe there is a way to run a browser on that or i may be mistaken.

---

