---
title: "Standardport on vnc"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by tigershark on 2007-01-16
Hi

I've allowed users to connect to my ubuntumachine using System -> Preferences -> Remote desktop and it works fine.

When I use for example realvnc to connect from an Windowsmachine it still works fine but when I try to connect through an webbrowser i doesn't work.

I assume that you need some portnumber or something, but which portnumber?

---

### Post by inCursorated on 2007-01-16
You can't connect to a vnc server from a web browser. you have to use a vnc client program like realvnc or tightvnc. the standard vnc port is 5900, fyi.

---

### Post by tigershark on 2007-01-17
Okey, so it is only in windows that that works through java...:(

---

### Post by inCursorated on 2007-01-17
i'm not sure what u're running on the windows machine to connect with java... the only remote access software windows comes with is rdp (remote desktop protocol) for xp and later... for which u need a client app just like vnc

---

### Post by tigershark on 2007-01-17
I'll guess that java has some vnc software.

Because the only thing I have installed is an webbrowser and java and when I use for example Firefox to connect to [http://192.168.1.1:5800](http://192.168.1.1:5800) assuming that I have port 5800 I get an loginform for vnc using javasoftware.

---

### Post by inCursorated on 2007-01-17
okay i take it back: u can connect to vnc server with a web browser... i've just always used a vnc client. see [here]("http://www.realvnc.com/javavncviewer.html").

its not platform dependant so u should be able to have the same setup on linux as with windows

u probably have the port wrong due to the display number...

> The server listens for HTTP connections on port 5800+display number. So to view display 2 on machine 'snoopy', you would point your web browser at:

    [http://snoopy:5802/](http://snoopy:5802/)

---

### Post by inCursorated on 2007-01-17
there are some instructions [here]("http://www.debianadmin.com/remote-desktop-sharing-in-ubuntu.html") but it doesn't say anything about http access. i'm using kde (kubuntu) not gnome so i can't really check the config. it may only enable the standard server on port 5900 and not the http one on 5800 or whatever.  try running this command to see what port(s) it's using:

```
sudo netstat -tnlp | grep vnc
```

or u might have to grep for vino which is the vnc server for gnome

```
sudo netstat -tnlp | grep vino
```

---

### Post by tigershark on 2007-01-18
> **inCursorated said:**
> 
```
sudo netstat -tnlp | grep vino
```

The output for that was:
tcp        0      0 0.0.0.0:5900            0.0.0.0:*               LISTEN     5714/vino-server


And for this example
```

The server listens for HTTP connections on port 5800+display number. So to view display 2 on machine 'snoopy', you would point your web browser at:
[http://snoopy:5802/](http://snoopy:5802/)

```

...it didn't work

---

### Post by inCursorated on 2007-01-18
ok, so it's only listening on port 5900 for standard vnc connections. i don't know that vino supports vnc via http/java... i think you're going to have to use a different vnc server app to get this funtionality. i'd disable vino and try tightvnc (install the tightvncserver + tightvnc-java packages via apt or synaptic).

---

### Post by inCursorated on 2007-01-18
this may be an easier solution:  [HOWTO: Server Side VNC Client]("http://www.ubuntuforums.org/showthread.php?t=107503")

it's a rather unconventional setup... the remote user connects to your apache web server which launches a java vnc client to establish the standard vnc session.

---

### Post by venik212 on 2007-02-08
Actually, the Java version of VNC allows you to use a web browser as a client/viewer.  I do it all the time.

---

### Post by dannyboy79 on 2007-02-08
I feel that Remote Desktop Protocol is insecure. I would use Nxserver, Nxnode, and Nxclient if I were you. They make a Windows client as well. It actually runs over SSH so all your traffic is encrypted. Check it out. There are plenty of threads on this subject already

---

### Post by venik212 on 2007-02-08
I tried to instaall that package, but Kubuntu gagged, and would not install it....If I cannot revive VNC under Kubuntu I'll have to return to Gnome.

---

### Post by venik212 on 2007-02-09
I would dearly love to know how to connect from a remote computer to my Kubuntu machine.  VNC worked fine with Gnome, but I do not know how to do it with KDE.  I tried to install freenx but the installation failed.

---

