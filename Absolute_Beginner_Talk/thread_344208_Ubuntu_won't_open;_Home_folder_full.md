---
title: "Ubuntu won't open; Home folder full?"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by PaulFXH on 2007-01-22
Hi
I have a dual boot system with WinXP and Ubuntu 6.10
While Ubuntu is my default boot option, I'm writing this from XP as I can no longer get into Ubuntu.
Today, when trying to login I found that typing my name and password just brings back the same login page over and over.
Now and again, however, an error message opens claiming that login is not possible either because my Home folder is full or because the Home folder won't open for some other reason.
It is entirely possible that the home folder has little or no spare disk space as I did have a similar warning a short while ago.
OK, so it seems the problem has been diagnosed but how do I resolve it?
As I can't get into Ubuntu and I can't access ext-3 partitions from Windows, I'm in a bit of a quandary?
Any suggestions?

---

### Post by Iarwain ben-adar on 2007-01-22
Hi there,
for login, have you tried via terminal? (Ctrl-Alt-F1)
This could work i think.

As for windows: try [this](http://www.fs-driver.org/download.html).
This nifty little program allows you to access your drives via Windows.


Iarwain

---

### Post by taurus on 2007-01-22
Boot into recovery mode from GRUB menu and at the prompt, run

```
aptitude clean
rm /root/.Trash/*
rm /home/**username**/.Trash/*
(Replace **username** with the actual name that you log in with.)
df -h
```

Now, see if you have freed up some space on / with the output of the last command.

---

### Post by PaulFXH on 2007-01-22
Thanks to everybody for the advice.
Yes, I'm back into Ubuntu after using the recovery mode to do a little clean-up.
Now that I know how to resolve this problem I can happily continue to be profligate in my use of disk-space :D 
Best wishes
Paul

---

