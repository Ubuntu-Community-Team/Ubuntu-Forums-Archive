---
title: "Remote Desktop on alternate port?"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by Booji on 2007-05-21
I recently put Feisty AMD64 on my box, dual booting with Windows. I want to connect to it from work. At home, I have no router, just a direct cable connection. At work, most ports are blocked so I cannot connect to Vino at port 5900. In XP, I just changed the RDP port to 80 and connected that way, which worked fine for me. I can't figure out how to connect to Ubuntu, however. I used gconf-editor and changed the port to 80 and selected "use alternate port", but to no avail. What I have read states the vino port # must be higher than 5000, and none of those will work for me. From work's unsecured wireless network, I was able to get in using port 5900, but I can't do that from my work desktop. Is there any way for me to do this?

---

### Post by lazyart on 2007-05-21
Use X11VNC (in the repositories) and you can use a different port.

---

### Post by krunge on 2007-05-21
Yes, with x11vnc just run (as root, of course, for ports less than 1024):

```
x11vnc -rfbport 80
```

plus any other options you like.  E.g. with newer x11vnc versions (not in debian repositories) you could specify "-ssl SAVE" for SSL connections and "-http" to serve an SSL enabled Java viewer to web browsers.

You probably also want the option "-forever" to have it keep listening for new connections after the first one, and "-usepw" (or -rfbauth ~/.vnc/passwd) to set up a password (otherwise anyone could connect to your desktop if they discovered you had VNC on port 80).

---

### Post by Booji on 2007-05-22
Thanks, works OK. Is there any way to speed up VNC: it is not nearly as responsive as XP's remote desktop.

---

### Post by krunge on 2007-05-22
> Is there any way to speed up VNC: it is not nearly as responsive as XP's remote desktop.

Not really.  However if things are unusably slow that usually means something is misconfigured (a common example is accidentally using the raw VNC encoding thru a tunnel).

VNC was designed as an open protocol that tends to favor compatibility and interoperability over the speed one can get in a proprietary protocol and client+server implementation.  

VNC also seems to have as a goal that the client should be extremely simple to implement. Indeed it is, but that leads to lower performance because, for example, pixmap data is not cached on the client-side.  I have a project to improve this for x11vnc [http://www.karlrunge.com/x11vnc/#faq-client-caching]("http://www.karlrunge.com/x11vnc/#faq-client-caching")  , but it is still a work in progress.  UltraVNC has some client-side caching, but that server is Windows only.

If you don't need to view your physical X session (i.e. the one displayed on your monitor), but rather a virtual X session is acceptable, then NX should give you the best remote desktop performance available on unix.

BTW, I don't think many people do it, but you could also view that NX session locally (ie. when at home) if you wanted to. E.g. by running nxclient on a "naked" X server with no window manager.  There is a ubuntuforums thread on this.  The same method works for real or tight vncserver.

---

