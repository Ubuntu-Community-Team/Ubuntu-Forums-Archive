---
title: "ssh X11 forwarding"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by dfreer on 2007-06-23
Evidently I'm an idiot... cuz it seems like this should be really easy to do.

I have my sister's computer setup as an SSH server, running Ubuntu Feisty. I'd like to be able to (over the secure ssh connection) do some sort of remote desktop/applications from another Ubuntu Feisty client (all the guides I've found are for windows clients). I don't need to "share" a desktop with my sister, I have my own login on the system and would just like to be able to run a GUI app from her server and have it display on my client machine. So the two of us can work with seperate apps/gnome sessions at the same time, if that makes any sense.

Anyways, I tried this command:
```
ssh -X 10.0.0.7
```
and I get this error:
```
/usr/bin/X11/xauth:  error in locking authority file /home/dfreer/.Xauthority
```
it lets me log in though, so then tried some x apps:
```
$ xclock
X11 connection rejected because of wrong authentication.
X connection to localhost:10.0 broken (explicit kill or server shutdown).

$ xterm
X11 connection rejected because of wrong authentication.
X connection to localhost:10.0 broken (explicit kill or server shutdown).
```

Can anyone help?

EDIT: willing to use any other software like XDCMP, vnc, freenx or whatever. It just needs to be secure, and I need to know the port numbers the software uses so I can poke holes in my firewall.
```
ls -l ~/.Xauthority
-rw-r--r-- 1 root root 177 2007-06-23 12:56 .Xauthority
```

---

### Post by thelinuxguy on 2007-06-23
Try this after the ssh login
```

rm -r ~/.Xauthority
touch ~/.Xauthority

```

Then launch your applications.

---

### Post by dfreer on 2007-06-23
Thanks! single apps like xterm and xclock work now!
One last question, how would I launch the desktop itself?

EDIT: also, is it possible to pipe sound output so that it plays on my client machine instead of the server?

---

### Post by thelinuxguy on 2007-06-23
> **dfreer said:**
> One last question, how would I launch the desktop itself?


Set up VNC server on the remote machine to accept local connections (for security, local connections only - I don't know how to do this on Ubuntu. Used UltraVNC on Windows which had these options). Then use vncviewer localhost from the ssh session.

---

### Post by dfreer on 2007-06-23
sweet I'll try that out. thanks again!

---

### Post by lhomme on 2007-07-13
or to lunch the desktop once you have sshed in with the -X option would be to run "gnome-session"

you also may want to through on -C for compression, things get bandwidth hungry

---

### Post by dfreer on 2007-07-13
Thanks for the tip! I haven't tried loading the desktop proper, instead I used X11 forwarding to run a vnclient from the server over SSH. Problem was, it was too slow even with the -C option. Maybe loading the desktop itself will run faster...

---

### Post by scxtt on 2007-07-13
what OS are the other boxes you connect to running?  is use Xephyr (via XDMCP) to connect to my other boxes (in the LAN) ...

Xephyr -screen 1280x1024 -query <server-name> :1

---

### Post by dfreer on 2007-07-13
Ubuntu -> Ubuntu, although it is remote (about 200 miles away), it probably just doesn't have a fast enough connection lol.

---

