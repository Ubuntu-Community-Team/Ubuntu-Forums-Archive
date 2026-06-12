---
title: "Ubuntu Pen Drive - Recovering my USB Pen Drive"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by KarmaticStylee on 2008-02-08
I followed [these instructions]("http://www.pendrivelinux.com/2007/09/21/usb-ubuntu-704-persistent-install/") hoping to boot ubuntu off of my pen drive but it didn't work out.

Now my usb pen drive is showing up as having only 750MB! When I booted into Ubuntu off the CD, it shows sda1 and sda2 - one is 750 and the other 250...

How do I fix this? I'm completely new to ubuntu but it seems as though it's treating it like two different pen drives.

edit: I should add that the 250mb one is showing up as casper-rw in the browser

---

### Post by talsemgeest on 2008-02-08
Boot off the live cd, then go to system>administration>partition editor and select from the list your flash disk. 
Then delete all the partitions and format the whole thing to whatever it was.

Hope this helps :)

---

