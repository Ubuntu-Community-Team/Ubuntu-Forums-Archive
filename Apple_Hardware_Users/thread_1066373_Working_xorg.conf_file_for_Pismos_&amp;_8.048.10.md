---
title: "Working xorg.conf file for Pismos &amp; 8.04/8.10"
date: 2009-02-10
forum: Apple Hardware Users
---

### Post by SphereCat1 on 2009-02-10
Hi everybody! I recently went though some issues installing Hardy on my Pismo, specifically with the screen displaying half-size. I fixed it by extracting the xorg.conf file from an Edgy live cd and replacing the one in Hardy with it. I've attached the working file so future users can fix it quickly.

All you have to do is remove the .txt part of the file name and move it into /etc/X11, replacing the existing xorg.conf. I also deleted everything else that said xorg.conf for good measure, including the one marked failsafe.

Good Luck! :)
SphereCat1

---

