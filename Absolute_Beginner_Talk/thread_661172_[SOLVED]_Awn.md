---
title: "[SOLVED] Awn"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by Valthinos on 2008-01-07
I tried installing AWN but I get the error: W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3E231AC7F4ECF181
W: You may want to run apt-get update to correct these problems

Could someone please tell me how to fix this problem? Or tell me step by step how to do a clean install of AWN from beginning to end please (because I think I did something wrong in the beginning anyway)?

Really appreciate all the help!

---

### Post by esodin on 2008-01-07
I used [this]("http://ubuntuforums.org/showthread.php?t=385981&highlight=avant") How-To - it worked for me.

---

### Post by mejy on 2008-01-07
What tutorial did you follow?  It's not a big problem - essentially, the package is signed which allows you to be assured of the original author, and you've failed to import the public key that's needed to verify it.  Judging from the URL, it's likely you followed [this]("http://www.ubuntugeek.com/howto-install-avant-window-navigator-awn-in-ubuntu-710-gutsy-gibbon.html#more-368") tutorial, in which case you just need to execute these commands:

```
wget http://download.tuxfamily.org/syzygy42/reacocard.asc
sudo apt-key add reacocard.asc
rm reacocard.asc
```

---

### Post by Valthinos on 2008-01-07
Thank you both! I now have AWN running!

---

