---
title: "Default Ubuntu wallpaper?"
date: 2005-09-05
forum: Art &amp; Design
---

### Post by johngarrett on 2005-09-05
I'd like to know where I can get the default Ubuntu wallpaper (the swirly brown one from 5.04) in PNG format?  I can't seem to find it no matter where/how I search... so if anyone could give me a pointer on what directory to find it in, I'd really appreciate it.

Also, if anyone would like to be particularly generous and post it here, that would be wonderful.

---

### Post by parktownprawn on 2005-09-05
[QUOTE=johngarrett]I'd like to know where I can get the default Ubuntu wallpaper (the swirly brown one from 5.04) in PNG format?  I can't seem to find it no matter where/how I search... so if anyone could give me a pointer on what directory to find it in, I'd really appreciate it.

Also, if anyone would like to be particularly generous and post it here, that would be wonderful.[/QUOTE]

try

/usr/share/backgrounds/warty-final-ubuntu.png

---

### Post by ulysses768 on 2010-05-31
I had a similar problem after trying to change the background with a script.  I solved it using gconftool-2.

1. Find a desktop background in /usr/share/backgrounds/

2. Then point gconftool-2 to the jpg.  The example uses Yellowflower.jpg
 
```
gconftool-2 -t string -s /desktop/gnome/background/picture_filename /usr/share/backgrounds/Yellowflower.jpg
```

---

### Post by DrWer2 on 2010-05-31
Is this it? 

I hate how it is impossible to find old backgrounds once a new release comes out. From now on I am saving all of them.
Edit: This was one of my favorites.

---

