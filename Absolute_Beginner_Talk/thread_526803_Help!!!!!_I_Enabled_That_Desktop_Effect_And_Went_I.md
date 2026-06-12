---
title: "Help!!!!! I Enabled That Desktop Effect And Went Into A Blank!!"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by boom2k1 on 2007-08-15
Help!!!!! I Enabled That Desktop Effect And Went Into A Blank!!

How Do I Turn It Off?? (any Keyboard Shortcuts?)

After I Reboot And As Soon As I Log In To The System, I See The Blank White Screen!

Which part of the OS is responsible for this? xorg?

---

### Post by sysikon on 2007-08-16
Don't worry. Your current hardware doesn't support it. Trust me, took me awhile to figure out.

Go into Add/Remove and search for your graphics card.

For example, I have a nVidia. 
Search: nvidia
Results: nVidia X.org Driver.

Try it.

Edit: Or tell me what graphics card you have.

---

### Post by ricardoec on 2007-08-16
Idid not post this but if you can understand, please read that he has the screen BLANK !!!! How can he go to do an ADD/REMOVE??

Things to try:

1) Boot in Debug Mode
2) cgo to /etc/X11
3) return to your original xorg.co

Hope you are in look otherwise reinstall.

---

### Post by shanix on 2007-08-16
sudo apt-get remove compiz-core

---

### Post by Mazza558 on 2007-08-16
Oh, and it's Ctrl + Alt + F1 (OR F2) to get to terminal.

---

