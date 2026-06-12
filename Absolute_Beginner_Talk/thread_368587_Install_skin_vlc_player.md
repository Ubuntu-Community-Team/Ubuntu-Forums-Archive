---
title: "Install skin vlc player"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by Lorenz on 2007-02-23
Hi guys!

Wanted to install a skin for VLC player, it tells me to put it in the Skin2 folder.
Problem is, it this:

Error while copying to "/usr/share/vlc/skins2".
You do not have permissions to write to this folder.

How can I fix this?

Many thanks,
Lorenz

---

### Post by true_friend on 2007-02-23
gksudo nautilus /usr/share/vlc/skins2
will lead you to destination folder with root privilages but u will have to open an other window with same permissions to copy that skin then simply paste it in required folder.
Replace 'gksudo nautilus' with 'kdesu konqueror' if u are using KDE.
Cheers

---

### Post by xfile087 on 2007-06-30
> **Lorenz said:**
> Hi guys!

Wanted to install a skin for VLC player, it tells me to put it in the Skin2 folder.
Problem is, it this:

Error while copying to "/usr/share/vlc/skins2".
You do not have permissions to write to this folder.

How can I fix this?

Many thanks,
Lorenz

Or you could just install the skins to your home folder...

---

### Post by elektr10 on 2007-07-07
When we add a new skins to here:/usr/share/vlc/skins2
we have to choose this directory everytime when we want to change the skin.
Isn't there any way not to folow this directory everytime?
I mean all skins we've downloaded will be in settings->skins

---

### Post by diskotek on 2007-09-30
i have a different question about this vlc skin. when i changed the skin, it return it's default one when i re-started. anybody know this issue?

---

### Post by kerry_s on 2007-09-30
> **diskotek said:**
> i have a different question about this vlc skin. when i changed the skin, it return it's default one when i re-started. anybody know this issue?

your settings.

---

### Post by diskotek on 2007-09-30
thank you kerry_s, i've trying to do that for all day. oh my shinny vlc player :)

---

