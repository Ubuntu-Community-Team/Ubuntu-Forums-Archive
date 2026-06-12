---
title: "How do I power down the display?l"
date: 2007-10-14
forum: Apple PPC Users
---

### Post by JoJoRaz on 2007-10-14
I'm now running Feisty 7.04 Server(no GUI) on a G4 Powerbook (15" Titanium) as the sole OS.  I'm administering it with SSH from a WindowsXP machine so I don't need/want the screen live on the Tit. Admittedly, the screen does go blank after a while, but it's still illuminated. How can I power it down completely from the command line?  I've seen reference to 'xset' and DPMS, but there seems to be no manual pages on them. 
I hope this is less painful than my Yellow Dog experience.

---

### Post by JoJoRaz on 2007-10-15
Is there a record for the highest number of reads with no replies?  Perhaps I should only ask easy questions!

---

### Post by chimaera on 2007-10-15
well, happens quite often. IRC turns out to be helpful. also i recommend the gentoo wiki (and forums). although not having used gentoo myself for about four years, they have quite an active community with lots of howtos and hints which can be easily adapted to any other distribution.

---

### Post by sinclair44 on 2007-10-17
On my machine, "xset dpms force off" does the trick, until the mouse is moved or a keystroke occurs.

---

### Post by JoJoRaz on 2007-10-17
Thanks for the replies. 

But 'x'set is for X. I only have/want Feisty server installed so I need to do it in the command line, so it will have to be a kernel feature I think.

---

### Post by chimaera on 2007-10-17
check setterm's -powersave and -blank switches [1]. it's not instant but you can set the time, for example:

```

setterm -powersave powerdown
setterm -powerdown 1
setterm -blank 1

```

to save the settings:
```

setterm -store

```

[1] [http://www.faqs.org/docs/Linux-HOWTO/Keyboard-and-Console-HOWTO.html#s19](http://www.faqs.org/docs/Linux-HOWTO/Keyboard-and-Console-HOWTO.html#s19)

---

### Post by JoJoRaz on 2007-10-18
chimaera to the rescue! Many thanks!

---

### Post by cleaner416 on 2007-11-04
I'm having the same issue, but I can't seem to get the instructions to work ... did you follow the instructions through an ssh connection or directly on the box?

Also, after the first command, I get:

cannot (un)set powersave mode

Basically, I want the powerbook to have it's lid closed with the screen off.  All of my interaction with it is at the ssh level.  (It's just a server afterall!)

Thanks!

---

