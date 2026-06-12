---
title: "SSH Connection and X display"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by xtankfixr on 2006-07-07
Hi everyone,

I'm new to ubuntu and linux in general and just have a quick question regarding an ssh connection and getting it to display the gui interface back into my x window display.

So I am able to ssh into my ubuntu box from my mac using an x11 window, or my windows laptop using putty. I'd like to be able to display the gui interface back but I'm not sure if this can be done. Anyway, any advice would be very much appreciated and btw... I'm really having a lot of fun with Ubuntu.

-David

---

### Post by mogelhead on 2006-07-10
Sure it can be done!

You just have to configure the SSH-client to use X-forwarding.

Using putty (version 0.55):
In the left tree, navigate to: Connection - SSH - Tunnels
Check the "Enable X11 forwarding" box.

As for MAC, I'm not sure. But if it is from a command line you are using ssh you can try the -X swith (replace host with the correct ip or hostname of your ubuntu box)
```
ssh -X host
```

I found [this thread]("http://ubuntuforums.org/showthread.php?t=190907") on the forum, which indicates that you also might try to replace -X with -Y.

---

### Post by xtankfixr on 2006-07-10
Thank you, I'll give it a try and let you know how it works!

---

### Post by xtankfixr on 2006-07-11
That did the trick, I was actually able to get VNC viewer to display back from my Mac, which is exactly what I wanted to do.

Thank you for the help.

-David

---

