---
title: "What does the dist-upgrade command really do?"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by veli on 2006-09-24
Hi guys, the Edgy is approaching and my fingers are impatiently waiting to type the upgrade command. As a newb, I wanna know, what will the upgrade process change in my system (Ubuntu 6.06). I've applied all possible tweaks to optimize the performance: kernel 2.6.18-686, tweaked ext3, prelink, reprofiling, cut services for faster booting, XML optimization, and many others according to the famous thread. Also, I removed many applications like Evolution, OO, Gaim, Games and many other packages as well. I use Amarok 1.4 and Kaffeine, F-Spot, Star Office 8 instead of OO.

I know I'll have to reinstall ubuntu-desktop for the upgrade.

Will my system upgrade safely to Edgy in this case?

Will all these programs remain and function properly after the upgrade?

What is the mechanism of dist-upgrade? Will I get evolution, OO and the other Ubuntu regular applications, or the upgrade process will only update the packages currently installed.

Thanks for your cooperation,

---

### Post by pay on 2006-09-25
It should only upgrade the package that are installed.

---

### Post by bluefrog on 2006-09-25
with all the things you've changed I am not sure if you really want to do a dist-update.

Or you'd better do an image of your system first (using partimage for example) so that you can revert to a working state in 2 minutes.

James

---

