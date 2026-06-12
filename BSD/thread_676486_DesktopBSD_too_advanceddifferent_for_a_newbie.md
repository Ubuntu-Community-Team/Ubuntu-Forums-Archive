---
title: "DesktopBSD too advanced/different for a newbie?"
date: 2008-01-23
forum: BSD
---

### Post by kiisu on 2008-01-23
Hey I've been experimenting with various distros but I am only a few months into Linux experiences. Any of you BSD users think it would be difficult for me if I went ahead and installed it? I have the liveCD burned and was able to boot into it no problem, and it was also the fastest liveCD i've used eyet.

My biggest concern will be getting my Atheros wifi card up and running, none of the distros I've tried yet have beeen able to automatically do it. So far I've always used ndiswrapper but I get the impression it would be different in desktopBSD.

Oh I'm on a Toshiba p200 rt1 computer with an Intel945 graphics if that helps. cheers.

---

### Post by mips on 2008-01-24
You won't know until you try. Trust in yourself.

---

### Post by kiisu on 2008-01-24
Very true. Have no fear ....

I think I will try dual booting this first. Will desktopbsd give me the option to partition while installing or should i use something like Gparted first? It will be my first attempt at dual booting.

Currently I have a standard full install of mint kde on my laptop.

---

### Post by mips on 2008-01-24
> **kiisu said:**
> Very true. Have no fear ....

I think I will try dual booting this first. Will desktopbsd give me the option to partition while installing or should i use something like Gparted first? It will be my first attempt at dual booting.

Currently I have a standard full install of mint kde on my laptop.

I have not tried Dbsd in a while so I cannot comment on the partitioner. I do however recall that bsd needs its own slice of the hard drive. So if you are comfortable with gpater use it and create a blank primary partition that can be used by bsd.

---

### Post by kiisu on 2008-01-24
Thanks for your continued help.

I just went ahead and did a full install. I figure I can always redo Mint, which will auto-partition. But so far there's no need. I'm in D-BSD now and it really is much faster. Not sure why my system dislike Mint so much, but hey, I'm happy, I finally found a kde system that works at the speed of gnome on my laptop.

All I'm kind of worried about is getting my wireless to work. It sounds daunting. Do I use nDiswrapper? The wiki is telling me to add a few lines to my kernel config file, is this true and if so where is that located?

(I know, newbie newbie newbie, please be gentle!!!)

---

### Post by kiisu on 2008-01-24
Should have said: the wifi card I have in my computer is Atheros ar5007

---

### Post by Bachstelze on 2008-01-25
First things first ;)

Do a *ifconfig -a* and paste what you get.

---

### Post by mips on 2008-01-26
> **kiisu said:**
> Should have said: the wifi card I have in my computer is Atheros ar5007

"The ath(4) driver supports all Atheros Cardbus or PCI cards, except those that are based on the **AR5005VL** chipset. A list of cards that are supported can be found at"

Your card might be based on the AR5005VL chipset in which case you would have to use the madwifi driver od NDIS.
[http://nighthack.org/wiki/EeeBSD](http://nighthack.org/wiki/EeeBSD) has instructions for the madwifi on freebsd7

---

### Post by kiisu on 2008-01-30
Thanks guys. I had some problems but it actually wound being a problem with the laptop. So its getting repaired. Hopefully it will return soon and I'm planning to setup a dual-boot with Mint as originally planned. desktopBSD intrigued me but I did have some problems with it, therefor I think its best to keep a fully functional operating system on there and tool around with BSD in my spare time.

I'm a little bit confused by the 'slice' of the hard drive that it requires. I take it that it can't be installed onto a linux partition, so what would I need to do in Mint in order to get my computer ready for a dual-boot BSD install?

---

### Post by mips on 2008-01-31
> **kiisu said:**
> ...I take it that it can't be installed onto a linux partition, so what would I need to do in Mint in order to get my computer ready for a dual-boot BSD install?

No you cannot install it in a linux partition. Just leave blank space on your hd after mint and let the bsd partitioner handle it for you.

I dunno what the DBSD partitioner looks like but this is how things work in standard FBSD, [http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/install-steps.html](http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/install-steps.html)

---

