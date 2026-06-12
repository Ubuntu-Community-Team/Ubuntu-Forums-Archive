---
title: "Gdm broken for unknown reason"
date: 2014-07-12
forum: Any Other OS
---

### Post by gr4jp3r on 2014-07-12
Today I found out that gdm in my Debian 7.6 (Wheezy) got broken over the night. The login window changed from a grey, static one to a black with dynamic effects. After logging in I found out that none of the gnome extensions I was using are available any more. What's more, the desktop is empty and unresponsive - I can't click on it or anything. 
The day before I installed qt4 (a snippet from /var/log/apt/history.log below). It all worked great but when I saw the gdm change next morning I uninstalled all the packages. Unfortunately, that didn't bring old gdm back.
I also tried to change qtconfig settings but with no effect. I also switched to another terminal, stopped /etc/init.d/gdm3, and reinstalled gdm3 package but again, this didn't fix the situation.
I still get this new login screen, I can't use my desktop because it's unclickable and it doesn't display any of the ~/Desktop content (which is untouched btw), all gnome plugins are deactivated. 

What else can I do to get my gnome back? I'm getting pretty desperate here.

/var/log/apt/history.log snippet:
```
Start-Date: 2014-07-11  20:07:27
Install: libqt4-qt3support:amd64 (4.8.2+dfsg-11, automatic), libqt4-opengl-dev:amd64 (4.8.2+dfsg-11, automatic), libqt4-dev:amd64 (4.8.2+dfsg-11), libqtwebkit-dev:amd64 (2.2.1-5, automatic), libqt4-dev-bin:amd64 (4.8.2+dfsg-11, automatic), qt4-linguist-tools:amd64 (4.8.2+dfsg-11, automatic)
End-Date: 2014-07-11  20:07:40


Start-Date: 2014-07-11  20:11:06
Install: libqt4-core:amd64 (4.8.2+dfsg-11), libqt4-gui:amd64 (4.8.2+dfsg-11), libqt4-private-dev:amd64 (4.8.2+dfsg-11)
End-Date: 2014-07-11  20:11:12


Start-Date: 2014-07-12  10:02:18
Install: qt4-qtconfig:amd64 (4.8.2+dfsg-11), libphonon4:amd64 (4.6.0.0-3, automatic)
End-Date: 2014-07-12  10:02:44



```

---

### Post by Bucky Ball on 2014-07-12
*Thread moved to **Other OS/Distro Support**.*

---

