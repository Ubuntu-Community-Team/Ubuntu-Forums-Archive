---
title: "after update typing problems"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by franfran on 2008-01-21
hey guys

well after the update, things looked fine. but now when i type, it lags. it will be fine for a few moments, but then it lags and hangs, then most times it just finishes what im typing. but from time to time it holds a key and repeats it many times. may it be a letter or a space.

its weird, i never hhhhad the problem (see it just did it) before. any thoughts?

- frank

---

### Post by shearn89 on 2008-01-21
It may be xorg picking up your keyboard settings wrong? Backup xorg.conf (its in /etc/X11/), and run ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by franfran on 2008-01-21
i tried that and its           still broken. argh it keeps messing withh myy typing

---

### Post by OffAxis on 2008-01-21
Could be a script running in the background and stealing all your cpu cycles.

Try running the 'System Monitor' or htop (you'll probably need to install it)

```
sudo apt-get install htop
```

---

### Post by chinasteve2000 on 2008-04-21
Howdy!

I have similar keyboard problems, usually program-specific (Firefox, Thunderbird, OpenOffice and Skype), and I'm considering the suggestion of using what was suggested above to fix it:

sudo dpkg-reconfigure xserver-xorg

Sometimes the problem is that I can't type at all, and sometimes typing slows to a crawl (only in Skype). 

I have not been able to back up /etc/X11/ yet because I don't have permissions. 

Could someone help me along these issues? Thanks!

-Steve

---

