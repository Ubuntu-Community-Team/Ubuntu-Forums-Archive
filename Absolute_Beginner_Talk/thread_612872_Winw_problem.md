---
title: "Winw problem"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by BusDriverBloke on 2007-11-14
I've got a problem with Wine. I set it upto use it's own window at a resolution of 600 x 480. I started a program and found out that 600 x 480 wasn't big enough. So i went onto configuration and that too came up in the 600 x 480 window. I can change the details in the fields but can't click the OK button at the bottom as it appears offscreen and i can't move the window back up. I've tried uninstalling wine and reinstalling it but the same thing happens. i knew i shouldnt have changed it. :(

Just noticed also i typed winw instead of wine. Must go to bed.

---

### Post by smartbei on 2007-11-14
You need to purge wine, and only then re-install it. That way, all the configuration files are deleted re-installed as well. Try:

```

sudo aptitude purge wine
sudo aptitude install wine

```

There might be a one-liner to do the same thing but I am not next to my Ubuntu PC right now so that is the best I can do :).

---

### Post by lakris61 on 2007-11-14
Maybe You can TAB down to the Entry? Even if You don't see but at least guess a few times? Or if You see the system menu (usually the upper left corner of the application window, an icon or minus sign, or try pressing Alt-SPACE) then chose Move and move it up with the key cursors...

 just an idea.

---

### Post by BusDriverBloke on 2007-11-14
Thanks for that. I'd have neve thought of the tab key. It works fine now.

---

