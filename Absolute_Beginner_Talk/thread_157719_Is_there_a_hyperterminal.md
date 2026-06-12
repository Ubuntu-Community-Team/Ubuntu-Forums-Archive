---
title: "Is there a hyperterminal?"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by tsharpe62 on 2006-04-09
Is there a hyperterminal or Procomm type program for Ubuntu? If so, what is it called?

---

### Post by dcstar on 2006-04-09
[QUOTE=tsharpe62]Is there a hyperterminal or Procomm type program for Ubuntu? If so, what is it called?[/QUOTE]
Depening on what you want, gtkterm may be worth a look.

---

### Post by steve.horsley on 2006-04-10
For using the serial port for terminal emulation, try gtkterm or minicom.

---

### Post by tsharpe62 on 2006-04-10
I found and loaded gtkterm but I don't see where it has the ability to out dial. I did a search for minicom but didn't find anything. Can you provide a link?

---

### Post by cwaldbieser on 2006-04-10
[QUOTE=tsharpe62]I found and loaded gtkterm but I don't see where it has the ability to out dial. I did a search for minicom but didn't find anything. Can you provide a link?[/QUOTE]
You may need to enable extra repositories, but it is definitly in my apt package list.

---

### Post by SherpaDoug on 2006-12-01
I just tried out Gtkterm for looking at an RS232 stream, and the basic program works but the font is horrible!  I have to shut off the room lights and turn my monitor brightness up to see it.  Is there any way to change the font?
Someone mentioned "miniterm".  Where can I find that?

SherpaDoug

---

### Post by Lakefall on 2006-12-02
> **tsharpe62 said:**
> I found and loaded gtkterm but I don't see where it has the ability to out dial.
I would guess that to tone dial to number 12345, you would type ```
ATDT12345
``` and press enter. And to reset the modem, you would type ```
ATZ
``` while ```
ATA
``` answers an incoming phone call. Ah, the memories. I learnt this stuff in the nineties, when you only got laughed at by the normal people for fooling around with modems. These days geeks laugh too. :-P

But anyhow, what kind of modem user doesn't know the [AT commands](http://en.wikipedia.org/wiki/Hayes_command_set), but does knows what hyperterminal is?

(Okay, so it's a bit of an old post. So what?)

> **SherpaDoug said:**
> Someone mentioned "miniterm".  Where can I find that?
Nobody mentioned "miniterm". steve.horsley mentioned "minicom".
```
sudo aptitude install minicom
```

As far as I remember, it's a command line program.

---

