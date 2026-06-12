---
title: "Enable port 631 disable cups server"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by damianubuntu on 2006-02-20
Trying to share a printer across NFS network.
Following instructions given here:

[http://gerona.gov.ph/davidjr/?p=57](http://gerona.gov.ph/davidjr/?p=57)

which all seem to be fine, except they're not ubuntu specific.
If I edit the cupsd.conf file and uncomment the 
port 631
line, then after a cupsys restart I get:
teh cupsys server could not be contacted
(or something v.similar)
and yet surely I have to allow port 631 to share the printer???
Is this to do with the web interface being disabled and does anyone know hwat to do about it?

Thanks

---

### Post by damianubuntu on 2006-02-20
Following a lot of searching on trying to set up a printer share, and reading lots of posts from others who are equally stuck, and feeling that the general info in the wiki is not as great as some of the other stuff (it tends todefault towards samba), let me say I found this in a previous thread

[http://occy.net/printing](http://occy.net/printing)

THIS ONE WORKS!!!

thanks very much to occy

---

