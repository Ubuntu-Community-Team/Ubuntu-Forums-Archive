---
title: "Update on Airport original and WPA"
date: 2007-09-15
forum: Apple PPC Users
---

### Post by stmiller on 2007-09-15
I was searching for info on getting WPA going on my Airport original card. This wireless card is basically an orinoco silver 802.11b card. I know that OS X 10.4 offers WPA with this card. After searching the orinoco linux driver mailing list, I saw several threads like [this one]("http://sourceforge.net/mailarchive/forum.php?thread_name=46D528F1.6040600%40tiscali.it&forum_name=orinoco-users") which confirm it is a hardware limitation of the wireless card, but could be possible to do WPA in software, which is probably what OS X does.

So, basically we are in the hands of the [wpa_supplicant]("http://hostap.epitest.fi/wpa_supplicant/") project, as they could provide a software solution for WPA to work on this card. The wpa_supplicant page does list the Hermes chipset (which the airport card uses) as WPA I compatible, so that is good news...

---

### Post by buellman on 2007-09-19
Hmmm... sounds to good to be true :-) Maybe we will see if it will work in Gutsy?
Do you know where I could download the latest tribe of Gutsy for PPC?

Greets. Buellman

---

### Post by stmiller on 2007-09-19
Update! Read [this entire thread]("http://ubuntuforums.org/showthread.php?t=304217"). Looks like it can work. There someone has made a patched version of a proprietary driver for this card. The WPA enabled driver probably can't be included for license reasons. 

Trying this out now...

---

### Post by buellman on 2007-09-21
Cool. Thanks for the link!

Greets. Buellman

---

