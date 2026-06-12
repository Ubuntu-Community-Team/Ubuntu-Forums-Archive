---
title: "Installing Ubuntu"
date: 2011-08-01
forum: Apple Hardware Users
---

### Post by anw0625 on 2011-08-01
Can I install ubuntu by putting in the cd and restarting the computer by holding down the "C" key?  Or if not what is the best way?  Thank!

---

### Post by blane2 on 2011-08-01
Install it in virtualbox FIRST! Most people can use ubuntu just fine in virtualbox no problem... and it won't mess up your computer or your partition scheme. 

[http://moxiefoxtrot.com/2009/01/05/installing-ubuntu-810-in-virtualbox/](http://moxiefoxtrot.com/2009/01/05/installing-ubuntu-810-in-virtualbox/)


I needed to dualboot because specific programs didn't work well in Vbox for me.

---

### Post by anw0625 on 2011-08-01
If I just want to run ubuntu do I still do that?

---

### Post by megabenman on 2011-08-01
> **anw0625 said:**
> Can I install ubuntu by putting in the cd and restarting the computer by holding down the "C" key?  Or if not what is the best way?  Thank!

Yes.  If you're using the desktop CD then there will be an install ubuntu icon on the desktop, just click that.

---

### Post by nazgul42 on 2011-08-01
Virtualbox is great for testing out the operating system, but I've found that if you don't have a fast computer, it runs too slowly to be useful. Installing it to the hard disk runs much more quickly.

---

### Post by blane2 on 2011-08-01
> **anw0625 said:**
> If I just want to run ubuntu do I still do that?

If you want to get rid of OSx then sure. 
Some people still say to keep a small section for osx so you can get any updates to firmware boot or hardware. 
Google MacBook pro Ubuntu wiki to find info about your specific systematic compatibility and work arounds 

Partition the drive manually in disk utility. Format msdos
Give yourself swap and primary partitions. 
Put boot loader on the primary Linux partition.
Format ext4 in Ubuntu installer mount point / 
Swap format as swap 

I've had good luck using refit as my boot loader on the mbp. You can change default system boot and time out time through the configuration.

---

### Post by anw0625 on 2011-08-01
How do I do the dual boot?  Thanks

> **blane2 said:**
> If you want to get rid of OSx then sure. 
Some people still say to keep a small section for osx so you can get any updates to firmware boot or hardware. 
Google MacBook pro Ubuntu wiki to find info about your specific systematic compatibility and work arounds 

Partition the drive manually in disk utility. Format msdos
Give yourself swap and primary partitions. 
Put boot loader on the primary Linux partition.
Format ext4 in Ubuntu installer mount point / 
Swap format as swap 

I've had good luck using refit as my boot loader on the mbp. You can change default system boot and time out time through the configuration.

---

### Post by blane2 on 2011-08-01
> **anw0625 said:**
> How do I do the dual boot?  Thanks


follow these instructions but skip the windows parts. (it worked just fine for me.) I did manual install of rEFIt though

[http://lifehacker.com/5531037/how-to-triple+boot-your-mac-with-windows-and-linux-no-boot-camp-required](http://lifehacker.com/5531037/how-to-triple+boot-your-mac-with-windows-and-linux-no-boot-camp-required)

---

