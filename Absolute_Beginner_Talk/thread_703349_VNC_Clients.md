---
title: "VNC Clients"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2008-02-21
My job is in a windows environment and I've grown fond of a program called [Gencontrol]("http://www.gensortium.com/products/gencontrol.html") on 
Windows that temporarily installs a vnc server on the target machine then remotes it. Is 
there something like this for Linux so that I don't have to install VNC Server on every 
machine at my work?

Thanks for your help!

---

### Post by freelinuxhelp on 2008-02-21
If you need to remote control Linux machines, you have a few options. For command line, OpenSSH, for GUI, you have VNC and NXserver ([http://nomachine.com](http://nomachine.com))

I'm not aware of a program that will actually put the vnc server on the remote machine though.

I use ultraVNC at my job, you can make an executable that the end user downloads and runs. It will automatically connect to your listening viewer. And the UltraVNC viewer runs perfectly in wine.

---

### Post by shanepardue on 2008-02-21
Yeah, I'm aware of these options, but I am in a Windows environment and they don't have 
VNC servers (listeners) installed. Thanks anyway.

---

