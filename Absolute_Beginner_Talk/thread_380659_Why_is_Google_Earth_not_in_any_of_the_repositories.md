---
title: "Why is Google Earth not in any of the repositories?"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by willz06jw on 2007-03-09
Hey fellow Ubuntu guys/gals,

Why is Google Earth not in the Feisty "Add/Remove..." repositories?  I have all "All available applications" selected.  It should be in there even though it is commercial, right?

Thanks for your help,
Will

---

### Post by taurus on 2007-03-09
Download it from here, [http://earth.google.com/download-earth.html](http://earth.google.com/download-earth.html).

When done, open a terminal and run

Applications -> Accessories -> Terminal
```
cd ~/Desktop
chmod 755 GoogleEarthLinux.bin
./GoogleEarthLinux.bin
```

---

### Post by willz06jw on 2007-03-09
Yea I know, I have installed it already, but I am trying to spread the word about Linux and Im curious why it's not there.

Thanks again

---

### Post by Erlander on 2007-03-09
You can also install it with Automatix.

Rob

---

### Post by maniacmusician on 2007-03-09
> **willz06jw said:**
> Yea I know, I have installed it already, but I am trying to spread the word about Linux and Im curious why it's not there.

Thanks again
It's very proprietary and all that. Plus, it's likely that it's licensing is not properly documented in its source files.

I'm not sure of the exact reason, though.  Best to ask someone from MOTU (Masters of the Universe; they're the guys who package stuff and put it in the repos)

---

### Post by Kateikyoushi on 2007-03-10
Google earth is not totally open source.

---

### Post by GameGod on 2007-03-10
> **Kateikyoushi said:**
> Google earth is not totally open source.

Well, to be more precise, the issue is probably that Google Earth's license agreement doesn't allow for redistribution. That basically means you're only allowed to get it from Google themselves.

---

### Post by willz06jw on 2007-03-11
Somebody from Ubuntu should talk to them -- they at least sound like reasonable people at that company -- even if they arn't open source.

Will

---

### Post by xkocahete on 2007-09-17
It is in [Medibuntu]("http://www.medibuntu.org/").

X

---

### Post by graigsmith on 2007-09-17
google probably doesn't allow redistribution. that could be a reason it wouldn't be included in the repositories. but i dont know weather or not this is the reason, it's just a guess.

---

### Post by kostkon on 2007-09-17
It is in the [*medibuntu*]("http://medibuntu.org/") repository, as said above, although not the latest version. *Google* has its own *Ubuntu* repository and offers *Google Desktop* and *Picasa*. They have said that, in the near future, they are going to offer *Google Earth* too.

---

