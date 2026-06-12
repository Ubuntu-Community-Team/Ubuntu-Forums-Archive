---
title: "Macbook Tripleboot Correct?"
date: 2007-12-07
forum: Apple Intel Users
---

### Post by HARTEngr on 2007-12-07
I just finished installing WinXP and Gutsy (Ubuntu Linux 7.10 "amd64") on my Macbook (Intel Core 2 Duo, 1GB RAM, 111GB hard drive). I can boot into all three OSs and start a browser. Haven't tried much else yet. 

The reason for my post is that I had no trouble whatsoever (that can't be right for me!) even though I did not install any boot loaders or execute many of the commands I found on various webpages related to the Linux installation part for triple booting on Macbooks.  I am booting from the hard drive partition where I installed Gutsy (the installation CD has been ejected), so obviously the bootloader must be in place. I just wanted to make sure that nothing will come crashing down once I start doing real work in Linux because I omitted to execute a few things.

After installation, I did create the swap file and edited /etc/fstab as per the instructions on 
[http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu)
Do I need to do anything else? The above instructions are for Edgy (Ubuntu 6.10, ca Oct. 2006), so I am wondering if I can ignore all the steps related to boot loaders and such.

Thanks!

---

### Post by cyberdork33 on 2007-12-10
that is outdated. You should be fine. 

The only issue is that you might want to make the changes noted in the "multi boot properly' tutorial in my signature as you will have to go through grub to get to windows unless you have installed grub to the Ubuntu partition rather than the MBR.

---

### Post by HARTEngr on 2007-12-10
Thanks for your reply. I read your tutorial page. I am not sure what got done behind the scenes because I did not manually run Bootcamp at any time (I installed it on my Macbook following the various instructions I saw on-line). I did run "enable.always.sh" from the /efi/refit directory after installing rEFIt and making partitions for the 3 OSs via the "diskutil" command from an OS X terminal. I couldn't tell what Bootcamp's purpose was besides creating partitions, so I didn't see the need to invoke it. 

After installing Linux, I don't recall seeing any "Advanced" button (and certainly didn't click it, if it was there) and did not get asked about installing bootloaders (Grub or anything else) but Linux seems to come up fine from the hard drive. Do I assume that Grub or some other bootloader got automatically installed in the right place?

FWIW, I installed XP first and then Linux and rEFIt shows me the three OS icons when I power up the Macbook.

Thanks.

---

### Post by cyberdork33 on 2007-12-10
bootcamp has nothing to do with this, although many use it to partition the drive. (Bootcamp, in fact, just invokes the same command you used to accomplish this).

> **HARTEngr said:**
> After installing Linux, I don't recall seeing any "Advanced" button (and certainly didn't click it, if it was there) and did not get asked about installing bootloaders (Grub or anything else) but Linux seems to come up fine from the hard drive. Do I assume that Grub or some other bootloader got automatically installed in the right place? it is during the install, not after. Ubuntu does not prompt you to install a bootloader and/or ask you for a location. The advanced button is where you make changes to that.

> FWIW, I installed XP first and then Linux and rEFIt shows me the three OS icons when I power up the Macbook.Yes, as it should, but I am willing to bet that selecting the Windows Icon starts Grub... If not, then just don't mess with it.

---

### Post by HARTEngr on 2007-12-11
I think that my setup must be ok then. 

I powered down the Macbook completely and selected Linux to boot into from the rEFIt options and it came up fine without me executing any commands to load GRUB. I didn't start XP at all. 

JFYI, as it was coming up,  "GRUB loading stage2" was displayed, soon followed by the following 4 options (don't recall precise details):

- Ubuntu 7.10...kernel 2.6....generic
- Ubuntu 7.10...kernel 2.6....generic (recovery mode)
- memtest86+
- Other OSs
   Windows XP

The first option was selected by default and I let it boot the default.

Thanks.

---

### Post by cyberdork33 on 2007-12-11
> **HARTEngr said:**
> I think that my setup must be ok then. 

I powered down the Macbook completely and selected Linux to boot into from the rEFIt options and it came up fine without me executing any commands to load GRUB. I didn't start XP at all. 

JFYI, as it was coming up,  "GRUB loading stage2" was displayed, soon followed by the following 4 options (don't recall precise details):

- Ubuntu 7.10...kernel 2.6....generic
- Ubuntu 7.10...kernel 2.6....generic (recovery mode)
- memtest86+
- Other OSs
   Windows XP

The first option was selected by default and I let it boot the default.

Thanks.

yes that is fine, and the normal operation, but what happens when you select the Windows icon in rEFIt?

---

### Post by HARTEngr on 2007-12-12
Ah yes.  GRUB comes up again and gives me the same options when I select XP from rEFIt, as it did for Linux. The first (and only) time I had booted into XP, I had not installed Linux yet, so it went into XP directly.

So, is not having the boot loader in the right place just an annoyance or a real functional issue/likely to cause trouble in the future?

Thanks.

---

### Post by cyberdork33 on 2007-12-12
> **HARTEngr said:**
> Ah yes.  GRUB comes up again and gives me the same options when I select XP from rEFIt, as it did for Linux. The first (and only) time I had booted into XP, I had not installed Linux yet, so it went into XP directly.

So, is not having the boot loader in the right place just an annoyance or a real functional issue/likely to cause trouble in the future?

Thanks.

annoyance, and especially so if your keyboard doesn't work in grub like many...

---

### Post by HARTEngr on 2007-12-12
Cool! So I won't fix what ain't really broke, and trust my Macbook kbd to continue to behave. 

Thanks a lot for all your feedback.

---

