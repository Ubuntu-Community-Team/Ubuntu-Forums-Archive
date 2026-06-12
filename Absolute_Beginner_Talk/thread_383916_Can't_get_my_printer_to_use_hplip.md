---
title: "Can't get my printer to use hplip"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by gnoel on 2007-03-13
I see that the packages hplip and hplip-data (version 1.6.9) are installed when I look in synaptic.  Using the Ubuntu printer properties GUI, hpijs is the recommended driver and hplip is not on the list.  I tried to install the driver, but I could only find this PPD: /usr/lib/hplip/fax/HP-Fax-hplip.ppd.

Are there separate PPDs for fax, scan, and print functions?  I did notice a lot of other .ppd files, but none that seemed to correspond to hplip.

Thanks in advance!

---

### Post by Toontwnca on 2007-03-13
> **gnoel said:**
> I see that the packages hplip and hplip-data (version 1.6.9) are installed when I look in synaptic.  Using the Ubuntu printer properties GUI, hpijs is the recommended driver and hplip is not on the list.  I tried to install the driver, but I could only find this PPD: /usr/lib/hplip/fax/HP-Fax-hplip.ppd.

Are there separate PPDs for fax, scan, and print functions?  I did notice a lot of other .ppd files, but none that seemed to correspond to hplip.

Thanks in advance!

System->Administration->Printing takes you to a window called Printers.

When you add a New Printer the connection wizard should
automatically detect what drivers you need for your printer.
Do not use the Install Driver button, just click Forward and let 
the wizard do its thing. It will install it.

If this is the way you attempted it and had no luck,
then I'm out of ideas.

hpjis is the one I need for my printer. The install went without a hitch.

---

### Post by gnoel on 2007-03-13
I used the wizard and it suggested hpijs, while hplip was not listed as an option.  My understanding is that hplip is the new gold standard, plus it includes the things my multifunction PSC500 needs.

---

### Post by Toontwnca on 2007-03-13
> **gnoel said:**
> I used the wizard and it suggested hpijs, while hplip was not listed as an option.  My understanding is that hplip is the new gold standard, plus it includes the things my multifunction PSC500 needs.

Ok.
Well then, as I've said I'm out of ideas. Sorry.
Some of the guru's here are sure to have an 
answer for you. That's the beauty of this place.

---

### Post by halitech on 2007-03-13
check this thread

[http://www.ubuntuforums.org/showthread.php?t=127514&highlight=PSC500]("http://www.ubuntuforums.org/showthread.php?t=127514&highlight=PSC500")

---

### Post by gnoel on 2007-03-14
I tried installing the latest version from sourceforge and ran into some of the problems well documented on other threads in this forum.  I tried uninstalling and reinstalling hplip via the synaptic "neural net."  I finally chose the "least resistance" path and bagged the whole idea of using hplip by installing hpoj instead and configuring it to use the parallel port and the PSC500.  After that, xsane recognized the scanner and it printed fine using hpijs.

The whole experience has been yet another "only in Linux" adventure.  I wouldn't say that the two evenings have been wasted, since I learned a lot and got my device working properly.  However, even though this is my second distro in three years, and even though I work in IT using a UNIX box, I have still been humbled.  Either you gotta lotta beans or you ain't got beans.

---

