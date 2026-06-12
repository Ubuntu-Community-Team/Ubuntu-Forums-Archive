---
title: "how to startup programs at login"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by gagatz on 2007-01-03
Hello, i want to mount an encrypted (truecrypt) harddisk automatically directly after the login. How is it possible? Note, that for this purpose it is necessary to enter a password, so its not sufficient (as far as i tried it) to put a link into ~/.config/autostart. There must be a way to do this.

Thanks

---

### Post by MiCovran on 2007-01-03
Maybe it's my lack of knowledge, but what's the point of encrypting a hard drive and putting a password on it if it gets mounted automatically? It's purpose is to not let anyone without the password access it.

---

### Post by gagatz on 2007-01-03
Of course. The point is, if it gets mounted automatically, there must at some point be a request for a passphrase. What I want, is that it tries to mount right after login, and then asks me for the correct passphrase. If I enter it, the volume gets mounted and otherwise not.

---

### Post by bartbes on 2007-01-03
You need to create a script/program that asks for the password, and than mounts the disk. I assume you already have one.
To start the program automatically go to System>Administration>Sessions
There's a tab with startup programs, just add it there and you're done.

P.S. The names may not be correct, because I have to translate them from Dutch.

---

### Post by gagatz on 2007-01-03
Ok thats what i did. I created a launcher on the desktop, and told him to execute it in a terminal (rightclick desktop create launcher). If i doubleclick this item a terminal appears and asks me for the password. If i enter the correct one, the volume gets mounted and the terminal disappears. If otherwise i enter the wrong password the terminal disappears after 3 tries without mounting the volume. Thats what i want. but if i put this application into systems | preferences | sessions | startup programs, logout and in again, nothing happens, so how can i start this script automatically?

---

### Post by bartbes on 2007-01-03
and what are the contents of the file (with the name of the script+.desktop) in .config/autostart?

---

### Post by gagatz on 2007-01-03
The name of the launcher is truecrypt and the content of the file ~/.config/autostart/truecrypt.desktop is

[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Exec=/home/niko/Desktop/truecrypt 
TryExec=
Name[en_GB]=truecrypt
Name=truecrypt

X-GNOME-Autostart-enabled=true


the content of the file ~/Desktop/truecrypt.config is

[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Exec=truecrypt --mount-options 'rw,sync,utf8,uid=1000,umask=0000' /dev/hdd3 /home/niko/Desktop/Kino/
TryExec=
Icon=/usr/share/pixmaps/gnome-error.png
X-GNOME-DocPath=
Terminal=true
Name[en_GB]=truecrypt
GenericName[en_GB]=
Comment[en_GB]=
Name=truecrypt
GenericName=
Comment=

---

### Post by MiCovran on 2007-01-03
> **gagatz said:**
> Ok thats what i did. I created a launcher on the desktop, and told him to execute it in a terminal (rightclick desktop create launcher). If i doubleclick this item a terminal appears and asks me for the password. If i enter the correct one, the volume gets mounted and the terminal disappears. If otherwise i enter the wrong password the terminal disappears after 3 tries without mounting the volume. Thats what i want. but if i put this application into systems | preferences | sessions | startup programs, logout and in again, nothing happens, so how can i start this script automatically?

If you put terminal programs to startup, they will execute. It's just that they wont show a new terminal. Try to put this to startup: ```
gnome-terminal -x your_command
```

I hope it works.

---

### Post by Atomic Dog on 2007-01-03
> **MiCovran said:**
> If you put terminal programs to startup, they will execute. It's just that they wont show a new terminal. Try to put this to startup: ```
gnome-terminal -x your_command
```

I hope it works.

Let us know if this worked.

---

### Post by gagatz on 2007-01-03
great! that did it. Is it also possible to put the system in a halt until the password is entered and if it is wrong the computer logs me out again?
Is it possible, that the terminal opens first of all, before metacity and desktop picture and all this stuff?

The reason why i want to know this is, that i would like to have as many parts of the homedirectory encrypted as possible. And for this purpose it is good to have the decryption as soon as possible.

---

### Post by geo_bio on 2007-01-03
I really don't see why you would even want this. First, if it is a truecrypt file (like I have), then you'd want to protect it from other people. Having it automatically mounted seems to defeat the purpose. If you want to do as you say, I would recommend not making it a truecrypt, and just have it as a regular partition.

If you have an external drive that you take around with you, and only use it on your own computer, then I may partially understand.

Anyways, I believe you can make it prompt you for the password on startup, but I don't think it's possible to have it startup truecrypt, enter a password, and then have it all mounted for you w/o you doing anything.

---

### Post by MiCovran on 2007-01-03
> great! that did it.
I'm glad my advice worked.

> Is it also possible to put the system in a halt until the password is entered and if it is wrong the computer logs me out again?
I believe a login window does that with the username and password. :-D
Surely it can be done, It's a free software world. Only that I don't know how. It's a programming problem, I believe.

> Is it possible, that the terminal opens first of all, before metacity and desktop picture and all this stuff?
I can't help you with this. Sorry.

---

### Post by gagatz on 2007-01-03
> **geo_bio said:**
> I really don't see why you would even want this. First, if it is a truecrypt file (like I have), then you'd want to protect it from other people. Having it automatically mounted seems to defeat the purpose. If you want to do as you say, I would recommend not making it a truecrypt, and just have it as a regular partition.

If you have an external drive that you take around with you, and only use it on your own computer, then I may partially understand.

Anyways, I believe you can make it prompt you for the password on startup, but I don't think it's possible to have it startup truecrypt, enter a password, and then have it all mounted for you w/o you doing anything.

Since it asks for a passphrase, nobody can read the data which is in the encrzpted volume. The only information that is published by this procedure is that everyone knows that an encrypted volume exists, which is useless without the passphrase.

Any suggestions, as how to do this in xterm before all the other stuff loads and or how to put the system in a halt until the password is entered and if it is wrong the computer logs me out again?

---

