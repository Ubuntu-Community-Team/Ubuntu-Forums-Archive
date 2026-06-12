---
title: "Graphic settings on server"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by D_2 on 2007-08-31
I have install LAMP and also the desktop. For some time I have been able to just SSH into the box and do what I need to do untill I installed a program called Openfire and it says to go to localhost:9090 to get to the admin page, so that meens I need to be on that system to do what I need. (links doesn't support jave so it wornt work in helping set this up from what I have read) so I want and reconnected a monitor to the system and some how the graphic settings are at a point where when the desktop loads I loose the screen because desktop settings are beyond what my monior can handle. Is there a way I can SSH into the box and edit some conf file to some basic setting for the desktop so I can start using that monitor when needed, and or does anyone know how I can just use my browser on like this box act like my server and get to its localhost:9090 so I can start configuring Openfire from a system that can handle java.
 
Thanks to anyone that has some ideas about this.

---

### Post by D_2 on 2007-09-01
Anyone know if there is a conf file that I can go look at to see what the desktop video settings are? I know with Windows I can go look at the system.ini file and if have to I can change the resolution from there, or back in the Win9x days I can. I haven't had to worry about thtat since then and going into safe mode can solve most video problems but I am not sure hwo to do do that with Ubuntu server with the desktop loaded.
When the system is starting up, I do see it starting to load Ubuntu and then on my screen it says unsupported mode so I am not sure what changed for this not to show. I normaly don't view things through that monitor I just SSH into it and do my thing. But now I need to do some things localy there but can't because the desktop starts to load and no video.

---

### Post by benfindlay on 2007-09-01
I would suggest launching a terminal and typing ```
sudo dpkg-reconfigure xserver-xorg
``` and reconfiguring your display settings to something your monitor can handle

Hope this helps!

---

### Post by D_2 on 2007-09-01
Will that work for the desktop area of the server. I can SSH into the system all I want, but when I go to use a monitor it wont work. When I did apt-get install desktop things ran fine, but for several weeks I have been using SSH so I didn't think much about it, but now I am needing to use a desktop to configure a program but can't see what is on the screen. Not sure how something got changed to where I can't see anything on the screen.

---

