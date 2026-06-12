---
title: "Is it possible to remove &quot;press ENTER&quot; when shutdown PC"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by saknarak on 2007-07-25
How to shutdown PC without press ENTER to power down PC

---

### Post by aysiu on 2007-07-25
It's to allow you time to take the Desktop ("live") CD out of the drive before the computer shuts down.

---

### Post by saknarak on 2007-07-25
After I'd install on harddisk, when i shutdown, it still have 'press Enter' to power down
can i modify the shutdown script

I found I can change start up script by modify initrd.gz (casper-bottom)
but i can't find sequence file that use for shutdown process

---

### Post by az on 2007-07-25
> **saknarak said:**
> After I'd install on harddisk, when i shutdown, it still have 'press Enter' to power down
can i modify the shutdown script

I found I can change start up script by modify initrd.gz (casper-bottom)
but i can't find sequence file that use for shutdown process

Once the installation is complete, casper should be completely removed.  Did the installation throw out any error once done?

Try 

sudo apt-get -f install 

and then

sudo apt-get remove casper

---

### Post by saknarak on 2007-07-26
Thank you for your reply.
I'm running Ubuntu from USB with persistance option so casper still exists.
I wonder if someone can modify shutdown script to ignore the press ENTER at the last.

---

