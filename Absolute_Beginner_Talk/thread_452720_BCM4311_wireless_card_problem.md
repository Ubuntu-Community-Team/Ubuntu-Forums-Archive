---
title: "BCM4311 wireless card problem"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by mongooseman1128 on 2007-05-23
I've tried getting my wireless card up and running using the ndiswrapper method. That did not appear to work at all. I also tried using the tutorial at [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty)
I have done this and when fwcutter installs I've tried both using the program to fetch the firmware and not to. then, I use the ```
sudo /usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.s
```h scriptn this the LED that indicates my wireless card is on will turn blue for a few minutes then turn back to orange. also, I have tried using the .sys file that's on my computer, unfortunately it's bcmwl6 instead of bcmwl5 and when I try to use it I get an error that the md5 checksum is not recognized (I assume this is because this file is not yet supported by fwcutter. Should I possibly try using one of the bcmwl5 files that the zless command? is there another method that is known to work with bcm4311?

---

### Post by manishk on 2007-05-23
I have the same card on a HP laptop...I followed the guide here [http://www.ubuntuforums.org/showthread.php?t=322761](http://www.ubuntuforums.org/showthread.php?t=322761). 

It strangely uses a Dell driver, but nevertheless it worked for me.

I have broken my system a hundred times before getting my WiFi working. May be you can give this one a try too!!

---

### Post by mongooseman1128 on 2007-05-23
actually it using a dell driver makes a bit of sense because I remember when I looked at the device manager in Ubuntu seeing somethng funny about it being Broadcom Dell corporation 4311 card (or something to that effect) thanks for the info.

---

### Post by mongooseman1128 on 2007-05-26
okay, I still can't get my wireless up and running. When I blacklist bcm43xx iwconfig no longer recognizes my device. It doesn't seem like it would make a difference but my card is in a HP dv6308nr and the windows driver for it uses a bcmwl6.inf file.  Maybe I need to download a different dell driver. I think now I'm gonna check out the dell site and try and ditch feisty and see if somehow edgy gives me better results. I won't have a chance to do this for a while so if anyone has better suggestions I am all ears.I did just open up my computer though and my card is a bcm4311kfbg I doubt this will make any difference what so ever but if it does let me know

---

