---
title: "Flash player ....."
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by mourad on 2006-07-20
I have flash player plugin for firefox installed by automatix, but when I try to open metacafe website and watch the clips it tells me that I don't have the latest version for flash player, I tried to download manually the latest version for linux from Adobe website, but it appeared to be version 7, which I already have .... How to get the latest version of flash player for firefox ????  the latest version is 9 ....
Thanks in advance ....

---

### Post by aysiu on 2006-07-20
You might have to install the Windows version of Firefox (using Wine) and then install Flash 9 from there.

---

### Post by avtolle on 2006-07-20
No version 9 for linux until 2007. There are threads on the forums discussing how unfair this is, etc. Best solution may be to run Flash 9 under Wine.

Edit: Aysiu's beat me to it with a more complete explanation.

---

### Post by OU812 on 2006-07-20
From a different thread. Try this

 Default  Re: Make websites think you are running Flash player 9?
This will make most sites think you are running version 9 in Ubuntu even if you are not.
Don't forget to copy/backup the file before editing it.

Open the file ~/.mozilla/firefox/pluginreg.dat
change
Shockwave Flash 7.0 r63:$
to
Shockwave Flash 9.0 r63:$

Hope this helps.
__________________
Malac
"Time Is Precious, Waste It Wisely"
Registered Linux User No.: 416897
Reply With Quote

john

---

