---
title: "changing video drivers"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by barrykgerdes on 2007-03-05
Hi
 I am a real begginer that set up ubuntu dapper on a SiS display platform and it worked correctly. I have now put the hard disk into another computer that has a nvidia gforce video card and I don't have the GUI all I get is the command line. This computer is not connected to the internet. What do I need to do to set up the display so that it recognises the card.

Barry

---

### Post by sunexplodes on 2007-03-05
TRY entering:
```
dpkg-reconfigure xserver-xorg
```
then, go through the steps to reconfigure, then try 
```
dpkg-reconfigure gdm
```

---

### Post by barrykgerdes on 2007-03-05
Hi 

Thanks muchly. I knew there had to be an easy way to do it. worked first up perfectly.

Barry

---

