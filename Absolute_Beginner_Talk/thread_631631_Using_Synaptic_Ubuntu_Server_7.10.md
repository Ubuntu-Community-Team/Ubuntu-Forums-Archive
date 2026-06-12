---
title: "Using Synaptic Ubuntu Server 7.10"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by JD876 on 2007-12-04
I wish to use Synaptic in a server context. I have installed it using "sudo apt-get install synaptic". What's next?

The Ubuntu page on Synaptic simply says:

"To launch Synaptic, choose System > Administration > Synaptic Package Manager". I fail to see any of these. All I see is my command line.

Neither "sudo synaptic" nor "gksudo work". What I get is a "Gtk-WARNING" about not being able to open the display.

---

### Post by njparton on 2007-12-04
Do you have gnome installed?

Synaptic is a gnome package so you need to be running that to use it.

---

### Post by JD876 on 2007-12-04
I installed it. When trying to actually run Gnome, I received the same failure message. Comment: if Synaptic is Gnome dependent, wouldn't it be a part of its install package?

---

### Post by christhemonkey on 2007-12-04
if you want to have a GUI then install a desktop:
```
sudo apt-get install ubuntu-desktop 
```

If you just want some sort of package management tool, try:
```
sudo aptitude 
```

---

### Post by PeterJS on 2007-12-04
Are you running any sort of X desktop? It sounds like you've got some X apps installed, but aren't running any sort of desktop. Graphical applications aren't going to work from the command line. If you've got another linux machine running X you could log in via ssh with XForwarding enabled and run it that way.

---

