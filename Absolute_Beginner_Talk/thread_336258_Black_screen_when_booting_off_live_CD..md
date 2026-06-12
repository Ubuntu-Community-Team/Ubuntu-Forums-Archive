---
title: "Black screen when booting off live CD."
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by timlongs on 2007-01-11
Hey everyone.

I downloaded the iso, and put it onto a disc, as soon as I put the disc back in, (still on windows) a ubuntu file popped up, so I knew the disc was working.

So I restarted my computer and I got the ubuntu menu, and let it run, it started doing its loading, then stopped. And I got 2 messages about an error. Then a loud beep and the screen went black.

My graphics is: Nvidia GeForce Go 6150 and my Laptop is a Hp Pavillion dv6000.

Any help is great.

---

### Post by jvc26 on 2007-01-11
You need to run an md5 check on the downloaded iso (if this fails then you know there is a fault, whether it effects the autorun on the XP Pc or not) Then you need to burn at the lowest speed to reduce the chance of burn errors (which this may be a result of).

The other thing is - can you tell us what the error messages were? This will give as a much better idea of what is wrong.
Il

---

### Post by taurus on 2007-01-11
Can you get into a console by pressing <Ctrl><Alt>F2?  At the prompt, try to reconfigure X again with

```
sudo dpkg-reconfigure xserver-xorg
```
And if you're not sure about an answer, just use the default but use **vesa** for the driver of your graphic card.  Once you're done, press <Alt>F7 to get back to the Gnome.  You may have to press <Ctrl><Alt>Backspace to start X again.

---

### Post by dbott67 on 2007-01-11
It could be related to screen refresh rate. Most LCD panels run at 60Hz and for whatever reason when X windows starts, it goes to a higher refresh rate.

When you're at the blank screen, try pressing CTRL-ALT-F1 (or CTRL-ALT-F2).  If you get a terminal window then it's more than likely a refresh rate issue.

I needed to download the "Alternate ISO Image" to avoid this problem.

-Dave

---

### Post by timlongs on 2007-01-11
Right I'm going to reboot now, and see if I can get into this console.

I'll also take a picture of the error.

Ok, just tryed to reboot with the disc, same error and black screen, tryed the ctrl + alt + f1, nothing.
Heres a picture

[[img=http://img159.imageshack.us/img159/2903/dscf0562vg5.th.jpg]](http://img159.imageshack.us/my.php?image=dscf0562vg5.jpg)

Any help?

---

### Post by timlongs on 2007-01-11
*bump*

Did an MD5 check got this: B950A4D7CF3151E5F213843E2AD77FE3

---

### Post by jvc26 on 2007-01-11
Check that MD5 against the one for the cd you downloaded on the site (the md5s are above the downloads list on the ubuntu site if i remember rightly) If they match then the iso is ok, and it may be down to a burn error, in which case reburning at a low speed like x4 will reduce the chances of it happening again :)
Il

---

### Post by timlongs on 2007-01-11
I can only use 10 x burn speed using nero burning rom. What other programs can I use?

---

### Post by jvc26 on 2007-01-11
The correct md5s btw:
For 6.10: (From [ftp://ftp.easynet.be/ubuntu-iso/edgy/MD5SUMS](ftp://ftp.easynet.be/ubuntu-iso/edgy/MD5SUMS))
99c3a849f6e9a0d143f057433c7f4d84  ubuntu-6.10-desktop-amd64.iso
b950a4d7cf3151e5f213843e2ad77fe3  ubuntu-6.10-desktop-i386.iso
a3494ff33a3e5db83669df5268850a01  ubuntu-6.10-desktop-powerpc.iso

For 6.06: [http://se.releases.ubuntu.com/6.06/MD5SUMS](http://se.releases.ubuntu.com/6.06/MD5SUMS)
50e3912c555f98f7bca56b2a0200b205  ubuntu-6.06.1-desktop-amd64.iso
fb3af44c21f1f68cc25fda7edb8c1bd3  ubuntu-6.06.1-desktop-i386.iso
502911770ad173dbe82c698379ed7d11  ubuntu-6.06.1-desktop-powerpc.iso
(Just in case you couldnt find them :))

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)
Has a good pointer to a suitable app
Il

---

### Post by bcom on 2007-01-11
I used ImgBurn from [www.imgburn.com](www.imgburn.com) to burn a copy of the Alternate Install CD.  ImgBurn is a windows program.  It let me burn at 1x -- this solved installation problems I was having with other installation CDs burned at a faster rate/

---

### Post by timlongs on 2007-01-11
Ok, I managed to boot the live CD, I tryed to install it, and it didnt work, it said something about a place to install. 

*shrugs*

---

### Post by timlongs on 2007-01-11
*bump*

Guys any help?

---

