---
title: "What's this one mean?!"
date: 2005-05-22
forum: Absolute Beginner Talk
---

### Post by Error_Msg on 2005-05-22
(gedit:7426): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Just to cryptic for me

---

### Post by matej on 2005-05-22
gedit tries to connect to gnome session manager. You are running it from sudo or root terminal and you aren't running Gnome environment as user root, but as your normal working user. 
I think because of that gnome session manager reject connection. 

You can turn message off like that:
 ```

gedit --sm-disable

```

---

### Post by Error_Msg on 2005-05-22
Yes, that's exactly what I was doing. I opened the root terminal to uncomment a line in smb.conf. 
I just don't know any other way to open things as root.
The edits to smb.conf seem to have taken though.

E_M

---

### Post by matej on 2005-05-22
[QUOTE=Error_Msg]
The edits to smb.conf seem to have taken though.
[/QUOTE]
Yes, that message is only warning concerning session management, no function of gedit (or any other application) is affected.

---

