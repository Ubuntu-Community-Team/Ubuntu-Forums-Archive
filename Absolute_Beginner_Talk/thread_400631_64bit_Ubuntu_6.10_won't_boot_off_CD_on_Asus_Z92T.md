---
title: "64bit Ubuntu 6.10 won't boot off CD on Asus Z92T"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by DeltaP on 2007-04-03
I am new to Linux and Ubuntu.  I have an Asus Z92T Laptop with a turion X2, 1gig of Ram, and an nVidia Go 7600 graphics  card.

I have tried to run the 64 bit version of Ubuntu 6.10 off of a Live CD however every time I run it the installation process stops on the line

[40.439430] io scheduler cfq registered (default)

The computer then becomes unresponsive (there is a blinking cursor below this line but I can not type anything) and I have to manually turn the laptop off and on.

I have successfully run the exact same CD on my friends laptop, a HP with a regular turion processor and it worked fine.

Any suggestions?

---

### Post by in_flu_ence on 2007-04-03
have you tried the alternative cd? It might help.

---

### Post by DeltaP on 2007-04-03
Where can I get an alternative CD and what is the difference?

---

### Post by in_flu_ence on 2007-04-03
[http://releases.ubuntu.com/6.10/](http://releases.ubuntu.com/6.10/)

It might help.

---

### Post by DeltaP on 2007-04-03
Thank you.  Do I have to reformat my hard drive for this option?

I was hoping to use the Live CD until I had time to back up all of my files and set up a fresh dual boot.  If I have to reformat my hard drive to use the alternate version then I won't be able to set it up for a week or so :-?

---

### Post by in_flu_ence on 2007-04-03
I have not used the alternative version myself. So i won't give empty comments. But I have seen people having problem at their installation to use the alternative cd.

Maybe it will be good to do a search on alternative cd for a change.

Not sure if it has the Live CD option.

Alternatively, you might try to burn the DVD version. Buy from amazon or ..

I have found a ftp that provides dvd download
[ftp://ftp.acc.umu.se/mirror/cdimage.ubuntu.com/releases/edgy/release/](ftp://ftp.acc.umu.se/mirror/cdimage.ubuntu.com/releases/edgy/release/)

The DVD version basically has the livecd + alternative and with more add-ons that might not be included in the CD. So there might be a chance there are some drivers which will be in the DVD but not in the CD that might fix your problem.

Hope it helps.

---

### Post by rsambuca on 2007-04-03
If you want to try the liveCD environment, try pressing F6 (I think) for the boot options at the start menu.  Try adding ```
ide=nodma
```before the double '--' and leave a space before the dashes.  Then try booting.  If that doesn't work, there are other boot options to try out as well.

---

