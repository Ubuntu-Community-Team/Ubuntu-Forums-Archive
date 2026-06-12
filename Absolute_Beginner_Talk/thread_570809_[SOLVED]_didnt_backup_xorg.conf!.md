---
title: "[SOLVED] didnt backup xorg.conf!"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by Nolroz on 2007-10-08
I had my computer up and running with duals and everything when I attempted to install compiz/beryl Ive had it all working before, but this time I forgot to backup my xorg.conf now it boots, the xserver crashes, but I can still login text only.

Does anyone know how to rebuild the xorg.conf from run level 3? 

I want to kick myself for doing this, I should have know better.

Thanks in advance.

---

### Post by skymera on 2007-10-08
ok ok

sudo dpkg-reconfigure -phigh xserver-xorg

try that it should work

---

### Post by om1 on 2007-10-08
yes that is a life saver command.... ive had to use it several times
easy and quick fix

---

### Post by Nolroz on 2007-10-08
Thanks for your quick response guys!  I got my baby back up and running with a little fiddling...now to get compiz working or crash trying!

---

### Post by Beggar on 2007-10-08
May not be useful now, but you would be surprised how many copies of your corg.conf file are made. I did the same thing when I installed beryl, only beryl made a copy called xorg.conf.beryl I believe. Moral of the story,


```
ls /etc/X11/xorg.conf*
```

Oh, and as always mark your thread as solved, thanks :)

---

