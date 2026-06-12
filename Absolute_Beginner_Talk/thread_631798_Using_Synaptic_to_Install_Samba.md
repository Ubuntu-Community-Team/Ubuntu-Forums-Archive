---
title: "Using Synaptic to Install Samba"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by Recondaddy on 2007-12-04
OK, so I managed to get Samba installed, and I'm following the Ubuntu Bible to get it configured.  I'm modifying the smb.conf file, but now that I'm finished, how the heck do I save the changes?

That brings me to the title of this thread.  I also installed (or so I thought) the samba-doc.pdf document, which I hoped would point me in the right direction.  However, now that I've supposedly installed it, I can't find the darned thing to read it.  Where the heck did it get stored when I installed it??

I've done a search of the entire file system looking for "samba-doc", but I'm coming up with nothing.

Thanks!

---

### Post by davidgarcin on 2007-12-04
See this how-to on all things samba:  [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server)

After modifying the smb.conf, just hit the save button and exit.  If it says you don't have permissions to modify the file, you need to run the edit command as a superuser, i.e.

sudo gedit /etc/samba/smb.conf

-David

---

### Post by Threbus5 on 2007-12-05
Hi,

I seem to recall that Ubuntu 7.10 detected Samba requirements and offered the opportunity to self install Samba components as necessary.

Otherwise, in terminal enter sudo su, complete the password, and then gedit the smb.conf file at the location as described in the earlier post.

Good luck

---

