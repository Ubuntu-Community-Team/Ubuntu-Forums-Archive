---
title: "no trackpad !"
date: 2007-08-28
forum: Apple PPC Users
---

### Post by elgoof on 2007-08-28
I followed the directions in the wiki for installing a trackpad on a ppc (g4, 12") and when I use the command:

sudo trackpad notap

I receive:

no trackpad !

How can I disable the tapping function, it is driving me crazy!

Thanks!

goof

---

### Post by rhetoric on 2007-10-08
I'm having the same problem and this tap function is driving me NUTS. New to ubuntu and linux.  The trackpad seems to be functioning... Please assist.

---

### Post by jwprolo on 2007-11-01
I'm no poweruser myself, but I got the same thing and here is what fixed it.  open a terminal session and type:

gksudo gedit /etc/X11/xorg.conf

Then find the input device section for the synaptics touchpad and replace the text with the text from here: [https://help.ubuntu.com/community/SynapticsTouchpad/AppleIbookG4](https://help.ubuntu.com/community/SynapticsTouchpad/AppleIbookG4)

restart X (crtl+alt+delete) and it should work.

---

### Post by shacamin on 2007-11-02
The easier way is to get a program called qysnaptics.

```
sudo apt-get install qsynaptics
```

You can configure just about anything with the trackpad in there.

---

