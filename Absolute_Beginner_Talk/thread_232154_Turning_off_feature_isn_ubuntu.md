---
title: "Turning off feature isn ubuntu"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by smile-its-smiley on 2006-08-08
Is it possible to turn off feature like bluetooth and wireless, as i'll never need to use them and my laptop doesn't have it inany case.

---

### Post by moma on 2006-08-08
Yes it is.

Install BUM (Bootup and Service Manager)
[http://www.marzocca.net/linux/bum.html]("http://www.marzocca.net/linux/bum.html")

$ [COLOR="Green"]sudo apt-get install bum [/COLOR]

$ [COLOR="Green"]sudo bum[/COLOR]
Select the Advanced option and choose [Services] tab-page.
Shutdown unnecessary services.

---

### Post by smile-its-smiley on 2006-08-09
I was unable to install BUM.  help.

---

### Post by 3rdalbum on 2006-08-09
> **smile-its-smiley said:**
> I was unable to install BUM.  help.

Did you get an error message when you tried to install it? Do you have the Universe and Multiverse repositories enabled? Try going into "Software Properties" in the Administration menu and enabling all the repositories.

If that doesn't help, please describe exactly what happens, and post any error messages you get, and we'll do our best to help you.

---

