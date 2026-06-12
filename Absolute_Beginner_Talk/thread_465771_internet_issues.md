---
title: "internet issues"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by Odd_sam on 2007-06-06
ok i am not even 3 hr new to linux and i try connecting to the internet using a card that isnt built on to the motherboard of a dell computer (optiplex GX260) i am running linux ubuntu 6.06x86 (thats what teh case said) and i dont know how to connect to the internet using only a logon/password and phone number *is on dialup* i need a butt load of help and i (can't download the new version btw too large)

---

### Post by viciouslime on 2007-06-06
I would start here: [https://help.ubuntu.com/community/DialupModemHowto]("https://help.ubuntu.com/community/DialupModemHowto") However, it is quite likely that your modem is a winmodem in which case things might get a little complicated, or even be altogether impossible :(

EDIT: I forgot to put the link in!

---

### Post by coffeecat on 2007-06-06
I would think viciouslime is correct, but a word of explanation. A winmodem is hardly a modem at all. Most of what a modem would do is done by the CPU running a dedicated Windows driver. These drivers don't work in Linux. Some people have managed to get some winmodems working under Linux but, as viciouslime says, it's - um - complicated.

A few suggestions:

1 If that's a PCI card modem you've got there, open a terminal (Applications > Accessories > Terminal) and do:

```
sudo lspci
```Enter your password when prompted. By the way, that's an L in lspci, but enter it all as lower-case. Linux, unlike Windows, is case sensitive. You'll get a whole load of output. Look for the line that contains information about the modem. Then search on these forums to see whether anyone has got it to work.

2 If you can afford one - they're not expensive - and you have a serial port on your machine, get yourself a serial external modem. From what I've read on other forums they will all work quite easily under Linux, but you might want to search these forums for 'serial modem' and see if anyone says differently.

3 If you want to get the latest version of Ubuntu, you can request a free pressed CD. [Here is the link.]("http://www.ubuntu.com/getubuntu") Be warned though that it will take a few weeks to arrive and that the latest version of Ubuntu will almost certainly not deal with a winmodem any more than 6.06.

---

### Post by viciouslime on 2007-06-06
Sorry odd_sam, I meant to add a link to [https://help.ubuntu.com/community/DialupModemHowto]("https://help.ubuntu.com/community/DialupModemHowto") after "here" :oops:

---

### Post by Odd_sam on 2007-06-06
thanks guys ill try that but yeah i think it is a pci modem and im using like i said above a dell pc made for windows xp if you find anything else or anyone else has had these same issues or they know how to fix it please feel free to either post in this thread or email me at [email]oddsam91@gmail.com[/email]
will post new info after i try that ...

---

