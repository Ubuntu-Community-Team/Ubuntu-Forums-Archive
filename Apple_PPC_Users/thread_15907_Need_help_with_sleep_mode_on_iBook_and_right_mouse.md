---
title: "Need help with sleep mode on iBook and right mouse click"
date: 2005-02-17
forum: Apple PPC Users
---

### Post by jocknerd on 2005-02-17
I've got sleep working on my iBook except when I shut the lid, the screen stays lit.  Is there a way to make it go to sleep automatically when I close the lid?

Also, how in the heck do I right click when using the track pad?  I tried holding the ctrl key, the option key, and even the apple key, as well as many others.

---

### Post by Thomas Ferreira on 2005-02-18
Check out this article for programming a key on your keyboard to act as the right mouse click.  It worked for me using Yellowdog Linux on my Powerbook Pismo in the Window Maker UI.  Probably will work for you also.  

[http://www.linuxjournal.com/article/7012](http://www.linuxjournal.com/article/7012)

Best of luck,

Thomas

---

### Post by toojays on 2005-02-18
Ubuntu is setup by default so that F12 is right click and F11 is middle click on a mac.

---

### Post by jocknerd on 2005-02-18
Figured out the right click.  I have to hold the fn key at the bottom left and the F12 at the top right.  Aaarrrrggg!  

Still need to figure out closing the lid.

---

### Post by gruepig on 2005-02-23
You can change the keys for the middle and right mouse buttons to something else by editing /etc/sysctl.conf.  I'm using F10 and F11 on my iBook G3 (PowerBook4,3).

/etc/sysctl.conf:
  dev/mac_hid/mouse_button_emulation = 1
  dev/mac_hid/mouse_button2_keycode =68
  dev/mac_hid/mouse_button3_keycode =87

Before editing /etc/sysctl.conf, you can test keys with:
  echo 1 > /proc/sys/dev/mac_hid/mouse_button_emulation
  echo 68 > /proc/sys/dev/mac_hid/mouse_button2_keycode
  echo 87 > /proc/sys/dev/mac_hid/mouse_button3_keycode

If '68' and '87' aren't the keycodes you want, try something else.

I found the keycodes using showkey (which is part of console-tools), though there are probably better ways to do so.  (Note: If you do use showkey, you need to run it from an actual console, not a terminal window within X.)

---

