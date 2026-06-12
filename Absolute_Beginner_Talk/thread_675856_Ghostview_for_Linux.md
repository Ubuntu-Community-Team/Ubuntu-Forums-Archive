---
title: "Ghostview for Linux"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by darthshak on 2008-01-23
Hi all

I run Ubuntu 7.10 Gutsy Gibbon 64-bit. I read a lot of pdf documents on a daily basis and I needed a good pdf viewer. I tried out evince document viewer that came with my Ubuntu install and frankly, it consumed a LOT of memory and I was not too happy with its performance in general. I tried xpdf without much satisfaction.

I decided to try out gv which was on my ubuntu repository. I was horrified at the way it was rendering pdf documents. FIrstly, they always started rotated 90 degrees. Rotating it back is not an option as the page size does not resize on changing display to portrait from landscape. 

I wanted to know if there is any way I can get gsview 4.9 to work on my ubuntu install as I had used gsview before with much happiness. It was the closest to a no-nonsense pdf reader....gv was outright bad...

---

### Post by hyper_ch on 2008-01-23
well, you could install acrobat reader if you want to... but I dunno how well that one is on linux

---

### Post by arjayes on 2008-01-23
Hey 
try this site for adobe acrobat for linux .... [http://www.adobe.com/products/acrobat/readstep2_allversions.html](http://www.adobe.com/products/acrobat/readstep2_allversions.html)

---

### Post by hyper_ch on 2008-01-23
no need for that. Acrobat is in the medibuntu repos.

---

### Post by mali2297 on 2008-01-25
I managed to compile gsview and start the program. It won't open any pdf's though. It seems like it does not support the ESP version of gs (which is the version in the repositories).

I recommend that you give xpdf another try, I would say that is the best option for a *lightweight* pdf viewer.

---

### Post by dondos on 2008-02-28
By the way, does anybody know where I can find gnome-gv? That was my preferred viewer for ps, eps and pdf files. I used to have it installed on my system, up to version 6.10. Now I think it is gone from the repositories. Gnome-gv was an excellent front-end for Ghostscript, simple, fast and elegant. Is it no longer maintained?

---

### Post by rich_wookey on 2008-03-04
The advantage of GSview is that you can create .pdf files as well as view them (and convert between many other formats)

I'm new to Linux, but managed to get GSview 4.8 working by downloading the gsview-4.8-1.i386.rpm from [http://pages.cs.wisc.edu](http://pages.cs.wisc.edu) (there is a later version, 4.9, but you would have to compile from the source files) I then used "Alien" to create a .deb file which I then installed.  

After installation, GSview ran, but when I tried to open a postscript file (or any file) I got an error:

....
Failed to load libgs.so
.... 

I fixed this selecting Options/ advanced Configure...  changing 
Ghostscript Version to 861
Ghostscript Shared Object to libgs.so.8
leaving other fields as default

Rich

PS I'm running out-of-the box Ubuntu 7.10 32 bit on Dell XPS 1300

---

### Post by mali2297 on 2008-03-05
> **rich_wookey said:**
> The advantage of GSview is that you can create .pdf files as well as view them (and convert between many other formats)

I'm new to Linux, but managed to get GSview 4.8 working by downloading the gsview-4.8-1.i386.rpm from [http://pages.cs.wisc.edu](http://pages.cs.wisc.edu) (there is a later version, 4.9, but you would have to compile from the source files) I then used "Alien" to create a .deb file which I then installed.  

After installation, GSview ran, but when I tried to open a postscript file (or any file) I got an error:

....
Failed to load libgs.so
.... 

I fixed this selecting Options/ advanced Configure...  changing 
Ghostscript Version to 861
Ghostscript Shared Object to libgs.so.8
leaving other fields as default

Rich

PS I'm running out-of-the box Ubuntu 7.10 32 bit on Dell XPS 1300

Thanks for sharing the solution.

---

