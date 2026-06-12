---
title: "rEFIt boot error sudendly happened, reason ??"
date: 2018-08-02
forum: Apple Hardware Users
---

### Post by nandayo on 2018-08-02
Hello everybody,

I installed rEFIt on the macbook pro (2010 I guess) of a friend two years ago ; the macboo then could boot both on OS X (Lion I think) and Ubuntu (16.04 I guess, then LM 17).

Yesterday, she booted on OS X to play on steam (the only reason why OS X is still installed, better perf and compatibility than on LM), and today, when she tried to boot on Linux, she had screen error (see below...) More incredible, when booting on OS X, she also gets an error !


I took his laptop today, and made some tests. I had really strange behaviors :



1) The HDD is good, the linux installation is good, the OS X is good (more details below)

2) If I try to boot on OS X on rEFIt, it works perfectly (no errors, OS X works)

3) If on rEFIt I try to boot FIRST linux, then I get the floowing screen error 
[[img]https://image.noelshack.com/minis/2018/31/3/1533088040-attach46334-20180731-181116.png[/img]](https://www.noelshack.com/2018-31-3-1533088040-attach46334-20180731-181116.jpg)


AND, if THEN I return to rEFIT, and then boot OS X, I also get an error :
[[img]https://image.noelshack.com/minis/2018/31/3/1533088040-attach46336-20180731-181148.png[/img]](https://www.noelshack.com/2018-31-3-1533088040-attach46336-20180731-181148.jpg)

4) _More and more strange_ : if I plug an USB Linux live key, start rEFIt, and then try to boot the **USB key Linux** then rEFIt launches... THE GRUB of the Linux **installed on the HDD** (yes yes...), and then I can boot the Linux perfectly (the HDD one !), this is crazy !

5) Finally, more and more odd, always with the USB key pluged, if I try to launch the HDD Linux, then rEFIt launches... the Linux of the USB key...


It sounds like, I don't know, rEFIt was looking at a bad number of partition, and if I put the USB key, then it gives the (almost) good number of the Linux partition, and then I can boot it... but by choosing the USB Key Linux... Something like that... But I dont know how to check it, and then how to correct it.

BTW, I tryed to reinstall rEFIt from OS X, but it didn't change anything.

Many thanks for any help...


PS : She tells me she didn't make (or didn't notice though) any update neither on OS X nor Linux before this happened. This is a complete mystery to me, and I will take her mac to investigate, but I would be glad if someone has some ideas...

---

### Post by slickymaster on 2018-08-02
*Thread moved to **Apple Hardware Users**.*

---

### Post by nandayo on 2018-08-02
Oh great, thanks, I didn't see this category....

---

### Post by oldfred on 2018-08-02
Do not know Mac.

But it was my understanding that rEFIt is not maintained and rEFInd is the newer fork of rEFIt.
       [http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

You can create a bootable flash drive with rEFInd and see if that shows or will boot system.

And/or use Ubuntu live installer, add ppa for Boot-Repair and post link to its summary report. Those that know Macs may then see something out of place.
       
 May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by nandayo on 2018-08-02
Hello,

Thanks for that, I have the laptop now, I'll give it a try tomorry. 

I made some tests, and I have so precisions to add in the first post : I had really strange behavior... Here is a summary :


1) The HDD is good, the linux installation is good, the OS X is good (more details below)
2) If I try to boot on OS X on rEFIt, it works perfectly (no errors, OS X works)
3) If on rEFIt I try to boot FIRST linux, then I get the floowing screen error 
[[img]https://image.noelshack.com/minis/2018/31/3/1533088040-attach46334-20180731-181116.png[/img]](https://www.noelshack.com/2018-31-3-1533088040-attach46334-20180731-181116.jpg)


AND, if THEN I return to rEFIT, and then boot OS X, I also get an error :
[[img]https://image.noelshack.com/minis/2018/31/3/1533088040-attach46336-20180731-181148.png[/img]](https://www.noelshack.com/2018-31-3-1533088040-attach46336-20180731-181148.jpg)

4) _More and more strange_ : if I plug an USB Linux live key, start rEFIt, and then try to boot the **USB key Linux** then rEFIt launches... THE GRUB of the Linux **installed on the HDD** (yes yes...), and then I can boot the Linux perfectly (the HDD one !), this is crazy !

5) Finally, more and more odd, always with the USB key pluged, if I try to launch the HDD Linux, then rEFIt launches... the Linux of the USB key...


It sounds like, I don't know, rEFIt was looking at a bad number of partition, and if I put the USB key, then it gives the (almost) good number of the Linux partition, and then I can boot it... but by choosing the USB Key Linux... Something like that... But I dont know how to check it, and then how to correct it.

BTW, I tryed to reinstall rEFIt from OS X, but it didn't change anything.

Many thanks for any help...

---

### Post by nandayo on 2018-08-04
Thanks for the advice... It did the trick, that's perfect, thank you !

I will not know why rEFIt decided to crash finally, that's a bit frustrating, but, you know, anyway...

---

### Post by hrsetrdr on 2018-08-04
Glad you found a fix, gotta love Linux on a mac!  ;)

---

### Post by nandayo on 2018-08-05
Yes she has been enjoying Linux on her mac for years now, and thanks to you guys this will continue !

---

