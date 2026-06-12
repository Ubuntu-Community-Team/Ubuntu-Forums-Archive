---
title: "WiFi trouble! WG311v2"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by no friends on 2006-06-04
I've been trying to install a WiFi card; Netgear WG311v2, using ndiswrapper

I've been at it all afternoon and no matter what driver i try and use, I always come up with the same error message!

[IMG]http://i5.photobucket.com/albums/y176/nofriends99/wg311error.jpg[/IMG]

The card shows up in device manager, but not in the "Windows Wireless Device".
It shows that their is a driver installed, but no hardware connected. 

Also, in /etc/ndiswrapper/wg311v2 - there are no files. Obviously the wg311v2 part goes after you uninstall it...

Oh yea, i'm on dapper drake aswell. 

Any help?!?

---

### Post by no friends on 2006-06-06
Is there really no one who can help....

btw, click the image to make it bigger...

---

### Post by jml on 2006-06-06
Getting wireless to work is one of the toughest things to accomplish in Linux.  There are two places you may be able to find help.  First check out this site.  Its Ubuntu's wireless troubleshooting guide.

[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

You should also check out the Wireless sub-forum that is nested under the Hardware forum.  You may find an answer there.  That sub-forum has a lot of activity on it.  hope this is of help.

Joe

---

### Post by no friends on 2006-06-06
Hey, cheers dude. I'll have a look through there etc :)

---

### Post by GQed76 on 2006-06-06
I have my WG311v2 installed via ndiswrapper so it can be done.  Make sure you have all the drivers in the folder, not just the wg311v2.ini file.  make sure the path that the are located in are accessable to you and not in a directory that needs special permissions.

I forget what versions Im using but that card ahs about 4 driver versions out there.  experiment with different ones

---

### Post by kafitz22 on 2006-06-06
I have the same card and know how frustrating it is. I found this 
fourm: [http://ubuntuforums.org/showthread.php?t=183031&highlight=acx111]("http://ubuntuforums.org/showthread.php?t=183031&highlight=acx111")

to work for me. It is a little confusing at times but you can PM if you need help.

---

