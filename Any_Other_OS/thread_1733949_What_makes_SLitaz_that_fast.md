---
title: "What makes SLitaz that fast ?"
date: 2011-04-19
forum: Any Other OS
---

### Post by linuxyogi on 2011-04-19
Hi,
**What makes Slitaz so fast ?**

I am using Ubuntu 10.04 on the old Celeron PC with fluxbox as DE.

Despite using fluxbox its still not as fast as slitaz.

---

### Post by Plumtreed on 2011-04-20
Slitaz is small to enable it to run entirely in ram and therefore appears to be very fast.

---

### Post by Spice Weasel on 2011-04-20
It's stripped down, optimized and runs in memory.

If you're not using Ubuntu Server you're probably also using the GNOME display manager which slows the PC down like 'eck, along with all of the other stuff that Ubuntu runs on start up.

---

### Post by linuxyogi on 2011-04-20
> **Spice Weasel said:**
> 
If you're not using Ubuntu Server you're probably also using the GNOME display manager which slows the PC down like 'eck, along with all of the other stuff that Ubuntu runs on start up.

I am actually running fluxbox over a Xubuntu. So, is GNOME display manager running in my case ?

> **Spice Weasel said:**
> 
along with all of the other stuff that Ubuntu runs on start up.

Is there a way to remove/disable them ?

Thanks to both.

---

### Post by Spice Weasel on 2011-04-20
> **linuxyogi said:**
> I am actually running fluxbox over a Xubuntu. So, is GNOME display manager running in my case ?

Yes. Xubuntu includes GNOME display manager for some reason. apt-get removing *gnome* then installing LXDM or another lighter one might be a good idea.

You might also want to try compiling a version of the kernel from kernel.org and configuring it for your hardware. The Linux kernel is one of the easiest things to compile, it has a nice configuration GUI/TUI and you don't have to worry about dependencies. It's worth it for the speed increase.

---

### Post by linuxyogi on 2011-04-20
> **Spice Weasel said:**
> Yes. Xubuntu includes GNOME display manager for some reason. apt-get removing *gnome* then installing LXDM or another lighter one might be a good idea.


Just did it. I can see some improvement. I don't want to sound repeatitive but still Slitaz is faster.

> **Spice Weasel said:**
> 
You might also want to try compiling a version of the kernel from kernel.org and configuring it for your hardware. The Linux kernel is one of the easiest things to compile, it has a nice configuration GUI/TUI and you don't have to worry about dependencies. It's worth it for the speed increase.

Never done that before. I will end up breaking the installation. 

Let me tell you the apps I am using

Browser: elinks (text only)
              midori
Email: sylpheed
Multimedia : mplayer (cli)
Torrent Client : deluge

Tried rtorrent but its seems quite complicated.

---

### Post by Spice Weasel on 2011-04-20
Deluge is sloowww. Try transmission from your browser. Run transmission-daemon then navigate to [http://127.0.0.1:9091/transmission/web/#all](http://127.0.0.1:9091/transmission/web/#all)

Very fast.

---

### Post by linuxyogi on 2011-04-20
> **Spice Weasel said:**
> Deluge is sloowww. Try transmission from your browser. Run transmission-daemon then navigate to [http://127.0.0.1:9091/transmission/web/#all](http://127.0.0.1:9091/transmission/web/#all)

Very fast.

Okay, I will try that the next I need to download something & tell you how it goes.:D

---

### Post by Dlambert on 2011-04-23
SLitaz is also under 30MB, whereas (Livecd) of ubuntu is 600 Some.

---

### Post by linuxyogi on 2011-07-15
Installed Natty Minimal Install. 

Everything runs smoothly including FF, Deluge.

---

