---
title: "Can't import pics from digital camera"
date: 2005-08-18
forum: Absolute Beginner Talk
---

### Post by GrootBrak on 2005-08-18
Got an HP850 digital camera. Gthumb Image Viewer does support it and as soon as I switch it on it detects it and show that it has "unloaded" pictures in memory. When I try and import th pics I get this error.
> 
Could not append 'DEVICEID.XML' to folder '/store_00010042/MISC' because this file already exists.

What's wrong and how do I fix it?

---

### Post by poofyhairguy on 2005-08-18
[QUOTE=GrootBrak]Got an HP850 digital camera. Gthumb Image Viewer does support it and as soon as I switch it on it detects it and show that it has "unloaded" pictures in memory. When I try and import th pics I get this error.


What's wrong and how do I fix it?[/QUOTE]

try this command:

> gksudo gthumb

then plug camera in.

---

### Post by GrootBrak on 2005-08-22
[QUOTE=poofyhairguy]try this command:



then plug camera in.[/QUOTE]
 Got the same error with the command.

---

### Post by KingBahamut on 2005-08-22
hrmmm....

apt-get install gphoto2 gtkam, 

Have you tried using Gphoto?


HP PhotoSmart 850 (PTP mode) is in the list of approved devices.

---

### Post by GrootBrak on 2005-08-23
[QUOTE=KingBahamut]hrmmm....

apt-get install gphoto2 gtkam, 

Have you tried using Gphoto?


HP PhotoSmart 850 (PTP mode) is in the list of approved devices.[/QUOTE]
 Will try it out and see what happens. I have another one that I tried, but I cannot recall what the name is/was.

---

### Post by GrootBrak on 2005-08-23
Thanx. gtkam works. gphoto is command line, so its not very friendly.
> /store_00010042/MISC
The file above sits on the camera, and is created by the camera as far as I can make out. It is possible to view the file with XP if the camera is in "USB disk" mode. I am unable to get it working as a "USB disk" in ubuntu, I tried that first.

Why would the DEVICEID be appended by Gthumb? Is there a fix for it, or should I try and report this to the developers of Gthumb?

---

### Post by Owdy on 2005-09-15
[https://bugzilla.ubuntu.com/show_bug.cgi?id=12132](https://bugzilla.ubuntu.com/show_bug.cgi?id=12132)

Can someone explain how to install that pach?

---

