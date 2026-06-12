---
title: "Printer recommendations"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by jmtjet on 2006-09-18
I currently have a Lexmark Z32 printer that doesn't seem to play nice with Ubuntu. I think I'm going to replace it. Does anyone have a recommendation for a printer that is known to work well with Ubuntu? Thanks.

---

### Post by Kilz on 2006-09-18
> **jmtjet said:**
> I currently have a Lexmark Z32 printer that doesn't seem to play nice with Ubuntu. I think I'm going to replace it. Does anyone have a recommendation for a printer that is known to work well with Ubuntu? Thanks.

[http://www.linuxprinting.org/suggested.html](http://www.linuxprinting.org/suggested.html)

---

### Post by jmtjet on 2006-09-19
Thanks for the link. I've bookmarked it to use as a guide. :)

---

### Post by ronmarley1 on 2006-09-19
For what it's worth, here at school I print to HP Laserjet5, Laserjet4, Laserjet2200 and Deskjet935 printers just fine.  At home, I print to an HP Deskjet882C just fine as well.  Good luck!

---

### Post by deadgobby on 2006-09-19
HP printers would be your best bet and less of a headache. Hp is a very Unix/Linux friendly.
GObby

---

### Post by skymt on 2006-09-19
I have an HP Laserjet that doesn't work at all with Linux. There's a project working on drivers, but it doesn't look good.

I wound up hacking a .ppd for a similar Laserjet that *does* work in Linux, to send the print job to my Mac via netcat. The Mac has a launchd entry that listens on a port and pipes anything it receives to lpr. What can I say, it works! =D>

I love netcat.

---

