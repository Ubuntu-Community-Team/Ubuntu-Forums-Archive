---
title: "More advice please (wireless networking)"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by DaveElson on 2007-06-11
Hello All
My first attempt to load Ubuntu last night did not work, but after reburning the ISO file at 1x speed, other than apparently not recognising the floppy disc (big deal) I have now Ubuntu loaded on my old Athlon 1.3.

My first question is that it doesn't seem to recognise all the hard disc space. I have 2 hard drives and it only seems to see 35 gigs free. I'm sure I have more than that (in fact the live cd did show more).
My biggest (and expected) problem is that I can't access the wireless network. The cable modem is in another room and the Linksys 2.4 ghz wireless adapter doesn't seem to work yet.
Now, I do see that when I check the connection in Ubuntu, that it seems to show a speed, at one stage 54mbps and then later 48.
So I think I'm close. I'm a little confused about how to set it all up.
I try the icon close to the clock and it does seem to show an available connectioon (a list of numbers) but when I try it, after a couple of mins I still get no connection.
 A search of Linksys produces many threads but I'm still in the dark.
How do I try the iwconfig? where do I type it?
Appreciate any advice.

---

### Post by Inxsible on 2007-06-11
Do you see the name of your network, when you click on the icon near the clock ?

Open up a terminal : Applications -> Accessories -> Terminal

and type in
```
ifconfig
```
```
iwconfig
``` Post the output here.

---

### Post by DaveElson on 2007-06-11
i tried terminal, I get a box on the lower taskbar telling me it's starting, but nothing happens. ??

---

### Post by Inxsible on 2007-06-11
You mean the terminal never starts ?

---

### Post by DaveElson on 2007-06-11
correct.

---

### Post by Bachstelze on 2007-06-11
Press Alt+F2, you'll get the "Run command" dialog. Type *gnome-terminal* and press Enter. If it still doesn't work, try *xterm*.

---

### Post by DaveElson on 2007-06-11
Sorry, but Alt + F2 doesn't do anything either. 
I d/loaded yesterday.

---

### Post by Inxsible on 2007-06-11
> **DaveElson said:**
> Sorry, but Alt + F2 doesn't do anything either. 
I d/loaded yesterday.
Wow !  are you sure you didn't get any errors during the installation ?

---

### Post by Bachstelze on 2007-06-11
Browse through the menus, you should have a "Run command" item somewhere.

---

### Post by DaveElson on 2007-06-12
Sorry, don't see a run command. Have three drop down menus - Apps - Places and System.
Don't see Run in any of them.

---

### Post by Inxsible on 2007-06-12
are you sure you tried Applications --> Accessories --> Terminal ?

I am sorry, it jsut seems strange that you have a working Ubuntu install and not have Terminal because it is installed by default.

---

### Post by DaveElson on 2007-06-12
I rebooted and it works, although even the Quit command didn't work.
So I found terminal, and am now trying to copy the results onto a USB disk, so I can paste them onto my other windows/internet machine. The text file seems to show up in Ubuntu but not in windows. Perhaps I'm doing this all wrong but very frustrating.

---

### Post by DaveElson on 2007-06-12
I wonder if my machine is overheating, as Ubuntu is back not opening up applications.
I'm off to bed, thanks for the help.

---

