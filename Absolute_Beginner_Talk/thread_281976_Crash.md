---
title: "Crash"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by captk3570 on 2006-10-21
After installing Automatix2 can I still use the add remove programs in Ubuntu I had a mysterious crash which I had to manually shut down the computer and reboot after using the add remove prog any suggestions??

---

### Post by jordanmthomas on 2006-10-21
You shouldn't have any problems after using Automatix and should be able to continue using Add / Remove.

Sometimes, Automatix will overwrite your sources.list with its own and that can lead to troubles.

can you do this for me?
Applications --> Accessories --> Terminal
```
cat /etc/apt/sources.list
```
could you post the output of this?

---

### Post by arnieboy on 2006-10-21
> **jordanmthomas said:**
> Sometimes, Automatix will overwrite your sources.list with its own and that can lead to troubles.
The default AX sources.list is simply the dapper/edgy official sources.list + AX sources.list and the user's sources.list is only overwritten with the user's explicit permission. Dont see how that can create any problem.

---

### Post by jordanmthomas on 2006-10-21
I didn't know it was the default.  I wonder why it used to cause me all kinds of problems and replacing it with my own seemed to fix it.:-k   I haven't used Automatix in a long time, though and it was a godsend when I first started out.

also, I guess it wouldn't cause enough of a problem to have to reboot even if the sources.list was faulty.

---

### Post by arnieboy on 2006-10-21
> **jordanmthomas said:**
> I haven't used Automatix in a long time, though and it was a godsend when I first started out
Automatix2 is quite sophisticated in design. It is the only app in its category which lets you recover your original sources.list after a complete computer crash (if and when that happens) by just clicking on File --> Restore sources

---

### Post by cantormath on 2006-10-21
Hey arnieboy,

is automatix for edgy yet?

if so, where?

---

### Post by arnieboy on 2006-10-21
> **cantormath said:**
> Hey arnieboy,

is automatix for edgy yet?

if so, where?

[http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_on_.28K.2CX.29Ubuntu_6.10_i386_.28Edgy.29](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_on_.28K.2CX.29Ubuntu_6.10_i386_.28Edgy.29)

---

### Post by jordanmthomas on 2006-10-21
I didn't even know there was an Automatix2 yet, I might install it just for the heck of it to see how it's come along.

Cheers

---

### Post by cantormath on 2006-10-21
> **arnieboy said:**
> [http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_on_.28K.2CX.29Ubuntu_6.10_i386_.28Edgy.29](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_on_.28K.2CX.29Ubuntu_6.10_i386_.28Edgy.29)

Thanx dude, automatix rocks...

---

