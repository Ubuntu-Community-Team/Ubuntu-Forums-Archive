---
title: "wifi troubles"
date: 2005-11-09
forum: Absolute Beginner Talk
---

### Post by danne on 2005-11-09
hi,
when I try to activate my wifi-card (ralink chipset) my pc totaly stops responding. Sometimes I manage to activate it just by pulling the card out and back in...but when I select my ESSID he also stops responding:confused: :confused: :confused: actually...my pc just stops on random times when I try something with that card....:(.....a friend also tried the card on his ubuntu-system and everything runs smoothly:???: 
some help??

kind regards,

danne

---

### Post by janne5011 on 2005-11-09
this problem can be error in the card and not Ubuntu.. can you test the card in another PC or with windows?

---

### Post by danne on 2005-11-09
[QUOTE=janne5011]this problem can be error in the card and not Ubuntu.. can you test the card in another PC or with windows?[/QUOTE]

that is what I've tried with my friends pc....He also has ubuntu 5.10 -->card working fine and also in windows it works.

---

### Post by IYY on 2005-11-09
Maybe it's a hardware problem with the slot you try plugging the card into? An easy way to check would be to run the Ubuntu LiveCD on your PC and your friend's, and test the card on both. That way, you have two identical software configurations, and you can check if it's a hardware problem you're experiencing.

---

### Post by janne5011 on 2005-11-09
[QUOTE=IYY]Maybe it's a hardware problem with the slot you try plugging the card into? An easy way to check would be to run the Ubuntu LiveCD on your PC and your friend's, and test the card on both. That way, you have two identical software configurations, and you can check if it's a hardware problem you're experiencing.[/QUOTE]

thats a good suggestion from IYY. You can also try put in the card in the other slot most laps have 2 slots

---

### Post by danne on 2005-11-09
Hmm seems unlikely to me...We both tried the card when we just installed ubuntu. But I have an acer aspire 1800 with internal wifi...ubuntu doesn't recognize the card but is it possible that there STILL is a conflict between the two cards?

---

### Post by janne5011 on 2005-11-09
hm this is hard to help I should do this: remove the card from slot. then look in system->adminstation-->network make sure there is no card, if it is disable it.
Then install ndiswrapper for the card you want.

---

### Post by danne on 2005-11-09
[QUOTE=janne5011]hm this is hard to help I should do this: remove the card from slot. then look in system->adminstation-->network make sure there is no card, if it is disable it.
Then install ndiswrapper for the card you want.[/QUOTE]

O there's a way I can disable unremovable hardware....!;) 
I'll do that first and thn check it out again...

thx

---

