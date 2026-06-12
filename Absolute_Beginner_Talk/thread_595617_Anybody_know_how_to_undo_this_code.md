---
title: "Anybody know how to undo this code?"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by mrukus on 2007-10-28
i was given this code from bmartin who is a great guy, he allowed us acer users to unlock our wireless cards, and ever since i installed this code, it takes about 5 or 6 tries to get kubuntu to open up...any ideas on how to undo what this string is doing?

```
mkdir -p $HOME/.kde/Autostart/
cd $HOME/.kde/Autostart/
wget http://blakecmartin.googlepages.com/wicd-tray
cat wicd-tray
chmod 755 wicd-tray
```

---

### Post by gerbman on 2007-10-28
> **mrukus said:**
> i was given this code from bmartin who is a great guy, he allowed us acer users to unlock our wireless cards, and ever since i installed this code, it takes about 5 or 6 tries to get kubuntu to open up...any ideas on how to undo what this string is doing?

```
mkdir -p $HOME/.kde/Autostart/
cd $HOME/.kde/Autostart/
wget http://blakecmartin.googlepages.com/wicd-tray
cat wicd-tray
chmod 755 wicd-tray
```Sure:```
rm $HOME/.kde/Autostart/wicd-tray
```

---

### Post by wuzzerd on 2007-10-28
```
cd $HOME/.kde/Autostart
rm wicd-tray

```
Should take out what the script installed.

---

### Post by mrukus on 2007-10-29
thanks a bunch guys

---

