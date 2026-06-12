---
title: "Changing charset in irssi?"
date: 2006-03-12
forum: Absolute Beginner Talk
---

### Post by Klejs on 2006-03-12
Hi all, 

Im from Sweden and therefore I dont use the default charset for my keyboard layout. All the programs I have installed atm are using the right charset wich I 
think is ISO-8859-1. 

The thing is that when I'm in school I want to be able to use IRC from my laptop, but the admin have closed all the ports to IM's and P2P and, well you know. But when I use ssh to log onto my Ubuntu box at home I can run and connect thru irssi. 

Is there any way I can change the charset that irssi is using to my local one, or do I have to adept and always write in english?

---

### Post by kaamos on 2006-03-12
You (probably) need irssi 8.10 or later for this.

```
/set term_charset latin1
```

Look also /help recode, that could be useful

---

### Post by Klejs on 2006-03-13
ok thaks!

---

### Post by dakilla on 2006-03-14
hi i have the same problem..
i have tried with the script "charsetwars.pl"
and i tried the "/set term_charset latin1" thing to.
but nothing seams to work for me :(

what am i doing wrong?

---

