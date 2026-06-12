---
title: "[SOLVED] Can't reenable visual effects"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by dwally89 on 2008-02-14
So I was trying to install NetBeans 6.0.1, and when I opened the installer, all I got was a grey box, so I read on the forum to disable visual effects, so I disabled them, and sure enough, it worked, and I've installed it, and its working fine.

However...

I can't reenable virtual effects now.

When I go onto System>Preferences>Control Centre>Appearance

The box appears, but doesn't react when I click on any of the buttons.

Please can someone help? :-)

---

### Post by dwally89 on 2008-02-14
Help please, I need my desktop looking nice again :-)

---

### Post by dwally89 on 2008-02-14
Managed to sort it out, turns out I had to:

```

sudo apt-get remove gtk-qt-engine

```

---

### Post by jan quark on 2008-02-14
I like this

users who solve their problems alone :)

please mark as solved
and be proud

---

