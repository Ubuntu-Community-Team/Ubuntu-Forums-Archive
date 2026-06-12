---
title: "Resolution issue"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by prestono99 on 2007-11-08
My problem is that I mistakenly selected an unsupported resolution for my monitor and now when I boot I get a black screen.  I assume it is booting ok I just can't see anything.  Is there a way I can reset my resolution from recovery mode?

---

### Post by taurus on 2007-11-08
Press <Ctrl><Alt>F2 to get into another console.  Log in with your username and password and at the prompt, reconfigure your X with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
When you are done, get back to the GUI login screen with <Alt>F7 and restart X again with <Ctrl><Alt>Backspace.

---

### Post by JohnSGruber on 2007-11-08
> **prestono99 said:**
> My problem is that I mistakenly selected an unsupported resolution for my monitor and now when I boot I get a black screen.  I assume it is booting ok I just can't see anything.  Is there a way I can reset my resolution from recovery mode?

You may be able to get another resolution to work from the black screen by pressing Control-Alt-Minus repeatedly. The minus key that works this way is the one by the keypad, not the one at the top of the keyboard. Each time you press it you should get another resolution, but this does depend on your hardware and on your xorg.conf file.

---

