---
title: "Which network card is active? How to switch between cards?"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by softtower on 2007-09-19
I have a laptop with two network cards: wi-fi and a regular wired ethernet. 95% of the time I am on wireless and everything works great.
But every once in a while I take my laptop to work where I hook it to the wired connection. But all ubuntu programs continue trying to connect via wireless card.

How do I "switch" ubuntu to wired connection? Right now I do it in two steps:
1. Disable wi-fi (hardware switch on my laptop)
2. Restart wireless:
        $ sudo /etc/init.d/networking restart

Is there an easier way? How does Ubuntu pick which card to use? Because it won't even try to use the regular (wired) card unless I power wireless off.

---

### Post by AliL on 2007-09-19
Have you tried using a different network program to the standard one? If not, then I reccommend [wicd]("http://wicd.sourceforge.net/").

Hope this helps

AliL

---

### Post by OffAxis on 2007-09-19
The way I understand it, the cards are brought up in the order defined by the 
**/etc/network/interfaces** file;
so if you want your wired card to register as the primary (default) card then I think all you need to do is reorder your list.

As for a slightly easier way of manually bringing the cards up or down, try
[B]ifup [card name]
ifdown [card name][/B]

The 'card name' is listed on a 
**ifconfig**
command.
Omitting the card name on either command will bring them all up or all down.

---

