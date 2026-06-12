---
title: "Why aren't macbook pro drivers included by default?"
date: 2008-05-02
forum: Apple Hardware Users
---

### Post by suchawato on 2008-05-02
Seems prety straitforward.
It's easier to install on a dell than a mac.
I need to download wireless drivers when my internet isn't working!!!

It's a wireless network.
That's pretty retarded if you ask me.

-Sara

---

### Post by wannadumpwindows on 2008-05-02
You're here now, so you have some kind of net connection, download the drivers you need, and transfer them over to your other computer. They can't fit everything on one CD.

---

### Post by suchawato on 2008-05-02
> **wannadumpwindows said:**
> You're here now, so you have some kind of net connection, download the drivers you need, and transfer them over to your other computer. They can't fit everything on one CD.
If I new how to do that I would.
Is there anything wrong with using a dvd?
-Sara
-A version with extra drivers

---

### Post by cyberdork33 on 2008-05-02
Please file a bug, or make a suggestion in the appropriate channel if you think something is broken. We have tried to explain this in other threads already, and there is really nothing that we can do in this forum anyway... we are not the ubuntu developers.

---

### Post by russo.mic on 2008-05-02
> **suchawato said:**
> Seems prety straitforward.
It's easier to install on a dell than a mac.
I need to download wireless drivers when my internet isn't working!!!

It's a wireless network.
That's pretty retarded if you ask me.

-Sara

The drivers aren't included because it's proprietary hardware with absolutely no manufacturer support whatsoever.  Why don't you write a driver that could be included in the next kernel release?  

Is there a place where windows users go to complain about problems after they PAY for an OS?  Windows doesn't include the drivers by default either!

NDISWrapper is a small download.  You have the Windows drivers for your card either in bootcamp or on OSX disk one, depending on your version of OSX.  build-essentials package is included on the CD.

Type:
sudo apt-cdrom add
sudo apt-get install build-essentials

then follow instructions to build ndiswrapper.

Russo

---

### Post by cyberdork33 on 2008-05-02
> **russo.mic said:**
>  sudo apt-cdrom add

Nice shortcut, didn't know about that one.

---

### Post by wannadumpwindows on 2008-05-03
How many threads relatng to the same topic are you going to start? Seems like the people on your other thread told you exactly how to do this, you just don't seem to want to do what needs to be done. If you aren't willing to help yourself, there isn't much we can do for you either.

Your other post . . . .
[http://ubuntuforums.org/showthread.php?t=778354]("http://ubuntuforums.org/showthread.php?t=778354")

---

