---
title: "Upgrading Ubuntu?"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by joshdudeha on 2008-03-08
In April when Hardy comes out, when I want to upgrade 7.10, I type that command (forgot it atm) that upgrades my release.

What is the procedure of the download?
Are my files still intact, such as my home folder and my firmware to connect my adsl?
Or are they completely wiped?
I just want to know.Thanks

---

### Post by PriceChild on 2008-03-08
When Hardy is released, you will be able to find an upgrade howto on [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

Basically the same as [https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)

It will update all your programs, but leave your entire /home directory intact. This includes all your user settings.

---

### Post by tangibleorange on 2008-03-08
As far as I know, all the upgrade tool does is update your sources.apt file so that you get the newest software. It will keep all your files and settings.

I prefer my installs clean however. I find my computer gets clogged and it does it good to have a clean install every 6 months.

I think the update tool is pretty good with complex setups though, and if you need lots of custom settings that you don't want to re-enter, I would recommend.

BTW, the upgrade command is:

```
sudo apt-get dist-upgrade
```

---

### Post by joshdudeha on 2008-03-08
Thanks for the help =]

---

