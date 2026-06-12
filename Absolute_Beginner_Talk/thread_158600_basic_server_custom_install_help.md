---
title: "basic server custom install help"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by medz on 2006-04-11
hi i want to install a server boot installation and use fluxbox as my windows manager as well as having synaptic installed so i can download the applications i want to use...

could someone be kind enough to explain what i have to do...i know i have to edit the sources.list and etc and know all that but what else?

---

### Post by htinn on 2006-04-11
If you go the "server" route, you're going to need to get comfortable using the CLI and commands like apt-get and nano.

For a start, once you can login, you'll need to edit your /etc/apt/sources.list as desired, make sure your network is working properly (you may need to read up on ifconfig if it isn't working), then do the following:

sudo apt-get update

At that point, most of what you want should be available through sudo apt-get install package (where package is the name of what you want to install).

It sounds to me like you want GTK support, so you'll probably want to install "gdm" and get that running, then install "fluxbox" and then whatever else you need for that environment.

---

### Post by medz on 2006-04-11
thank you for your help

---

