---
title: "Running Gutsy kernel on Feisty can fix suspend"
date: 2007-07-01
forum: Apple Intel Users
---

### Post by thully on 2007-07-01
After experiencing the unstableness of Gutsy for a while, I decided to reinstall Feisty (while saving space for testing Gutsy or any other OS - I liked testing it, but I wanted a stable Linux around...).  However, my MacBook won't suspend at all in Feisty, but will in Gutsy (though the userland support for this is currently broken).  I had heard some talking about running the Gutsy kernel in Feisty, and tried it.  

The verdict - as of the moment, Gutsy's kernel works fine in Feisty, and allows my MacBook to suspend.  It also lets you have all of the other 2.6.22 improvements, and may make madwifi work on new MacBooks (I have a first generation, so can't test that).  If you have a MacBook (or MacBook Pro) which won't suspend running Feisty, you may want to give this a try.  Just be forewarned that it could still break - though much less probable than running all-gutsy.

---

### Post by darkmaster on 2007-07-01
> **thully said:**
> After experiencing the unstableness of Gutsy for a while, I decided to reinstall Feisty (while saving space for testing Gutsy or any other OS - I liked testing it, but I wanted a stable Linux around...).  However, my MacBook won't suspend at all in Feisty, but will in Gutsy (though the userland support for this is currently broken).  I had heard some talking about running the Gutsy kernel in Feisty, and tried it.  

The verdict - as of the moment, Gutsy's kernel works fine in Feisty, and allows my MacBook to suspend.  It also lets you have all of the other 2.6.22 improvements, and may make madwifi work on new MacBooks (I have a first generation, so can't test that).  If you have a MacBook (or MacBook Pro) which won't suspend running Feisty, you may want to give this a try.  Just be forewarned that it could still break - though much less probable than running all-gutsy.

Can you suggest a simple and easy way to install the latest kernel in gutsy without having to upgrade to gutsy? A repository or something, or a deb.

---

### Post by kzm. on 2007-07-01
@darkmaster: take a look at thread [432335]("http://ubuntuforums.org/showthread.php?t=432335&page=3") for the gutsy kernel.

@thully: i run feisty 64bit so far and i am curious about your side note that wifi works better with the gutsy kernels for the macbook c2d. dos this apply for 64bit as well? where do you have this information from, if its not first hand?

---

### Post by thonuz on 2007-07-01
I can confirm suspend works fine here on gutsy with macbook core 2 duo 64 bit version. Also wireless is better but I did a full gutsy install and have had it break a few times. Desktop effects will break wireless and power management currently. Magically if you disable them the wireless and battery applets pop back. I disable desktop effects before reboot and no problem. I like the new window slider effect ubuntu has set. less heat too.

---

