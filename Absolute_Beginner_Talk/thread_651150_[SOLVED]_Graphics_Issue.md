---
title: "[SOLVED] Graphics Issue"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by Captain Jack on 2007-12-27
So basically, I went to boot one day and the GRUB bootloader gave me an error code 15. Well, I went ahead and booted into the Ubuntu Live CD. I formatted the hard drive then reinstalled Ubuntu. Now I am having a new problem. When I boot into Ubuntu, it will show the Ubuntu Logo, then it will the screen resolution goes off whack. I can barely make out anything that is being displayed on the screen at the login screen. I can guess where my username goes and password and I can sem- make out that I have booted into the GUI. But I can hardly navigate because the resolution is so poor. I didn't have this problem before I did the format so I am a little confused here. Please help me.

---

### Post by Cypher on 2007-12-27
if you re-formated and re-installed Ubuntu you shouldn't be having this problem..but anyway..when you're booted into the GUI, hit ALT-F1 to get back to the text console, log in if you aren't already and then type the following
```

sudo dpkg-reconfigure -phigh xserver-xorg

```

---

### Post by taurus on 2007-12-27
Press <Ctrl><Alt>F2 and log in with your username and password.  Then, reconfigure your X server again with

```
sudo dpkg-reconfigure xserver-xorg
```
Either restart your X again with <Ctrl><Alt>Backspace or reboot if you wish.

```
sudo shutdown -r now
```

---

### Post by Captain Jack on 2007-12-27
What will that do?

---

### Post by overdrank on 2007-12-27
> **Captain Jack said:**
> What will that do?

Hi and it will hopefully reconfigure your xorg and correct the display issues you described.

---

### Post by LowSky on 2007-12-27
FYI: when using the command ```
sudo dpkg-reconfigure xserver-xorg
```

if you dont know the answer then use the default choice that xorg picks. Especially for things like monitor sync rates (who the hell keeps track of that...lol)

---

### Post by chewearn on 2007-12-27
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

will give you simpler questions.

---

### Post by Captain Jack on 2007-12-28
Yay! The commands worked! My screen resolution is fixed and I can get a better resolution than before I formatted my hard drive! Thanks so much!

---

### Post by overdrank on 2007-12-28
> **Captain Jack said:**
> Yay! The commands worked! My screen resolution is fixed and I can get a better resolution than before I formatted my hard drive! Thanks so much!

Great glad to hear. and can you mark the thread as solved under thread tools :KS

---

