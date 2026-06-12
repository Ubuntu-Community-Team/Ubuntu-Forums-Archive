---
title: "Root Administration Programs Missing?"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by Mr Match on 2006-06-26
At the main login screen, I login under the username root, but once I'm logged in,
 under the System bar, and in the Administration programs, there are only:
Device Manager
Network Tools
Printing
System Log
System Monitor

:confused: 

I've gone into the Alacarte Menu Editor, but it says that they are all checked! Yet 
none of them are showing up in my menu...](*,) 

p.s. I also have a question on the Apache server, I've set it all up in the Var>WWW>Apache2-Default
 folder, but how do I *start* the server?

Thanks all!
Cheers~Mr Match

---

### Post by x64Jimbo on 2006-06-26
You should NEVER log in as root. There is nothing that you need in a root login. Everything can be done with sudo. 
As far as the web service goes, just type this command: 
httpd &

---

### Post by need2eat on 2006-07-03
mr match,

the following worked for me:

type "users-admin" in a terminal, highlight root > properties > "user privileges" tab > then check all the boxes.

it is also possible to manually add root to multiple groups in the file - /etc/groups which the first method does:

adm
admin
cdrom
dip
dialout
floppy
tape
audio
video
lpdadmin
plugdev
scanner

hope this helps you and others!

---

