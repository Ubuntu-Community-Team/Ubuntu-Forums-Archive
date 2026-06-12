---
title: "Lexmark Z11 printer"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by naknak987 on 2007-05-23
I can't get my Lexmark Z11 printer to work, could someone help me out. I'm currently using the feisty fawn w/ all updates. thanks.

---

### Post by dstew on 2007-05-23
Does your computer see the printer at all? Does it see it, but not print, or print funny?

---

### Post by naknak987 on 2007-05-23
How can you tell if it can even see the printer, I dont know how to tell.

---

### Post by theicyj on 2007-05-23
Did you try going to "System" menu -> Administration -> Printing -> New Printer ?

You could also check [http://www.linux-foundation.org/en/OpenPrinting/Database/DatabaseIntro]("http://www.linux-foundation.org/en/OpenPrinting/Database/DatabaseIntro") to see if your printer is supported in Linux.

---

### Post by naknak987 on 2007-05-23
i Just tryed it, but i couldn't find anything for the z11, only the z12, I tred printing with the z12 stuff, but then it prints wierd, like wrong colors and stuff not were its supposed to be.

---

### Post by dstew on 2007-05-24
According to [foomatic]("http://www.linux-foundation.org/en/OpenPrinting/Database/Foomatic"), you printer is supported, at least partially. Have you installed the foomatic driver? You can get it through the Synaptic package manager. Then, you can use the Modify Printer dialog and select the foomatic driver. [Here]("http://openprinting.org/show_printer.cgi?recnum=Lexmark-Z11") is the specific page about the Lexmark Z11 driver.

---

### Post by naknak987 on 2007-05-24
Thanks alot man, I needed this. It is working now.

---

