---
title: "is there an alternative to air tunes on linux"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by raymond1234 on 2007-06-05
it don't have to be air tunes it would just have to be able to play my music files on my stero wirelessly from my laptop. 

Is there a product out there that does this that works with ubuntu?

---

### Post by bobbybobington on 2007-06-05
From what I could find, there are two other hardware devices that do the same thing as airTunes. The [Linksys Wireless-G Music Bridge]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1137451822026&pagename=Linksys%2FCommon%2FVisitorWrapper") , and [Logitech Wireless Music System for PC]("http://reviews.cnet.com/pc-speakers/logitech-wireless-music-system/4505-3179_7-31631888.html") are the closest alternatives and would be better as they aren't inhibited by DRM like airTunes is. From what I could find these alternatives aren't supported on linux :sad:. You may want to consider going with a simpler route with a radio transmitter system like [this one]("http://www.usr.com/products/device/p-device-product.asp?sku=USR6003"). This of course would only work realistically on a desktop and the stereos would have to be connected to a radio receiver. Hope this helps, I wish I could help you more, but this is honestly all I could dig up:(

---

### Post by dswebb on 2007-07-15
there are a few scripts that you can use to stream music to the airport express.

RAOP Play -  the actual player is not so hot, but this comes also with a PCM driver that allows you to make a alsa PCM device that should be detected by your music player.  It took me a bit of tweaking to finally get this working but it was worth it. 
[http://raop-play.sourceforge.net/](http://raop-play.sourceforge.net/)

Note: if you are using rythmbox or exaile (or any player that just uses the default alsa device) check out this thread on how to change the default alsa player.  
[http://ubuntuforums.org/showthread.php?t=432713&highlight=raop](http://ubuntuforums.org/showthread.php?t=432713&highlight=raop)

JustePort - a command line player.  Not very practical but if you search about people have managed to hack this together to stream from one of the gui players, search for FIFO and airport on google

[http://nanocrew.net/software/justeport/](http://nanocrew.net/software/justeport/)

Raop-Client - looks like someone rewrote justeport in ruby.  

[http://rubyforge.org/projects/raop/](http://rubyforge.org/projects/raop/)

If you have any questions let me know.

---

### Post by sunset_studies on 2007-09-01
> **bobbybobington said:**
> From what I could find, there are two other hardware devices that do the same thing as airTunes. The [Linksys Wireless-G Music Bridge]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1137451822026&pagename=Linksys%2FCommon%2FVisitorWrapper") , and [Logitech Wireless Music System for PC]("http://reviews.cnet.com/pc-speakers/logitech-wireless-music-system/4505-3179_7-31631888.html") are the closest alternatives and would be better as they aren't inhibited by DRM like airTunes is. From what I could find these alternatives aren't supported on linux :sad:. ...


I can confirm that the Logitech device you mention *is* supported. It worked for me out of the box (running Debian Etch here). I was pleasantly surprised :) Thanks to the kernel/driver hackers who worked on Linux support for this device, it's a beauty.

---

