---
title: "Educate me about FreeNX"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by NTolerance on 2007-11-30
I've been using VNC to connect to my Ubuntu systems and I'm getting tired of the limitations such as lack of encryption, resolution scaling, etc...  But the one thing I like about VNC is connecting to display 0.  I like this for two reasons - not having to re-login to the local machine when I use it, and also being able to control my HTPC from my couch without staring at a login screen.

I have been reading that FreeNX is a good alternative.  Are there any others?  With FreeNX can I...

1.  Connect to display 0?
2.  Be able to reach the GDM login screen so if a remote PC loses power I can still connect to it upon reboot?
3.  Scale resolutions?

Thanks!

---

### Post by daflame on 2007-11-30
> **NTolerance said:**
> I've been using VNC to connect to my Ubuntu systems and I'm getting tired of the limitations such as lack of encryption, resolution scaling, etc...  But the one thing I like about VNC is connecting to display 0.  I like this for two reasons - not having to re-login to the local machine when I use it, and also being able to control my HTPC from my couch without staring at a login screen.

I have been reading that FreeNX is a good alternative.  Are there any others?  With FreeNX can I...

1.  Connect to display 0?
2.  Be able to reach the GDM login screen so if a remote PC loses power I can still connect to it upon reboot?
3.  Scale resolutions?

Thanks!

I have a forum with instructions on how to install FreeNX here:
[http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx](http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx)
However, the current fault with the version I supply is that there is no access to screen 0 via VNC.  This is a normal feature of FreeNX, but it isn't working on this version yet.  If you want display 0 you can download the limited free version (2 connection max) at [www.nomachine.com](www.nomachine.com) it is called NX Server Free Edition.  It iis commercial software whereas FreeNX is open source.  FreeNX in and of itself does not by default access screen 0, instead it creates a virtual screen at around 1000 and sends that using X remote desktop technology compressed (with NX display technology) and encrypted by ssh.  However, VNC proxy is an option for NX to proxy VNC connections at the server and on the commercial version desktop shadowing is also possible.  I am not the developer of FreeNX, but I have recently started supporting it on Ubuntu and I hope to resolve the VNC issue soon.  I hope that answers your questions.

---

