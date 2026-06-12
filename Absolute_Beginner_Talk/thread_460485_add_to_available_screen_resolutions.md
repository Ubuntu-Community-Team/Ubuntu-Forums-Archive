---
title: "add to available screen resolutions"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by leesway on 2007-05-31
I'm using 6.06 lts. The only choices I have for screen resolution is 640x480 and 800x600. I used "sudo dpkg-reconfigure xserver-xorg" and added resolutions that windows says I have, but when I reboot I still only have 640x480 and 800x600. should I change the horizontal and vertical sync rates? Thanks for any help you can give me.

---

### Post by BobLand on 2007-05-31
I had this problem with my GeForce4 card.  Took me a loooong time to resolve it.  What worked was getting the correct driver from nVidia (I ran a lot of them but only one worked).

You might have to remove all of the old drivers too.  If your card is nVidia google 'remove envy' and see what they say.

Hang in there.  You will eventually find it.  When you do.  Document everything in case you have to do this again.

Good luck,
bobland

---

### Post by leesway on 2007-05-31
I'm using a laptop with S3 savage /IX 86C270-294 adaptor

---

### Post by jcconnor on 2007-05-31
What driver are you using for that adapter.  Generally, having a correct driver allows a better range of resolutions for a particular card.  Much like the other response, once I got the correct Nvidia driver loaded it recognized the entire range of resolution options.

Also, I Googled your card and found this:

[http://www.leenooks.com/S3+Savage+IX]("http://www.leenooks.com/S3+Savage+IX")

and this: (from this site - [http://www.internecik.com/?pg=howto&pg2=portege3440linux]("http://www.internecik.com/?pg=howto&pg2=portege3440linux")

SVGA S3 Savage/IX
XFree 4.2.1 support this card by "savage" module
Section "Monitor"
Identifier "TFT11"
HorizSync 30-70
VertRefresh 50-160
EndSection

Section "Device"
Identifier "S3 Savage IX MV"
Driver "savage"
EndSection

Hope this helps!

John

---

