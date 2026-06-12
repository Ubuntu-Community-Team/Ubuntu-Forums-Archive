---
title: "Ubuntu/Xbuntu startup/shutdown"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by clarkth on 2006-08-03
I've installed the Xbuntu desktop to test it out, and I switch between sessions to get whichever desktop I want to use, however Ubuntu (Gnome) is the default for my userid and when I turn the computer on the Ubuntu splash screen is displayed, but when I shutdown the computer, the Xbuntu splash screen is displayed even if I didn't use the Xbuntu desktop.

Is this normal?

---

### Post by Ziox on 2006-08-03
> **clarkth said:**
> I've installed the Xbuntu desktop to test it out, and I switch between sessions to get whichever desktop I want to use, however Ubuntu (Gnome) is the default for my userid and when I turn the computer on the Ubuntu splash screen is displayed, but when I shutdown the computer, the Xbuntu splash screen is displayed even if I didn't use the Xbuntu desktop.

Is this normal?

This happens to be too.  I doubt it's a "major" problem.  You just need to probably change some file and stuff...I don't really mind it personally, because most of the time, i'm no longer infront of the computer when it goes through this :p

---

### Post by clarkth on 2006-08-03
I don't mind it either, it just wasn't expected so I just wanted to ask.

Thanks.

---

### Post by jordanmthomas on 2006-08-04
You can just reinstall usplash.

```
sudo apt-get remove usplash
sudo apt-get install ubuntu-desktop
```


This will remove xubuntu-desktop and usplash, then replace it with ubuntu's default (ubuntu-desktop shouldn't be installed any more if you installed xubuntu-desktop).  It won't get rid of anything else as xubuntu-desktop just installs a bunch of other packages to make it more convenient than selecting each one.  

Hope that makes sense.

---

