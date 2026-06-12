---
title: "USB Full Install Problems - GRUB"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by scottb613 on 2008-02-08
All,

    Hi - I am brand new to Linux and this is my first experience with ubuntu,,,
    I like what I see so far,,,

    I have made my bootable CD - and - I have also created a bootable USB chip with ubuntu... The USB is persistant with the LIVE partition and the Casper RW partition,,,

   All works as advertised... 

   I now wanted to install the full blown version on my 4GB USB Flash Drive... After several attempts I now have a working copy of ubuntu loaded on USB - however - I have two issues,,,

   1) I messed with the advanced tab and it installed the GRUB Boot Loader... The problem is the laptop will not boot unless the USB chip with ubuntu is installed ??? Can I fix this and get the laptop to boot off of my Vista hard drive agaitn ??? I get a GRUB error 21 - I think - immediately after boot,,,

   2) The USB chip with ubunto - will only boot off the laptop I installed it on... Any other machine does not see it as a bootable device... Can I make this good install - work off any other machines ???

Thanks.
Scott

---

### Post by Afkpuz on 2008-02-08
Generally, GRUB cannot dynamically change to match hdd setups.  I would suggest installing on your main hdd.  If you have a windows partition, you can use gparted and keep your data.  But as a rule, if you install the real deal on a flash drive, that needs to stay with the computer you installed it on.  If you want a trying dynamic ubuntu, use the live CD or follow instructions on pendrivelinux.com

---

### Post by scottb613 on 2008-02-08
Hi...

Thanks for the quick response...

Do I have to use GRUB ???
Can I not make this Full Version of ubuntu boot without grub ???
It's already on my chip...
Am I missing something ???
You know - just like the original USB Persistent install on my USB...
That works without GRUB - right ???

Also - is there any hope for my existing Vista install...
Any suggestions on how to recover ???
The windows file systems all seem to be in tact - it's just that GRUB appears to be mangled...

Again - thanks for taking the time to respond...

Regards,
Scott

---

