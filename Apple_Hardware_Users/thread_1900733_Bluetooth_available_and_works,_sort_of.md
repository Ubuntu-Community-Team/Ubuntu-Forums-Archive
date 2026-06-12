---
title: "Bluetooth available and works, sort of"
date: 2011-12-27
forum: Apple Hardware Users
---

### Post by rfkrocktk on 2011-12-27
I'm running amd64 11.10 on a 2011 8,3 MacBook Pro. Bluetooth is showing up as being available in the app indicator menu, but I have really strange issues with it. 

When I try and run "hcitool scan", I usually won't see anything, though I have seen my phone (which is in visible mode) a few times. It seems that support is kind of sporadic for it. I've noticed that if I initiate a pairing request from my phone to the computer, then things generally work a bit better, the computer invariably sees the request and is able to respond to it, granting me access to my phone. 

I'm trying to pair my Motorola S305 headphones to the computer, but unfortunately it doesn't see them at all. Does anyone know how I can try and resolve this?

(I am able to get my Bluetooth hardware's address via "hcitool dev".)

---

### Post by hansdown on 2011-12-27
:)Hi, rfkrocktk.

Motorola seems to be holding out on supplying drivers.

The quality is very good, but they need to work, right?

[http://www.google.com/search?client=ubuntu&channel=fs&q=Motorola+S305+headphones+in+ubuntu+11.10&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=Motorola+S305+headphones+in+ubuntu+11.10&ie=utf-8&oe=utf-8)

Check the first link.

---

### Post by rfkrocktk on 2011-12-27
Actually, this headset works on another computer running Ubuntu 11.04. It works, I just need to fix Bluetooth on the MBP to get going. It often can't find my phone or my other Bluetooth headset either, even when they're in pairing mode.

---

