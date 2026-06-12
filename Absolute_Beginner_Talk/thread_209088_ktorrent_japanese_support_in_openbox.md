---
title: "ktorrent japanese support in openbox"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by hikitsu4 on 2006-07-04
what do i need to install to get japanese support in ktorrent. I dont have kde installed, im using openbox. I only got ubuntu 6.06 as a base then xfce,openbox installed.

---

### Post by stoeptegel on 2006-07-06
You can check if there's a file called ktorrent.mo in this folder:
/usr/share/locale/ja/LC_MESSAGES/

If not, you may want to download the po file [here](http://i18n.kde.org/stats/gui/stable/ja/extragear-network/index.php) (for 1.2), and first convert them to binary ktorrent.mo with
```

msgfmt -o ktorrent.mo ktorrent.po

```

before moving that file to above folder with
```

sudo mv ktorrent.mo /usr/share/locale/ja/LC_MESSAGES/ktorrent.mo

```

---

