---
title: "Vnc?"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by LoicNyssen on 2007-05-08
Hi, I had to restart my ubuntu machine remotely, and for some reason I cant connect to it using VNC, I can only use SSH, I have had this problem once before and the only way I was able to connect to the computer using VNC again was to actually log my self in while physically at the computer. 

Why is this? Is there a way to get the VNC service back up and running?

---

### Post by [ajax] on 2007-05-08
I don't know why the vnc service won't restart if the computer restarts.  I have found the included VNC server, VINO, to be unreliable.

Here is a fix if you can only access your server by ssh (this should work):

```
sudo apt-get install x11vnc
```

This will install a new VNC server on Ubuntu, that you can use for emergencies, or as you choose.  After installing, just type

```
x11vnc
```

to run it, then try and connect (by default you shouldn't need a password).  From there, you can start to fix problems.

Of course, there must be a way to add the VINO server to startup programs via terminal, I just don't know what it is.  The above is what I can suggest.

---

### Post by LoicNyssen on 2007-05-08
> E: Couldn't find package xllvnc

mmmmmm it doesn't seem to want to work... is there an alternative?

---

### Post by [ajax] on 2007-05-08
From the text it looks as if you typed "L L" instead of "one one".  If you didn't, I don't know why it isn't working.

---

### Post by LoicNyssen on 2007-05-08
yes i did, My bad	:oops:

---

