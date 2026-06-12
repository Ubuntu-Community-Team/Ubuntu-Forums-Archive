---
title: "3D accelleration on ATI Mobility 200"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by eaglestrike7339 on 2008-01-26
I have a Toshiba L25 laptop, which i just recently installed Ubuntu on it, dual booting with xp pro (also have data partition, if it matters somehow). It has an ATI Mobility 200M integrated graphics card. 

My goal is to have it compiz-fusion enabled/or look pretty somehow, preferable animated. I took a look at the Hardware post, whwre it explained how to enable 3D accelleration. ([https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html#installatidriver](https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html#installatidriver))

I tried that, and when i run "glxinfo | grep rendering", the command to find out whether it is 3d rendering or not, i get this

"matt@matt-lappy:~$ glxinfo | grep rendering
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
"

Frankly, i have no idea what to do from here. My other ubuntu computer works as a server, and has a graphics chip to match (read: nonexistant for practical purposes)
 Any help will be appreciated, and any extra info will be happily provided

Thanks, 
Matt

---

### Post by luisromangz on 2008-01-26
Try using the Restricted Driver Manager, if you are using a recent Ubuntu version. If you can't enable the drivers there, look for the driver you are currently using in the file /etc/X11/xorg.conf, section Device, and if it isn't fglrx, change it.

You can also run 

sudo aticonfig --initial 

in a terminal, and that should configure your driver properly.

---

### Post by eaglestrike7339 on 2008-01-26
ok, tried exactly what you said. 

Looked in the restricted driver manager, saw it was not enabled. (hmm, could've sworn i did that earlier); enabled it, restarted

now, i run 

matt@matt-lappy:/etc/X11$ sudo aticonfig --initial
Found fglrx primary device section
Nothing to do, terminating.
matt@matt-lappy:/etc/X11$ glxinfo | grep rendering
direct rendering: Yes

But still, when i go to system>preferences>appearance>visual effects, and try to set my preselected "none" to even normal, i get a popup error, reading:

"The Composite Extension is not available"

ok, well now i am rendering right, but i cannot even use it? How would i make the composite extension available?

Thankyou, luisromangz, for the help you have given me so far, is there anything else?

---

### Post by spitf1r3 on 2008-01-26
You have to insert this into xorg.conf:
```
Section "Extensions"
       Option  "Composite" "Enable"
 EndSection
```

---

### Post by kamasabi on 2008-01-26
I have that same cursed GPU.........if you are new (like I was, I'm a little better now), try using envy to download the newest drivers, that worked like a charm for me, the 3d acceleration runs well, but 2d blows.  Like you can actually have the cube effect, wobbly windows, etc., and they will run flawlessly, but if you try to browse around online with a lot of text or pictures, it is like a snail.  When I'm screwing around I use fusion, and then switch back to metacity when I'm browsing and stuff.

---

### Post by eaglestrike7339 on 2008-01-26
hmm, ok, when i followed 
"http://ubuntuforums.org/showpost.php?p=3530421&postcount=23"

which told me to change "Composite" to "1", and install xserver-xgl, stuff started working

Thanks to everyone who helped me out, especially luisromangz (+1), and spitf1r3, who would gave me the right answer, but i checked back after i solved it (+1 anyway)

You guys are the best, keep up the good work

who knows how long it will be until i come back again, since i am going to go all out and try out the whole compiz-fusion suite.......

Thanks again, 
Matt

---

