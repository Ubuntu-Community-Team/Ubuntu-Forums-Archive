---
title: "Power Options?"
date: 2006-05-19
forum: Absolute Beginner Talk
---

### Post by hangster on 2006-05-19
Hi, I've just installed Ubuntu today and I was wondering how could I adjust the brightness of my laptop screen and how do I hibernate my computer when I close my lid.  Are there options for those commands?  I've tried the Power Options but the dimming of my screen never worked...  Thanks for the help.

---

### Post by slimdog360 on 2006-05-19
Sometimes things work and sometimes things dont. The hibernate on my laptop doesnt work properly. It goes into hibernate alright but never comes out. 
Dapper for my improved alot of things like brightness, hibernate, volume etc on my laptop. 
My suggestion is that if you dont already have dapper, give it a go and see if it improves anything.

---

### Post by dmizer on 2006-05-19
very very true that sometimes it works and sometimes it doesn't.  but it will help to know what laptop you have, because sometimes a utility package will help. also, there is a HUGE community here.  you can bet that someone else has a laptop exactly like yours.

---

### Post by Sef on 2006-05-19
What version are you using:  Brezzy or Dapper?

---

### Post by hangster on 2006-05-19
[QUOTE=Sef]What version are you using:  Brezzy or Dapper?[/QUOTE]

My laptop is Sony VGN-FS675P/H and I'm using the Brezzy Badger version of Ubuntu.  Also, I have no clue about linux so I don't know what Dapper is...  Furthermore, my restart always freezes and my laptop can never get out of hibernation, it sometimes even have trouble shutting down...  I have a lot to learn.... but that answers your question.

---

### Post by xyz on 2006-05-19
Hi-
There's something here about brightness:
[http://www.ubuntuforums.org/showthread.php?t=88611&highlight=brightness](http://www.ubuntuforums.org/showthread.php?t=88611&highlight=brightness)

I have a Toshiba Satellite A40 and use this command line to adjust:
```
 echo 'brightness : 1' > /proc/acpi/toshiba/lcd

```
in root. The number "1" is what you may want to change. Hope this helps you.

---

