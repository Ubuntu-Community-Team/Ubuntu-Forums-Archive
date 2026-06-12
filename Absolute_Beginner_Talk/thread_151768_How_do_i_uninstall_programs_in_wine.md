---
title: "How do i uninstall programs in wine?"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by wolfee on 2006-03-28
I installed esword and can't install add ons so I want to uninstall it but I can't find wine on applications menue. do I run winecfg in terminal?

---

### Post by Pragmatist on 2006-03-28
Wine has a program called **uninstaller **Try typing this in a terminal:
```
uninstaller
```
If that doesn't work, you'll want to do a search for the software and install it.  Then you can use uninstaller in the future.  I tried finding the place to download, but Wine's website is really bad.  If you still can't find it, I'll check again.  Let us know what happens.

---

### Post by wolfee on 2006-03-28
Thanx! uninstaller ran!! I still say a visual version of wine like it runs in mandrake 10.2 limited addition would be easier!!!!!

---

### Post by Pragmatist on 2006-03-28
I don't use Wine, but in synaptic I see there is a package called **xwine**
Go into synaptic by typing this in a terminal (or find it in the menus):
```
sudo synaptic
```
then do a search using the keyword **xwine**
If it isn't installed, check the box, hit apply and when synaptic is all done, open a terminal and type **xwine**  If you like that, you can make a menu entry for it by typing **smeg** in a terminal and then using the GUI app to edit the menus.

---

### Post by YokoZar on 2006-03-28
[QUOTE=Pragmatist]I don't use Wine, but in synaptic I see there is a package called **xwine**
Go into synaptic by typing this in a terminal (or find it in the menus):
```
sudo synaptic
```
then do a search using the keyword **xwine**
If it isn't installed, check the box, hit apply and when synaptic is all done, open a terminal and type **xwine**  If you like that, you can make a menu entry for it by typing **smeg** in a terminal and then using the GUI app to edit the menus.[/QUOTE]
Do not use xwine, it will not work with anything.

xwine was a *very* early version of winesetup which was obsoleted by what's included with Wine over 2 years ago.  By all means it should be removed from the repository, but Ubuntu policy is not to do so once the release is made.

---

