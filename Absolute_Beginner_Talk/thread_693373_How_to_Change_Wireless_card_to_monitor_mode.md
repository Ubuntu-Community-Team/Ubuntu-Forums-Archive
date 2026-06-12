---
title: "How to Change Wireless card to monitor mode"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by tototime on 2008-02-10
Hello,

As I am somewhat new to Ubuntu and Linux i was wondering if anyone out there knew how to change a wireless card to monitor mode and the code in terminal to figure out what wireless card im using.  The only clue i have is that in restricted drivers the chipset was broadcom.

Thanks,
Tototime

---

### Post by Presto123 on 2008-02-11
The type of card will be displayed when you type this into the Terminal (Post the output, and we will tell you the card):

```
lspci
```

Also, if you are trying to get the card to get the drivers, just click the box to enable the card, and the pop-up screen that follows will give you a couple of options: 1 Is to use a file from the computer, other is to get from the internet. Select the internet one and it will search and grab the correct driver unless there is an error somewhere.

---

### Post by tototime on 2008-02-11
ok the name of it is  Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

---

### Post by motoxjosh17 on 2008-02-11
Hey i am trying to get my card into monitor mode but have no clue how to start i am using windows. Can anyone help?

---

### Post by jan quark on 2008-02-11
wow 
> ok the name of it is Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
you have the trickiest card ever made for ubuntu :)

try this small guide to set it up and prey that this works

[http://laiconic.quotaless.com/tutorial1.html](http://laiconic.quotaless.com/tutorial1.html)

I had to remove mine and install another one to get my wireless to work flawlessly

---

### Post by Presto123 on 2008-02-11
Here's mine:

```
06:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

```

Exact same card. Works flawlessly with 7.10 in my case using the normal Restricted Drivers Manager.

---

