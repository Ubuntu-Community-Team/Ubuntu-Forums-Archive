---
title: "Gimp allows me printing max 600x600 DPI ?"
date: 2006-11-13
forum: Art &amp; Design
---

### Post by amanita on 2006-11-13
Hi, I would like to print photographs (GIMP2.2) in good quality, but when go to menu print > resolution it allows me (except 150x150max,300x300) max. 600x600 resolution. 
Whatever settings max. resolution is 600x600 but my HP Deskjet 5550 is capable of 4800x1200 dpi.

Any suggestions, please?

---

### Post by TuxCrafter on 2006-11-17
Try to print it to file *.ps and then print it via evince or a other ps vieuwer. Then it will go around the gimp print engine.

---

### Post by amanita on 2006-11-22
Thanks, I did what you suggested with better result but the maximum I can get is only 1200 dpi. I do not understand why printing in better resolution is not possible. 

When look at old photos printed in M$ Windows I still see the difference :(

---

### Post by TuxCrafter on 2006-11-22
Did you check your linux support for your printer at linux priters . org?
Check if you have the correct print drivers etcetra.

I see you use a HP that is good news. There is a special program for HP printers you can install it via the package manager. something like hplib or hpijs you can find the correct information on the linux-printing.org site.

---

### Post by amanita on 2006-11-27
Sorry for late response TuxCrafter, I have checked linuxprinting.org and make  sure that have all packages installed - gimp-print, guten-print, hplip, hpijs. The higher resolution cannot get out of this, although they say that especially the 1200-dpi high resolution mode gives excellent photo quality. (gimp allows me max. 600x600-dpi)
I will buy another photopaper ( I have got the HP Everyday Photo Paper), it may helps... ?

---

### Post by TuxCrafter on 2006-11-27
Have you already run that special program of HP and check if it resieves al the info of you printer?

you can run that program form the command line

---

### Post by amanita on 2006-11-27
Which one do you mean ? :-k

---

### Post by TuxCrafter on 2006-11-27
> **amanita said:**
> Which one do you mean ? :-k

```
sudo apt-get install python-qt3
sudo apt-get install hplip
sudo /etc/init.d/hplip restart
hp-toolbox

```

---

### Post by amanita on 2006-12-02
Thanks for help! I was not aware of hp-toolbox :-# 

I happened to hear that someone also mentioned it [here]("http://www.linux.com/article.pl?sid=06/10/03/203206") that to get the best results when printing color photographs on HP printers, save them as PostScript files in the GIMP, then print them from the command line ( with properly configured CUPS of max.1200x1200dpi but the printer hardware does an interpolation then and prints with the printer's highest resolution). 

I got the same result in GIMP when went to File>Print and in Setup Printer selected Adobe > PostScript Level 2. I found my PDD file in /etc/cups/ppd/deskjet5550.ppd 

I cannot recommend HP Everyday Photo Paper for this printer as ink leaves trace on my hand even after 3 days of drying but on proper paper it prints nicely.

---

