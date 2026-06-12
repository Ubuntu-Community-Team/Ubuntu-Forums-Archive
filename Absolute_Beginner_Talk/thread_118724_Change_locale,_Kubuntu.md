---
title: "Change locale, Kubuntu"
date: 2006-01-17
forum: Absolute Beginner Talk
---

### Post by goyan on 2006-01-17
Hi all,

When I installed the kubuntu, I chose Traditional Chinese as the default language. Very few applications supports it. So I want to change it to English. Do I have to resinstall the whole OS?

Thank you for your time.

Goyan

---

### Post by Mission 10 on 2006-01-17
sudo dpkg-reconfigure locales

Then choose english.

---

### Post by goyan on 2006-01-17
Thanks... sorted!

---

### Post by PuNGS on 2006-01-17
By the way, I choosed english, but the programs title don't support latin characters (&#225; &#233; &#237; &#243; &#250;). There's a way to fix this without changing Ubuntu's language?

Oh, and I use GNOME, not KDE.

---

### Post by jimrz on 2006-01-17
PuNGS: not absolutely certain, but think if you go to System > Preferences > Keyboard you can on the Layout tab add a Latin keyboard layout which should provide the characters you want while retaining english as the os language. It also looks like you can have both layouts set up and swicth back and forth between them. I have not tried any of this, but just looking at the options there it looks like should work.

---

### Post by PuNGS on 2006-01-17
Forget it, I just fixed. Thanks, by the way.

---

