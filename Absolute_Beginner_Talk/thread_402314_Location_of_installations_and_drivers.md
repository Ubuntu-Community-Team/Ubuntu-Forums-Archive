---
title: "Location of installations and drivers?"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by r2000 on 2007-04-05
Hi can anyone tell me where the default install directory is in Ubuntu?, well, im trying to find where Mozilla is installed, so i can modify it to support Java 1.5.0.11.

Also does anybody know of any good WIFI software so ive got some kind of wireless interface of such.  Or is there one in Ubuntu?

Also can anybody tell me where i can get the latest drivers for my WIFI card, its a Netgear FA311T, and how to install them.


Cheers, and many thanks.

---

### Post by steve.horsley on 2007-04-05
try looking in /usr/lib/mozilla. I used this command to find it:
**locate -r mozilla$**

Sorry I can't help with the wireless stuff.

---

### Post by r2000 on 2007-04-05
Cheers.

I will just keep looking around for some wireless tools.

---

### Post by LaurelLynn on 2007-04-05
dpkg -L   program-name

will show you all of ¨program-name¨´s installed files. There will be alot all over. It´s easiest to install extensions to firefox from within it.

From the Browser menu go to Tools->Extensions.  Click on ¨Get More Extensions¨. Should be available straight from Netscape.

Laurel Lynn

---

### Post by r2000 on 2007-04-05
I tried using the Mozilla install helper but it said i had to manually install Java.

Cheers for the other command syntax.

---

