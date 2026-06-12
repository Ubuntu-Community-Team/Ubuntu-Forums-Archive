---
title: "how do i set up a home network"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by antisocialist on 2008-01-27
i have fresh install of ubuntu ultimate livedvd on 2 computers (just got rid of official ubuntu earlier) and windows xp on another. i want to network at least the 2 ubuntu ultimate ones, and hopefully the xp one as well. i am not going to use a firewall, i have 827 digit encryption on my wireless (nobody can crack that in under 1 mo as far as i am concerned)

---

### Post by swoll1980 on 2008-01-27
you mean share files. if thats it easy way right click a file you want to share go to share file on network it will install progam automaticly then all you have to do is set pass word
```
sudo smbpasswd -a your_user_name
``` set your new pass word and your good to go do this on both machines

---

### Post by jonandrews on 2008-01-27
To have full file transfer capability to a hybrid network including windows machines, there is a little more configuring to do. Have a look at my Ubuntu / Windows networking guide:

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)

---

### Post by antisocialist on 2008-01-27
> **bloor75 said:**
> you mean share files. if thats it easy way right click a file you want to share go to share file on network it will install progam automaticly 

i right click a file and it has no "share file on network" option

---

### Post by mortsahl on 2008-01-27
On my internal network I've got Ubuntu and windows boxes.  For file sharing between the Ubuntu boxes, I use NFS (Network File System).  To set it up, see ...

[http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html](http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html)
(that's a much better explanation than what's on the Ubuntu wiki)

To file share with the Windows boxes, I use Samba.  In Ubuntu 7.10 the set is trivial.  On Windows, allow sharing of the directories you want, know what your workgroup name is -- then in 7.10 go to Places->Network ... a Windows Network icon will appear, click on it and it'll show you the workgroup(s) available ... click on the workgroup of your choice and your shared directories should appear.

If you want graphical access to your comupters use RDP for the Windows boxes (much faster than VNC) and VNC for the Ubuntu boxes.

---

