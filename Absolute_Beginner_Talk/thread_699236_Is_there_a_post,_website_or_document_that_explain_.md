---
title: "Is there a post, website or document that explain all the security groups"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by aochoa on 2008-02-17
Is there a post, website or document that explain all the security groups

I have been looking around for some explanation on the Ubuntu **[COLOR="Red"]security groups[/COLOR]** (/etc/group) but I haven’t found anything yet. Does any one know of a good resource of information on this topic?

---

### Post by ashmew2 on 2008-02-17
[http://www.cyberciti.biz/faq/understanding-etcgroup-file/](http://www.cyberciti.biz/faq/understanding-etcgroup-file/)

I think that gives you the superficial knowledge u need. If you want to know about the /etc/group for a specific reason , do tell the reason. That way I would be able to point you in the exact direction.

---

### Post by aochoa on 2008-02-17
Dear ashmew2, thank you very much. The post you recommended is a good reference. I have read it and I have also read the related articles, but I didn't really find an explanation on the different groups.

This is what happened; I installed Virtualbox on my Ubuntu machine and it messed up with my user's rights. There were a few things that stooped working like sudo, audio, firewall, etc., etc. and with some help from people in these forums I have managed to put the user's rights back to a stable state. You can read more about the problem I had in this post:

[http://ubuntuforums.org/showthread.php?t=697783]("http://ubuntuforums.org/showthread.php?t=697783")

What I'm looking for is more in detail explanation on the predefined groups. I would appreciate if you can guide me on this subject.

---

### Post by ashmew2 on 2008-02-18
How about this then ? [http://www.debian-administration.org/articles/109](http://www.debian-administration.org/articles/109)

Ill keep digging the insides of the Internet and try to keep this thread updated :lolflag:

---

### Post by p_quarles on 2008-02-18
> **aochoa said:**
> Dear ashmew2, thank you very much. The post you recommended is a good reference. I have read it and I have also read the related articles, but I didn't really find an explanation on the different groups.

This is what happened; I installed Virtualbox on my Ubuntu machine and it messed up with my user's rights. There were a few things that stooped working like sudo, audio, firewall, etc., etc. and with some help from people in these forums I have managed to put the user's rights back to a stable state. You can read more about the problem I had in this post:

[http://ubuntuforums.org/showthread.php?t=697783]("http://ubuntuforums.org/showthread.php?t=697783")

What I'm looking for is more in detail explanation on the predefined groups. I would appreciate if you can guide me on this subject.
One thing to keep in mind is that manually editing the /etc/groups file increases the chances of breaking things via a syntax error. When I want to change a user's groups, I use the command to do it for me:
```
sudo adduser *someuser somegroup*
```
As for what the groups do: they each give the user access to certain functions, usually those that involve using kernel modules as opposed to executing applications. 

The output of "groups" for my user is thus:
```
*username* dialout cdrom floppy audio video plugdev lpadmin vboxusers fuse admin
```
All of these groups do more or less what you'd expect: cdrom, for instance, allows me to mount CDs without being root. "plugdev" is, I believe, for transient devices, lpadmin is for printing, vboxusers is for running the Virtualbox kernel module, and fuse allows for mounting certain types of filesystems. "admin" is the one that grants sudo privileges to members of that group, in Ubuntu.

---

### Post by aochoa on 2008-02-19
Dear p_quarles,

the problem was that my system didn't even allow "sudo" at all. The only solution was the one suggested by macogw on [http://ubuntuforums.org/showthread.php?t=697783](http://ubuntuforums.org/showthread.php?t=697783)

I was very careful when editing /etc/group using nano. What I did was to install Ubuntu inside a virtual machine using Virutalbox in my windows pc. I set up the same username and password as my "damage" Ubuntu. With this &#8220;clean&#8221; installation I revised the file /etc/group, and then basically I copied this configuration on my damage machine, and Voila!! After rebooting it worked perfectly.

I appreciate the information in your response because now I know how to play with users and groups using "sudo". Thanks !

---

