---
title: "driver for canon bjc -1000"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by firedancer on 2007-05-16
forgot about driver 

so the prints are very small unreadable , surely can't use this for my work 


suggestions how i can fix the problem ?

found something in forum [http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-BJC-1000](http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-BJC-1000)

but still complicated  :?:

---

### Post by aidanr on 2007-05-16
aplications -> accesories -> terminal
```
sudo aptitude install alien lsb
wget http://www.linuxprinting.org/download/printdriver/RPMS/i486/gutenprint-5.0.0.99.1-3lsb3.1.i486.rpm
sudo alien gutenprint-5.0.0.99.1-3lsb3.1.i486.rpm
sudo dpkg -i *.deb
```
> Set up a print queue with your distribution's printer setup tool.

---

### Post by firedancer on 2007-05-16
explain me your quote

do you mean   the Printer configuration-localhost

---

### Post by aidanr on 2007-05-16
i think it's gnome-cups-manager (i'm on xfce and don't have a printer so i'm not sure) it should be in the menu anyway

---

### Post by firedancer on 2007-05-18
well , through administration i select printer and then i can configure the stuff (printer configuration)

then i choose make and model , then i can change the driver , BUT WHEN I 'APPLY'

---

### Post by firedancer on 2007-05-18
well , through administration i select printer and then i can configure the stuff (printer configuration)

then i choose make and model , then i can change the driver , but when  I 'apply'  then  i need to   
type in passw. for root in localhost , but none of my passw work  i get back : not authorized passw maybe incorrect


what's next , t need to have stuff printing next sunday




it does print , but everything very s mall  , like a passport picture or so , 

can i maybe  change it in another way ?

---

### Post by Najand on 2007-05-18
Push Alt+F2 and then type:
```

gksu gnome-cups-manager

```
Then configure it again.

---

### Post by firedancer on 2007-05-18
ok, yes it was already printing 


but only very small , do i adjust that , instead of 'portrait' to 'landscape'

i tried i believe but it just came side ways but small again, 


so maybe i'm not doing something i should do and maybe someone can tell me what it is

:(

---

### Post by firedancer on 2007-05-20
fixed :popcorn:

i had to check which of the drivers was rite for me

---

### Post by el_itur on 2007-05-31
I have the same printer and I've tried with almost every driver around. and still the printer doesnt give me any output. no printed pages nor error log.

What can be wrong? firedancer, wich driver do get the printer running for you?

---

### Post by firedancer on 2007-05-31
i  think it's the bjc-600 , i believe you have 5 of them , when u install test print to see if it reacts (prints)

but let me know what you are doing to get it printing , then i can tell u how i did it (it wasn't with codes or anything) , let me know , because it can be another problem too , you never know 


does it print at all , test print or not , otherwise the driver is not installed it took me a week then i figured it out


do you see your printer in system>>administration>>printer  next to 'add new printer as 'ready' or NOT

---

### Post by xkendrax on 2007-08-02
Hello firedancer, i got the same printer but i cant get it to work quickly, it takes too much time for printing a line, and it pauses often. What can i do to fix it?

---

### Post by el_itur on 2007-08-02
> **firedancer said:**
> i  think it's the bjc-600 , i believe you have 5 of them , when u install test print to see if it reacts (prints)

but let me know what you are doing to get it printing , then i can tell u how i did it (it wasn't with codes or anything) , let me know , because it can be another problem too , you never know 


does it print at all , test print or not , otherwise the driver is not installed it took me a week then i figured it out


do you see your printer in system>>administration>>printer  next to 'add new printer as 'ready' or NOT

I've tried everything. On two diferents machines. The printer works properly on windows. But on linux It doesn't moves, not at all.
Even lp or lpr with a raw text input returns nothing, in the console or in the hardware. I said, it doesn't give me any error, but the printers doesn't moves.

I'm almost crazy about it. I can't figure out what nto do or hoiw to debug this.

---

### Post by gkinal on 2007-08-03
I had the same problem with tiny print when I installed the CUPS driver.

INSTEAD, select the BJC-1000 BUT USE the BJC-600 driver.

Works just fine.

Somebody should update the printer database to show that the BJC600 driver is the recommended one for BJC-1000.

The only problem might be with the color model ( I think the BJC-600 has the full four or five color ink set, not changeable cartridges), but I am using only the black cartridge so that is not an issue.

GK

---

### Post by dionisis on 2008-05-23
I had the same problem with tiny print. After some experimentation the driver for BJC-600 was not working for me (I have the Canon BJC-1000SP). Instead what I did was to use the default BJC-1000 driver (CUPS+Gutenprint v5.0.2 Simplified) and change the printer option "Shrink Page If Necessary to Fit Borders" to "Expand (use maximum page area).

---

