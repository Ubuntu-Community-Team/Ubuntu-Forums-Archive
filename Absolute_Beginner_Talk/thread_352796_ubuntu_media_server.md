---
title: "ubuntu media server"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by Loki57701 on 2007-02-03
Currently I have a home media server running winXP pro, a simple system volume share along with some USB drives  on my local network of 4 computers. Ive already got ubuntu installed on 1 of my laptops (for the last 6 months or so). And I am interested in using ubuntu as my servers OS. My primary concerns are:

1. Remote desktop connection. Is there remote desktop connection software similar to the one MS uses, for linux. I really depend on the ability to log into my server from a different computer, because I dont have alot of extra monitors laying around. I suppose I could buy a KVM switch though.

2. I havent really looked into SAMBA that much but it seems like thats what I would need to do the same thing im doing now for sharing drives over my network. Its looks pretty complicated, and although im willing to try using it in the command line is there a better way to use it preferably with a gui of some sort (i know i know, all u noob haters out there can have something to rant on now)

3. Do I have to use the server version of Ubuntu or can i install the desktop version and download all the SAMBA stuff. 

-------------------------------------------------------------------------------------------------------

---

### Post by shareMenaPeace on 2007-02-03
hi, 
if you don't find an answer in the beginenrrs forum checkout

Networking & Wireless Forum
[http://ubuntuforums.org/forumdisplay.php?f=136](http://ubuntuforums.org/forumdisplay.php?f=136)

Cheers

---

### Post by chalex on 2007-02-03
In your case, there will not be any useful difference between the server version of Ubuntu and the regular version.

1) Look for VNC.  Do a search for vncserver or vino.
2) Samba is not too difficult to set up.  You can edit one file /etc/samba.conf.  I hear there's a web interface called SWAT but I haven't used it.
3) no difference.

Here's a random link from a google search for "ubuntu SWAT": [http://lists.samba.org/archive/samba/2006-January/116082.html](http://lists.samba.org/archive/samba/2006-January/116082.html)

---

