---
title: "Modem problem.... new to linux"
date: 2005-08-09
forum: Absolute Beginner Talk
---

### Post by biju_abraham on 2005-08-09
I have a 56 K modem and installed ubuntu recently... I created a connection using : sudo pppconfig
But I don't know how to dial.. how do I dial the connection which I created?

---

### Post by az on 2005-08-09
pon or sudo pon, depending on whether you put your user into the "dip" group.  Also, the default provider name is "provider"  If you created a connection with a different name, you will have to do
pon (name)

---

