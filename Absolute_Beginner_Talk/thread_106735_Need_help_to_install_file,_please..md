---
title: "Need help to install file, please."
date: 2005-12-21
forum: Absolute Beginner Talk
---

### Post by L Campbell on 2005-12-21
I have this instruction:-

Install the two Ubuntu packages sl-modem-daemon and sl-modem-source.  You may have to get them through the online repository [http://packages.ubuntu.com/](http://packages.ubuntu.com/) 
if not on your install CD.  Move into the Linux folder they have been copied
into and Install with:
# sudo dpk -i *.deb

OK, so I've got the 2 files and they're on a floppy, since I had to download them with the Win side of my dual boot system.

Since they aren't, currently, in a Linux Folder, how would I modify the above command, to get them from my floppy to where they need to be?  (I do know how to 'mount' my floppy)

Thanks.

---

### Post by localzuk on 2005-12-21
You can run the command from /media/floppy (if the disk is mounted - which you can do by opening it in the normal way in ubuntu).

ie.

```

sudo dpkg -i /media/floppy/*.deb

```

should do what you want.

---

### Post by L Campbell on 2005-12-21
[QUOTE=localzuk]You can run the command from /media/floppy (if the disk is mounted - which you can do by opening it in the normal way in ubuntu).

ie.

```

sudo dpkg -i /media/floppy/*.deb

```

should do what you want.[/QUOTE]

Hi, thanks for your help, I appreciate it.
.....................
lcampbell@ubuntulewis:~$ sudo mount /media/floppy
Password:
Sorry, try again.
Password:
lcampbell@ubuntulewis:~$ sudo dpkg -i /media//floppy/*.deb

Selecting previously deselected package sl-modem-daemon.
(Reading database ... 56661 files and directories currently installed.)
Unpacking sl-modem-daemon (from .../sl-modem-daemon_2-1.9.10+2.9.9d-6ubuntu1_i386.deb) ...

Selecting previously deselected package sl-modem-source.
Unpacking sl-modem-source (from .../sl-modem-source_2.9.10+2.9.9d-6ubuntu1_i386.deb) ...

Setting up sl-modem-daemon (2.9.10+2.9.9d-6ubuntu1) ...
grep: /proc/asound/cards: No such file or directory
FATAL: Module slamr not found.

SmartLink modem driver not available for this Kernel. Please read README.Debian
or try to install the package sl-modem-modules-2.6.12-9-386. Exiting...
invoke-rc.d: initscript sl-modem-daemon, action "start" failed.

dpkg: dependency problems prevent configuration of sl-modem-source:
 sl-modem-source depends on module-assistant; however:
  
Package module-assistant is not installed.
 sl-modem-source depends on debhelper; however:
  
Package debhelper is not installed.
dpkg: error processing sl-modem-source (--install):
 dependency problems - leaving unconfigured

Errors were encountered while processing:
 sl-modem-source
lcampbell@ubuntulewis:~$
...................

Much more information than I had expected.

Kind regards.

---

### Post by Swab on 2005-12-21
Those 2 packages seem to depends on other packages... you'll need to download those too.... Ubuntu is a real pain without a network connection.

---

