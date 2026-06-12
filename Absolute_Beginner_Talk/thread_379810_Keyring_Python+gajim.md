---
title: "Keyring: Python+gajim"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by LookTJ on 2007-03-08
[img]http://img263.imageshack.us/img263/9871/screenshotunlockkeyringie3.png[/img]

any idea how to fix it so i don't have to type the keyring whenever i start up gajim?

---

### Post by LookTJ on 2007-03-09
Does anyone else have a keyring popup everytime you open an app?

---

### Post by MattJ100 on 2007-03-12
Yes, me! Also looking for a way around it...

---

### Post by gloawu on 2008-04-25
Yep, me too! I've tried to investigate the bug a little. I just filed a bug report with my findings. So if you can, please contribute to fixing it. Have a nice weekend!
[https://bugs.launchpad.net/ubuntu/+source/gajim/+bug/221851](https://bugs.launchpad.net/ubuntu/+source/gajim/+bug/221851)

---

### Post by trevelyon on 2008-05-07
I updated [https://bugs.launchpad.net/ubuntu/+source/gajim/+bug/221851](https://bugs.launchpad.net/ubuntu/+source/gajim/+bug/221851) to show what the problem is and post a diff for /usr/share/gajim/src/common/passwords.py to get it to use login.keyring as the default.  It now opens on login without prompting for a password.  I did have to enter the password the first time to get it into the keyring.  I'm using Ubuntu Hardy.  Hope this helps,

---

