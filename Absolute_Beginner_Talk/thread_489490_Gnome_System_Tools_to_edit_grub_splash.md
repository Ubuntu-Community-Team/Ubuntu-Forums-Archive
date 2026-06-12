---
title: "Gnome System Tools to edit grub splash"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by gentlemanmasher on 2007-07-01
I see on the site for grubconf that it says this capability is in the Gnome system tools.

[http://grubconf.sourceforge.net/](http://grubconf.sourceforge.net/)


How can I edit the Grub splash through Gnome System Tools?  I don't see that anywhere?


Help please

---

### Post by orb9220 on 2007-07-01
> How can I edit the Grub splash through Gnome System Tools? 

I believe GrubConf added that before being retired. and Gnome Sytem Tools does not have that.
When they recommend you to switch to other it doesn't mean it has all the features of the old one.

To switch grub artwork I use:

[B]sudo update-alternatives --config usplash-artwork.so
[/B]

Which allows me to switch to other already installed usplash.
Then to save the changes I:

> sudo dpkg-reconfigure usplash


Hope this helps and I am wrong about Gnome System tools.

---

