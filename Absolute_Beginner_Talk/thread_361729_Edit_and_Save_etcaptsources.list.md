---
title: "Edit and Save /etc/apt/sources.list"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by hppyfngy on 2007-02-14
Okay, I'm really new to this so how do I edit the sources.list file and save it?  I can add lines in  Terminal from within desktop, but how do I save it?  Or do I have to edit it elsewhere?  



:confused:

---

### Post by Spike-X on 2007-02-14
from Terminal:

gksudo gedit /etc/apt/sources.list

This will open it up in Text Editor. Make the changes you want, then hit save.

---

### Post by x1a4 on 2007-02-14
Hi,

Open the file with super user priviledges to be able to write to it.  

eg.: from the gui: 

*gksudo <your_fave_text_editor> <file_to_edit>*

on the command line: 

*sudo <your_fave_text_editor> <file_to_edit>*

---

### Post by tronica on 2007-02-14
make sure after you edit your sources.list, that you run 

> sudo apt-get update

---

### Post by hppyfngy on 2007-02-15
Thanks All!

---

### Post by punx45 on 2007-02-15
**[COLOR="Red"]back it up first![/COLOR]**

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```

and it doesnt have to be backup it could be sources.list.thedate or whatever works for you!

just try and decide on something and stick with it so your backups don't look like my xorg.conf backups haha

```
geoff@toaster:~$ ls /etc/X11/xorg.conf*
/etc/X11/xorg.conf                 /etc/X11/xorg.conf.backup
/etc/X11/xorg.conf~                /etc/X11/xorg.conf.backup2
/etc/X11/xorg.conf.20061223183257  /etc/X11/xorg.conf_backup_200701022108
/etc/X11/xorg.conf.20070102003015  /etc/X11/xorg.conf.numbers
/etc/X11/xorg.conf.20070102205624  /etc/X11/xorg.conf.tv~

```

---

### Post by r4ik on 2007-02-15
For Edgy,

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)

and Dapper,

[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories)

You could also create you're own,

[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

Take care and Good luck !

---

