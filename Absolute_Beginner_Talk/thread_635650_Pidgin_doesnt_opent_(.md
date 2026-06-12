---
title: "Pidgin doesnt opent :("
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by webmiester on 2007-12-08
Hi guys,

Ive recently installed Gutsy Gibbon and everything has been working fine.

Today though, my pidgin doest open :(

When I select it, the bar in the bottom shows up "Loading Pidgim..."  then simply disappears after sometime almost like as if it forgot what it had to do :(

Does anyone have any idea what's wrong with it?

Thanks aplenty!

---

### Post by lamalex on 2007-12-08
try running it from the command line, and watch the output. It might give hints.
Open a terminal and type ```
pidgin
``` and hit enter. If you want, paste the output here and we'll try and find what's wrong.

---

### Post by webmiester on 2007-12-09
Nothing happened :(

webmiester@mobile-one-linux:~$ pidgin
webmiester@mobile-one-linux:~$

---

### Post by Tux.Ice on 2007-12-09
that is so wierd try going

<code>
sudo pidgin
</code>
might help

---

### Post by Tux.Ice on 2007-12-09
that is so wierd try going


```
sudo pidgin
```

might help

---

### Post by webmiester on 2007-12-09
Hey, I finally got it working!

Using the terminal, I tried activating it using:

sudo pidgin

Then it loaded!  After configuring it, it told me that I had logged in from another location, etc...

But then, the buddy list came up and 2 pidgin icons appeared on the upper bar :) (there used to be none)

After I closed both of them, pidgin starts normally now :)

Thanks so much :)

---

### Post by meborc on 2007-12-09
this might be related to a known bug in pidgin that is now fixed (the newest version currently is 2.3.1)

---

