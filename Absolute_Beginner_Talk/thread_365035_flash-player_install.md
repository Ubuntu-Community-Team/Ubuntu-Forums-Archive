---
title: "flash-player install"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by the_nomad on 2007-02-19
im trying to install flash player 9 cause my webbrowser asks for it (opera 9.1)...but i get the following 'error':

```

NOTE: Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.

```

so, where is this directory of the Mozilla? 

thanx in advance.

---

### Post by aysiu on 2007-02-19
Could be in /usr/lib/firefox/plugins

Try this in the terminal: ```
sudo updatedb
locate xpti.dat
```

---

### Post by the_nomad on 2007-02-19
> **aysiu said:**
> Try this in the terminal: ```
sudo updatedb
locate xpti.dat
```

ok this worked but is there any command in terminal that can allow me to delete that file? i tried through nautilus but says that i dont have permisssion to delete it

---

### Post by aysiu on 2007-02-19
Press Alt-F2 and type ```
gksudo nautilus
``` Then go to the directory and delete the file.

---

### Post by the_nomad on 2007-02-20
i still get that error :( 

```
----------- Install Action Summary -----------

Adobe Flash Player 9 will be installed in the following directory:

Mozilla installation directory  = /home/thbk4u/.mozilla

Proceed with the installation? (y/n/q): y

NOTE: Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.


Installation complete.


Perform another installation? (y/n):

```
:confused: :( ](*,) ](*,)

---

### Post by aysiu on 2007-02-20
Try this?
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

