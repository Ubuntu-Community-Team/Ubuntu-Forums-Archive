---
title: "Command to randomly change wallpaper in Linux Mint 13 MATE?"
date: 2012-12-01
forum: Any Other OS
---

### Post by Rytron on 2012-12-01
Hi.

What command would randomly change the wallpaper in Linux Mint 13 MATE?

I used to use this in GNOME2 but it does not seem to work in MATE:

```
bash -c 'gconftool-2 -t str -s /desktop/gnome/background/picture_filename "$(find ~/Documents/Wallpaper -type f | shuf -n1)"'
```

and used the shortcut keys 'Win + w'.

---

### Post by zombifier25 on 2012-12-01
There's "wallch", a feature-rich wallpaper changer that supports random wallpaper from a set of images. It works on MATE, so install it and give it a try.

---

### Post by Rytron on 2012-12-01
> **zombifier25 said:**
> There's "wallch", a feature-rich wallpaper changer that supports random wallpaper from a set of images. It works on MATE, so install it and give it a try.

Thanks for the tip.

---

### Post by Rytron on 2013-07-19
This works fine:

```
bash -c 'mateconftool-2 --type string --set /desktop/mate/background/picture_filename "$(find ~/hal/Wallpaper -type f | shuf -n1)"'
```

---

