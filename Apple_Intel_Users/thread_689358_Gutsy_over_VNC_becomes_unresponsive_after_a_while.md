---
title: "Gutsy over VNC becomes unresponsive after a while"
date: 2008-02-06
forum: Apple Intel Users
---

### Post by dmber on 2008-02-06
I log into my Gutsy box over VNC with my Macbook.  I just use my Gutsy box to download torrents with uTorrent on Wine.  

I wish I could be more specific, but *after a while*, my VNC connection loses responsiveness.  I can still see my screen and the screen updates (like the uTorrent windows shows the progress moving) but "clicking" doesn't do anything.  I can't click anywhere -- taskbar, program, I can't even shutdown Gutsy with it.  

It's frustrating.  Not a HUGE deal, because I usually just control uTorrent with a webUI on my macbook, but I also have a bunch of my music on my Gutsy box and have that plugged into my stereo.  So I lose control of that too.

Any ideas?

I'm on 10.4.11 using VNC Viewer.

thanks.

---

### Post by cyberdork33 on 2008-02-06
probably has to do with the lack of bandwidth due to the torrents. Try SSH when it is like that. You should still be able to run commands that way, and browse your directories and such.

---

### Post by dmber on 2008-02-06
not sure how to do SSH.  can you link me to a good guide if it's complicated or give me a quick rundown if it's not?  thanks a lot.

---

### Post by cyberdork33 on 2008-02-06
you just need to install an ssh server on the machine you want to access, 

```
sudo aptitude install openssh-server
```

then on the other machine in a terminal, type: ssh username@ipaddressofothermachine

---

### Post by dmber on 2008-02-06
then i can use any terminal commands i want?

sounds too easy ;)

---

### Post by prana on 2008-02-06
As cyber suggested, you can use ssh but that will only work for non-GUI programs. If you want to access GUI programs, you need to use X port forwarding via SSH and ensure that OS X has X installed.

By the way, what do you use as a VNC client on OSX and the VNC server on Ubuntu? You might be better off trying to tweak that instead of going the SSH route.

---

### Post by cyberdork33 on 2008-02-06
> **prana said:**
> As cyber suggested, you can use ssh but that will only work for non-GUI programs. If you want to access GUI programs, you need to use X port forwarding via SSH and ensure that OS X has X installed.

By the way, what do you use as a VNC client on OSX and the VNC server on Ubuntu? You might be better off trying to tweak that instead of going the SSH route.I was just trying to establish that it was the VNC that was laggy, and not his machine that was freezing up, and, if you have the issue, and "can't even shut down", you can log in via ssh and run whatever command you want. X forwarding over ssh is a nice trick to learn though.

---

