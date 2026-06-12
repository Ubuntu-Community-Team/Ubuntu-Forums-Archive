---
title: "Apple one-button mouse"
date: 2004-10-22
forum: Apple PPC Users
---

### Post by Sorin Paliga on 2004-10-22
I have had problems with configuring desktop with the standard Apple one-button mouse. I think the default settings for the ppc version should be the ones usual in MAC OS, i.e.
- ctrl-click = right button
- option = Alt
- Command = PC control
Further, command-E = eject media etc.

The workaround was to borrow a Mac-Ally two-button mouse, yet this is NOT a solution. I read somewhre in your forum(s) [even though the correct plural should be fora, not forums! ] that someone has problems with a four-button mouse. Gee! I would like to see a solution wfor the usual one-button mouse. I just like Apple one-button mice; the oldest one I have, 5 and a half years old, still works. Any idea?

---

### Post by stereo on 2004-10-23
it's not problem there's a simple hack to use F11 and F12 instead of middle and right mouse button. and the special thing about it, it's already made in ubuntu...

have fun with it, it's a bit strange but helps

bye stereo

---

### Post by schasi on 2004-10-23
Hi, i'm new to the forum and from Germany. I thought as there are more posts in the English form than there are in the German one, i could just register here.

The F12 hack would be nice if it worked. It doesn't, for me. If i press a network connection on the desktop for example, it just acts like the normal mouse button. 

Could that be because i chose "Open things with one click"? I don't have another explanation. 

Thank you

schasi

---

### Post by pyx on 2004-10-23
You could google for 'mouseemu' (IIRC) - this is a tool that makes ctrl+leftclick a rightclick..

---

### Post by Sorin Paliga on 2004-10-24
[QUOTE=stereo]it's not problem there's a simple hack to use F11 and F12 instead of middle and right mouse button. and the special thing about it, it's already made in ubuntu...

have fun with it, it's a bit strange but helps

bye stereo[/QUOTE]

It did not work for me, but I promise to try again later today. 
Is there a way to customize right-button emulation in the Control Centre (or whatsoever it may be labelled)?

I have a banal problem: right-button emulation. Otherwise, hat off, works fast and seems reliable.

---

### Post by stereo on 2004-10-25
okay folks.... here is the little hack:
to check the keycodes, use 
xev
it'll tell you the keycodes for every key on your board
afterwards editing the /etc/sysctl.conf just like mine and it works... 

so long,
stereo

ubu:~# cat /etc/sysctl.conf
#
# /etc/sysctl.conf - Configuration file for setting system variables
# See sysctl.conf (5) for information.
#
#kernel.domainname = example.com
#net/ipv4/icmp_echo_ignore_broadcasts=1

# Emulate the middle mouse button with F11 and the right with F12.
dev/mac_hid/mouse_button_emulation = 1
dev/mac_hid/mouse_button2_keycode = 87
dev/mac_hid/mouse_button3_keycode = 88

---

### Post by zoexii on 2007-02-06
the sysctl.conf file you show seems to be the default.  My file is exactly the same, yet the F11 and F12 buttons do not work, with or without the 'fn' key pressed.  I remember earlier ubuntu installs (5.10) had ctl+click=right click work out of the box...  don't break it if it ain't broken dammit!

---

