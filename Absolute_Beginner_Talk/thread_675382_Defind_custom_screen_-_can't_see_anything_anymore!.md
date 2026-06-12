---
title: "Defind custom screen - can't see anything anymore!!"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by ben22 on 2008-01-22
Hello,

the screen I am  using is SyncMasgter 206BW. After installation it assumed the default sceen, that was ok, because I could use Ubuntu.

After configuring to this screen the dispslay of the screen is a mess and nothing visible anymore.

When I previously had the problem I reinstalled Ubuntu completely but want to prevent it this time.

How do I change back to default plug and play screen?

THANKS!!!

---

### Post by chewearn on 2008-01-23
What is your graphics card?

---

### Post by mister_pink on 2008-01-23
In future, before editing an important file make a backup:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

So then you can just copy back the original file in recovery mode if things go wrong. For now you ought to be able to do:
sudo dpkg-reconfigure xserver-xorg
You don't need the sudo bit if you're in recovery mode though, since it makes you root anyway.

---

