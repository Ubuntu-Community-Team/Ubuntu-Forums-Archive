---
title: "Remote Login"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by richard101 on 2007-07-13
Hi All

I cannot seem to get remote desktop working - although I'm close :-)

Weirdly, VNC on my laptop will only connect to VNC on my Ubuntu 6.06 desktop when I'm logged in (that is - when I login to Ubuntu).

I've a static ip, and apache installed.


any ideas??

Richard101

---

### Post by steve8track on 2007-07-14
I haven't tried, but I think that vnc can only be used after the computer being viewed has logged in.  If you want to have the ability to log in with the remote access, try xdmcp.

You can read about it here:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Remote_Access]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#Remote_Access")

Also, I just barely posted on another thread you may want to keep an eye on to see if other relevant help comes up there too (though probably nothing there yet):

[http://ubuntuforums.org/showthread.php?t=500807]("http://ubuntuforums.org/showthread.php?t=500807")

Good luck.

---

### Post by steve8track on 2007-07-31
I've tried xdmcp, and it works way better for me than vnc did, though you have to use it from your ubuntu login, but it does the logging in for you on the remote machine.  You just won't be able to use your local machine at the same time.   Also, for security reasons, it is used on a local network only (though I guess you could port forward). It looks and feels like I'm on the other computer, only with the graphics card of this one, which is fine by me. It seems to use local graphics, while using the remote hard drive and remote processor.

What would be funny is to log onto the remote machine and use the remote machine to remotely log onto your local maching through vnc...  It's like when I wanted to run a Windows 98SE virtual machine that itself was running the embedded version of DSL.  It's fun to do stuff for no reason...

Good luck.

---

