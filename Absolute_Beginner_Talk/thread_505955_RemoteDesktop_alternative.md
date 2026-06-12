---
title: "RemoteDesktop alternative?"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by Tixer on 2007-07-20
I currently use RemoteDesktop, or whatever it's called in Ubuntu. I've heard alot of people say it's slow, so I'm wondering what a faster solution is, that can be used from Windows to see Ubuntu.

My only requirement is that it must be able to view :0, as I don't want to keep starting sessions, and it must be easy to set up.

---

### Post by geist27 on 2007-07-20
I have used VNC before, there are lots of flavors of it

[http://www.realvnc.com/](http://www.realvnc.com/)
[http://www.tightvnc.com/](http://www.tightvnc.com/)

---

### Post by inque_54 on 2007-07-21
[Ultra VNC]("http://www.ultravnc.com/") works ok for me 

very light program and runs pretty fast, but I connect through LAN only though.

---

### Post by HermanAB on 2007-07-21
Cygwin with OpenSSH.  Enable X forwarding and simply run whatever you want from the command line.  You don't really need the desktop crap - just run the program by name, like 'firefox', 'gedit' or whatever:

$ ssh -X -c blowfish-cbc herman@myserver
Password: supersecret
$ gedit

Cheers,

Herman

---

### Post by Tixer on 2007-07-21
I'm only using this on a LAN, but I'm trying to emulate the appearance of having a KVM, in essence. Forwarding an X session sounds like a good idea if I'm not home, but if I'm home, I'd rather have the whole desktop appear.

I wasn't aware UltraVNC is for Linux. I currently use Remote Desktop + TightVNCviewer.

Also, with all these ideas, can people provide how-to's?

---

### Post by Ephilei on 2007-07-21
I'm pretty sure UltraVNC does not have a Linux build.

---

### Post by inque_54 on 2007-07-21
> **Tixer said:**
> I'm only using this on a LAN, but I'm trying to emulate the appearance of having a KVM, in essence. Forwarding an X session sounds like a good idea if I'm not home, but if I'm home, I'd rather have the whole desktop appear.

I wasn't aware UltraVNC is for Linux. I currently use Remote Desktop + TightVNCviewer.

Also, with all these ideas, can people provide how-to's?

Oh crap sorry I forgot to mention that, I use UltraVNC on my windows machine to control the Linux server 

Haha sorry bout that

---

### Post by kvonb on 2007-07-21
Vino (the standard remote desktop thing) is a vnc server which serves the currently running desktop.

Unfortunately it uses a lot of CPU power, so on a slow machine it can be a pain.

I use it on my server which is a P4 1.6 and it is bearable over LAN, a little sluggish at times, but it's ok.

All you can do to speed it up is lower the resolution on your server and the colour depth too, I'm down to 1024x768 16bit colour and it is quite good.

There is plenty of bandwidth to spare, the only limit it seems is the CPU speed!

---

### Post by Tixer on 2007-07-21
Well, thats the issue. I'm running it at 1280, and I don't want to reduce it.

Also, my server (what I'm vncing into) is a piece of crud. Think 733Mhz.

---

### Post by Tixer on 2007-07-21
Bump.

---

### Post by irish_flu on 2007-07-21
I'm using the package called "vnc4server" (from the repositories) to view an X session on an Ubuntu box over the internet (attached to a T1).

On the Windows side, I use TightVNC to view it.

It works GREAT, IMHO, especially considering that I'm doing it over the internet.  I'm regularly amazed at how speedy it is.

I *think* I used this thread to configure it (it was awhile ago that I set it up):
[http://ubuntuforums.org/showthread.php?t=191564](http://ubuntuforums.org/showthread.php?t=191564)

My favorite thing about it is that my session stays running if I close my window but don't log out, just like Terminal Server (Remote Desktop) does in Windows 2000/2003/XP.  Maybe that's a standard for VNC (and thus not a big deal), but I don't have a ton of experience with VNC and I got the impression that not all VNC servers support this.

---

