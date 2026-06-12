---
title: "photo printing (gimp or photo print) features not available"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by jsmitton on 2007-07-02
ubuntu 7.04 installed on Intel p4 as a standalone . HP D7160 photosmart connected, installed and recognized as the default printer (as the D7100 series) . Variables of paper type, print quality etc seem well defined here . under gimp 2.2 and under photoprint, this printer is not found under the hp list and the features necessary (dpi and max quality etc) are not available 
Question : is the data in the HP table (and i believe in CUPS) not available to applications using the print services? Can I make it available so that the same options are visible when I call for print from those aps?

---

### Post by Raineer on 2007-07-02
Try one of them from [here]("http://hpoj.sourceforge.net/suplist.shtml"), they don't have D7160 but they have some from the 7100 series.

---

### Post by jsmitton on 2007-07-02
thanks for the link but the 7100 series is a very different animal than the D7100. Perhaps I should also clarify that when I select System/Administration/Printing, the D7100 is loaded as my default printer and selecting Properties gives all options. It is when I try to print from Gimp that a limited set of options are given as if Gimp is not referencing the same file. The HPLIP file does contain the correct info but Gimp and Photoprint don't seem to access it.

---

### Post by william_nbg on 2007-09-19
Have you already installed the hplip tool box which is in the repositories. I have the same printer as you, and I don't get the printing options in Gimp to work how I want but I can easily set up a print job just how I want with these tools. It's a great configuration tool for all hp printers.

---

### Post by jethro10 on 2007-10-26
See my new question here [http://ubuntuforums.org/showthread.php?t=592213](http://ubuntuforums.org/showthread.php?t=592213)

I beleive what i've said is how things are. Choose Postscript level 2 as you printer, setup the printer default as photo quality etc and your away.

Jeff

---

