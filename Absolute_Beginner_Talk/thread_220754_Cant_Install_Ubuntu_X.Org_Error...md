---
title: "Cant Install Ubuntu X.Org Error.."
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by SWR on 2006-07-22
Ok, Ubuntu Live CD is loading, then all of te sudden, it goes to this odd message. 
[IMG]http://img221.imageshack.us/img221/3540/dsc00255jz1.jpg[/IMG]
Anyway to work around this?
Um, my specs are:
P4, 2.6Ghz
512Mb Ram

---

### Post by professor_chaos on 2006-07-22
try saying no to that screen and then
pressing 
```
ctrl+alt+f2
```
then login
then
```
sudo dpkg-reconfigure xserver-xorg
```

reconfigure X and then what happens?

---

### Post by GuitarHero on 2006-07-22
What video card do you have, I would try installing it without the video card in it(if you have one).  Then install the drivers for your card and try it again.

---

### Post by SWR on 2006-07-22
OK, I said no to the screen, then it just went to a prompt saying:

ubuntu@ubuntu:~$:

and it wants me to type something?

Note: I cant log in because ubuntu isnt installed yet...

---

### Post by GuitarHero on 2006-07-22
That prompt is where you try sudo dpkg-reconfigure xserver-xorg

If you just want to install ubuntu, try the alternate installer from ubuntu.com

If you're just looking to try it without an install live cd is the only option.  I would try it sans-video card

---

### Post by SWR on 2006-07-22
Ok, it wants me to select the desired x server driver...what should I choose?

Edit: My video card is some weird off-brand MadCatz 64Mb thing, I had to buy it because My comp fell over once, and my moniter plugin was ripped out.

So, I dont see MadCatz on the list of Chipset manufacturers, what one would you choose? :-k

Edit: So, if I just used the alternate CD, I wouldn't have to deal with the X server stuff?

---

### Post by SWR on 2006-07-22
Ok, I configured a driver, I dont know if it works...how to I continue the installation through the live cd?

---

### Post by SWR on 2006-07-22
Bump..

---

