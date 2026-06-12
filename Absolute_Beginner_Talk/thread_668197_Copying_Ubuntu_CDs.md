---
title: "Copying Ubuntu CDs"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by alamjadtawfiq on 2008-01-15
I've tried to copy Ubuntu CDs that I've received three times (two times on Windows, and one on Ubuntu), but all of them didn't work, is there a special way that I have to consider?

---

### Post by Paul820 on 2008-01-15
If you use k3b there is an option under the tools menu to copy a CD or DVD. Other applications should have the same options.

---

### Post by jd65pl on 2008-01-15
[See this https://help.ubuntu.com/community/BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto")

---

### Post by bumanie on 2008-01-15
It shouldn't be any different than copying any cd. There is no encryption on the discs.
The main thing is to ensure your burn speed is slow, so as to reduce the chance of getting burning errors. Any of the ubuntu burning tools should do it such as k3b and the generic cd/dvd creator.

---

### Post by jd65pl on 2008-01-15
You could use dd to copy the disk

```
man dd
```

---

### Post by sumguy231 on 2008-01-15
> You could use dd to copy the disk
Even if DD can handle CD-Rs, that's kinda like slicing bread with a battleaxe. It should be avoided if possible.

---

### Post by zipperback on 2008-01-15
> **alamjadtawfiq said:**
> I've tried to copy Ubuntu CDs that I've received three times (two times on Windows, and one on Ubuntu), but all of them didn't work, is there a special way that I have to consider?

You can easily copy the ubuntu cd with brasero

sudo apt-get install brasero

Once it installs you just need to launch it.

Applications -> Brasero Disc Burning Application

Click the Copy Disc button

That's about as simple as it gets. :)

- zipperback

:popcorn:

---

