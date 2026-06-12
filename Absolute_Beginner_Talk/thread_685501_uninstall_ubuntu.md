---
title: "uninstall ubuntu"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by manzoor on 2008-02-02
Hi I mess with Ubuntu and Now when ubuntu is booting at the start, it gives me some error and then scroll on for more

so I can't really see whats written.

The only msg I can see is 

There are differences b/w boot sector and hardisk

so can any one tell me how to reinstall ubuntu without messing with the win xp installed on my hdd

I want to completely remove it and then install it again. How to uninstall GRUB too ?

---

### Post by jan quark on 2008-02-02
I would do the following

download the gparted live cd
[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

boot with it

format the ubuntu partition

install ubuntu once again on the free blank partition

---

### Post by mikeyphi on 2008-02-02
Check the name of your Ubuntu partition (eg sda3)

Start install with the LiveCD - when you get to partition choose 'Manual'
select your Ubuntu partition - select delete
now select the same (old and now deleted) partition space - configure as /
check the 'format' box....select apply

Ubuntu will install in the same space as your old system....MS should not be touched - as long as you don't make a mistake!!
Grub will be updated during the install.

---

### Post by manzoor on 2008-02-02
how to check the name of my partiotion (eg sda3 or sda4)
and what about swap partition do I also have to delete it ?

---

### Post by mikeyphi on 2008-02-02
If you only have MS and Ubuntu installed then when the partitioner scans your system - and you select 'Manual' - you will see your Ubuntu partition marked as 'ext3'
Don't worry about the Swap partition - leave it alone (it will be automatically included in the reformat process)

---

### Post by manzoor on 2008-02-02
ok When I restarted and the cd booted 

it loaded the linux kernel and then took almost 5 mins to load ubuntu when reached to the yellow screen stage it stopped there I don't know whats wrong

I dont have any unallocated space 

does the live cd needs some space to run ?

---

### Post by bumanie on 2008-02-02
As far as I know live cd's don't need any hard drive space (I stand to be corrected on this). The files on the cd are as brief as possible and unpack into ram, therefore if you live cd wont 'open' completely and it is the same cd you used before, I'm not sure what's wrong. You could do a scan of the cd to check for defects, heat, cold, light etc., can affect cd's. The other alternative is to download gparted live cd ([http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)) and format the partitions you want to reinstall ubuntu to and make the partitions as unallocated space. During install the partitioner should use this space. In theory you should not have to do this, but sometimes there are little gremlins hanging around that make theories defunct. Check the cd for defects first; also you can do a complete shutdown and reboot, just to set everything back to 'zero' in case something has got out of synchronisation.

---

