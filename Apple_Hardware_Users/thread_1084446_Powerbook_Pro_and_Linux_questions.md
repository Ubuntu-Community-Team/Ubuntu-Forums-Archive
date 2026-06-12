---
title: "Powerbook Pro and Linux questions"
date: 2009-03-02
forum: Apple Hardware Users
---

### Post by dman777 on 2009-03-02
I am thinking about buying a new laptop. The only ones that really appeal to me are the Macbook Pro's. My main system is linux and I'd rather die than not use linux. Here's are my musts:

Linux
Compiz Fusion 
Virtualbox with Windows XP guest.

Will all this work on a Macbook Pro? Will it be buggy? Can I expect the above to run just as good on the Macbook Pro as it would on a PC laptop?

---

### Post by cyberdork33 on 2009-03-02
> **dman777 said:**
> I am thinking about buying a new laptop. The only ones that really appeal to me are the Macbook Pro's. My main system is linux and I'd rather die than not use linux. Here's are my musts:

Linux
Compiz Fusion 
Virtualbox with Windows XP guest.

Will all this work on a Macbook Pro? Will it be buggy? Can I expect the above to run just as good on the Macbook Pro as it would on a PC laptop?
If you don't want to use OS X, then don't get a Mac. It much easier to buy a machine designed to be Linux-Compatible.

---

### Post by khelben1979 on 2009-03-02
Since the Powerbooks uses intel hardware nowadays, "I think" that it is going to work pretty good. ASUS PC:s would probably work much better with any Linux distribution, though.

I think that [Yellow Dog Linux]("http://en.wikipedia.org/wiki/Yellow_Dog_Linux") might be a very attractive Linux flavour in this regard. Have you ever heard about it? 

I have never tried the distribution myself, but I have read about it several times on the net, and it seems pretty cool. My own favourite will always be Debian, though.

---

### Post by cyberdork33 on 2009-03-02
> **khelben1979 said:**
> I think that [Yellow Dog Linux]("http://en.wikipedia.org/wiki/Yellow_Dog_Linux") might be a very attractive Linux flavour in this regard. Have you ever heard about it? 
YDL is only for PowerPC hardware.

---

### Post by khelben1979 on 2009-03-02
> **cyberdork33 said:**
> YDL is only for PowerPC hardware.

I see. In that case it probably works good with older mac hardware using PPC then.

---

### Post by dman777 on 2009-03-02
> **cyberdork33 said:**
> If you don't want to use OS X, then don't get a Mac. It much easier to buy a machine designed to be Linux-Compatible.

Isn't the hardware the same as a PC now(Motherboard and CPU)? is this only because of the EFI or other issues also? 

The Macbook Pro's have everything I like in a laptop hardware wise, rather the PC laptops all have something I don't like(various).

---

### Post by buntuLo on 2009-03-02
Dman,
i perfectly agree with you, and Macbook Pro was my choice. i never used macosx and i didn't spend more than ten minutes with it in the first two months with this laptop. i believe it's a great os, but my choice is simply for open source software.
Cyberdork is correct in saying that there are many other machines with much better support (thinkpads first of all) in gnu\linux, but i consider this last creature from cupertino being worth the (relatively small) efforts to setup a usable linux system on it :~)
the main problem is power management: short battery life and high temperature. have a look at the documantation page [MacBookPro5-1Intrepid]("https://help.ubuntu.com/community/MacBookPro5-1/Intrepid")
 to get an idea and judge yourself based on your expectations and needs. Lo.

---

### Post by dman777 on 2009-03-02
> **buntuLo said:**
> Dman,
i perfectly agree with you, and Macbook Pro was my choice. i never used macosx and i didn't spend more than ten minutes with it in the first two months with this laptop. i believe it's a great os, but my choice is simply for open source software.
Cyberdork is correct in saying that there are many other machines with much better support (thinkpads first of all) in gnu\linux, but i consider this last creature from cupertino being worth the (relatively small) efforts to setup a usable linux system on it :~)
the main problem is power management: short battery life and high temperature. have a look at the documantation page [MacBookPro5-1Intrepid]("https://help.ubuntu.com/community/MacBookPro5-1/Intrepid")
 to get an idea and judge yourself based on your expectations and needs. Lo.

Wow, thank you. This gives me more insight.

I prefer a raw Linux/GNU system:
Gentoo 
Compiz Fusion
No desktop managers/Guis(I use strictly command line with urxvt windows). 

I want to stick with this if I got a Macpower book. Where would I get the modules/packages to enable MAC hardware outside of the Ubuntu/Debian repositories?

---

### Post by cyberdork33 on 2009-03-02
> **dman777 said:**
> Isn't the hardware the same as a PC now(Motherboard and CPU)? is this only because of the EFI or other issues also? .
There is the EFI thing, though it is not too bad for single-booting.

It is things like the use of non-Linux-Friendly hardware choices that make it difficult. WiFi card is proprietary (Broadcom), Video Card is Proprietary, etc. A system designed for Linux just has much more compatible hardware choices included.

---

### Post by buntuLo on 2009-03-02
> **dman777 said:**
> Wow, thank you. This gives me more insight.
I prefer a raw Linux/GNU system:
Gentoo 
Compiz Fusion
No desktop managers/Guis(I use strictly command line with urxvt windows). 
I want to stick with this if I got a Macpower book. Where would I get the modules/packages to enable MAC hardware outside of the Ubuntu/Debian repositories?

if gentoo is your choice, you'd better read - and ask :~) - here:
[http://en.gentoo-wiki.com/wiki/Apple_Macbook_Pro]("http://en.gentoo-wiki.com/wiki/Apple_Macbook_Pro")
as written around half of the page, you can give the mactel kernel-patches (for vanilla-source) a try:
[https://mactel-linux.svn.sourceforge.net/svnroot/mactel-linux/trunk/kernel/]("https://mactel-linux.svn.sourceforge.net/svnroot/mactel-linux/trunk/kernel/")
also have a look at the links at the bottom of the page.
anyway, try using google with the keywords: "macbook pro" 5.1 aluminium unibody. ciao, Lo.

---

### Post by dman777 on 2009-03-27
> **buntuLo said:**
> if gentoo is your choice, you'd better read - and ask :~) - here:
[http://en.gentoo-wiki.com/wiki/Apple_Macbook_Pro]("http://en.gentoo-wiki.com/wiki/Apple_Macbook_Pro")
as written around half of the page, you can give the mactel kernel-patches (for vanilla-source) a try:
[https://mactel-linux.svn.sourceforge.net/svnroot/mactel-linux/trunk/kernel/]("https://mactel-linux.svn.sourceforge.net/svnroot/mactel-linux/trunk/kernel/")
also have a look at the links at the bottom of the page.
anyway, try using google with the keywords: "macbook pro" 5.1 aluminium unibody. ciao, Lo.


That link helped alot, thanks. But now I want to get teh 13.3 Macbook and it's not considered a "Macbook Pro", even though it still has the intell chipset. The Gentoo wiki list only the "Macbook Pro" line as the supported hardware. Is there a difference in hardware between the 13.3 Macbook and the Macbook Pro line? Am I taking a risk with the 13.3?

---

