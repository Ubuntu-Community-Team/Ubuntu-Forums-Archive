---
title: "Ubuntu 7.10: How to REALLY install Kubuntu?"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by flameproof on 2007-10-26
I have now 7.10 installed and it really does not work for me. How to I install Kubuntu?

All the information I have seen so far is only sketchy and uncomplete..

---

### Post by stimpack on 2007-10-26
```
sudo apt-get install kubuntu-desktop
```

By mixing DE's you get a mess of menu entries which some don't like. However you will be able to see if Kubuntu works any better for you before burning a kubuntu CD.

---

### Post by TeaSwigger on 2007-10-26
> **flameproof said:**
> I have now 7.10 installed and it really does not work for me. How to I install Kubuntu?

All the information I have seen so far is only sketchy and uncomplete..

The info is very precise at [http://www.psychocats.net](http://www.psychocats.net) - copy 'n' paste-able precise. :)

---

### Post by thelocust on 2007-10-26
[COLOR=#666666]If you just went to 7.10 then I suggest you go strait kubuntu if you want to use kde exclusively. A gnome base with kde install makes for some funkyness. So I would reinstall from scratch[/COLOR]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]

---

### Post by flameproof on 2007-10-26
that sounds straight forward. Will do it as soon as I can open terminal (not so far this afternoon).

I can not do a clean install as I have some directories I want to keep.

Also, will thunderbird work? Will all my emails stay?

---

### Post by thelocust on 2007-10-26
I use thunderbird in kubuntu you might have to reinstall but you'll keep your emails.

---

### Post by flameproof on 2007-10-26
can I later chose/swap between the 2?

---

### Post by thelocust on 2007-10-26
You will be able to open read and send mail in Gnome and KDE.

---

### Post by flameproof on 2007-10-26
well, I get the blue Kubuntu logo when I startup, but then I get the normal brown Ubuntu desktop.

---

### Post by rich.bradshaw on 2007-10-26
log out, and choose KDE or Kubuntu from the sessions menu.

---

### Post by flameproof on 2007-10-26
> **rich.bradshaw said:**
> log out, and choose KDE or Kubuntu from the sessions menu.

What sessions menu? When I logout I get the blue login screen, which brings me back to Ubuntu.

---

### Post by rolnics on 2007-10-26
At the bottom left of the screen there should be an "OPTIONS" button, that will be up a menu where you can select you session . . . . KDE should be an option.

---

### Post by flameproof on 2007-10-26
> **rolnics said:**
> At the bottom left of the screen there should be an "OPTIONS" button, that will be up a menu where you can select you session . . . . KDE should be an option.

Ok, got it. It was partly out of the screen. Kubuntu looks worse to me. But that's a matter of taste.

But my main problem, that SCIM eats all avalable memory also happens in Kubuntu. So I will stick with Ubuntu and remove SCIM again. 

Anyone tried Xp? I heard that's a really smooth system. 

(just kidding)

---

### Post by flameproof on 2007-10-26
Kubuntu does not solve my problem, so how I get back to Ubuntu ?

sudo apt-get install ubuntu-desktop  ???

---

### Post by benerivo on 2007-10-26
Firstly you only want one login manager, so remove kde's with```
sudo apt-get remove kdm
```then reboot and it should take you to the standard ubuntu login (gdm). Make sure the session is set to gnome and then login. From here you are fine, but you can fully remove kde if you want to.

---

### Post by flameproof on 2007-10-26
> **benerivo said:**
> Firstly you only want one login manager, so remove kde's with```
sudo apt-get remove kdm
```then reboot and it should take you to the standard ubuntu login (gdm). Make sure the session is set to gnome and then login. From here you are fine, but you can fully remove kde if you want to.

I did sudo apt-get remove kdm - I still get on startup the blue Kubuntu logo and blue login screen.

---

