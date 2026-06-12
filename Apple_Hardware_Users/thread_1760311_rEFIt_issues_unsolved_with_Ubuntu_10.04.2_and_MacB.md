---
title: "rEFIt issues unsolved with Ubuntu 10.04.2 and MacBook Pro 5,1"
date: 2011-05-16
forum: Apple Hardware Users
---

### Post by feveryear on 2011-05-16
Hey all.

It has been a long time since I've explored the world of Ubuntu, and now I'm back. I am tryin to dual-boot Snow Leopard and Ubuntu 10.04.2 LTS on my MacBook Pro 5,1. Ubuntu installed fine, and if I hold the Option key at start up, I can access Grub2 to get to Ubuntu. When I start the MacBook Pro, rEFIt shows up, and it will select and boot into Snow Leopard just fine. When I run the partitioning tool, it says the tables are fine, no fixin needed. But when I select the Tux icon for my Ubuntu, it flashes the gray screen with the small gray Tux in the middle, and then the screen goes black and the MBP won't respond until I manually power it off and turn it back on. I've been back and forth everywhere tryin to find a fix for it, and I don't know how.

Some things I'm not sure matter or not, I installed GRUB to dev/sda4, which is my Ubuntu partition, like I did way back when I installed Ubuntu before. Is there anyway to dual-boot without rEFIt? I tried bootin into Snow Leopard from Grub and Grub2 and it didn't work either way. 

So either a fix for rEFIt that I haven't found yet would be appreciated, or a way to dual-boot without rEFIt or having to hold the Option button. I would prefer Ubuntu to be my default OS as well. The only reason I am keepin Snow Leopard on my MBP is for my iPod Touch and MBP updates. Installing Ubuntu as the only OS works perfectly fine for me, but I have yet to perfect the dual-boot installation.

Any help would be appreciated! Thanks!

---

### Post by jerrycal on 2011-05-17
> **feveryear said:**
> Hey all.

It has been a long time since I've explored the world of Ubuntu, and now I'm back. I am tryin to dual-boot Snow Leopard and Ubuntu 10.04.2 LTS on my MacBook Pro 5,1. Ubuntu installed fine, and if I hold the Option key at start up, I can access Grub2 to get to Ubuntu. When I start the MacBook Pro, rEFIt shows up, and it will select and boot into Snow Leopard just fine. When I run the partitioning tool, it says the tables are fine, no fixin needed. But when I select the Tux icon for my Ubuntu, it flashes the gray screen with the small gray Tux in the middle, and then the screen goes black and the MBP won't respond until I manually power it off and turn it back on. I've been back and forth everywhere tryin to find a fix for it, and I don't know how.

Some things I'm not sure matter or not, I installed GRUB to dev/sda4, which is my Ubuntu partition, like I did way back when I installed Ubuntu before. Is there anyway to dual-boot without rEFIt? I tried bootin into Snow Leopard from Grub and Grub2 and it didn't work either way. 

So either a fix for rEFIt that I haven't found yet would be appreciated, or a way to dual-boot without rEFIt or having to hold the Option button. I would prefer Ubuntu to be my default OS as well. The only reason I am keepin Snow Leopard on my MBP is for my iPod Touch and MBP updates. Installing Ubuntu as the only OS works perfectly fine for me, but I have yet to perfect the dual-boot installation.

Any help would be appreciated! Thanks!

You can remove refit...It should be in your home folder  (MacOSX) - just drag it to trash...
Then you'd be using "Option" key on start up --- it won't go to Ubuntu by default.
How to remove refit:
[http://refit.sourceforge.net/doc/c1s3_remove.html](http://refit.sourceforge.net/doc/c1s3_remove.html)

---

### Post by feveryear on 2011-05-17
I've removed rEFIt before, and found that way to dual boot, but I guess if that's the only way I can do it, because I can't get rEFIt figured out. thanks, jerrycal, I appreciate the input.

---

