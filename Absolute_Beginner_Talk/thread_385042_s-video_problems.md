---
title: "s-video problems"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by kristiansuhl on 2007-03-15
Hello everyone!

I am interested in using a normal TV for watching movies and stuff with my laptop but I don't know how to do this. I was thinking of using an S-video out cable for the connection with the TV. Do I need to change stuff in the xorg.conf file to make this work?

I have a HP Pavilion computer called dv1263ea with an internal PCI card from Intel called "82852/855GM Integrated Graphics".

I have the Ubuntu 6.10 version.

Does anybody know a good solution to my problem?

Thanks for all your previous help also, the support here is very good! ;-)

---

### Post by Scorpuk on 2007-03-15
If you just want to display your current desktop on the TV and not do anything fancy like using the tv as a second monitor then xorg.conf shouldnt need any changes.


Just make sure of the following:

1. you connect the s-video cable to an s-video in on the tv (not a composite connector after using an adaptor). On my TV I need to select the Ext2-S (The S meaning S-video) connecting to the scart socket 2 with an adaptor

2. Switch on your computer while connected to the tv, otherwise your card may not detect anything there and not switch on the tv-out.


Also bear in mind that your TV may or may not support the resolution you have set for your current monitor. It may be best to drop down to 800 x 600 or even 640 x 480.

Hope this helps. :-)

---

### Post by kristiansuhl on 2007-03-15
Ok thanks for the tip! :-)

I wonder though - with this method I have to restart the computer when I want to use the TV. Is there a good way of turning this function on and off or will it always be on?

The reason I'm asking about this, is that in windows XP the default setting is "off" and you have to turn the clone screen function on manually in order for it to work. In Ubuntu this is done automatically when you reboot?

Thanks alot!

---

### Post by kristiansuhl on 2007-03-15
I tried restarting the computer with the cable connected and tv in the right mode - but it did not work. :-( Any other suggestions?

---

