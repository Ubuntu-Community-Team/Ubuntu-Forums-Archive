---
title: "Motorola Wireless Card"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by Drifter on 2008-01-28
I have a motorola wireless card in a desktop, it is model # WPCI810G.  Will this card work with unbuntu 7.10

---

### Post by jan quark on 2008-01-28
this is the list of the supported wireless cards
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

haven't look for your card but will do it now

---

### Post by jan quark on 2008-01-28
please run 
lspci
in your terminal and search for the exact name of your card
is your card maybe a motorola card?

if yes, I think there is no linux driver for motorola cards, you have to use ndiswrapper and the native windows drivers to enable this card

---

