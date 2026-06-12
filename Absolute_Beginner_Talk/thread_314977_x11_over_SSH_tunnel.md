---
title: "x11 over SSH tunnel"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by matt.runion on 2006-12-08
Hello,

I am able to establish an SSH -X session from one Ubuntu host to another Ubuntu host.  I am even able to tunnel xclock.  However, I cannot display the entire remote desktop thru the tunnel.  I assumed (and incorrectly so) that I could issue "startx", but that doesn't work.  The error I get is:

"Fatal server error: Server is already active for display 0. If this server is no longer running, remove /tmp/.X0-lock and start again. Couldn't get a file descriptor referring to the console

I don't know that startx is the correct command or if there's additional systax necessary or further configuration.

Thanks for the help in advance.

Matt

---

### Post by stalker145 on 2006-12-08
The only way that I am aware of, in my limited experience, is to >  ssh -X xxx.xxx.xxx.xxx application name

ex. ssh -X 192.168.1.1 firefox

I use vnc viewer to view the desktop of my server. I know it's not the most efficient, but it's what I know at this point ;) 

>  vncviewer 192.168.1.1

---

### Post by kebes on 2006-12-08
I don't know if you can run an entire desktop session through X-forwarding. I think that's mainly intended for forwarding just one application at a time.

Another option is to use VNC, which essentially transmits screencaptures in one direction and mouse events in the other direction. The end result is that you can have a window with a full desktop that is running on a different machine. Very neat. You can make this window fullscreen if you like.

There are many VNC implementations. I've used TightVNC.

So on the "remote" machine, you install:
$ sudo aptitude install tightvncserver

And on the "local" end, you install:
$ sudo aptitude install xvncviewer

The cool part is that the "local" end can be any kind of machine, even a Windows or Mac OS box. You just download the vnc-viewer (from [http://www.tightvnc.com/](http://www.tightvnc.com/) for instance).

VNC will give you remote access to a full desktop environment. It can be slow at times, however. I'm not sure if this does what you want it to.

---

### Post by brt on 2006-12-08
you may also want to have a look at "freenx":

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

### Post by richardward101 on 2006-12-08
you can indeed run an entire session, the problem is that its the only session you can really run on a single X display (useful if for example you don't mind starting another X with startx or if you are doing it from a windows cygwin X server) as it won't be windowed or anything. Type gnome-session once ssh -X is connected.

xrdp is also quite good, as you'll be able to log in from windows machines without having to download vnc to them.

---

### Post by yioan on 2006-12-09
hello,
very concisely :):) :

- First approach:
on the client site,

press CONTROL-ALT-F1 and login as usual

execute xinit -- :1

in the new X window connect to the remote server using ssh as normal (ssh -X user@remote_server)

execute the command gnome-session

Note that, this works with ubuntu but not with every linux distribution because usually the default init level is set to 5 but it must be set to 3 in the /etc/inittab configuration file under the server machine.

This approach is just fine if the remote server is connected in a very fast local area network

- Second approach:

You can use NX. There are two versions, a completely open source implementation and closed but still free version.

For the closed free version follow the following steps:

For the server,
Download deb files for nxclient, nxnode and nxserver from [http://www.nomachine.com/download.php](http://www.nomachine.com/download.php)

install libstdc++2.10-glibc2.2 with apt-get (i.e. sudo apt-get install libstdc++2.10-glibc2.2 )

install nxclient, nxnode and nxserver

For the client,
install nxclient and you will be able to connect to the server machine

The advantage of NX is... SPEED. Really, it's very very fast. I am using it over an ADSL connection and is really very responsive. Note, that it also works over ssh and you don't have to set up any accounts.
I tested nomachine NX in ubuntu EDGY

For the opensource implementation of NX, instructions can be found at [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

Feel free to ask any other questions.

---

### Post by matt.runion on 2006-12-11
Thanks all for the help.  It seems that issuing the "gnome-session" command via the ssh tunnel seems to get me closer than I've come yet.  It actually seems to start up the window manager across the tunnel (even though the start-up sounds are issued from the remote server), but then there is a error message that pops up:

There was an error starting the GNOME Settings Daemon.  Some things, such as themes, sounds, or background setting may not work correctly.  The Settings Daemon restarted too many times.  The last error was: System exception: IDL:Bonobo/GeneralError:1:0 Child process did not give an error message, unknown failure occurred.  Gnome will still try to restart the Settings Daemon next time you log in.

HOWEVER, it seems that I can sort'a toggle between the application pannels between the remote system and the local system and run programs from either...just a little hard to distinguish between which system I'm on since the desktop background is only of the local system.

Anyways, running one app at a time (instead of the whole desktop) also works, and each app is "windowed".

Once again, thanks for the help.  This Ubuntu stuff is cool!!

---

