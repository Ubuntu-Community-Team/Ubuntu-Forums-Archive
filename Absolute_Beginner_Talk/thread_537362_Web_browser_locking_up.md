---
title: "Web browser locking up"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by Parkinsons on 2007-08-28
As of today my web browsers firefox and epiphany lock up when I go to some sites. One site is amazon.com, I go to it and the load bar said it is about 3/4 done but it looks 100% done, the site is not responsive. If I minimize the browser it will not maximize. After a while of waiting it will allow me to maximize and use the page.

This never happened to me before today.

I am running feisty 64 bit.

---

### Post by reset3x on 2007-08-28
```
sudo killall firefox-bin
```

---

### Post by Parkinsons on 2007-08-28
That does not solve my problem, it only closes all the windows.

The pages still do not load correctly/fast

---

### Post by Parkinsons on 2007-08-29
It is also not just firefox.

The page will load 75% then lock up. I can't open a new tab or even go to an old tab, it just freezes. 5 min later the browser will unfreeze then finish loading the page. This happens for 90% of the pages I load.

---

### Post by philinux on 2007-08-29
I had this with the version of firefox that comes with ubuntu. At the same time my cpu would go to 100%. I could run other stuff though.
I went for the ubuntuzilla version of firefox which has reduced the number of freezes to a mere fraction.

[http://ubuntuzilla.wiki.sourceforge.net](http://ubuntuzilla.wiki.sourceforge.net)

It leaves the ubuntu version untouched so synaptic with not complain and updates carry on as usual.

But the ubuntuzilla version gets immediate updates from mozilla.

---

### Post by Parkinsons on 2007-08-29
> **philinux said:**
> I had this with the version of firefox that comes with ubuntu. At the same time my cpu would go to 100%. I could run other stuff though.
I went for the ubuntuzilla version of firefox which has reduced the number of freezes to a mere fraction.

[http://ubuntuzilla.wiki.sourceforge.net](http://ubuntuzilla.wiki.sourceforge.net)

It leaves the ubuntu version untouched so synaptic with not complain and updates carry on as usual.

But the ubuntuzilla version gets immediate updates from mozilla.

Thank you, you are a life saver.

fixed

---

### Post by jms1989 on 2007-08-30
I need to fix firefox not replace it.

---

