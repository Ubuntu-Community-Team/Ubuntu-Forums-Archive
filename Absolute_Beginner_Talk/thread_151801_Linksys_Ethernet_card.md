---
title: "Linksys Ethernet card"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by Abu Imak on 2006-03-28
Hi i have recently installed Ubuntu on my pentium 2 relic and i have a problem connecting to the internet, it doesnt recognize my LNE100TX Linksys ethernet card and I'm a complete newbie to linux, 

I mean I'm a REAL newb at linux, i don't know squat. Could any one give me some guidance?

---

### Post by Zimmer on 2006-03-28
Go  Applications>Accessories>Terminal 
and at the command line
type:

dmesg | grep eth

 and see what the results are...

---

### Post by Abu Imak on 2006-03-28
sorry for the long wait between reply, lotsa school work,

it says

[   40.9713SO] etho:ADMtek Coment rev 17 at 0001e400,

00:12:17:4E:A3:CD, IRQ 11


thanks for the interest in my problem.

---

### Post by Zimmer on 2006-03-29
From that it looks like it has recognised a ADMtek device ???

Have a look here
[http://ubuntuforums.org/showthread.php?t=85186&highlight=LNE100TX](http://ubuntuforums.org/showthread.php?t=85186&highlight=LNE100TX)

Assuming it is a desktop PC you could turn off acpi...
Also, if it is an old machine try removing and refitting the card...
EDIT: and in a similar way.. see post #10
[http://ubuntuforums.org/showthread.php?t=151096](http://ubuntuforums.org/showthread.php?t=151096)
in case it is a BIOS Plug and play isuue...

---

### Post by Abu Imak on 2006-03-29
i finally got it to work! A friend of mine(whos a gentoo lover) taught me to get it to load tulip on start and then i went into my network tools and enabled it. but it wasn't going to recognize the card without tulip. thank for your help though!

---

### Post by pssparkman on 2007-09-21
How did you set linux up to load tulip on start?

---

