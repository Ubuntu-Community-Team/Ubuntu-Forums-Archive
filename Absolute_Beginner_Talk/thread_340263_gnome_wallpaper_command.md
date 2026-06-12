---
title: "gnome wallpaper command"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by StreetSmart on 2007-01-16
Is there a command that you can use to set your wallpaper in gnome?

---

### Post by Pobega on 2007-01-16
In Gnome can't you just right click an image in Firefox and set it as your wallpaper?

I'm not on Gnome but if I had to guess it would be Settings -> Preferences -> Desktop/Wallpaper, or something similar. Just look around that area, I know it's in there.

---

### Post by StreetSmart on 2007-01-16
Setting the wallpaper isnt the problem. But I wanted to know the command for doing it. I just want to make a simple script with that command after.

---

### Post by bvc on 2007-01-17
gconftool -s --type=string /desktop/gnome/background/picture_filename /path/to/image.ext

---

### Post by StreetSmart on 2007-01-17
thanks a lot!

---

### Post by Daniel9389 on 2007-01-17
OH um i can i find any picture and set as wallapaper and im on gnome its rel easy for me:-D

---

### Post by CameronCalver on 2007-01-17
> **Daniel9389 said:**
> OH um i can i find any picture and set as wallapaper and im on gnome its rel easy for me:-D

[B]Please Dont Spam Daniel9389 The Thread Has already been solved and dont be a smarty pants about the problem
[/B]

---

