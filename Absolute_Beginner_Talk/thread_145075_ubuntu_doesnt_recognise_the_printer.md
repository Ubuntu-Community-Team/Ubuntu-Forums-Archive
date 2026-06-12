---
title: "ubuntu doesnt recognise the printer"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by zexoc on 2006-03-15
which is strange because while loading, ubuntu lists **hp printing services** yet when I try to add it thorugh:

**system > printing > administration > printers > add a printer**

it shows no new printers.

any help would be appreciated

---

### Post by Sef on 2006-03-15
> which is strange because while loading, ubuntu lists hp printing services yet when I try to add it thorugh:

system > printing > administration > printers > add a printer

it shows no new printers.

any help would be appreciated

What kind of HP printer do you have?

---

### Post by Sef on 2006-03-15
First it doesn't post, then it posts double. sigh

---

### Post by zexoc on 2006-03-15
its a hp psc 2175

---

### Post by zexoc on 2006-03-15
not a very new model, its 3 - 4 years old, so it should be supported in ubuntu 5.10

---

### Post by Sef on 2006-03-15
> not a very new model, its 3 - 4 years old, so it should be supported in ubuntu 5.10

Not necessarily without a little bit of help provided below.

I have a PSC 1610, and this is how I go it running, thanks to wondering jew:

[http://www.ubuntuforums.org/showthread.php?t=39625&highlight=PSC+1610]("http://www.ubuntuforums.org/showthread.php?t=39625&highlight=PSC+1610")

---

### Post by zexoc on 2006-03-15
i tried ```
sudo apt-get install hplip
```, which it did fine. but when i run through the process in my original post, still no printer....

---

### Post by Sef on 2006-03-15
>  tried
Code:

sudo apt-get install hplip

, which it did fine. but when i run through the process in my original post, still no printer....

Did you try ```
sudo apt-get install hplip gtklp xpp hpijs python-qt3-doc libqt3-mt-mysql hplip-ppds

```?

---

### Post by zexoc on 2006-03-15
once you type in ```
sudo apt-get install hplip
``` the rest follows automatically.

so far i've managed to 'install' it and tried to print a test page, but it doesnt work.

one thing that is better in using the printer on linux (once I get it to work) is that I dont have to install the hp utilities program which is a resource hog in windows xp.

---

### Post by Sef on 2006-03-15
> system->administration->printing > printer> add printer and in step 2 I selected psc 1600 from 'HP (HPLIP)' in the manufacturer drop down menu (as opposed to just 'HP' which did make a difference for me )

In step 2, did you select, HP (HPLIP)?

---

### Post by zexoc on 2006-03-15
yep tried both HP and HPLIP

---

### Post by Sef on 2006-03-15
From LinuxPrinting.org

> Got this printer yesterday.  Works perfectly for me with the hpoj driver for photos, printing, copying and scanning. 
Just make sure to apt-get install hpoj, apt-get install hpijs, apt-get install cups and all cups-related packages. 
Then, simply follow the instructions that came with your hpoj: file:///usr/share/doc/hpoj/html/index.html.  No glitches, so I don't know what else to add. 

For more info:

[http://linuxprinting.org/show_printer.cgi?recnum=HP-PSC_2175]("http://linuxprinting.org/show_printer.cgi?recnum=HP-PSC_2175")

---

### Post by zexoc on 2006-03-15
thanks for your help Sef.

---

### Post by Sef on 2006-03-15
Glad I could be of help to you.

---

