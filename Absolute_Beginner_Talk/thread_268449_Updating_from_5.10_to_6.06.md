---
title: "Updating from 5.10 to 6.06?"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by hyper_ch on 2006-09-30
Hiya

A friend of mine wants to install k/ubuntu but for some reason the live cd with 6.06 doesn't work at all. He tried K/X/Ubuntu as well as FC5... neither of those worked.

Since I have an old 5.10 Ubuntu disk I would like to know whether he can upgrade that completely to 6.06?

---

### Post by bulldog on 2006-09-30
Upgrading to 6.06 could be done by replacing your repo's by the Dapper repo's.
But be aware you can run in some trouble so if you not to comfortable with Linux,I suggest a clean install.

But if you wanna try some replace the repo's [hold the old one as a backup]
and type inyour terminal, ```
sudo aptitude update
sudo aptitude dist-upgrade 
``` and see what happens.

Good Luck.

---

### Post by petri on 2006-09-30
Oh yes he can :)

[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

but there is other ways too, if your Ubuntu installer lets you down: 
[https://help.ubuntu.com/community/Installation/FromKnoppix](https://help.ubuntu.com/community/Installation/FromKnoppix)

and install from windows:
[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

---

### Post by gn2 on 2006-09-30
> **sjau said:**
> Hiya

A friend of mine wants to install k/ubuntu but for some reason the live cd with 6.06 doesn't work at all. He tried K/X/Ubuntu as well as FC5... neither of those worked.

Since I have an old 5.10 Ubuntu disk I would like to know whether he can upgrade that completely to 6.06?

Yes, it can be done, I've done it myself as a way to get 6.06 on a laptop which is maxed out at 192mb RAM.

When the 5.10 install was complete and updated, I was told by a dialogue box that a newer version is available, would I like to upgrade?
I said yes, and hey presto it upgraded to 6.06 all on it's own.

Now that's magic!

---

### Post by hyper_ch on 2006-09-30
ok, it's that simple...

I thought a dist-upgrade would eventually upgrade it to 6.10 ^^ hence I asked :)

---

