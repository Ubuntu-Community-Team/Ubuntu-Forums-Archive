---
title: "Networked web development environment"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by Tim Thumb on 2006-03-19
I run a small website design business with the following network set up:

2 WinXp boxes
1 Mac OS X
1 Ubuntu

We use a simple Windows peer to peer network without any kind of server. The machines that need it run a local Apache/MySQL/PHP set up.

What I'd like to do is add another machine to use as a fileserver and localhost server for LAMP, that all machines can tap into without the need for AMP on separate machines. All web worked would be served up from here. I'll be using Ubuntu on this machine.

What I don't need is a mailserver or a real webserver to the outside world.

Now, I'm pretty sure that all the information I need to set up the component parts is readily available to me here, but I don't really what those parts are. Can someone tell me the pieces of the jigsaw I need?

---

### Post by Pragmatist on 2006-03-19
Maybe these will help?

localhost:
[https://wiki.ubuntu.com/LocalhostSubdomain?highlight=%28localhost%29](https://wiki.ubuntu.com/LocalhostSubdomain?highlight=%28localhost%29)

fileservers:
[https://wiki.ubuntu.com/SettingUpSamba?highlight=%28samba%29](https://wiki.ubuntu.com/SettingUpSamba?highlight=%28samba%29)
[https://wiki.ubuntu.com/PureFTP?highlight=%28ftp%29](https://wiki.ubuntu.com/PureFTP?highlight=%28ftp%29)

---

### Post by Tim Thumb on 2006-03-20
Thanks - seems like a good start for me.

---

