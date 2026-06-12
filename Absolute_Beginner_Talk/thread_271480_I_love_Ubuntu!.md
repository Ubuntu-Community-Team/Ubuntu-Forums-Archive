---
title: "I love Ubuntu!"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by Brenlae on 2006-10-04
I must say, I truely love Ubuntu! It detected my broadband connection flawlessly (can't say that for FC5), runs solidly, and apt is just so great!

The only real question I have now, is how do I install the nvidia drivers with just using
sh nvidiadrivername.run

You see, I can't find a way to kill X for more than a few seconds.

Should I just follow the Ubuntu specific guide or not?

---

### Post by jordanmthomas on 2006-10-04
To kill X, you need to stop gdm
```
sudo /etc/init.d/gdm stop
```
after you're done and want X back
```
sudo gdm
```

---

### Post by Nut on 2006-10-04
Wow, lucky.

---

### Post by djsroknrol on 2006-10-04
There are quite a few distros getting better at hardware detection these days, but this one will always be one of my favorites...it's been great for me since Breezy and Edgy should give my compy a good boost...

---

### Post by Frak on 2006-10-04
use EasyUbuntu under 3rd party on Ubuntu forums home page, it has an automatic installer that is a breeze to use, it took me only 3 clicks.

---

