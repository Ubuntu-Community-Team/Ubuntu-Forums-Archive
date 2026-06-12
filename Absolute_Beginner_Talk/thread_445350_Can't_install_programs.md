---
title: "Can't install programs"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by locustfist on 2007-05-15
When i select an app to install it just hangs on the spinning thing forever...i was at one time able to install. this is my 3rd day on linux/ubuntu

---

### Post by Nythain on 2007-05-15
what does it say if you type
sudo apt-get install packagenamehere
in the terminal

---

### Post by locustfist on 2007-05-15
i think this has something to do with it...what do i do

Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

---

### Post by Billy McCann on 2007-05-15
Sometimes running a program from a command line will help diagnose a problem.

Close Synaptic or the "Add/Remove Programs" window.  

Then in a terminal (Applications > Accessories > Terminal), type
```
sudo apt-get update
```
and see if you get any error messages.  

If not try to install a program, like say xmms.
```
sudo apt-get install xmms
```

Whatever errors you get, copy and paste them here for us.

---

### Post by Felin_Greenleaf on 2007-11-20
I'm having the same issue, actually, and Firefox can't install any plugins.

I did the update thing, then tried for XMMS, and this is what I got.

> E: Couldn't find package xmms

---

