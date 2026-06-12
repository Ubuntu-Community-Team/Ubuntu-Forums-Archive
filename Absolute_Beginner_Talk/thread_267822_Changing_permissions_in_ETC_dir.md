---
title: "Changing permissions in ETC dir"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by lavikl on 2006-09-29
I've installed 3D desktop, and i havn't manage to make it work.
when i looked inro the 3ddesktop.conf file i noticed it's configured to KDE and i'm using GNOME. I changed the configuration to gnome but it won't let me save the file, saying i don't have permission to edit files in ETC directory.
I'm using the admin account (the only account in my linux) and i'm using  Ubuntu 6.06 LTS - the Dapper Drake.

how can change the permission ? i already tried to right click the file and change it on the permission tab but wasn't succesfull.

Thanks guys...

---

### Post by bluefrog on 2006-09-29
in a console:

gksudo gedit /etc/3ddesktop.conf

you will edit the file with root rights.

remember to close gedit when you're done.

James

---

### Post by Jussi Kukkonen on 2006-09-29
bluefrog's got it right, but I'll paste this link just so you aren't totally in the dark about what you actually did:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

To sum up: there's no need to change the permissions (that would be a bad solution securitywise), using sudo to edit the file is better.

---

### Post by lavikl on 2006-09-29
Thanks everyone !
got it :-D 
one more question, how do i make 3D Desktop work after it's been installed ?

---

### Post by Jussi Kukkonen on 2006-09-29
One of these will no doubt help you with that:
```
less /usr/share/doc/3ddesktop/README.gz
man 3ddesktop

```

---

### Post by Kilz on 2006-09-29
> **lavikl said:**
> Thanks everyone !
got it :-D 
one more question, how do i make 3D Desktop work after it's been installed ?

open a terminal and type ```
3ddesk
``` You can also add it to the pannel. Right click on an empty spot, click add to panel, click create a custom launcher. Name it 3ddesk, put 3ddesk in the command box, click on the no icon to select one, click ok. Then to launch it , you just click the icon.

---

### Post by vanth13 on 2006-10-02
what about if I want to copy a file in the etc directory? what is the command for copy?

---

### Post by blackened on 2006-10-02
```
man cp
```

Preceed the cp command with *sudo* if you don't have user level write permissions (anywhere other than your home directory).

---

