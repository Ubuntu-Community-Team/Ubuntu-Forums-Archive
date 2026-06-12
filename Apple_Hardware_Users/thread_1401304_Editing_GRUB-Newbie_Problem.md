---
title: "Editing GRUB-Newbie Problem"
date: 2010-02-07
forum: Apple Hardware Users
---

### Post by wearyroad on 2010-02-07
Hey all, I've been working with Ubuntu on a macbook pro 2,2, and just  recently I installed the program (and I'm not too sure of the program's name) Startup Editor. (to configure the way  GRUB manages the startup) I chose to lower the default time it took to  boot into an OS from 10 seconds to 5, chose to display the GRUB menu in a  (I think...) 1200 by 900 resolution, and chose Mac OSX as my default  operating system. When I rebooted into Grub, however, several things  happened.

1, it starts off with the default OS as Memtest. (which I've run, and it  says things work fine.)

2, backstory: when I first dual booted both Mac and Ubuntu, Ubuntu  looked perfect but Mac loaded into a really bloated resolution, 800 x  600 instead of 1400 x 1150 (?) I think this has something to do with  changing the res. of GRUB, but now it loads into the 1200 x 900 res. 

3, I can no longer boot into Ubuntu. I get the error message that  "vga=795 is deprecated." (that's all I can read before the screen goes  blank)

Does anyone know what's going on, and/or how to help? The only thing I  have left to configure is the command line (from the GRUB interface) and  I'm most definitely a newbie at that. Anything is appreciated!



Thanks! 
-really (really) lost newbie.

---

### Post by linuxopjemac on 2010-02-08
I think you have to boot in safe modus, so you end up in a terminal then adapt the grub configuration file to your needs:

[http://members.iinet.net/~herman546/p20/GRUB2%20Splashimages.html#Boot_Menu_Resolution_](http://members.iinet.net/~herman546/p20/GRUB2%20Splashimages.html#Boot_Menu_Resolution_)

---

### Post by wearyroad on 2010-02-24
> **linuxopjemac said:**
> I think you have to boot in safe modus, so you end up in a terminal then adapt the grub configuration file to your needs:

[http://members.iinet.net/~herman546/p20/GRUB2%20Splashimages.html#Boot_Menu_Resolution_](http://members.iinet.net/~herman546/p20/GRUB2%20Splashimages.html#Boot_Menu_Resolution_)

it doesn't quite work for some reason, the GRUB doesn't take some of the commands your site recommended and I'm only good enough with CLI to understand (minimal) parts of what I'm typing, so I can't work around it myself. Any other suggestions?

---

### Post by linuxopjemac on 2010-02-25
I can't help you more, you are on your own here as far as I'm concerned:
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by wearyroad on 2010-02-25
can someone please post the code that appears for a dual boot linux in GRUB?

that is, in the GRUB menu 
select linux, 
hit "E", and 
write the code shown into a post here. 

At this point I think I could just copy and paste that code (or write it all out and execute it) and it wouldn't do any more damage to the poor computer... and this is one solution I can foresee working.

---

### Post by linuxopjemac on 2010-02-25
[http://mac.linux.be/files/Gallery/index.html](http://mac.linux.be/files/Gallery/index.html)

Command (m for help): p

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  GPT
/dev/sda2   *          26       20604   165293240   af  HFS / HFS+
/dev/sda3           20604       30036    75764648+  83  Linux
/dev/sda4           30036       30402     2935859   82  Linux swap / Solaris

---

