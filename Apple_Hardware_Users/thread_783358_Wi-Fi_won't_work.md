---
title: "Wi-Fi won't work"
date: 2008-05-05
forum: Apple Hardware Users
---

### Post by braveryonions on 2008-05-05
I just upgraded to 8.04 from 7.10. It doesn't seem to recognize that I have a wireless card in my Mac Mini. There is no option to ad a wireless network. Any ideas?

---

### Post by tchorix on 2008-05-06
Hi there... This is not at all an expert option, just what I experience.

I have a macbook pro 1st gen and my upgrade was a completely dissaster... wireless stop working withouth even recognizing the wireless card as it happened to you. The graphics were also reduce to a minimal functionality with a very bad resolution (unchangeable) and bluetooth keyboard stop working.

After several tries of fixing the stuff, I decided to just back up my home directory (plain cp using the archive option to respect permissions)

cp -a ~myself /media/externalHD/myselfBackup

and then made a full instalation of 8.04 from the Ubuntu CD. Everything is working fine again, and even better than with 7.10... wireless, graphics and bluetooth (after removing bluetooth-utils)... so If you can't fix it, try a clean instalation.

cheers
Tchorix

---

### Post by braveryonions on 2008-05-07
Thanks, it's fixed.

---

