---
title: "kismet issue"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by ivanko on 2008-02-06
okay im stumped. it seems like my adapter stops working after about 3 or 4 minutes. the packets per second number goes to zero in kismet and the mac addresses in airodump begin to disappear one by one.

Then when i close all the windows and open kismet again, it now lists 5 adapters for me to choose from (wifi0, ath0, ath1, ath2, kis) when before there were just 2 (wifi0, ath1).

No matter which one i choose it eventually says the same “fatal” error and closes the window itself. only way to get it working again is to reboot.

I am using a Neatgear WG511T it has an Atheros chipset

---

### Post by ubutufan on 2008-02-06
I was dealing with similar behavior in another post.

I had the same problems when Network Manager was taking care of networking. I changed to wicd and everything works brilliantly.
You may want to give it a go look at
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by sirzepp on 2008-02-06
WICD solved all my problems on my laptop as well.  It didn't work so hot on my desktop...but Network manager is working fine there.  Not sure why it didn't work well on the desktop...but on my laptop it simply ROCKS.  I love it.  I'd love to switch the desktop over as well...

---

### Post by ivanko on 2008-02-06
I forgot to mention that I am using BackTrack 2 . 
How do I add packages in backtrack2 ? Can I add this **wicd **as well ?

---

### Post by ubutufan on 2008-02-07
sorry i cannot help. i have no knowledge of BT2 and how it may or may not affect networking

---

