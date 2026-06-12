---
title: "Opening a Fat32 external disk"
date: 2009-07-07
forum: Apple Hardware Users
---

### Post by Breath! on 2009-07-07
Hello, everyone!

I'm using an iBook G3 with a PowerPC port of Hardy. Previously, I was using Dapper and I could open anything I plugged in that was Fat formated and read and write to it. Now that I've upgraded to Hardy it gives me this error: 

mount: wrong fs type, bad option, bad superblock on /dev/sda1, missing codepage or helper program or other error. In some cases useful info is found in syslog- try dmesg | tail or so 

Was does this mean, and how can I fix it?

Thanks!

---

### Post by tripolitan on 2009-07-07
Plug in your USB external HD AFTER you boot, not before. If that doesn't work, please explain the situation a little more (type of connection, /etc/fstab content, fresh install or upgrade)

---

### Post by Breath! on 2009-07-07
I have always plugged it in after boot. 

And I forgot to mention, while booting, Ubuntu tries to load hardware drivers but fails. If that has anything to to with this.

I'm running an upgrade from Dapper to Hardy and all during the upgrade I was getting Perl warnings about Locales. 

Hope that helps!

---

### Post by tripolitan on 2009-07-07
Yes indeed it does help. The upgrade did not go as planned, a fresh install (with the USB drive disconnected) is probably your best course of action, in this case.

---

### Post by Breath! on 2009-07-07
:( Is there any way I could keep my current installation? Like a driver?

---

### Post by tripolitan on 2009-07-07
Your current installation has already been damaged. If it is worth it to you to keep a damaged install, go ahead. If not, re-install, it only takes an hour.

---

### Post by Breath! on 2009-07-07
I guess I'm just stubborn... I'll keep my install. :)

And I fixed with the XFCE file manager, Thunar. 

Thanks for your help!

---

### Post by tripolitan on 2009-07-08
Fantastic, thunar and xfce are probably more suitaable for G3 than Gnome or kde anyway. Just out of curiosity, how do you find Hardy on G3 laptop, in terms of speed? what is the speed of  your G3 processor? thanks.

---

