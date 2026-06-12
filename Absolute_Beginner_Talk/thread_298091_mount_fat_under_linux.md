---
title: "mount fat under linux"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by Jareth on 2006-11-12
Hi,
I had this working the first time I did it but I just wondered if there was something else I did the first time to get it working. I can't remember posting about it before. These are the instructions I'm following:

First off open a console >>>
 
cd /
 
sudo mkdir windows
 
sudo chmod 777 -R /windows
 
then >>>
 
sudo gedit /etc/fstab
 
then add this line at the end >>>
 
/dev/hda1  /windows   vfat   iocharset=utf8,umask=000   0       0
 
then press enter to the next line down
 
and save the file and reboot, you will then have your windows drive accessable and writeable
 
to get to it goto System > places > filesystem > windows
 
HAVE FUN


Im on ubuntu 6.06 by the way, partitioned with win98
Cheers!

---

### Post by Bartender on 2006-11-12
Here's [aysiu's]("http://www.psychocats.net/ubuntu/mountwindows") directions...

---

### Post by Jareth on 2006-11-12
Is there any chance that might mess things up with what I've done already?

---

### Post by Jareth on 2006-11-12
I twigged what I was doing wrong, the windows partition is hda3 not hda1 so I just changed it and it worked.
Fantastic!

---

