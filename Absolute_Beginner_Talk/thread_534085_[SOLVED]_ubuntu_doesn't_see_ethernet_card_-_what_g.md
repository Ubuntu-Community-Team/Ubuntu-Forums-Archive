---
title: "[SOLVED] ubuntu doesn't see ethernet card - what gives?"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by LordKthulhu on 2007-08-24
OOOOOKay... tried to connect, Ubuntu does not seem to detect ethernet card (pppoeconf neither: as far as it is concerned, it doesn't exist)? What gives? Any troubleshooting ideas? Thanks!

---

### Post by Kingsley on 2007-08-24
Try to get the specific name of the ethernet card.

---

### Post by livestockPimp on 2007-08-24
well pppoeconf will only work if its installed (apt-get install pppoeconf), also if ubuntu does not detect your card out the box then you will probably need to find drivers and compile them. for this you need to know the model of the network card.

---

### Post by LordKthulhu on 2007-08-24
OK, I'll have to see if those bastards will tell me. I already called them, spent 30 minutes and got nothing out of it except for them swearing up and down that all drivers are on their website (they aren't). Wish me luck...

---

### Post by mysticmatrix on 2007-08-24
Post the output of following command, perhaps we can tell what network card you have
Goto Applications --> Accessories --> Terminal and typr
```
lspci
```

---

### Post by LordKthulhu on 2007-08-24
Yeah, it dawned on me to do just that. Intel Generic device 10/100 or somesuch was the answer. So, lspci sees it, but pppoeconf doesn't... where do I go from here? Thanks!

The line literally is: 00:19.01 Ethernet controller Intel Corporation unknown device 10c0 (rev. 02)

Oh, and modem is Westell 6100, and this combo works fine under Vista...

---

### Post by LordKthulhu on 2007-08-24
Call me stoopit, but how do I delete this?

---

### Post by LordKthulhu on 2007-08-24
Resolved according to this:

[http://ubuntuforums.org/showthread.php?t=502058&highlight=530+network+card](http://ubuntuforums.org/showthread.php?t=502058&highlight=530+network+card)

Down to Hiweed's post (#4), followed instructions to the letter. After reboot everything worked. Thanks y'all!

---

