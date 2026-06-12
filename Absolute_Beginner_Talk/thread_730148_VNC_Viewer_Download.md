---
title: "VNC Viewer Download?"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by k8fox1 on 2008-03-20
Running Gutsy

I wish to download VNC viewer. Which file do I chose from synaptic? I have attempted this but can't find the file anywhere. :confused:

---

### Post by Shabbro on 2008-03-20
I just ran 
>  sudo apt-get install xvncviewer
in the terminal.

To start it I just ran> xvncviewer

---

### Post by fela on 2008-03-20
I thought there was a viewer included with gutsy...

try ```
vncviewer <ip address><port number>
``` and there's more options aswell...

theres also of course xtightvncviewer, to install type ```
sudo apt-get install xtightvncviewer
``` then to run it, same as vncviewer but replace 'vncviewer' with 'xtightvncviewer' if I'm right...

the default vncviewer won't work for viewing the built in OS X leopard screen sharing feature, but xtightvncviewer does (just a tip if that's what you want to do) :guitar:

---

### Post by dedmonds on 2008-03-20
I believe I am using the xvnc4viewer package that shows in Synaptic. I call it with the "vncviewer" command, but the detail that shows when I run "vncviewer --version" says that I am running version 4.1.1 which agrees with the xvnc4viewer version in Synaptic.

---

### Post by k8fox1 on 2008-03-20
I launch xvncviewer but it won't let me type in the window to enter an address! Why?

---

### Post by erwall on 2008-04-09
> **k8fox1 said:**
> I launch xvncviewer but it won't let me type in the window to enter an address! Why?
try vinagre

it's in the repos

---

