---
title: "Open application via putty"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by Frank_F on 2008-01-28
Hello

I am trying to open an ubuntu application (ie. firefox) via putty and receive "GTK-WARNING **: cannot open display."

I changed my ssh_config file to include FowardX11 yes and followed the instructions below

Single Applications

You can forward graphical applications with the -X option.

ssh -X user@server

Once the connection is made enter your command in the terminal, firefox & for example. This will start Firefox on the server and forward the Firefox interface to the client.

You can do this as a single command/application if you like :

ssh -XC user@server firefox


Thanks

---

### Post by Joeb454 on 2008-01-28
Are you running Windows on the Client machine? because if so you obviously won't have the X Window Display installed, and that's why you're getting that error

---

### Post by Frank_F on 2008-01-28
ohhps sorry, yes I am using Windows, I guess this was a dumb move on my part. So I guess there is no way of opening applications from my Windows machine then ?

---

### Post by Joeb454 on 2008-01-28
I don't think so no. It may be possible to install the X Window system on Windows though I have never tried it. I know X Forwarders exist, but they are quite expensive.

If I find a way I'll post it back here

---

