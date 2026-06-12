---
title: "really basic terminal question"
date: 2006-03-17
forum: Absolute Beginner Talk
---

### Post by Insinion on 2006-03-17
I installed ubuntu 5.10 yesterday on my old inspiron 3500. The grapic chip only supports 16bit and ubuntu is set to 24bits. So i searched the forums and found that i had to edit /etc/X11/xorg.conf.

When i manually opened the file it was read only so i couldn't edit it. Then with my noob skills i opened a terminal logged in as a su and typed 'gedit /etc/X11/xorg.conf'. And it screwed my ubuntu installation cause it removed everything in the file :D :D.

My question is how can i edit this file without screwing everything up.

---

### Post by dermotti on 2006-03-17
sudo gedit /etc/X11/xorg.conf

If you screw it up, you can always type 

sudo dpkg-reconfigure xserver-xorg

and it will make you a new xorg.conf

---

