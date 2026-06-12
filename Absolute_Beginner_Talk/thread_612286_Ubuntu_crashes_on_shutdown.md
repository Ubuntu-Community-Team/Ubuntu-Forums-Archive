---
title: "Ubuntu crashes on shutdown"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by tafsen on 2007-11-13
Hi
Some times when I shutdown my machine the screen goes black, and the light fir cpu-load turns on. No mather how long I wait, nothing happends.  This happends aprox. every fourth shutdown.  How can I find out what's wrong?

---

### Post by elctb on 2007-11-13
I have the same problem. I don't know what's going on, but when that happens I switch to another screen via "ctrl-alt-f1" (you can try f2, f3, etc instead of f1 until you get a login prompt) and I get a login prompt. I login as root and issue the "/sbin/shutdown -h now" command. This works every time.

---

### Post by alienexplorers on 2007-11-13
Try adding a line
> acpi=force
to any open line in your menu.lst file.

---

### Post by tafsen on 2007-11-25
That didn't help at all. Now it crashes on every shutdown.

---

### Post by tafsen on 2007-11-25
> **elctb said:**
> I have the same problem. I don't know what's going on, but when that happens I switch to another screen via "ctrl-alt-f1" (you can try f2, f3, etc instead of f1 until you get a login prompt) and I get a login prompt. I login as root and issue the "/sbin/shutdown -h now" command. This works every time.

That doesn't work for me. Im not able to change to another screen.

---

### Post by scrooge_74 on 2007-11-25
> **tafsen said:**
> Hi
Some times when I shutdown my machine the screen goes black, and the light fir cpu-load turns on. No mather how long I wait, nothing happends.  This happends aprox. every fourth shutdown.  How can I find out what's wrong?

Read your /var/log/system and look for clues for what is going on

---

### Post by tafsen on 2007-11-28
[http://pastebin.com/m69b9a646](http://pastebin.com/m69b9a646)

---

### Post by scrooge_74 on 2007-11-28
> **tafsen said:**
> [http://pastebin.com/m69b9a646](http://pastebin.com/m69b9a646)

Try killing your network manager previous to a shutdown and and remove any external device you have.

I had some issues in the past with my network manager, you could also shutdown the network card first.

From what I can read HAL is trying to manage some of the devices and it is falling somehow, could be with the network cards.

My laptop is kind of picky about its broadcom card and after struggling with it I installed Debian Etch on it (I had several problems with suspend and resume and the occasional shutdown issues)

---

