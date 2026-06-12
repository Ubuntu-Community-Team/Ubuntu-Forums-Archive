---
title: "upgrade from 6.06 to 6.10"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by Russellvg on 2007-03-30
How would I upgrade my linux server running ubuntu 6.06 to ubuntu 6.10 without reformatting?

---

### Post by bignickel on 2007-03-30
from terminal, type

> sudo apt-get dist-upgrade

---

### Post by Russellvg on 2007-03-30
how long would it take?

---

### Post by donfolk on 2007-03-30
Do you know if this can be realistically accomplished on dial up? Thanks

---

### Post by dca on 2007-03-30
That could take a while....
 
 
Me, personally, I've never tried to upgrade.  I've heard that in the past (I'm sure it's much better now) that things can go wrong so I simply copy the data (most are b/u anyways) and use the install CD of the newer vers.  If you time it out, all the elements that need to be d/l over a phone line...  Still faster to copy data and do a fresh install and copy back...

---

### Post by Zuuswa on 2007-03-30
I believe you also have to edit your srouces.list and change every 'dapper' to 'edgy' before dist-upgrading.  Then do ```
sudo apt-get update && sudo apt-get dist-upgrade
```
You should repeat it a few times just to make sure it got everything upgraded, I know when I upgrade mine it always takes a few apt-get dist-upgrades to get it right.  And no, it is not very realistic at all to do this on a dial-up connection, I believe the download amount is in the hundreds of megs so it would take hours upon hours.

---

### Post by zvacet on 2007-03-30
Yes in few days time you will complete download.If you have dial up best way is to order it from Ubuntu.

---

