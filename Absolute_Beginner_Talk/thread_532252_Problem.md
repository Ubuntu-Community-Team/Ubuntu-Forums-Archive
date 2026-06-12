---
title: "Problem"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by Ozcu on 2007-08-22
I just reinstalled ubuntu, and now when i try to start it, the screen just shines some red and blue colours and then I tried to type my username and password, and I hear the login sound, but the screen just stays black.

---

### Post by PetePete on 2007-08-22
do you know what your video card make/model is? post that info here, and also post your /etc/X11/xorg.conf

someone might be able to advise you on the settings needed

---

### Post by Ozcu on 2007-08-22
ATI Radeon... was it 700? 152MB

Whats the command to see files in console?

---

### Post by jamvegan on 2007-08-22
> **Ozcu said:**
> Whats the command to see files in console?

You could use:
```
more /etc/X11/xorg.conf
```
(Space bar will page forward through the file, "b" will page backwards, Enter/Return will advance one line, and "q" will get you back to the command line.)

---

### Post by Dave54 on 2007-08-22
If you can't figure out good settings, fall back plan:```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Ozcu on 2007-08-22
Still freezes...

[http://ubuntuforums.org/showthread.php?p=2890370](http://ubuntuforums.org/showthread.php?p=2890370)

How can I edit menu.lst in recovery mode?

---

### Post by jamvegan on 2007-08-22
You can use any text editor.  If you're not already familiar with any, nano might be easiest:
```
nano /boot/grub/menu.lst
```
nano has commands listed at the bottom of the screen.  The ^ means to hold down the CTRL key while typing the letter.  The letters are all shown in upper case (for clarity, I assume) but you can type them lowercase.  So, when you've made your changes you'll type CTRL-o to write your changes, it will prompt you with the current file name and you can just hit the Enter key, then type CTRL-x to exit nano.

---

### Post by Jimmyfj on 2007-08-22
Have you tried downloading the alternate install Cd? This works just fine with ATI X700, and other ATI graphics cards

---

