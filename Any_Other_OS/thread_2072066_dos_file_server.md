---
title: "dos file server"
date: 2012-10-17
forum: Any Other OS
---

### Post by joseavelar91 on 2012-10-17
Hi, I have a file server that has and still is running in ms-dos. I keep running to the memory problem. Any possibility of running my ms-dos file server with wine in ubuntu to help fix my memory problem. would I need to run it in 32 bit also instead of 64 bit.

---

### Post by shreepads on 2012-10-17
What protocol(s) does this file server running in ms-dos support?

For a simple SMB network file share, you could instead use the native Samba on Ubuntu for file sharing, very convenient and works like a charm across Linux and Win boxes...

See this: [http://www.sitepoint.com/ubuntu-12-04-lts-precise-pangolin-file-sharing-with-samba/](http://www.sitepoint.com/ubuntu-12-04-lts-precise-pangolin-file-sharing-with-samba/)

And then you have standard FTP servers as well...

---

### Post by oldos2er on 2012-10-17
Moved to Other OS/Distro Talk.

---

### Post by lykwydchykyn on 2012-10-19
> **joseavelar91 said:**
> Hi, I have a file server that has and still is running in ms-dos. I keep running to the memory problem. Any possibility of running my ms-dos file server with wine in ubuntu to help fix my memory problem. would I need to run it in 32 bit also instead of 64 bit.

Without knowing more, it's hard to say, but you'd probably have more luck with dosbox, or running freedos in a virtual machine, than with wine.

What "memory problem" are you running into?

---

### Post by ?#Yhf%*&amp; on 2012-10-29
You might be interested in my DOS-based operating system called [LightDOS]("http://lightdos.wordpress.com/"). You could run your existing DOS file server binary program without emulation, and LightDOS requires only a little more RAM than standard DOS because it has an alternative command line interpreter and a desktop.

---

