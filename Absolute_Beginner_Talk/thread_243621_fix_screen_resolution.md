---
title: "fix screen resolution"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by bplus on 2006-08-25
Hi,
I ve just installed dapper.
I can get my desired screen res of "1280 x 800".
I added 1280 x 800 to the xorgconf file and saved it, but still the option doesnt appear system, prefereces, screen res,

can any one help me?

Thanks in advance!

---

### Post by Kobalt on 2006-08-25
Hi,

in a terminal, run this command :
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

Make sure to select the resolutions you want avaliable with the SPACE BAR and then, restart X by pressing CTRL+ALT+BACKSPACE.

Cheers !

---

