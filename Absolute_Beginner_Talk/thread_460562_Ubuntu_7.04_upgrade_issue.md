---
title: "Ubuntu 7.04 upgrade issue"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by occiferfriendly on 2007-05-31
Hey all, first post.  Hope this is the right place for it.  

I've been using Ubuntu 6.10 for a little while now, and I decided to upgrade to 7.04.  I did that using the upgrade box.  

When I rebooted after it had done its business, it got to the Ubuntu load screen and just hung there.  It won't boot!  

I'm guessing I have to re-install 6.10 - but is there some way to help it boot?  

My specs are:
Pentium D 940
Asus P5LD2-VM
2GB OCZ Platinum RAM
WD 120 GB IDE drive
generic DVD ROM drive

Thanks for your help!

---

### Post by confused57 on 2007-06-01
> **occiferfriendly said:**
> Hey all, first post.  Hope this is the right place for it.  

I've been using Ubuntu 6.10 for a little while now, and I decided to upgrade to 7.04.  I did that using the upgrade box.  

When I rebooted after it had done its business, it got to the Ubuntu load screen and just hung there.  It won't boot!  

I'm guessing I have to re-install 6.10 - but is there some way to help it boot?  

My specs are:
Pentium D 940
Asus P5LD2-VM
2GB OCZ Platinum RAM
WD 120 GB IDE drive
generic DVD ROM drive

Thanks for your help!
I'm not sure, but you might need to check your menu.lst to see if the kernel line is using root UUID:
[http://users.bigpond.net.au/hermanzone/p15.htm#Fiesty_Fawns_new_menu.lst](http://users.bigpond.net.au/hermanzone/p15.htm#Fiesty_Fawns_new_menu.lst)

You can use the live cd, open a terminal & run the command:
```
blkid
```
this will show the UUID's of your partitions filesystems

then mount your root partition with the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

Check your /etc/fstab to make sure the UUID's are correct and your /boot/grub/menu.lst & change the kernel root to UUID(or make sure it's correct).

Not sure if this is your problem, but it would be a good place to start.

---

### Post by occiferfriendly on 2007-06-01
I have figured out the problem, 7.04 did not like my old DVD-ROM drive.  Took it out and it booted.  Thanks!

---

### Post by zrx1200 on 2007-06-02
where can i download a upgrade version of 7.04

---

### Post by digz6666 on 2007-06-21
How to upgrade live cd version of Ubuntu 7.04 to dvd version of Ubuntu 7.04?
I've installed Ubuntu from live cd. Then i've downloaded Ubuntu 7.04_dvd.iso and i need to install it from hard drive using previously installed live cd version of Ubuntu. What should I do? Please help me?

---

