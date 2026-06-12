---
title: "ubuntu to debian"
date: 2007-02-24
forum: Apple PPC Users
---

### Post by dnbkid on 2007-02-24
Is there a way to upgrade ubuntu to debian etch? Example would changing the apt sources to debian and running upgrade install etch onto my system?

---

### Post by maggot_brain on 2007-02-24
I wouldn't do that if I was you.  Some of the Etch packages are also older than the Edgy ones.  If you've got /home on a separate partition (always a VERY good idea) just install Etch over the top withouth formatting the /home partition.  You can run the following command to get a list of installed packages and save them to a file:

dpkg --get-selections > selections.txt

After you've installed Debian you can run Synaptic and then go to **File** -> ** read selections** and then ** apply ** to get the same packages install on Debian.

---

### Post by dnbkid on 2007-02-24
Thanks alot!

---

### Post by maggot_brain on 2007-02-25
I'd subscribe to the Debian PowerPC mailing list as well.  The folks over there are quite friendly and always willing to lend a hand.  Let me know how you get on.

---

### Post by Gen2ly on 2007-02-25
Etch on my iBook runs very well.  I let developers know of a couple bugs (small ones) and actually had one of them email and ask me questions!

---

### Post by dnbkid on 2007-02-26
Well I decided just to flat out install Debian. The main problem is that I cannot get sound working, which worked with Ubuntu out of the box. It does seem Debian runs a bit better though. Not sure with what I'm gonna stick with.

Thanks for all your help guys!!

Its an imac g5 Rev A in case you all are wondering

---

