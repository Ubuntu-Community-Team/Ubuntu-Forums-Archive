---
title: "[SOLVED] How to set-up bluetooth printer in Gutsy???"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by azalamo99 on 2007-11-08
Well my printer worked in Feisty using bluetooth. I have tried every hci tool, cups tool and a lot of hair pulling since I upgraded to Gutsy. Everything seems to be in order. Just one little problem, nothing comes out of the printer. I get a message from the CUPS set-up that  my "backend" in bluetooth failed (or sometimes couldn't connect / or open). All these applications see my printer, know that it is a bluetooth connection, and it worked before the upgrade. Does anyone have any suggestions that haven't been posted here yet? :confused:

I am definitely not a Ubuntu guru, but I don't consider myself a newbie either. Something like this shouldn't be this hard to get working. I hope someone knows some way to get a printer working in Gutsy using bluetooth. There are a lot of "suggestions" out there and I think I have tried all of them but so far nothing has worked.

I spent almost two weeks trying to get Gutsy to work on the internet connection only to find it wasn't Gutsy at all, Firefox decided to look at IPv6 first instead of IPv4. Who knew? This all should be simpler by now! [http://ubuntuforums.org/images/smilies/eusa_boohoo.gif](http://ubuntuforums.org/images/smilies/eusa_boohoo.gif)

Enough of the ranting! It is free software and you get what you pay for.

azalamo99

---

### Post by azalamo99 on 2007-11-09
Ok I finally found something that worked:

[https://bugs.edge.launchpad.net/ubuntu/+source/cupsys/+bug/152537](https://bugs.edge.launchpad.net/ubuntu/+source/cupsys/+bug/152537)

Hope this will help others.

---

