---
title: "kermit"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by jimmy85 on 2007-02-14
Hi guys, I have a problem with application kermit.
In Ubuntu, what is the equivalent command to kermit?
How to use this comand if I establish a connexion with a Linux PC with a Cisco Router?
Thank's

---

### Post by go2dell on 2007-02-14
I notice that both gkermit (free, in Universe) and ckermit (non-free, in Multiverse) are available if you're happy with kermit.  There's also gtkterm (also in Universe).

If you need any information about the Universe and Multiverse repositories, you can find it here:

[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html).

You can also try searching or browsing the packages at:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/).

---

### Post by jimmy85 on 2007-02-14
Thank you, I have installed gkermit, but i don't understandd how I have to use.
My intention is establish a connection with a Cisco Router and a PC. Anybody know how I have to do?
the router and Pc are connected via consola port of the router to serial port of the pc.

With gkermit :
jaume@labxarxes11:~$ gkermit
G-Kermit CU-1.00, Columbia University, 1999-12-25: POSIX.
Usage:  gkermit [ options ]
Options:
 -r      Receive files
 -s fn   Send files
 -g fn   Get files from server
 -a fn   As-name for single file
 -i      Image (binary) mode transfer
 -T      Text mode transfer
 -P      Path/filename conversion disabled
 -w      Write over existing files with same name
 -K      Keep incompletely received files
 -p x    Parity: x = o[dd],e[ven],m[ark],s[pace],n[one]
 -e n    Receive packet-length (40-9000)
 -b n    Timeout (sec, 0 = none)
 -x      Force Xon/Xoff (--x = Don't force Xon/Xoff)
 -S      Disable streaming
 -X      External protocol
 -q      Quiet (suppress messages)
 -d [fn] Debug to ./debug.log [or specified file]
 -h      Help (this message)

But not establish the connection.

---

### Post by go2dell on 2007-02-15
OK, after some searching I found [this thread]("http://ubuntuforums.org/showthread.php?t=250461") discussing connecting to the console port on a Cisco box.  It looks as though *minicom* is your friend.  HTH

FYI, I just searched using "cisco serial" as my search terms.  Might turn up something else that works better for you.

---

