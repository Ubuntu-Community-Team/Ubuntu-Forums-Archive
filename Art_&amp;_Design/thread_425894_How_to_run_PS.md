---
title: "How to run PS"
date: 2007-04-28
forum: Art &amp; Design
---

### Post by pisio on 2007-04-28
How I can run PhotoShop CS3 or Dreamweaver CS3?
Whit Wine or  other program?
[-o< [-o<

---

### Post by hyperair on 2007-04-28
Photoshop CS3 I have no idea how to run, it just won't work for me. I don't think there's a Dreamweaver CS3, considering the fact that Dreamweaver began as a Macromedia product and is not in Adobe's Creative Suite.

For Dreamweaver:
First install wine:
```
sudo apt-get install wine
```

Then, double click on the intsaller as you would do for Windows. It'll setup everything nicely for you including a desktop shortcut.

---

### Post by pisio on 2007-04-28
> **hyperair said:**
> Photoshop CS3 I have no idea how to run, it just won't work for me. I don't think there's a Dreamweaver CS3, considering the fact that Dreamweaver began as a Macromedia product and is not in Adobe's Creative Suite.

For Dreamweaver:
First install wine:
```
sudo apt-get install wine
```

Then, double click on the intsaller as you would do for Windows. It'll setup everything nicely for you including a desktop shortcut.

10x

---

### Post by mech7 on 2007-04-28
Dreamweaver CS 3 comes with the creative suite now.. as Adobe has bought Macromedia.. anyway the entore CS 3 suite doesn't run.. Dreamweaver 8 seems to run great though.

Photoshop 7 works the best but it is still buggy with palletes and save for web window can't be resized.. with PS CS 2 i have gotten it to run but it is very buggy and it also has the pallettes 

> **hypebug.

rair said:**
> Photoshop CS3 I have no idea how to run, it just won't work for me. I don't think there's a Dreamweaver CS3, considering the fact that Dreamweaver began as a Macromedia product and is not in Adobe's Creative Suite.

For Dreamweaver:
First install wine:
```
sudo apt-get install wine
```

Then, double click on the intsaller as you would do for Windows. It'll setup everything nicely for you including a desktop shortcut.

---

### Post by hyperair on 2007-04-28
I can't even get PS CS2 to run! How did you?

---

### Post by mech7 on 2007-04-28
> **hyperair said:**
> I can't even get PS CS2 to run! How did you?
I udated to latest WINE now 0.9.36

I got a portable version of photoshop cs 2 which you can put on a usb stick and run.. As it is impossible for me to install from setup.exe :(
Then i downloaded 2 dll files from the web found them on google first hit..

MSVCP71.DLL
msvcr71.dll

And i placed them inside the dir and then it runs.. still though with the palletes bug having to reset them everytime and having them overlay on other apps when i alt + tab it is almost unusable for me as i need to switch between apps regulary :(

In some ways CS 2 looks better though then 7 with drop down boxes it does not overlay the text :)

[[IMG]http://img243.imageshack.us/img243/268/screenshottv7.th.png[/IMG]](http://img243.imageshack.us/my.php?image=screenshottv7.png)

---

### Post by smartalecks on 2007-04-28
[SIZE="3"]Neither Photoshop CS3 or Dreamweaver CS3 have been reported to work on Ubuntu Feisty Fawn using Wine.[/SIZE]

**Photoshop CS3:**
[http://appdb.winehq.org/appview.php?iVersionId=6584](http://appdb.winehq.org/appview.php?iVersionId=6584)

**Dreamweaver CS3:**
[http://appdb.winehq.org/appview.php?iVersionId=7694](http://appdb.winehq.org/appview.php?iVersionId=7694)

[SIZE="3"]Some of the earlier versions of Photoshop and Dreamweaver do work, however.[/SIZE]

**Photoshop versions directory:** [http://appdb.winehq.org/appview.php?iAppId=17](http://appdb.winehq.org/appview.php?iAppId=17)
**Dreamweaver versions directory: **[http://appdb.winehq.org/appview.php?iAppId=183](http://appdb.winehq.org/appview.php?iAppId=183)

---

### Post by hyperair on 2007-04-28
Dang I deleted my Portable Photoshop CS2 when I found it didn't run. Now I'll have to go Virtualbox and install PS CS2 or something. X_x

---

### Post by hyperair on 2007-04-29
I just tried the portable photoshop cs2 in wine. Thanks for the tip. I also tried the portable photoshop cs3, but it failed miserably.

---

