---
title: "ssh question: can I open docs from a  remote machine?"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by ginestre on 2007-06-10
OK, so I've got two PCs talking to each other, both running feisty and connected via an ethernet cable, using ssh. I can browse either from the other.  I can copy and paste etc. I'm asked for user name and password on connection, and it's all hunky dory.

But the next step is not just copying and pasting: I want to work on the remote files from here, without having to make  a local copy. Is this possible?

At the moment, if I click on a document on the remote PC to open it- in this case, in open office write- I get a new request for a password, with the  user name field already correctly filled in with my userID, and after giving the password I get a second window asking for a password, but without a user name field. There's the tex there on screen, saying 'user name' but no field following it. If I give my password, or the root password for either machine,or nothing, the same thing happens- an open office error box with the message 'A general internet error occurred'

what does it all mean?

TIA

---

### Post by Rui Pais on 2007-06-10
hi,
i usually log, if i want to run apps with GUI on remote machine, using -X flag with ssh, like:

```
ssh -X *user*@*remote.machine*
```

that allow to open a document document on remote machine as long as (if its a OO/MSOffice document) OO is installed on remote.

hth

---

### Post by tagra123 on 2007-06-10
ssh -X

also allows gedit, nautilus, and other gui programs to work too.

---

### Post by ginestre on 2007-06-10
Thanks;I tried and found I don't have display permissions for this

richard@kids:~$ /usr/lib/openoffice/program/soffice.bin X11 error: Can't open display: 
   Set DISPLAY environment variable, use -display option
   or check permissions of your X-Server
   (See "man X" resp. "man xhost" for details)



but maybe this is more complicated than what I need:  I don't want to run apps on the remote macchien (though that would be nice! I'll try to learn it next) I just want to be able to open edit and save a remote file using an app on the local machine  Surely this is possible?

---

### Post by Delkster on 2007-06-10
> **ginestre said:**
> I just want to be able to open edit and save a remote file using an app on the local machine  Surely this is possible?

Yes and no. For Gnome applications running in Gnome it generally works because they use the GnomeVFS library for accessing files, and GnomeVFS also handles files on remote machines over SSH, FTP and such. Thus, for applications using GnomeVFS, opening a file over SSH is pretty much similar to opening a file on the local machine. You can for example open a text file in Gedit over SSH and save it normally. It works.

KDE has a similar thing of its own, and things generally work for KDE applications as well (you'll have to supply the password separately to KDE and Gnome applications, though, because the password handling of KDE is separate from that of Gnome).

However, applications that haven't been written for Gnome probably don't use GnomeVFS (and similarly for the KDE equivalent) and don't benefit from its filesystem abstraction. I don't know if OpenOffice.org uses it (no time to check right now either) but I doubt it does.

---

### Post by tagra123 on 2007-06-10
On the remote machine try this

sudo xhosts + 

now try connecting using 

ssh -X

---

### Post by tagra123 on 2007-06-10
An easier way to edit remote (LAN) files would be to share a folder. I personally prefer NFS but also use samba  (windows) shares too.

---

