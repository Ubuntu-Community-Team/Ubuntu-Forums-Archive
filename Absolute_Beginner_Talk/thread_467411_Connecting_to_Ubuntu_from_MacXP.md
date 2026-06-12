---
title: "Connecting to Ubuntu from Mac/XP"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by BigMike007 on 2007-06-07
Hello,

How good is Ubuntu?!?!  I'm brand new to Linux and am thoroughly impressed with Ubuntu.  Just trying to find my way around etc and making OK progress... I'm just stuck on trying to connect to my machine running Ubuntu from either my Mac or XP machines... I can see the Ubuntu machine over the network within the workgroup fine - its just when I try and connect and authenticate, it rejects the username and password - but I know I'm typing it correctly?!?  I can see and connect to the Mac and XP machines from the Ubuntu machine OK....  Any help and advice on this would be much appreciated!

Cheers.

Big Mike


v. 7.04

---

### Post by Hendrixski on 2007-06-07
Hey.

You've come to the right place!  These forums are where all of us came when we had problems, and now we come here to help others with their problems... because we (just like you) are impressed with Ubuntu... and continue to be impressed with it every day as we see it get better and better in front of our eyes.

You're trying to see shared folders across your network?  you're looking for a program called Samba (which most likely automatically installed the first time you clicked on Network places"... if not... you can probably click on applications-->Add/Remove and select samba or anything else that has a description that says "networking".

Samba is the same program Mac uses I believe.  So it should work.
the only thing is... sometimes it's really slow when it comes to detecting other computers on the network. It's fast to transfer though.

---

### Post by Hendrixski on 2007-06-07
By the way.... WELCOME to the community.  I don't just mean the forums, I mean the wider community of people who use Ubuntu.  You may find it worthwhile to meet other people in your area who use Ubuntu, we have what's called the Ubuntu LoCo Teams for that.  Also, if you have questions you can ask them here (after you ask google first obviously) or you can ask them on IRC.  

To check out IRC go to applications-->Add/Remove and select XChat... then just connect and start chatting to real people who love Ubuntu, and are eager to help new people discover Ubuntu.

---

### Post by Daremo on 2007-06-07
> **BigMike007 said:**
> Hello,

How good is Ubuntu?!?!  I'm brand new to Linux and am thoroughly impressed with Ubuntu.  Just trying to find my way around etc and making OK progress... I'm just stuck on trying to connect to my machine running Ubuntu from either my Mac or XP machines... I can see the Ubuntu machine over the network within the workgroup fine - its just when I try and connect and authenticate, it rejects the username and password - but I know I'm typing it correctly?!?  I can see and connect to the Mac and XP machines from the Ubuntu machine OK....  Any help and advice on this would be much appreciated!

Cheers.

Big Mike


v. 7.04

In order to authenticate you will need to add a "Samba User" to the samba config. I generaly make it my same username and password. The samba user is distinctly different from a user account on the Ubuntu system. You can also set samba to "sync" user accounts as added to the system. Then you can set permissions as desired and should be able to logon to the samba share. Samba can also share printers if you're interested in that.

I like to use Webmin (I'm gonna get beat up for this as many consider webmin unsecure) for samba configuration as it is quite easy to do. Get it at  [http://webmin.com](http://webmin.com) . Hae fun and welcome to Ubuntu!

---

