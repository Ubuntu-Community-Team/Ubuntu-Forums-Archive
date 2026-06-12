---
title: "My wireless wont work!"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by iHentai on 2007-06-10
when i was installin ubuntu 7.04 it asked for my wireless crap and it didnt work it didnt get found how can  i resolve this?

---

### Post by jimrz on 2007-06-10
> **iHentai said:**
> when i was installin ubuntu 7.04 it asked for my wireless crap and it didnt work it didnt get found how can  i resolve this?

we will need more info in order to be able to try to help.
what wireless device are you trying to use? please give make/ model / chipset info.

you might also try searching these forums for "the model your wifi device" and see what info is already out there on how to get it working.

hang in there, most anything can be fixed but more specific information is required.

---

### Post by iHentai on 2007-06-10
um how do i find out i forgot and im very new 2 linux so how do i check on linux? but i nknow a have a nvidia one and another one but not shure

edit i ound out!

i have nvidia mcp51 ethernet controller and a broadcom coporation dell wireless 1290 wlan mini pci card?

---

### Post by iHentai on 2007-06-10
bump plz :"]

---

### Post by jimrz on 2007-06-11
> **iHentai said:**
> um how do i find out i forgot and im very new 2 linux so how do i check on linux? but i nknow a have a nvidia one and another one but not shure

edit i ound out!

i have nvidia mcp51 ethernet controller and a broadcom coporation dell wireless 1290 wlan mini pci card?

I SEARCHED FOR "BROADCOM" "1290" AND GOT ZERO RESULTS. DELETED THE "1290" FROM THE SEARCH AND IT RETURNED MANY THREADS. YOU MIGHT TRY [[COLOR="Sienna"]**_THIS_**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=297092&highlight=broadcom") LINK FOR STARTERS, IT'S FOR THE BROADCOM 1390 ON A DELL LAPTOP.

---

### Post by ugm6hr on 2007-06-12
Assuming you have now installed Ubuntu - In Terminal:

```
lspci
```
Look for the "Network Controller" to confirm which card chipset you have.

If you do indeed have a Broadcom card, you will have to search here for solutions (search for chipset ) - there are many posted in these forums for BCM43xx chipsets.

---

