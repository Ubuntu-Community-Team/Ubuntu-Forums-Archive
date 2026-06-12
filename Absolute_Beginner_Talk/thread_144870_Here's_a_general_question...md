---
title: "Here's a general question.."
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by Cloudy on 2006-03-15
A wee bit stupid (understatement), too.
How do I know what type of RAM my PC has? :oops:

---

### Post by _simon_ on 2006-03-15
There's normally a sticker on the ram. That will only tell you what type you currently have though, not what it can support.

To check what it supports you need to look in the motherboard manual or google your motherboard model.

---

### Post by Darkriser on 2006-03-15
Well, BIOS can tell you:
- restart (or turn on) the computer
- keep pressing F2 or Del key on keyboard (F2/Del depends on BIOS type you may have - try one and if not working then the other one)
- you'll get into BIOS - which has menus like any other program - the RAM amount should be somewhere there - just keep searching

---

### Post by _simon_ on 2006-03-15
yes that will tell you AMOUNT but not TYPE ;)

---

### Post by Iowan on 2006-03-15
Hop over to [crucial.com]("http://crucial.com").  You can hopefully find (I have a few computers they can't supply) what type RAM they'd provide.

---

### Post by StefanoCole on 2006-03-15
Cloudy, from terminal type:

sudo lshw

Stefano

---

### Post by Cloudy on 2006-03-15
Thanks. :D

---

### Post by SVwanders on 2006-03-15
WOW that is a cool command.

---

### Post by mlind on 2006-03-15
then there's report-hw too
```

report-hw | less

```

---

