---
title: "Need some (probably simple) help."
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by SolaceAvatar on 2007-01-19
Ok, I'm pretty new at all this, so if the answers are pretty obvious, I'm sorry.

First off, I'd like to install XChat. It says I first have to install XChat-common. I try to install XChat-common, and it says I first have to install XChat. Since this is logically impossible... help? :biggrin:
EDIT: Actually, I messed around a bit, and I think I might be able to get GAIM to work IRC...

Second, I want to install any MUCK client. TinyFuge is one, I think. I tried to install a lot of them, and none worked, although one said it wouldn't install because I already had it... except I couldn't find it under Applications or Search for files, so... I dunno.

Also, I have Gnome (I think), which... I dunno anything about it, but if it's important, I think I do.

Last, I got a new widescreen moniter, and I'd like to get the 1440X900 resolution it likes (or, well, basically any widescreen resolution in the meantime). No idea how; I can only find 3 options, and none are widescreen.

Anyway, thanks anyone who helps. :D

---

### Post by riven0 on 2007-01-19
For XChat, have you tried installing that through the terminal? It should take care of all those dependency issues. First try **sudo apt-get install xchat** but if that doesn't work try: **sudo aptitude install xchat**


For your resolutions problem, just do an xserver reconfiguration and choose your resolutions. Otherwise, if you have an intel integrated graphics card, install 915resolution.

---

### Post by Sef on 2007-01-19
> First try sudo apt-get install xchat but if that doesn't work try: sudo aptitude install xchat

First, ```
sudo aptitude update
```

Second, ```
sudo aptitude install xchat
```

Aptitude is an updated version of apt-get.   If it don't work in apt-get, it will no work in aptitude.

---

### Post by SolaceAvatar on 2007-01-19
Well, I just found out that Add/Remove programs on Ubuntu is about a thousand times more useful than on Windows; I just asked it to find and install XChat and it did. :biggrin: That is just awesome.

Couldn't find a MUCK client on it, though. :( Still need help on that.

> **riven0 said:**
> For your resolutions problem, just do an xserver reconfiguration and choose your resolutions. Otherwise, if you have an intel integrated graphics card, install 915resolution.
I don't have the intagrated card, so... what's an xserver reconfiguration, and how do I do one?

---

### Post by riven0 on 2007-01-19
> **SolaceAvatar said:**
> I don't have the intagrated card, so... what's an xserver reconfiguration, and how do I do one?

In the terminal, copy and paste:

> sudo dpkg-reconfigure xserver-xorg

Then choose your resolutions by hitting the space bar.

---

### Post by SolaceAvatar on 2007-01-22
Ok, instead of starting a new thread, I'm gonna resurect this.

1. I apparently have irssi installed. Which is cool. But it's stuck somewhere besides the application bar... how do I start it/put it there/find it?

2. I'd like... heck, nearly any MUCK client. I've tried 'apt-get install tf' to install tinyfuge (which I've heard good things about), but it can't find it. And I don't know how to do the tarball thing (I followed the directions as best I could, but Ubuntu said it didn't exist).

Oh, and thanks for all the help everyone. :D

---

### Post by riven0 on 2007-01-23
Okay, it seems that tf is a command line program. So try opening the terminal and typing either** tf** or **tinyfuge**. Whichever works.

Also, try installing this:

> sudo apt-get install mmucl

As far as I know, this is possibly another MUCK client. And again, if it doesn't appear anywhere in applications, type **mmucl** in the terminal to get it running.

Now for irssi, this is also command-line, :p , which means you must run it in the terminal. It may not be what you want, so you can just use gaim and install this plugin:

> sudo apt-get install gaim-irchelper

to get extra functionality.

Otherwise, I would recommend searching for **irc** in Synaptic Package Manager. There is a bunch of programs there... so many that I can't really make a recommendation on what will work the best. But try out several and see what fits for you.

---

