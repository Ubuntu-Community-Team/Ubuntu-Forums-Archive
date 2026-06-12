---
title: "SSH/Remote Desktop on Xubuntu?"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by Daergeth on 2007-02-07
Does Xubuntu come with an application that will allow me to log into my desktop remotely from a different Xubuntu PC?

---

### Post by Quintin Riis on 2007-02-07
/usr/bin/ssh

---

### Post by grumpymole on 2007-02-07
Daergeth,

For commandline login, use ssh, as per Quintin above.

For desktop access you will need to use something like vnc4server (will give you a new desktop login, i.e. :1) or x11vnc (will give you the same desktop session, i.e. :0).  Depends what you want to do.  There plenty of [tutorials ]("http://grumpymole.blogspot.com/2006/12/xubuntu-remote-desktop-with-vnc4server.html")around.  Of course, you can secure the vnc connection by running it over ssh.

Regards

---

