---
title: "Problem with installing program"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by nite owl on 2006-12-29
While trying to install Totem-xine I got the following output:
[I]niteowl@comp:~$ sudo dpkg -i totem*
(Reading database ... 69981 files and directories currently installed.)
Preparing to replace totem-xine 1.4.1-0ubuntu4 (using totem-xine_1.4.1-0ubuntu4_i386.deb) ...Unpacking replacement totem-xine ...
dpkg: dependency problems prevent configuration of totem-xine:
 totem-xine depends on libxine-main1 (>= 1.1.1); however:
  Package libxine-main1 is not installed.
dpkg: error processing totem-xine (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 totem-xine[/I]

.......any help as to what I could do???Thanks in advance everyone:)

---

### Post by taurus on 2006-12-29
From the error message, you need to install **libxine-main1** first before you can install totem-xine!!!

---

### Post by Sef on 2006-12-29
> dpkg: dependency problems prevent configuration of totem-xine:
totem-xine depends on libxine-main1 (>= 1.1.1); however:
Package libxine-main1 is not installed.

Iibxine-main1 is not installed and needs to be.   

Open the terminal (Applications > Accessories > Terminal)

```
sudo aptitude update
```

```
sudo aptitude install libxine-main1
```

Then try installing your program again.

---

### Post by nite owl on 2006-12-29
Thanks worked perfectly

---

### Post by Sef on 2006-12-29
You're welcome.   Please post any other questions that you have.

---

