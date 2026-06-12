---
title: "Remote Desktop?"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by u.b.u.n.t.u on 2006-06-09
Hi,

In Windows there is synergy and VNC. In ubuntu there is Remote Desktop.

I have enabled one ubuntu box to be controlled. My question is, how do I gain access to that box? This is a LAN, with the boxes about a meter apart, both on the net via a single router.

What is the dial in  program to gain access?

Thanks.

---

### Post by u.b.u.n.t.u on 2006-06-09
I did this on one ubuntu box:

System > Preferences > Remote Desktop

Then I enabled such. How do I gain access to that enabled Remote Desktop?

Thanks.

---

### Post by chimpsky on 2006-06-09
The remote desktop can be accessed by using VNC. Either from the command line in a 'nix box by using vncviewer, or by downloading tight vnc for windows:

[http://www.tightvnc.com/]("http://www.tightvnc.com")

---

### Post by musicinmybrain on 2006-06-09
Or use krdc as your vnc viewer on linux if you want a pretty graphical interface like you might be used to from Windows viewers. I haven't been satisfied with the standard tightvnc linux client. It's much better on Windows (though Windows also has UltraVNC).

---

### Post by Xilon on 2006-06-09
That doesn't really work :S I tried VNCing into my Ubuntu box from an XP box and got some socket read error... I tried setting up a tightvnc server on the XP box and vncviewer into it and it worked perfectly...

---

### Post by Somenoob on 2006-06-09
Do any other remote administration programs exist for Linux?

---

### Post by u.b.u.n.t.u on 2006-06-09
I have been using this program previously on XP.

synergy
[http://synergy2.sourceforge.net/](http://synergy2.sourceforge.net/)

Basically my mouse and keyboard contols the other desktop. However one needs to see both monitors. This isn't VNC.

Very handy program and it appears to run on nix too. (maybe).

---

### Post by Tom Fury on 2006-06-09
[QUOTE=Xilon]That doesn't really work :S I tried VNCing into my Ubuntu box from an XP box and got some socket read error... [/QUOTE]

That is interesting.  I vnc into my ubuntu box from an xp box all the time and never had an error.  On my xp box, I'm running the UltraVNC 1.0.1 viewer.

---

### Post by mjfarina on 2006-06-09
I've been using RealVNC and it seems to work fine...however, I can't connect anytime before I authenticate on the local machine. Is there a way to envoke that session from remote? I don't want to log into the local x-windows so I can connect to VNC.

---

