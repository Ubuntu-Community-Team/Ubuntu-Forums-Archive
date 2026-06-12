---
title: "[SOLVED] layout,  loginwindow"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by (((X))) on 2008-01-18
Hard to login  ubuntu, I type my password, but I see different letters, other than my password.
for example; - becomes /
                        ` becomes @

So, I want to make it normal again.

---

### Post by celticbhoy on 2008-01-18
I am guessing by your description that the language code is not set right for your keyboard. This is a common fault under windows in the UK, and your problem sounds similar

---

### Post by jd65pl on 2008-01-18
Note that the user defined keyboard layout (the one once you have logged in) is different to the one pre-login, you need to edit xorg.conf to fix this. I had the same problem and this fixed it.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo nano /etc/X11/xorg.conf
```

---

### Post by (((X))) on 2008-01-19
> **jd65pl said:**
> Note that the user defined keyboard layout (the one once you have logged in) is different to the one pre-login, you need to edit xorg.conf to fix this. I had the same problem and this fixed it.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo nano /etc/X11/xorg.conf
```

I noticed, When I boot to recovery partition, then type ~!@-G, but If showed me:"</G instead, so I dont think I can fix it with xorg.conf 

I tried to change "fr" to "en" in xorg.conf, but with no good result, now I get wrong character writing in openoffice and gedit too.

---

### Post by (((X))) on 2008-02-24
Help

---

### Post by (((X))) on 2008-03-14
Never mind, I fixed it.
I just did sudo dpkg-reconfigure xserver-xorg
There is an option to change keyboard-layout

---

