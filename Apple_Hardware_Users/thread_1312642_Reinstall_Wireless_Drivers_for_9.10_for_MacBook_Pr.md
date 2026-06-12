---
title: "Reinstall Wireless Drivers for 9.10 for MacBook Pro"
date: 2009-11-03
forum: Apple Hardware Users
---

### Post by kettle on 2009-11-03
Hi 
I recently install 9.10 on my new macbook pro after great trials and tribulations.  After I finally got everything into a glorious working state I went ahead and installed the latest CUDA drivers from NVIDIA to do some GPU work.  As a result of this I believe the GCC package was downgraded, and as a result of that, my wireless support packages seem to have disappeared.
 
Presumably all the necessary packages are on the CD so I should (hopefully) be able to restore wireless functionality, but I have no idea what the packages are so I'm a bit stuck.

Anyone out there with a clue as to how I might proceed?

---

### Post by ALLurGroceries on 2009-11-03
You should probably post your model #, you can find it with:
```
dmidecode -s system-product-name
```

To tell what wireless card you have:
```
lspci | grep 802
```

This info will be necessary for anyone to help. ;)

Good luck.

---

### Post by kettle on 2009-11-03
Sorry about that, I guess I thought there might be a way to tell the cd to 'just reinstall networking' or something.

>MacBookPro5,3

>Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller



> **ALLurGroceries said:**
> You should probably post your model #, you can find it with:
```
dmidecode -s system-product-name
```

To tell what wireless card you have:
```
lspci | grep 802
```

This info will be necessary for anyone to help. ;)

Good luck.

---

### Post by ALLurGroceries on 2009-11-03
I'm not sure there is a package for the BCM4322 in Ubuntu. I could be wrong since I run Debian Sid. If you want to install it the manual way, you should be able to use the directions in my MBP5,5 guide here:
[http://forum.notebookreview.com/showthread.php?t=418403#wireless]("http://forum.notebookreview.com/showthread.php?t=418403#wireless")

Good luck. :)

---

### Post by alexmurray on 2009-11-04
Try reinstalling bcmwl-kernel-source:

```
sudo apt-get install --reinstall bcmwl-kernel-source
```

---

### Post by kettle on 2009-11-04
Thanks for the suggestions.  I've tried everything and seem to still be getting nowhere so I think i may have to just reinstall from scratch rather than waste more time trying to figure this out.  

It's mainly frustrating because it WAS working perfectly fine, but my installing the CUDA drivers seems to have broken *only* the wireless.  I believe it may have down-graded the kernel but there are just too many variables to bother with.  Reinstallation is a huge pain in the ***, but it will probably end up being faster than pulling my hair out over the wireless at this point.

It would be nice if there was an installer *just for wireless* instead of the collection of odds and ends there is right now.  Oh well, I've no one to blame but myself I suppose.

---

### Post by kettle on 2009-11-04
So just to follow up, I just finished re-installing 9.10 from scratch. 

Interestingly, I previously was unable to successfully install 9.10 from the CD, and was initially forced to install 8.04, then upgrade my way to 9.10.  
I thought I would have to repeat this onerous process again, but before embarking on that thankless quest, thought, what the hell, let's give 9.10 one more try.  Previously I had what I could only explain as issues with GRUB2 and rEFit, which disappeared when I installed 8.04.  

This time however, I had no problems with installation, no problems with the bootloader and best of all, no problems with the wireless.

Of course this result is probably just about useless to everyone else, for which I apologize, but it seems that some kind of magic has taken place, and for now at least my problems (aside from the annoyingly over-sensitive track-pad) are solved.

I shall go on my merry way with my OSX/Koala dual-boot MacBook Pro5,5.  Yay.





and thanks again for all the feedback.  even if it doesn't solve the problem directly it provides encouragement and fodder for further ideas.

---

### Post by linuxopjemac on 2009-11-04
nice to hear :)

---

### Post by dranorter on 2009-11-07
Hi, I have a possibly different problem but I hope it's OK to ask here. My system is a macbook1,1 and I just upgraded from Jaunty, which caused my wireless to stop working. Reinstalling from scratch is undesireable as I have a lot of stuff I would have to back up (I know I know, I should have backed it up before upgrading. I hadn't intended to upgrade this machine; it was a frivolous moment.)

What makes my situation different is that lspci | grep 802 gets me absolutely nothing. Why does Ubuntu think I have no wireless card??

Thanks,

-Dran

> **ALLurGroceries said:**
> You should probably post your model #, you can find it with:
```
dmidecode -s system-product-name
```

To tell what wireless card you have:
```
lspci | grep 802
```

This info will be necessary for anyone to help. ;)

Good luck.

---

