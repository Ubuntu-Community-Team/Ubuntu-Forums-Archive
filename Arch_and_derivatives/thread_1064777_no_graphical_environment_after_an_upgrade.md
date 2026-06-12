---
title: "no graphical environment after an upgrade"
date: 2009-02-09
forum: Arch and derivatives
---

### Post by stonecoldjha on 2009-02-09
Hi,i have run myself into a real big trouble by pacman -Syu.the update successfully completed,but after i rebooted,X did not start,saying that it was not set up.i waited to see my good old gdm,that did not show up,but it was that messages.how do i fix this?

---

### Post by smartboyathome on 2009-02-09
You probably need to use a new xorg.conf. Try X -configure.

---

### Post by namegame on 2009-02-09
Also, make sure that you have dealt with the new Xorg hotplugging feature. If you search around you should find multiple, different solutions, which all work, depending on what you want. :)

---

### Post by stonecoldjha on 2009-02-09
X -configure didn't work out.

---

### Post by mips on 2009-02-09
> **stonecoldjha said:**
> i waited to see my good old gdm,that did not show up,but it was that **messages**.how do i fix this?

What messages? How are we supposed to know what those messages are if you do not tell us?

I suspect your issue is related to hotplugging. Many solutions on the arch forums as mentioned by someone above.

[http://wiki.archlinux.org/index.php/Xorg_input_hotplugging#I_don.27t_want_this_crap.2C_how_do_I_turn_it_off.3F]("http://wiki.archlinux.org/index.php/Xorg_input_hotplugging")

---

### Post by crimesaucer on 2009-02-09
> **stonecoldjha said:**
> Hi,i have run myself into a real big trouble by pacman -Syu.the update successfully completed,but after i rebooted,X did not start,saying that it was not set up.i waited to see my good old gdm,that did not show up,but it was that messages.how do i fix this?

What graphics card are you using.

---

### Post by stonecoldjha on 2009-02-11
thank you all for replying.i finally got it working,by setting it up from scratch.

---

### Post by handy on 2009-02-11
There are some things we just don't say out loud. :-|

---

