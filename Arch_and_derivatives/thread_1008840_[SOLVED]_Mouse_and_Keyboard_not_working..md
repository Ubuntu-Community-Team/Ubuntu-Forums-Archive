---
title: "[SOLVED] Mouse and Keyboard not working."
date: 2008-12-11
forum: Arch and derivatives
---

### Post by Newuser1111 on 2008-12-11
EDIT:
I think I got it working.
Now the keyboard and mouse work but the mouse is stuck to the top of the screen and moves very fast.

---

### Post by hrod beraht on 2008-12-12
If you haven't already read it, make sure you check out the new xorg paradigm by reading the [[COLOR="Blue"]xorg input hotplugging[/COLOR]]("http://wiki.archlinux.org/index.php/Xorg_input_hotplugging") wiki article.

Bob

---

### Post by billgoldberg on 2008-12-12
> **Newuser1111 said:**
> EDIT:
I think I got it working.
Now the keyboard and mouse work but the mouse is stuck to the top of the screen and moves very fast.

I had a similar issue when setting up Arch, for me Xorg was to blame.

Make sure you don't boot into a gui, maybe choose the second setting in the Arch Grub screen and using your root account and nano, edit /etc/X11/xorg.conf and add this line under the "ServerLayout" option.

Option "AllowEmptyInput" "false"

This did the trick for me, hope it works for you.

---

### Post by Newuser1111 on 2008-12-12
I forgot to say that I fixed the problem before any of you replied.
(I was using the wrong driver for the mouse.)

---

