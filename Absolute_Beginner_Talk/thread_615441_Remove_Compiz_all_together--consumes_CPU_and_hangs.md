---
title: "Remove Compiz all together--consumes CPU and hangs on my notebook"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by shuttleworthwannabe on 2007-11-17
Hi 

I have installed Compiz and it great, but i have noticed that CPU just goes up and machine heats up and shuts down suddenly.

I enjoyed it a lot, but I wish to remove everything that is Compiz on this machine. I have done this:

1. Set Visual Effects to NONE
2. Removed xserver-xgl (and rebooted)


Also I now get a screen nag after I login: something to do with keyboard setting to use either X settings or keep the Gnome settings...How to do I get rid of this nag screen? I am assuming this happened because I uninstalled the xserver-xgl

Hardware: HP compaq nw8240 notebook, ATI fireGL 500V, 128MB.

PS: I have installed compiz on my other machine, so I have nothing against compiz, just not on this machine.

Many thanks

S:(

---

### Post by gn2 on 2007-11-17
You can use this to reconfigure the Xserver: sudo dpkg-reconfigure -phigh xserver-xorg

To remove Compiz, just do a search of Synaptic and mark the offending packages for removal.

---

### Post by shuttleworthwannabe on 2007-11-17
the reconfigure command did not work; just got a blank balck screen with blinking cursor on top left; had to shutdown using power button.
What worked was to use System>Preferences>Keyboard and choose the keyboard there. Logout/login, and no nag screen.
Also uninstalled all things compiz in synaptic---machine is now behaving.
Thanks

S

---

