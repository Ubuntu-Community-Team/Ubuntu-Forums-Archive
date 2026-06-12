---
title: "remote login"
date: 2006-05-02
forum: Absolute Beginner Talk
---

### Post by big-hed on 2006-05-02
can or how do i setup my ubuntu pc to be available 24/7 so that i can login to it from anywhere via the web to work on when im away on business???

---

### Post by byenary on 2006-05-02
Install vnc on it vor visual login an openssh for shell login.
Give it a fixed ip, forward your router @ home to the fixed ip 
and aquire a dnsservice for your router, something like dyndns

---

### Post by the_tiger on 2006-05-02
I used the VNC over SSH wiki to set up a secure tunnel and then followed the resumable sessions post to login to GDM. VNC is a program for viewing remote screens. SSH creates an encrypted connection so that your session will be secure.

VNC over ssh.
[https://wiki.ubuntu.com/VNCOverSSH?highlight=%28vnc%29](https://wiki.ubuntu.com/VNCOverSSH?highlight=%28vnc%29)

This method will give you an X-terminal (windows and a terminal screen.)

In order to have resumable sessions try this. Some users have suggested it is less secure but as I long as you set up an ssh connection first I believe it is ok. (Enabling any form of remote access will always make a machine less secure.)

[http://ubuntuforums.org/showthread.p...hlight=gdm+vnc](http://ubuntuforums.org/showthread.p...hlight=gdm+vnc)

In order for remote access to work from across the internet you will need to ensure that your home firewall/router will forward the ports used by ssh and vnc. These are mentioned in the posts and I believe they are 22 for SSH and 5900/5901 for VNC.

---

