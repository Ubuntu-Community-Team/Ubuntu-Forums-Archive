---
title: "2 questions on drive mounting. USB and Network"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by ac251404 on 2007-02-04
Okay I am having 2 issues which I have been dealing with by dual booting to windows but I am now determined to fix in ubuntu.

The first is my mp3 player. Its a cowon iAudio and when I plug it in ubuntu recognizes it immediately and puts an icon on the desktop but will not let me write to the drive. I believe it is formatted in FAT32 so I thought I should be fine to write to it but I am not having any luck. 

Second, I have a fileserver setup also running ubuntu and sharing a 400gb drive through samba. Both my laptop and PC can see the drive fine and read/write to it but I cannot seem to stream video files off of it (to my other ubuntu machine) like you can over windows shares. If I boot into windows however I can view the videos fine.  I'm not sure at all the reason for this, but if I copy the movie to my ubuntu desktop it works so I know I have the proper codecs/player installed. I assume this means I need to mount the drive in some way but all the guides I found on mounting network drives assumed the samba share used username/login and I have mine setup for no authentication, so I don't know how that effects things.

Thanks for the help

---

### Post by amd-64 on 2007-02-11
I am guessing the problem with the mp3 player is that you need root permissions to write to the drive. try to copy a file as root. To confirm, use the following in a terminal with a proper file name and the actual mp3 drive name in your installation.

sudo cp filename /media/drivename/

---

### Post by nickburns on 2007-02-11
For the lazy, like me, to transfer files as root:

sudo nautilus


will open the default fie / directory browser so you can drag / drop files to that mp3 player.

---

