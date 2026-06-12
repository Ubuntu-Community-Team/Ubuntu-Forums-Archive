---
title: "[SOLVED] Trouble installing ndiswrapper"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by sunlover on 2008-01-24
I have Ubuntu 7.04 dual booted with Windows XP on my laptop.
I access the Net thru Windows XP using an OPTION GX 0202 wireless card and as this card is not supported directly by Ubuntu I downloaded ndiswrapper and extracted ndiswrapper-1.49 to Ubuntu desktop.
As per instructions on  ndiswrapper site I have opened terminal and typed in cd ndiswrapper-1.49 to get message that no such directory or file exists??

Any help would be greatly appreciated.
I like the philosophy behind Ubuntu and open source software but need some help on the basics to get started
Bruce.

---

### Post by lian1238 on 2008-01-24
When you open the terminal, you're in the directory ```
/home/<yourname>/
``` or simply ```
~/
```
To get to the Desktop, type:
```
cd Desktop
```
Now you can type ```
cd ndiswrapper-1.49
```
You can also just type ```
cd Desktop/ndiswrapper-1.49
```

A useful note: you can type the beginning of a command, then press TAB to auto-complete it. Double TAB to see a list of available options.
For example: you can type: cd De{TAB}ndi{TAB} instead of typing it all.

---

### Post by sunlover on 2008-01-29
Getting further with the Terminal with your suggestions, have ordered cd of latest version (Gutsy Gibbon) and will upgrade to this before tackling wireless connection.

---

### Post by oedha on 2008-01-29
after you installed ndiswrapper, 
have you point it to use your windows wireless driver files ?
because ndis will use your *.bin, *.inf files which can be found on your wireless driver for windows cd

regards;
~E~

---

