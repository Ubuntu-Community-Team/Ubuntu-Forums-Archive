---
title: "gksudo nautilus [Resolved]"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by gettinoriginal on 2007-03-15
when using gksudo nautilus, I get the following message, but I also get the root screen :confused: 

(nautilus:5130): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(nautilus:5130): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.

Also, can someone tell me how to edit the name in the applications list.  I installed Gyachi, but the title says GYachE Improved and it will not pick up the icon, so gives me the default Icon which will not add to panel.

sorry for being such a noob :lolflag:

---

### Post by Dr. Nick on 2007-03-15
1st error is no big deal, I think everyone get it.

2nd Im unsure about

To edit the menu items use alacarte, IF its not on the panel itself then press alt+f2 and type alacarte.

---

### Post by gettinoriginal on 2007-03-15
Thank you, that worked great

---

### Post by harpazo on 2007-03-27
Hi, 

I'm really new to Ubuntu.  I've just recently upgraded from Dapper to Edgy and everything seemed fine.  I noticed however that I am getting the same error message as the person stated in this post.

Consequently, when using gksudo nautilus, it won't let me access my sda1 partition (it doesn't even register it).  This was not a problem in Dapper.   

I checked and found that there is some kind of bug fix referenced here:

[https://bugs.launchpad.net/gnome-vfs/+bug/60959]("https://bugs.launchpad.net/gnome-vfs/+bug/60959")

but I have no idea how to use the patch.

Any help would be great.  Please let me know if you need any specific information that will help me resolve this.

---

