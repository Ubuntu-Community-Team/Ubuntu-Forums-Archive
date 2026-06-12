---
title: "start a gui app through ssh to the desktop"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by barbz127 on 2007-07-18
I forgot to kick off utorrent (through wine) after rebooting my mchine last night.

I can ssh to it but cant vnc.

Is there any way I can start utorrent.exe to the local desktop instead of it trying to run through the ssh?

Cheers
Paul

---

### Post by jfinkels on 2007-07-18
> **barbz127 said:**
> I forgot to kick off utorrent (through wine) after rebooting my mchine last night.

I can ssh to it but cant vnc.

Is there any way I can start utorrent.exe to the local desktop instead of it trying to run through the ssh?

Cheers
Paul

Well for some applications, there is a command line option to define which X display to use, so I think doing something like:```
firefox --display=:0
``` might work (assuming you only have one monitor in the standard desktop setup, which you probably do).

However, I don't know how to do this with wine.

If you want to restart vino-server (the default VNC server which starts when you log in to Ubuntu) you can try:```
sudo /usr/lib/vino/vino-server --display=:0
```I think that will work...

Alternately, you can use a native Linux torrent client, like Transmission or rTorrent, which is able to run from the command line only.

---

