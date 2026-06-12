---
title: "I just installed Ubuntu, but...one problem."
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by Sk1ppy on 2007-07-31
So I found one of my old my old 40gig IDE harddrives and decided to pop it into my computer and load Ubuntu onto it. I put as slave to my dvd rom. I installed Ubuntu onto the HD and then restarted my computer. The only problem is I don't know how to boot to that drive. when i go into the boot menu on my dell it only comes up with my SATA HD and my dvd-rom. Help?

---

### Post by pofigster on 2007-07-31
Try setting your hdd to "cable select"

---

### Post by Sk1ppy on 2007-07-31
> **pofigster said:**
> Try setting your hdd to "cable select"

Nothing changed. :(

---

### Post by ~~Tito~~ on 2007-07-31
Go into the BIOS and look for select drive(brings up which drive to select) or change the boot order when ever you want to run windows or ubuntu.

---

### Post by Sk1ppy on 2007-07-31
> **~~Tito~~ said:**
> Go into the BIOS and look for select drive(brings up which drive to select) or change the boot order.

In the BIOS it doesn't show up as a drive. :(

---

### Post by brocolli on 2007-07-31
Double check the jumper settings of your drive and make sure about the connection (master or slave).

---

### Post by Sk1ppy on 2007-07-31
Which should be the master, the dvd rom or the harddrive with Ubuntu on it?

Does it matter?

---

### Post by thedude88 on 2007-07-31
I always thought you were only able to put a hd on a hd only cable & that you couldn't mix and match a cd-rom and hd on the same cable. I could be wrong though...

---

### Post by ndefontenay on 2007-07-31
A long time ago, I read something about this.

I think that to have it booting, you should either:

1) Put your HD as a slave with your primary hard disk as a master.
2) Plug it on your CD-ROM cable as a master and the CD-ROM as a slave.

My favorite option would be to have it slave along with the primary hard disk as a master.

If well installed, you should have been prompted to boot on your Linux distro or windows at startup, with Linux being the default option.

---

