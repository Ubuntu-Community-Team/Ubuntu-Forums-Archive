---
title: "help me connect to the internet!"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by kemb913 on 2008-03-18
I am trying to connect ubuntu to the internet. i have a belkin wireless card for my desktop computer, but to get it working you must install the cd. I have internet on windows (which is how i'm typing this post), but not on ubuntu, because the cd won't install. i realize that you can run some windows executable files by using WINE, but to do that you must have the internet. Is there a way i could write WINE to a cd from windows, then boot ubuntu to install it? Please Help!:(

---

### Post by thomas7.10 on 2008-03-18
Well you just need drivers for your wireless card. If you are lucky then it will work out of the box and you just click on the right hand upper side on the network symbol and choose your  SSID. The rest should be self-explaining. If it doesn't work out of the box it's no reason to go to the attic and shoot yourself you can still use ndiswrapper to get the card to work with your windows driver...

You can follow this instruction: [http://ubuntuforums.org/showthread.php?t=563547]("http://ubuntuforums.org/showthread.php?t=563547")

---

### Post by kemb913 on 2008-03-18
thank you, i will try that.
my computer crashed with my wireless card still in it(this i s a dessktop computer), so i recoverd it and decided to install ubuntu. ubuntu didn't tell me it found it, and firefox wouldn't work.

Thanks for the help!

---

### Post by thomas7.10 on 2008-03-18
Well just tell me how it goes. Maybe i can help you later on. I'm not one of the geeks here but if you run into serious problems they will surely help you.

---

### Post by Tomatz on 2008-03-18
yeah most belkin (ralink) cards work out of the box just try l-clicking on the network icon (in systray). you should see available wireless networks :)

---

### Post by iAtari on 2008-03-18
Good Luck, have you tried disabling IPv6 in Firefox?

---

### Post by kemb913 on 2008-03-18
it doen't list my network when i l-click on it it just gives the options:
>Wired Network (whited out)
>Manual configuration...

---

### Post by thomas7.10 on 2008-03-18
Ok now i tell u what wieman01 told me ;) 

no type in the console:

```
sudo lshw -C network
```

that should show you what adapter you have and which version number.

copy the things you got right in here...

---

### Post by kemb913 on 2008-03-18
it tells me this:

> *-network UNCLAIMED
descripstion: Ethernet controller
product: Belkin
vendor: Belkin
physical id: 8
bus info: pci@0000:03:08.0
version: 20
width: 32 bits
clock: 33MHz
capabilites: bus_master cap_list
configuration: latency=32 maxlatency=64 mingnt=32

---

### Post by kemb913 on 2008-03-18
[SIZE="5"]anyone?[/SIZE]

---

### Post by kemb913 on 2008-03-18
thank you everyone for your help, i am now talking to u from ubuntu!:popcorn:

---

### Post by wieman01 on 2008-03-19
> **kemb913 said:**
> thank you everyone for your help, i am now talking to u from ubuntu!:popcorn:
What did you do? Out of interest...

---

