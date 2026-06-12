---
title: "Update Opera from 8.51 to 9.01"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by piniwi on 2006-09-07
I have Opera 8.51 and have downloaded the .deb-file to 9.01. But when I double click on it I get this message: 
Error: Conflicts with the installed package 'opera'

What shall I do to upgrade from 8.51 to 9.01?

/Nikolaj

---

### Post by jordanmthomas on 2006-09-07
You can do this

```
sudo apt-get remove opera
```

Then try to install it.  This *might* remove your settings, though som you may want to export them first so you can import them into the new opera.

---

### Post by piniwi on 2006-09-08
Hooray! It worked, thanks!

---

### Post by _simon_ on 2006-09-08
9.02 Build 419 is also out ;)

[http://my.opera.com/desktopteam/blog/](http://my.opera.com/desktopteam/blog/)

---

### Post by Psquared on 2006-09-09
hey, the build says its for intel - linux. I have an AMD processor. Am I going to have any trouble with 9.02 latest build?

Thanks,

---

### Post by Marsolin on 2006-09-09
> **Psquared said:**
> hey, the build says its for intel - linux. I have an AMD processor. Am I going to have any trouble with 9.02 latest build?

Thanks,

That shouldn't matter.

---

### Post by _simon_ on 2006-09-09
no it doesn't matter.

Running first build of 9.02 here without an issue.

---

