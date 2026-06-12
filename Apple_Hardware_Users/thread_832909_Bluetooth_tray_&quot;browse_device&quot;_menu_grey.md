---
title: "Bluetooth tray &quot;browse device&quot; menu greyed"
date: 2008-06-18
forum: Apple Hardware Users
---

### Post by jokoon on 2008-06-18
My ibook g4 saw a lot of ubuntu stuff these days.
First ubuntu was installed, with bluetooth working properly, I was able to browse my phone thanks to a obex bluetooth. connexion.

It is a quite slow laptop, so I decided to install xubuntu-desktop, unfortunately the session wasn't starting well, due to a corrupt packet apparently solved by a huge apt-get command to remove gnome software (given by somebody on an irc ubuntu channel).

Since then, bluetooth tray menu is still there, I can pair my phone with my laptop (I had to re-pair it, apparently my motorola u9 was saying my laptop already had some connection setting present, I just removed the pairing and re-paired), but when I right click on the bluetooth tray icon, the "browse device is greyed ! (so I can't click on it)...

Whats wrong ? I tried remove completely everything concerning bluetooth, reinstalled packets but it still doesn't work...

Please help :( :-({|= :confused:

---

### Post by nocive on 2008-07-03
I have this exact same problem. Anyone knows a fix for this?

Xubuntu Hardy Heron 8.04
bluez-gnome 0.25-0ubuntu1

---

### Post by tors on 2008-07-15
It looks like Nautilus must be running for the "Browse Device"-option not to be greyed out.

---

### Post by robglinka on 2008-07-27
I had this same problem, and since tors pointed out that nautilus was a dependency for the "browse device" I realized that I had apt-get remvoed nautilus to save some memory.

If you would like to browse bluetooth deviced with the bluez applet, you'll have to ```
sudo apt-get install nautilus
``` and it will show up.

I'm not sure if nautilus actually has to be running, but I don't think it does, just need to have it installed.

---

