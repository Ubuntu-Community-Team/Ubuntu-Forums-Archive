---
title: "Nvidia / ATI question"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by seshomaru samma on 2006-04-15
How do I know if I have an ATI card or Nvidia card or some other card?

---

### Post by trent dillman on 2006-04-15
lspci | grep VGA

---

### Post by seshomaru samma on 2006-04-16
Thanks,
This is what I get:
> 0000:00:02.0 VGA compatible controller: Intel Corp. 82845G/GL[Brookdale-G]/GE Ch ipset Integrated Graphics Device (rev 01)

Is that Nvidia?

---

### Post by Sutekh on 2006-04-16
No that's an Intel onboard video card.

Are you having video driver issues?

---

### Post by seshomaru samma on 2006-04-16
[QUOTE=Sutekh]No that's an Intel onboard video card.

Are you having video driver issues?[/QUOTE]
not at all
I was toying with the idea of trying to install XGL on one of the machines here (at work)

---

### Post by Sutekh on 2006-04-16
Cool. 

Sounds like fun!  Good luck!

---

### Post by seshomaru samma on 2006-04-16
I wonder if I can install xgl on this machine, all the instructions I've seen talked about either Nvidia or ATI....

---

### Post by Sutekh on 2006-04-16
You might want to have a read of PoofyHairGuy's Eye candy blog

[http://linuxeyecandy.blogspot.com/2006/03/david-revemans-response.html](http://linuxeyecandy.blogspot.com/2006/03/david-revemans-response.html)

This particular entry is in regards to an email to David Reveman (Novell employee working on XGL)

---

