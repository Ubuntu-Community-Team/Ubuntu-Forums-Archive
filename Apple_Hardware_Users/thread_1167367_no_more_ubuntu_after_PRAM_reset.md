---
title: "no more ubuntu after PRAM reset"
date: 2009-05-22
forum: Apple Hardware Users
---

### Post by bibomacmini on 2009-05-22
Hi all.
I was experiencing some sound problem from ubuntu (last release+mac osx) on my mac mini PPC.

Being used to Mac problem i did the good-old PRAM reset (command+option+P+R)

After that I have no more linux option on restart, my macmini boot directly on mac osx.

Any suggestion about the best way to make bootstrap menu appears again?

Thanks in Advance

Bibo - Italy

---

### Post by tiresia on 2009-05-23
Press the OPT-key at bootup. Open Firmware will show you an icon with Linux on it.
Choose it to boot Linux. In linux open then a terminal and run```
sudo ybin -v
```. Restart to check that everything is working as before

---

### Post by bibomacmini on 2009-05-23
Ok, it worked perfectly Many thanks Bibo

---

