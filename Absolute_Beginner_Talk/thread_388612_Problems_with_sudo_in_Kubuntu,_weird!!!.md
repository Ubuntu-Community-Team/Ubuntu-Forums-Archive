---
title: "Problems with sudo in Kubuntu, weird!!!"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by Cippa Lippa on 2007-03-19
Hi guys


after installing kde-desktop on ubuntu I decided to switch for now to kubuntu. I did a fresh install and I got some serious problems with Kate running as sudo. The bug was saying something like

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

That was fixed by commenting out some wacom related lines in xorg.config and typing
xhost local: 
at the terminal

Now the softwares work as sudo but when I launch them with sudo from the terminal I get this disturbing message 

Link points to "/tmp/ksocket-root"
Link points to "/tmp/kde-root"
kbuildsycoca running...
kio (KSycoca): ERROR: No database available!
Invalid entry (missing '=') at /tmp/kde-root/kconf_updateGGreGa.tmp:1
KWrited - Listening on Device /dev/pts/2
Launched ok, pid = 4995
QObject::disconnect: Unexpected null parameter
QFile::open: No file name specified

I have the feeling this message shouldn't be there to start with. Kate infact takes quite a while to start with sudo.
If I use kdesu instead of sudo I don't get any error messages. But still I would prefer sudo to work properly since this is a fresh install.

Any ideas guys. To whom will answer I can unveil the secret of proper pasta cooking (traditional italian style) ;)

Cippa

---

### Post by dbbolton on 2007-03-19
i think in kde, you are supposed to use root terminal rather than 'sudo' in a regualr shell.

---

### Post by Cippa Lippa on 2007-03-20
I just removed ksycoca and ksycocastamp from /var/tmp/kdecache-root/ as mentioned in this link [http://www.void.gr/kargig/blog/2005/02/25/kde-k3b-ksycoca-error-solving/](http://www.void.gr/kargig/blog/2005/02/25/kde-k3b-ksycoca-error-solving/)
I still get the error message when kate closes.

> **dbbolton said:**
> i think in kde, you are supposed to use root terminal rather than 'sudo' in a regualr shell.

As you say, I tried to run kate as root and it is even worse!

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified
xhost:  unable to open display ":0.0"

And even if I type xhost local: it gives me the same message!!!!
Please help guys - this sounds more and more scary... I spent the whole day getting my system up to speed I don't really want to reinstall!

Cheers

Cippa

---

### Post by Bachstelze on 2007-03-20
You shouldn't use sudo to run GUI apps as root. Use kdesu in KDE, gksudo in Gnome.

---

### Post by feed_sparky on 2007-03-20
I have always had the same problems, this is what is looks like when I use kdesu ```

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Link points to "/tmp/ksocket-root"
Link points to "/tmp/kde-root"
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
QObject::disconnect: Unexpected null parameter
njerry@Mobile:~$     
```

and this when I use sudo
```
njerry@Mobile:~$ sudo kate /etc/X11/xorg.conf
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
                      
```

It has always still worked when editing files even though you get error messages.

---

### Post by Bachstelze on 2007-03-20
Yep, those messages are harmless. If you want to get rid of them, delete the wacom sections in your xorg.conf.

---

