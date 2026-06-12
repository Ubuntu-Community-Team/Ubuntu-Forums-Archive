---
title: "real player gold 10"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by servolockdave on 2006-10-09
hi I wonder if anybody can help us with realplay gold10.....

we have download it vair firefox and followed the instructions from the forum  pages it all went well. However,when we go to the BBC website a popup box tells us that the speed is correct (> 2mb) and realplayer is installed! So we clicked on the ok box the it comes back with an error mesage:-

  * could not find an appropriate hxplay or realplay in the system path to use as an embedded player *

The computer is a pc and running ubuntu 6.10lts

 I would be greatfull for any help as the earache my XYL is giving me!
because of the autum/spring watch programs...  

           thanks in advance (overworked electronics engineer)

---

### Post by PPAAUULL on 2006-10-09
That is because it is looking for a plugin in FF to play the media in your FF window. All I do is download Automatix and get it to install Mplayer embeded player and that works like a charm for me.

---

### Post by wpshooter on 2006-11-25
> **PPAAUULL said:**
> That is because it is looking for a plugin in FF to play the media in your FF window. All I do is download Automatix and get it to install Mplayer embeded player and that works like a charm for me.

Is there any way to get things installed on this operating system other than using this Automatix and Easy Ubuntu (which about half of the time does not work correctly) ???

---

### Post by arochester on 2006-11-25
BBC Radio has an advice page for Linux/Unix users about Realplayer10 at [http://www.bbc.co.uk/radio/audiohelp_nix.shtml](http://www.bbc.co.uk/radio/audiohelp_nix.shtml). It might be principally for audio but it certainly works for video too.

The "secret" is "The files nphelix.so and nphelix.xpt must be in the browser's plugins directory for Opera, Firefox and Mozilla".

---

### Post by dus_10 on 2006-12-01
how do you get those files into the plugins directory?

---

### Post by mushroom on 2006-12-01
```
cp nphelix.so /usr/lib/firefox/plugins
```

and

```
cp nphelix.xpt /usr/lib/firefox/plugins
```

will put those two files in the proper directory. Firefox, Konqueror, Opera, and probably all of the other plugin-supporting browsers will be able to see them.

---

