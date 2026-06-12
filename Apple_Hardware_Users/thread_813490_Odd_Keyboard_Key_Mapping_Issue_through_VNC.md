---
title: "Odd Keyboard Key Mapping Issue through VNC"
date: 2008-05-30
forum: Apple Hardware Users
---

### Post by uberamd on 2008-05-30
I have Ubuntu 8 running on my 'media server'. I am trying to remote in through VNC and I can login fine. However the keyboard is mapped wrong. The "a" key outputs an "a" in VNC, however most other keys are mapped wrong:

<key pressed> -> <key displayed in VNC>

a -> a
s -> b
d -> f
f -> h
e -> g

and so on. I have tried switching the keyboard to "Macintosh" with to results. This is insanely annoying, when SSH'ing in it works fine (obviously), however VNC is throwing this curve-ball at me. Any ideas?

Edit: I should note I am connecting to the Ubuntu PC via VNC from a Macbook pro using Chicken of the VNC. The keyboard is NOT messed up when I vnc from my MBP to my FreeBSD server.

---

### Post by davidleelambert on 2010-02-11
Sounds like an open bug that I've also seen:

[https://bugs.launchpad.net/ubuntu/+source/vnc/+bug/112309]("https://bugs.launchpad.net/ubuntu/+source/vnc/+bug/112309")

Did you ever resolve this?

---

