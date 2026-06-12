---
title: "How to prevent X Crash when mouse is not attached?"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by mrdeeno on 2007-01-09
I'm running Dapper on a Sony Vaio laptop GRV680.
I have a mouse that I usually keep attached to my cordless Logitech LX7 mouse. 

Everything works fine most of the time except today when I went to my cousin's room.  

I shut down, disconnected everything and restarted when I was at my cousin's.  It booted up but X-server crashed and I'm sure it has something to do with my mouse, because that's all I had to connected to get it started.

How can I prevent it from crashing when the mouse is not connected?  I figured it would be smart enough to realize there is no mouse, or is there something special I have to do?

---

### Post by mrdeeno on 2007-01-10
so no one has this problem?

---

### Post by bodhi.zazen on 2007-01-10
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
```

Add this:

> Section "ServerFlags"
	Option "AllowMouseOpenFail"
EndSection

Note: If you have a ServerFlags section alread just add the 

	Option "AllowMouseOpenFail"

to it :)

HTH

---

### Post by mrdeeno on 2007-01-10
That didn't work...i get the same x server failed error when my mouse is not connected.

any other suggestions?

---

### Post by bodhi.zazen on 2007-01-10
Try this:

>  Option         "AllowMouseOpenFail" "true"

---

### Post by mrdeeno on 2007-01-12
I tried that and it didn't work either.

But I figured out the problem (Googled it)

[http://cfavatar.com/blogcfm/1/2006/11/XServer-crashes-on-startup-whithout-Mouse.cfm](http://cfavatar.com/blogcfm/1/2006/11/XServer-crashes-on-startup-whithout-Mouse.cfm)

I guess it has something to do with using evdev to get my forward/backward mouse buttons working and it crashed because it could not find the "core pointer".

So according to the website i found, i changed the touchpad to be the corepointer.  It works now and I can plug in my mouse after startup and still have all the functions.  The only difference is that the mouse speed was set to "default" again, but no big deal.

Thanks for the help though.

---

