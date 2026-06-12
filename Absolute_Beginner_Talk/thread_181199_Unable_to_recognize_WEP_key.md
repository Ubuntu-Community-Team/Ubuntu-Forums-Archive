---
title: "Unable to recognize WEP key"
date: 2006-05-23
forum: Absolute Beginner Talk
---

### Post by Maria_Firewire on 2006-05-23
Hello,

A couple weeks ago i finally got my Interent connection up and running, thanks to everyone's help here on the forum. However, my landlord just changed the WEP key. So i went to add a new wep key and it doesn't like the new one. it ends with '!!', whereas the old one was just letters and numbers. '!' apparently is a command of some sort in linux. so i tried entering it as:

sudo iwconfig ath0 'channel.....essid...mode.....' key blah\!\! 

but that still didn't work....although it changed the error to be something like:    cannot recognize string "blah!!"

I'm not at home but i can post more specific info tonight if that will help. 


forever newb,

Maria

---

### Post by Maria_Firewire on 2006-05-24
Hey,

well to answer my own question...just in case anyone else is as dumb as i am...:D ...it was just an ASCII/HEX discrepancy. I just needed to modify 
/etc/network/interfaces 
with the HEX version of the key...not ASCII.

Silly me! Thanks to everyone who was thinking about an answer!

Maria

---

