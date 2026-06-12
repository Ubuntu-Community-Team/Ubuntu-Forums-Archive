---
title: "Fresh Kubuntu Install-Needing Driver"
date: 2015-06-26
forum: Apple Hardware Users
---

### Post by freeman-n on 2015-06-26
Hi all,
I just installed Kubuntu 14.04 on a iMac G4 1.25.

Currently video is working but seems to be slow and not sure that I'm getting hardware acceleration. Currently showing that I'm using the nouveau driver.
Is there a Linux PPC driver from nvidia?

This is my system: [http://www.everymac.com/ultimate-mac-lookup/?search_keywords=w83522baqb7](http://www.everymac.com/ultimate-mac-lookup/?search_keywords=w83522baqb7)

Also sound is not working. I have looked everywhere I know for drivers but there doesn't seem to be any comprehensive list anywhere for PPC.

Any help is appreciated!

---

### Post by freeman-n on 2015-06-26
I guess after reading some more what I am really needing is an xorg.conf file. I really have no clue how to create one. Any help would be appreciated!

---

### Post by rican-linux on 2015-06-27
drop to console CRTL+ALT+F1 
then stop the display manager *sudo systemctl stop gdm*
then create xorg *Xorg --configure*
move the file to /etc/X11 *sudo mv new.xorg.conf /et/X11/xorg.conf*
reboot *sudo shutdown -r now*

---

