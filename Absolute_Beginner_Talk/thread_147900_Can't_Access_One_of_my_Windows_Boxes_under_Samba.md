---
title: "Can't Access One of my Windows Boxes under Samba :/"
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by darf681 on 2006-03-21
I just reinstalled Breezy on my main desktop, and now, after installing samba, and now I am having these two problems:

1)  I can access all of my windows shares, except shares on one windows computer.

2)  Clicking on Network Servers under Places shows all machines in the network, as well as the icon for WORKGROUP, which the servers are in also...  That wasn't there before I did the reinstall..

For the first one, I think I may have a different configuration on that one windows box, or may have inadvertently setup samba with wierd connection properties for that one box.  (I remember it asking for passwords and such for a couple of boxes the first time I tried to access them, and it hasn't happened again after I tinkered with samba...  is there a place to access specific settings per server in samba, or is there a way to start over with samba without reinstalling Breezy?)

thanks!

---

### Post by Iowan on 2006-03-21
I'm a bit confused as to which way the sharing is being done... you can access all shares except those ON one Windows box or FROM one Windows box (ie. which is the client, and which is the server?)  For a Samba server, there are ways to make shares behave differently depending on which user/host is accessing them.  I 'm SURE there are ways to start over with Samba without re-installing Breezy.  I suspect that careful editing of the /etc/Samba/smb.conf file will fix whatever is wrong with Samba... the Windows box will be a different story (but shouldn't require a re-install, either) ;)

---

### Post by darf681 on 2006-03-21
My ubuntu box is the client, and the windows boxes are the servers, one of which I can't access the shares on.

thanks!

---

