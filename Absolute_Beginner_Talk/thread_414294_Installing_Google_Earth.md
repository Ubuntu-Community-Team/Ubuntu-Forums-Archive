---
title: "Installing Google Earth"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by Insp Gadget on 2007-04-19
I just d/n Google Earth. The file extension ends in .bin but when I double click it, it opens in a text editor. How can I install this?

---

### Post by eyelessfade on 2007-04-19
make it executable. chmod +x fileNAME.bin
and run it with ./fileName.bin

---

### Post by blockcipher on 2007-04-19
Official help article:

[http://earth.google.com/support/bin/answer.py?answer=44713&query=linux&topic=&type=](http://earth.google.com/support/bin/answer.py?answer=44713&query=linux&topic=&type=)

---

### Post by Insp Gadget on 2007-04-19
Next stupid question. how do I change my directory in the Terminal? My Google Earth resides on the desktop, so I assume I have to switch to that dir first....

---

### Post by jhenager on 2007-04-22
jeff@jeff-desktop:~$ cd Desktop/
jeff@jeff-desktop:~/Desktop$ ls
GoogleEarthLinux.bin  Terminal.desktop
jeff@jeff-desktop:~/Desktop$ chmod +x GoogleEarthLinux.bin 
jeff@jeff-desktop:~/Desktop$ ./GoogleEarthLinux.bin 
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.0.2735.0..................................................................
Installing mimetypes...
Running /usr/bin/update-mime-database /home/jeff/.local/share/mime
Installing desktop menu entries...
/usr/lib/firefox/firefox-bin: /home/jeff/google-earth/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
jeff@jeff-desktop:~/Desktop$

---

