---
title: "Problems using Ubuntu 9.10 live cd on Macbook Pro 5,4"
date: 2009-10-29
forum: Apple Hardware Users
---

### Post by g4reth on 2009-10-29
Hi all,

My apologies if this has already been covered elsewhere - I did a quick search, but to no avail.

Basically, I would like to use the Ubuntu live cd (currently 9.10, but have tried several other versions and other linux versions too) on a 2009 Macbook Pro 5,4 - without at this stage installing to the hard disk - but I cannot get it to work at all. It will boot to the point where it asks what language and then, when I try to install Ubuntu without making changes, it just hangs. I've tried various things on the menus - safe graphics etc - to no avail. 

I've used Ubuntu for years on PCs without (too many!!) problems, but I'm relatively new to the Mac and have to admit I'm stumped. I even installed rEFIt to see if that helped, though as I say, I don't want to actually install Ubuntu at this stage. No luck anyway - that didn't appear to do anything.

I should also say that I'm using Snow Leopard and that I can confirm the cd works on a PC, so seems to have burned correctly.

Would really value your help. Many thanks in advance,
G

---

### Post by pelle.k on 2009-10-29
I've got the same problem with a mac mini 3,1 (not the very latest model, but late 2009). The install cd just hangs at pressing "install" or "boot live system". I've tried a couple of tricks i read about concerning MBP's and ubuntu 9.10 - boot the cd with acpi=off (or nosmp/maxcpus=1). Maybe that works for you, but it didn't for me anyway.
Strangely enough, the latest beta and the RC worked flawlessly on this machine!

---

### Post by pelle.k on 2009-10-31
Well, i've had some progress with booting the live cd. The problem seems to be with the 32bit live cd, because the 64bit version works just peachy! Now that i think back, the beta's and RC i tried were 64bit too.

---

### Post by goldtree on 2009-11-14
g4reth,

I have the same problem as you describe (only I intend to install Ubuntu). I have been wanting to install linux on my Macbook 5.2 since I got it, but all the live-CDs I have tried froze when booting them.

What could be causing this? I will write you if I find a solution, and would appreciate if you did the same should you solve this.

Jimmy

---

### Post by goldtree on 2009-11-18
I realised what the problem was. I had to *turn off *the computer, then boot from the CD by pressing alt at start up. I then had to set the acpi=off at the grub menu (by pressing e). Now it is installed but I still have to press alt at start up since it doesn't show up in the Grub menu, and then turn off the acpi manually.

Jimmy

---

