---
title: "Display Backlight - Keyboard Backlight"
date: 2008-06-07
forum: Apple Hardware Users
---

### Post by cvasilak on 2008-06-07
Hi there,

I have two problems under Hardy in a Macbook Pro C2D 2nd Generation.

The first is that Ubuntu doesn't save the value of the display backlight so upon reboot it resets it to a default value. Is there any way I can programmatically set the display backlight upon boot in form of a session startup program? I tried macbook-backlight but it doesn't compile? Further I remember some time ago the gnome-power-manager application used to have some scrollbars to modify the display brightness(in AC and in Battery mode) but they don't exist now.

The second problem I have is that after login when GNOME starts up, the keyboard backlight turns on and I have to press a button in the keyboard to turn it off. Is there any way I can turn it off by using a session start up program?

Note that both brightness and keyboard backlight keys work perfectly under Hardy.

Thanks for any help,

Regards,
Christos

---

### Post by cvasilak on 2008-06-07
ok,

I have managed to solve the first problem. Get the backlight sources from

[http://mactel-linux.svn.sourceforge.net/viewvc/mactel-linux/trunk/tools/backlight/](http://mactel-linux.svn.sourceforge.net/viewvc/mactel-linux/trunk/tools/backlight/)

Both the source and the Makefile

Edit the Makefile and adjust the 

LIBS=-lpci

to

LIBS=-lpci -lz

and then run 
sudo make
sudo make install

When finishes, it will produce a backlight program stored in /usr/local/bin

That's it

a little help:

backlight: read current value
backlight value: write value [0-255]
backlight +n: increase value by n
backlight -n: decrease value by n

You can the put it in the sessions start up so that it can load upon boot

Now on to the second problem :)

Regards,
Christos

---

