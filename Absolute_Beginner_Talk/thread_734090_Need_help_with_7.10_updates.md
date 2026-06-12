---
title: "Need help with 7.10 updates"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by lakelovers on 2008-03-24
I did a fresh install of 7.10, on a new hard drive. Ubuntu loaded fine but no updates were made because I didn't have an internet connection (an oversight). I now have an internet connection but the update manger says my system is up to date. Obviously it isn't. How do I get the upting process going?

---

### Post by Nano Geek on 2008-03-24
I'm in Windows right now, so I can't be absolutely sure about some names, but under **System=>Administration=>Software Sources** you have to check the repositories which were unchecked due to you not being connected to the internet during installation. 

It should work after that.

---

### Post by jken146 on 2008-03-24
Starting Update Manager (in the System -> Administration menu) should do it.  Otherwise, open up a terminal and type ```
sudo aptitude update && sudo aptitude upgrade
```

---

### Post by jken146 on 2008-03-24
> **asjdfwejqrfjcvm msz34rq33 said:**
> I'm in Windows right now, so I can't be absolutely sure about some names, but under **System=>Administration=>Software Sources** you have to check the repositories which were unchecked due to you not being connected to the internet during installation. 

It should work after that.

Yeah, that's probably it.

---

### Post by lakelovers on 2008-03-24
Thanks. . . I'm now downloading 201 packages. I left a number of the options unchecked.

---

