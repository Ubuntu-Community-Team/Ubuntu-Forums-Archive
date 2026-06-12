---
title: "Installation"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by Voyage on 2006-12-15
Hello all

I am having problems installing ubuntu. 
My pc is a amd64 3700 1gb ram, graphic card ati xt800. running a trial version of win vista ultimate. Downloaded the amd 64version of ubuntu3 times burned on 3 different machines. but i get the same error message every time :Failed to Start X Server. 
Please can anyone help before this pc goes out the window

thx Voyage

---

### Post by Bachstelze on 2006-12-15
I suggest you get an "Alternate" CD. The installer is text-based so a bit less pretty but also far less likely to fail on you.

---

### Post by PriceChild on 2006-12-15
Press ctrl+alt+F1

log in with the credentials you provided on the instillation.

Type:```
sudo dpkg-reconfigure -phigh xserver-xorg
```then```
sudo /etc/init.d/gdm restart
```If this doesn't work, then repeat the process, but instead of "sudo dpkg-reconfigure -phigh xserver-xorg", type```
sudo dpkg-reconfigure xserver-xorg
```Go throught he options accepting the default. When requested, choose the "vesa" driver instead of "radeon" etc.
```
sudo /etc/init.d/gdm restart
```And you "should" get the log in screen where it'll be easier for you to graphically change your configuration.

Tell us how it goes :)

---

### Post by Voyage on 2006-12-16
tried the above but still no luck get the message graphic FAIL guess it's back to XP for me

Many thanks

---

### Post by xpod on 2006-12-16
:confused: 
Did you give up on XP as easily those first days and weeks with it when you would`nt have known even the basics of running it?

If you are`nt willing to at least put some effort into it then mabey ubuntu is not for you after all.:-k 
I wasn`t just new to Ubuntu m8 but practically new to computers when i came here in july and if i can manage this stuff then anyone can........IF they give it just a little time & patience.

As advised already why dont you try an alternate cd installer which may find it a lot easier to install and give you something to work on.
If nothing else your "learning" about ubuntu before you`ve even got it running so surely that can only be a good thing??

Have a bit of patience pal and at least give it a decent go.These folks are all happy and willing to put their time into helping you and you will get ubu up and running if you just follow the advice im sure:D 
Good luck regardless

---

