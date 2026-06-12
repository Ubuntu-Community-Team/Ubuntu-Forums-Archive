---
title: "funny ftp problem"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by finer recliner on 2008-03-03
i have proftpd installed on my laptop, and i am behind a router. port forwarding is enabled. all has worked fine but all of a sudden, i cannot ftp to my laptop, from the same laptop.

i can ftp to my laptop from other computers with no problems. only from my computer back to the same computer has problems

gFTP times out when reading the directory:
```

gFTP 2.0.18, Copyright (C) 1998-2003 Brian Masney <masneyb@gftp.org>. If you have any questions, comments, or suggestions about this program, please feel free to email them to me. You can always find out the latest news about gFTP from my website at http://www.gftp.org/
gFTP comes with ABSOLUTELY NO WARRANTY; for details, see the COPYING file. This is free software, and you are welcome to redistribute it under certain conditions; for details, see the COPYING file
Looking up x.x.x.x
Trying x.x.x.x:21
Connected to x.x.x.x:21
220 ProFTPD 1.3.0 Server ready.
USER  username

331 Password required for username.
PASS xxxx
230-Welcome, archive user username@domain !
230-
230-The local time is: Mon Mar  3 23:19:53 2008
230-
230-This is an experimental FTP server.  If have any unusual problems,
230-please report them via e-mail to <root@laptop>.
230-
230 User username logged in.
SYST

215 UNIX Type: L8
TYPE I

200 Type set to I
PWD

257 "/" is current directory.
Loading directory listing / from server (LC_TIME=en_US.UTF-8)
PASV

227 Entering Passive Mode (192,168,1,100,173,101).
LIST -aL
// times out here

```

(my real ip address is replaced with "x.x.x.x" and my real user name is replace with "username" in the above excerpt) 

using the ftp command in the terminal lets me connect and log in, but i cant run simple commands like 'ls' without getting an error:
```

ftp> ls
500 Illegal PORT command
ftp: bind: Address already in use
ftp> 

```


oddly enough, if i use the ftp command from the terminal using my subnet host, ip or loopback address, everything works fine...
```

ftp 192.168.1.100
ftp laptop
ftp 127.0.0.1

```
^all work fine and i can browse my files/directories

i have tried restarting the computer, restarting proftpd, and restarting my router. nothing changed.

i have not edited my proftpd.conf recently. i have not installed any new ftp packages (although i did install sendmail, but quickly removed it and its related packages).


does any one have any ideas? has any one else seen this before?

---

### Post by ctyc on 2008-03-04
by "real" ip do you mean your wan ip?

are both ports 20 and 21 forwarded from the router?

---

### Post by finer recliner on 2008-03-04
yes, that is my WAN IP (sorry if i wasnt clear).

actually i was only forwarding port 21.

i just changed my router's settings to do port 20 as well, but no change.

---

### Post by freebeer on 2008-03-04
try logging using ACTIVE mode.  If you notice in your login session, you're being switched to PASSIVE mode (that's what the PASV message means).  Once in PASSIVE mode, the ports are different.

---

### Post by finer recliner on 2008-03-04
i unchecked passive mode in my settings in gFTP as you suggested, but now i now a different error:

```

gFTP 2.0.18, Copyright (C) 1998-2003 Brian Masney <masneyb@gftp.org>. If you have any questions, comments, or suggestions about this program, please feel free to email them to me. You can always find out the latest news about gFTP from my website at http://www.gftp.org/
gFTP comes with ABSOLUTELY NO WARRANTY; for details, see the COPYING file. This is free software, and you are welcome to redistribute it under certain conditions; for details, see the COPYING file
Looking up x.x.x.x
Trying x.x.x.x:21
Connected to x.x.x.x:21
220 ProFTPD 1.3.0 Server ready.
USER username

331 Password required for username.
PASS xxxx
230-Welcome, archive user username@domain !
230-
230-The local time is: Tue Mar  4 16:57:58 2008
230-
230-This is an experimental FTP server.  If have any unusual problems,
230-please report them via e-mail to <root@laptop>.
230-
230 User username logged in.
SYST

215 UNIX Type: L8
TYPE I

200 Type set to I
PWD

257 "/" is current directory.
Loading directory listing / from server (LC_TIME=en_US.UTF-8)
PORT 192,168,1,100,237,20

500 Illegal PORT command
Invalid response '5' received from server.
Disconnecting from site x.x.x.x

```

(again x.x.x.x = WAN IP, and username = my user name)

this is a similar result to when i ran ftp from the terminal (which i guess i was running in active mode.)


i tried running pftp (ftp in passive mode), and i got a timeout error similar to when i ran gFTP in passive mode from my first post.

so passive mode and active mode does not work from gFTP or the terminal.
passive mode times out and active mode just errors and disconnects me.

still need help. any more ideas?

---

### Post by ctyc on 2008-03-04
what happens when you use SFTP(port 22)
you will need to forward port 22 on the router of course.

---

### Post by freebeer on 2008-03-04
> **finer recliner said:**
> 
257 "/" is current directory.
Loading directory listing / from server (LC_TIME=en_US.UTF-8)
PORT 192,168,1,100,237,20


It looks like, for some reason, that your IP address is being passed as a parameter(?) and the ftp server is trying to interpret it as a port request?  What command are you issuing to connect?

---

### Post by finer recliner on 2008-03-04
> **ctyc said:**
> what happens when you use SFTP(port 22)
you will need to forward port 22 on the router of course.

SFTP/SSH2 works fine in both gFTP and the terminal ('sftp' command). please note that i have an ssh server set up on port 22 as well. but there has never been a problem with it.

---

### Post by finer recliner on 2008-03-04
> **freebeer said:**
> It looks like, for some reason, that your IP address is being passed as a parameter(?) and the ftp server is trying to interpret it as a port request?  What command are you issuing to connect?

in gFTP, there is no command to issue. its a GUI interface, that asks you for a host, port #, user name, password, and protocol.

i choose FTP from the list of protocols, and leave port number blank (which just means use the default). i fill in the rest with the correct information. then i press 'enter' to connect.

the stuff i was copy/pasting from is from the status/debug area of the program.



i dont think the line you mentioned is the problem:
```
 PORT 192,168,1,100,237,20 
```
if i put in my IP that the router assigns (192.168.1.100, which i mentioned earlier, works correctly) i get this as output in the status area:

```

...
CWD /
250 CWD command successful
Loading directory listing / from server (LC_TIME=en_US.UTF-8)
PORT 192,168,1,100,172,94
200 PORT command successful
LIST -aL
150 Opening ASCII mode data connection for file list
226 Transfer complete.

```
no timeouts, or disconnects. this is how it should work if i used my WAN IP. but it doesnt!

---

