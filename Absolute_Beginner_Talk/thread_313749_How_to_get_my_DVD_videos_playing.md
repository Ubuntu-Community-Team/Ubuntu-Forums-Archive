---
title: "How to get my DVD videos playing"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by trackrat on 2006-12-06
I have tried in movie player and installed Vlc, but cannot get either to play a video DVD.
I have installed Edgy Eft, I have got everything working except for playing DVD,s.
What am I missing, what do I need to install?.

---

### Post by r4ik on 2006-12-06
Check 1.6.23 here,

[http://ubuntuguide.org/wiki/Ubuntu:Edgy](http://ubuntuguide.org/wiki/Ubuntu:Edgy)

More goodies there.

Good luck !

---

### Post by den benne on 2006-12-06
you can also use [automatix](www.getautomatix.com) to enable dvd-player capabilities

---

### Post by burek on 2006-12-06
> **trackrat said:**
> I have tried in movie player and installed Vlc, but cannot get either to play a video DVD.
I have installed Edgy Eft, I have got everything working except for playing DVD,s.
What am I missing, what do I need to install?.

for sure either with kaffeine or totem,  it should work

---

### Post by trackrat on 2006-12-06
I've really messed it up, When I try to download any packages I get this error message.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


How do I go about running this manually and how did it happen.

---

### Post by mo79 on 2006-12-06
EasyUbuntu!..I'd add a link if I remembered it. :-k

---

### Post by dvarsam on 2006-12-06
Dear "trackrat",

I personally don't like automatix solution...

All you have to do is install the package "totem-xine".

The you should be able to play your DVDs in Totem Movie Player.

Good Luck!

P.S.> Don't forget to read about the Restricted Formats.

---

### Post by trackrat on 2006-12-07
> **trackrat said:**
> I've really messed it up, When I try to download any packages I get this error message.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


How do I go about running this manually and how did it happen.

I have sorted it out, all I had to do was run

sudo dpkg --configure -a

in a terminal and it is back to downloading again now.  :D

---

