---
title: "New video card"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by Gary Nored on 2007-10-09
I've got to change the video card in my Dapper Drake computer. So what happens if I shut down the system, change the card, and reboot? Will Ubuntu notice the difference? will the system work at all?

Maybe I have to change something before I put in the new one?

Gary

---

### Post by borris.morris on 2007-10-09
from what ive seen, it usually doesnt recognize this change and automatically update it. to do this boot it up after youve swapped cards (youll get a blue screen with some errors, ignore this). press ctrl+alt+f1 and login. then run,
"sudo dpkg-reconfigure xserver-xorg -phigh"
go through and select settings as best you can. then run, "sudo shutdown -r now". your system should be up and running.

---

### Post by bruce2000 on 2007-10-09
It may be that the x gui won't start or has the wrong resolution after you insert the new card.

In that case run this command from the terminal to reconfigure the x server:

```
sudo dpkg-reconfigure xserver-xorg
```

---

