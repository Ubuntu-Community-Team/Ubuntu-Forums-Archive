---
title: "How do I hook up to my wide screen tv?"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by drakebarimore on 2007-06-06
My graphics card has vga, s-video and dvi out.  When I hook up the DVI to HDMI my tv displays a "not supported" message.

Any ideas on how to make it work?

---

### Post by Bohlio on 2007-06-06
Make sure that the resolution and refresh rate that your card is outputting is a signal that your TV can handle.

---

### Post by drakebarimore on 2007-06-06
How do I do that?

---

### Post by nonewmsgs on 2007-06-06
there are a couple differernt ways.  one is to look up the tv and look at the specs and see if you can find the horizontal sync and vertical refresh (or is that vice versa) and the resolution.  if you can find that open a terminal window and then open a terminal and type "sudo gedit /etc/X11/xorg.conf" without the quotes and correct the bad entries.

otherwise 
sudo dpkg-reconfigure -phigh xserver-xorg

and it can try to run an OK wizard to help you with it.

---

### Post by nonewmsgs on 2007-06-06
also when you run the wizard, have the text in your terminal ready to press enter ( and dont forget the line then the password) and plug in your tv.  now the wizard should come on the tv and select the most correct video driver.  and it should be straight.

---

