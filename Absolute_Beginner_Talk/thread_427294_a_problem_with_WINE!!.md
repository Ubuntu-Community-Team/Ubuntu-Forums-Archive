---
title: "a problem with WINE!!"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by ianb72 on 2007-04-29
I have installed Wine as per the Wine HQ website

It all installed great, I installed abit of windows software and messed up so I uninstalled it using the the 'uninstaller' command and tried re-installing it but I can't and even the other windows software I have installed and uninstalled are still showing up in the menu on Applications> Wine

How can I completely remove all the uninstalled software??

I have tried completely removing Wine in Synaptics but still no joy!

Cheers
Ian

---

### Post by supersonicdarky on 2007-04-29
```
sudo apt-get remove --purge wine
```

?

---

### Post by mikeyphi on 2007-04-29
This is possibly due to installation by means other than synaptic...........!!

I had a similar problem with VMplayer some time ago....you need to find every file relating to wine and remove it and then reinstall. Use the find file facility and then open a terminal and navigate to the appropriate directory and use sudo 'rm' filename on each occurrence.
A bit long-winded but it worked for me!

---

### Post by ianb72 on 2007-04-29
> **supersonicdarky said:**
> ```
sudo apt-get remove --purge wine
```

?

I've done this and although wine is no longer installed, it still appears in the Apllications drop down menu

Any ideas how I can remove it??

---

### Post by onegreenparker on 2007-05-02
Try using the Alacate Menu Editor.

---

