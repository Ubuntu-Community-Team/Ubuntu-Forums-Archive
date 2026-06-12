---
title: "How do I get a report of what is happening on boot-up?"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by Barnable on 2007-05-23
When I turn on my laptop (Fujitsu Siemens Amilo PA 1510, AMDTurion dual core) a message flashes up about a "BIOS bug", but it flashes up and is gone too quickly for me to write it down and google it.

Presumably this is stored in a report somewhere.

Can someone please let me know where I can find it?

Thanks,


B.

---

### Post by ginestre on 2007-05-23
I had a similar question.

[http://ubuntuforums.org/showthread.php?t=448522](http://ubuntuforums.org/showthread.php?t=448522)

---

### Post by benanzo on 2007-05-23
you can check **dmesg** for messages you get during boot.

I would suggest doing this in a terminal
```
dmesg > ${HOME}/Desktop/dmesg.txt
```

This will take all the information in dmesg and put it in a text file on your desktop for easy reading.

---

### Post by Barnable on 2007-05-23
Thanks, people.

B.

---

### Post by Barnable on 2007-05-24
It was BIOS Bug #81.

Googling it shows it's probably something to do with the SD card reader (which I've never tested as I don't own an SD card!), and turns up a lot on Fujitsu-Siemens laptops like mine.

Thanks again,

B.

---

