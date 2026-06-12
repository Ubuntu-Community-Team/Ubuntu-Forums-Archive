---
title: "Do I Need NDISWrapper?"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by Ice_Dragon on 2007-07-17
I installed Ubuntu on my system today.  I'm enjoying it so far, but I'm having some wireless problems. My wireless network shows up when I click on the network button, but I can't actually connect to it.  After I type in the WEP key, it trys to connect but is unable to.  I have a Linksys WUSB54Gv.4.  Do I need to use NDISWrapper or am I just doing something wrong?

---

### Post by tennvolsmb on 2007-07-17
well what type of wireless card are you using? what type of computer do you have... you have to be more specific

---

### Post by Ice_Dragon on 2007-07-17
I'm using a Linksys WUSB54G v.4 and I'm running Ubuntu 7.04 i386. I just want to know if the card is working right and if I need NDISWrapper or not.  I can see the network but not connect to it.

---

### Post by tennvolsmb on 2007-07-17
in the terminal type in
```
sudo lshw -C
```

and paste what it says

---

### Post by phidia on 2007-07-17
This [link]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys")
shows your card working in fiesty

You may find some help [here]("https://help.ubuntu.com/community/InternetHowto")

---

### Post by iAlta on 2007-07-17
On an other note, please don't use WEP. It's easier to crack it than to type the password, seriously. Use WPA.

---

