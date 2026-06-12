---
title: "[SOLVED] reinstall everything or easier fix? (desktop problems)"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by PGScooter on 2008-03-02
Hi,

I upgraded to xubuntu 7.10 thinking that my problems would be fixed, but they were not.

I cannot click on a window in the background, so I can only have one thing open at a time (for example, I can't have the terminal open and firefox, well I can, but I can only use the first one that I opened because that's the one that stays on top). Also, if I open something, I cannot access the menu (the top pannel, the one I go to for the applications)- I must first quit whatever I opened.

Any ideas?

Thanks

---

### Post by LuisGMarine on 2008-03-02
This might be a long shot, but try re-configuring your xserver.

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by MONODA on 2008-03-02
> This might be a long shot, but try re-configuring your xserver.

Code:
sudo dpkg-reconfigure xserver-xorg
be carefull while doing that. try going to sys->prefs->windows and messing with the settings there

---

### Post by PGScooter on 2008-03-02
thank you luisgmarine and Monoda,

I first tried to reconfigure the x-server but got intimidated by all of the questions so I abandoned that idea for the moment. I then tried to go to the windows settings and got an error message "These settings cannot work with your current window manager (unkown)" so I searched online for this error and came up with this post:
[http://ubuntuforums.org/showthread.php?p=4440982#post4440982](http://ubuntuforums.org/showthread.php?p=4440982#post4440982)
All it required was a simple
```

xfwm4 --replace

```

---

### Post by Oldsoldier2003 on 2008-03-02
> **PGScooter said:**
> thank you luisgmarine and Monoda,

I first tried to reconfigure the x-server but got intimidated by all of the questions so I abandoned that idea for the moment. I then tried to go to the windows settings and got an error message "These settings cannot work with your current window manager (unkown)" so I searched online for this error and came up with this post:
[http://ubuntuforums.org/showthread.php?p=4440982#post4440982](http://ubuntuforums.org/showthread.php?p=4440982#post4440982)
All it required was a simple
```

xfwm4 --replace

```

Glad you got it sorted :)

---

### Post by PGScooter on 2008-03-02
> **Oldsoldier2003 said:**
> Glad you got it sorted :)

Me too! haha :)

---

