---
title: "X11 Forwarding"
date: 2008-06-25
forum: Apple Hardware Users
---

### Post by Redeyes_Gambit on 2008-06-25
Ok, first off I'm not entirely sure this is possible, but I'd love to get your input on it.

What I'd like to do is use X11's built-in forwarding to redirect applications running in my virtual machine Ubuntu to my Mac's copy of X11 for seamless side-by-side Ubuntu/OSX apps.

First of all, I am correct in stating that an X11 redirection sends just windows, not the entire desktop (ala vnc) yes? I don't really need the whole desktop, just individual windows.

Do you guys know if this is possible, and if so what do I need to set up on both the OSX and Ubuntu sides of the connection?

Thanks guys,
EQB

---

### Post by luisito on 2008-06-25
I don't have a mac to test, but I guess it should be possible.

X redirection sends only the window and not the whole desktop indeed. So you have the right idea. It is a bit slow though.

It we were talking about two linux machines, all you would do it is run from a terminal in the client computer:
```
ssh -X hostname
```
to connect to the other one (which should have an ssh server installed). Then execute the commands you wish.

---

### Post by pytheas22 on 2008-06-25
I don't have a Mac, but as long as your Mac has X11 installed, it should be very easy to do this.  You just need to install an ssh server on Ubuntu:
```

apt-get install ssh
```

and then on your Mac (those things come with ssh installed by default, right?), start an ssh session with X11 forwarding enabled:
```

ssh -X ubuntu-username@ubuntu-ip-address
```

then you can start any application by typing its name (e.g. firefox), and it will appear on your Mac's screen.

---

### Post by luisito on 2008-06-25
I've just realized you wrote "virtual machine Ubuntu". Are you running Ubuntu in the same Mac? Are you actually planning to send X11 from a computer to itself?

Well, seems reasonable. Why wouldn't it work?

---

### Post by Redeyes_Gambit on 2008-06-26
Well gosh that was too easy!

I was expecting this to be a semi drawn-out, quasi hacky procedure but no! Worked right off the bat thanks to you guys! And yes, I have Ubuntu running via parallels (but it should also work with Virtualbox/VMWare I assume). Latency isn't at all bad on my 2.2ghz Core 2 Duo. Video is pushing things a tad, but it still works. Quick response to input, virtually no lag at all for typing like you get with VNC.

Audio from Rhythmbox and Firefox works with nary a hiccup too.

Pretty slick. Pretty slick indeed.

---

