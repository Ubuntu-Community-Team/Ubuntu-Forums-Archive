---
title: "wtf is cupsys?"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by colomob on 2007-12-05
am updating 7.10 and when it whent to install something called cupsys it just froze. when i turn on the comp again the welcome screen didt came out at all. what can that be and how can i fix it?

---

### Post by scrooge_74 on 2007-12-05
cupsys is your print server.

How far it went in? The login screen came out but after login you could not go pass that point?

If that is the case go to a terminal CTRL+ALT+F1 log in then type

ls -la

then rm those files that start with a dot example .dmrc

One of those files got corrupted and it will be easier on you to just wipe it log out go back to the login screen CTRL+ALT+F7 and try login again

---

### Post by colomob on 2007-12-05
i re-boot my system and i didnt update that cupsys. is that important?? am afraid..is there anything else that might work instead of that?

---

### Post by 1337455 10534 on 2007-12-05
No, unless you have more than 2 obscure printers. :) lol

---

### Post by paydaydaddy on 2007-12-05
You can always get cupsys later if you have to. You can use "add/remove" under Applications or use synaptic under "system" - "administration".

---

### Post by Beggar on 2007-12-06
same thing happened to me, just uninstall cupsys (you need to remove ubuntu-desktop) then readd it, and ubuntu-desktop.

---

