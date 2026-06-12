---
title: "Software to Wipe/Secure Free HD Space?"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by F_r_e_d on 2007-04-13
Does anyone know of any Linux software that will completely wipe, overwrite, and secure the free space on the hard drive (while at the same time leaving existing files untouched)?

Usually this involves overwriting the free space with random 0's and 1's, up to as many times as you specify.

Or is there possibly a way that this can be done by entering code at the command line?

---

### Post by atihimself on 2007-04-13
sorry, but why do you need it, just asking from interest

---

### Post by F_r_e_d on 2007-04-13
I do much of my banking and financial transactions on line, along with some trading for a few clients, and want to make sure the transactions are fully erased.

---

### Post by az on 2007-04-13
You can run badblocks on the space in write mode.  You can even specify different patterns to write and the number of times to go over.

man badblocks

---

### Post by F_r_e_d on 2007-04-13
Thanks for the info.  Is badblocks a program that I need to download?  Any help would be appreciated.

---

### Post by n3tfury on 2007-04-13
> **F_r_e_d said:**
> Thanks for the info.  Is badblocks a program that I need to download?  Any help would be appreciated.

if you typed "man badblocks" in a terminal, it explains it all

---

### Post by Marsolin on 2007-04-14
You could also try [Gringotts]("http://linuxappfinder.com/package/gringotts"), [Wipe]("http://linuxappfinder.com/package/wipe"), or [Scrub]("http://linuxappfinder.com/package/scrub").

---

### Post by doas777 on 2008-04-03
Check out this page: [http://www.techthrob.com/tech/securedelete.php](http://www.techthrob.com/tech/securedelete.php)

the sfill utility in the ubuntu secure-delete package seems to meet your specs. I havn't tried it yet but looks promising if it runs as advertised.

BTW I did man badblocks and wipe, but neither had a feature for free space. The dude that documented (and presumably wrote) wipe has a distinct personality to say the least. you may want to check it out just for kicks. I use wipe regularly for file shredding, but not really right for free space wipe on a partially used partition. a good app though.

---

