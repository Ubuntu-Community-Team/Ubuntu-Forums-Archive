---
title: "Can't get a GUI when connecting through a VNC"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by habtish on 2006-11-21
I am trying to access my ubuntu box from an XP. The vnc server seems to be setup right and listening on the correct port.
Problem 1: When I make a successful connection to my ubuntu machine from an XP using tightvnc, all I see is the Ubuntu splash screen and nothing else. I have remote login enabled.

Could this be a problem with the vnc server I am running? apparently I am running Realvnc as a server [don't know how it happened]
< ps ax | grep -i vnc > shows ..
```

$ ps ax | grep -i vnc
18904 ?        S      0:00 Xrealvnc :3 -desktop X -auth /home/NAME/.Xauthority -rfbwait 120000 -rfbauth /home/NAME/.vnc/passwd -rfbport 5903 -fp /usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/usr/share/fonts/X11/misc,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType -co /etc/X11/rgb
24306 pts/0    S      0:00 Xrealvnc :1 -desktop X -auth /home/NAME/.Xauthority -rfbwait 120000 -rfbauth /home/NAME/.vnc/passwd -rfbport 5901 -fp /usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/usr/share/fonts/X11/misc,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType -co /etc/X11/rgb
24595 pts/0    R+     0:00 grep -i vnc


```Do the above line give some sort of meaning to the trained eyes??

Problem 2: The command I use to launch the server is```
vncserver
``` which opens a new port and a new display in increments of 1 every time the command is envoked.

forexample, display 0::5900 would be opened the first time. After a while I can not connect this this display so I try <vncserver> again, which opens display1:5901 and it keeps on going, tried ```
 vncserver [-clean] -kill :<number>
``` to no avail.

I know it's a long post, I am trying to state my problems as detailed as I possibly can so someone can take a look at and say, Hey I know how to fix this...
How do I get a GUI with controls and menus on VNC login other than the spalsh screen?
How do I clear/clean old ports/displays that are not being used?

---

### Post by finferflu on 2006-11-21
I've used remote desktop connection a couple of times. The best package I've tried is x11vnc, you could give a try.

sudo aptitude install x11vnc

hope it helps ;)

---

### Post by Jose Catre-Vandis on 2006-11-21
Look here
[http://www.ubuntuforums.org/showthread.php?t=191564](http://www.ubuntuforums.org/showthread.php?t=191564)
and here
[http://www.ubuntuforums.org/showthread.php?t=122402](http://www.ubuntuforums.org/showthread.php?t=122402)

This method works well for me from both ubuntu and windows machines. on windows I use realvnc to connect, you must remember to put a :1 after your IP addy or hostname

---

### Post by habtish on 2006-11-26
> **Jose Catre-Vandis said:**
> Look here
[http://www.ubuntuforums.org/showthread.php?t=191564](http://www.ubuntuforums.org/showthread.php?t=191564)
and here
[http://www.ubuntuforums.org/showthread.php?t=122402](http://www.ubuntuforums.org/showthread.php?t=122402)

This method works well for me from both ubuntu and windows machines. 

I read both threads and it seems to have gotten me in a worse state than I was before.

Prior to this I was running xvncserver which I had setup with a password that had worked in authenticating connections. I removed this package and installed vnc4server, set up xinetd as instructed and did the restart on the service.

>    3. Set the VNC passwd
     Code:
     [LEFT]sudo vncpasswd /root/.vncpasswd[/LEFT]
 
so I did sudo vncpasswd /root/.vncpasswd
Password:  put_my_password_here
Verify:  put_my_password_here

> service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd
        port = 5901
}so i did all this, and now when I try to connect from a remote machine, the vnc client complains about verification failure. I opened up another vncserver connection to see what was going on ...
```
vncserver :3 passwordfile = /root/.vncpasswd -fp /usr/share/x11/fonts/misc  
```when trying to connect from the remote client, the vncserver was reporting of a missing password file. I then tried connecting locally through vncviewer, it asks me for a passowrd ans when I supply to password I had set (when I did sudo vncpasswd /root/.vncpasswd), it rejects my password. I even tried my login password and that didn't seem tobe working.

So I have discarded a server I had that was accepting connection (eventhou my initial problem was getting a GUI), to setup another vncserver which is not accepting any connections because of password problems....Can anyone help?

---

### Post by Jose Catre-Vandis on 2006-11-30
You should be connecting with the following syntax:

xvncviewer localhost:1
(yourvncviewer yourremotepc:1)

---

