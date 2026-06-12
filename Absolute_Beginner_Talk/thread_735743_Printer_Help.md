---
title: "Printer Help"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by mtstifflers on 2008-03-25
I have a Lexmark X1150 and it doesn't work with my new installation of Ubuntu and i was hoping someone could help me with this!

Thank you.

---

### Post by zen_waters on 2008-03-26
hmm, don't see that printer on the lexmark site.

---

### Post by bumanie on 2008-03-26
Lexmark used to have reasonable linux support, but I believe that is not necessarily the case any more.

---

### Post by bumanie on 2008-03-26
Lexmark used to have reasonable linux support, but I believe that is not necessarily the case any more. In fact, I know someone who runs a virtualized windows just so that they can use their lexmark printer.

---

### Post by chicki on 2008-03-28
> **mtstifflers said:**
> I have a Lexmark X1150 and it doesn't work with my new installation of Ubuntu and i was hoping someone could help me with this!

Thank you.

According to this URL:
[http://openprinting.org/printer_list.cgi?make=Lexmark](http://openprinting.org/printer_list.cgi?make=Lexmark)

The Lexmark X1150 PrintTrio should work perfectly with Linux (three penguins).

Many people here with Lexmark printers (including myself) have been having trouble getting their printer to work on LInux. 

If you do a lot more reading on these forums (as I did), you'll find out that all you need to do is install the z600 driver. Even if you do not have a Lexmark z600, the z600 driver should work on a lot of Lexmark printers. 

Here's a helpful forum on installing the z600 driver:
[http://ubuntuforums.org/showthread.php?t=49714&highlight=x1150](http://ubuntuforums.org/showthread.php?t=49714&highlight=x1150)

HELPFUL TIP: 
Remember to install the following packages: 

sudo apt-get install libstdc++5 alien


Good Luck! If you have any questions, please feel free to reply. 

~chicki

---

### Post by chicki on 2008-03-28
I forgot to mention:

After Installing the z600 driver, I can only print on my Lexmark x1150 PrintTrio printer.

However, I have not gotten the scanner to work properly yet. Maybe you'll have better luck. 

~chicki

---

### Post by LowSky on 2008-03-28
Lexmark has never payed well with Linux, the only driver they have is for the z600 (it must be a huge seller to offices or something)
here there development website for linux drivers
[http://www.lexmark.com/lexmark/sequentialem/home/0,6959,204816596_659668505_0_en,00.html](http://www.lexmark.com/lexmark/sequentialem/home/0,6959,204816596_659668505_0_en,00.html)

---

