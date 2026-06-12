---
title: "Uninstalling SuSe"
date: 2006-05-18
forum: Absolute Beginner Talk
---

### Post by Belathor on 2006-05-18
I installed SuSe 10.1 on a separate partition just to try it out. Now I am done with it. How should I uninstall it? Will just erasing the partition work? Or will that mess up my MBR?

Thanks!

---

### Post by Sef on 2006-05-18
I would just delete it with Gparted on a live cd or GParted by itself.  It won't mess up your boot partition unless you are booting from that partition.

[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

---

### Post by xXx 0wn3d xXx on 2006-05-18
[QUOTE=Belathor]I installed SuSe 10.1 on a separate partition just to try it out. Now I am done with it. How should I uninstall it? Will just erasing the partition work? Or will that mess up my MBR?

Thanks![/QUOTE]
Don't erase your Suse partition. It will cause grub to panic. Do the following steps:

1. Grab a Ubuntu install disc (Breezy, Dapper, whatever)

2. Boot it and continue through a normal installation until you get to the partitioning.

3. Delete your SuSE partition and then select your Ubuntu partition and make it the root filesystem + bootable flag.

4. Resize your Ubuntu partition if you want.

5. Make sure you have no, do not format selected for your Ubuntu partition.

6. Then select "Finish Changes and write to the disk."

7. And error message should come up, press "go back." You should be back at partitioning.

8. Press ESC and select install grub bootloader to the hard disk.

9. Grub will then install and update. Do not install the base system after that.

---

### Post by Mr Fat Bat on 2006-05-18
On a side note:

What did you think of SuSE 10.1?  I am about to install it onto my laptop for work, *while keeping Ubuntu as my primary OS of course ;)*

[URL="http://easylinux.info/wiki/Ubuntu_dapper"]
[/URL]

---

### Post by Belathor on 2006-05-18
> On a side note:

What did you think of SuSE 10.1? I am about to install it onto my laptop for work, while keeping Ubuntu as my primary OS of course 

I thought it looked great, but it was just too slow for my liking.

Thanks for the info everybody!

---

### Post by Belathor on 2006-05-18
Ok... I followed MasterChiefs instructions although with a little variation as I encountered different screen than I was expecting. Anyway, I reloaded GRUB onto my hard drive, however, it setup another completely unusable ubuntu operating system and boots to that. However, if I hit ESC, I can access my working Ubuntu partition. Is there a way to edit my GRUB bootloader to delete the false boot option and have it default to my real ubuntu?

Thanks!

---

### Post by Mr Fat Bat on 2006-05-18
Sure can!  Follow the awesomer guide here : [http://easylinux.info/wiki/Ubuntu_dapper](http://easylinux.info/wiki/Ubuntu_dapper)

There's a whole bunch of stuff on GRUB!

---

### Post by Mr Fat Bat on 2006-05-18
Just realised it does not mention how to remove the false option!

Just open /boot/grub/menu.list and remove the lines concerning the bad option ;)

---

### Post by Belathor on 2006-05-18
ok! Worked like a charm! Thanks Mr Fat Bat! :D

---

### Post by joshrobinson on 2006-05-18
> **Mr Fat Bat]On a side note:

What did you think of SuSE 10.1?  I am about to install it onto my laptop for work, *while keeping Ubuntu as my primary OS of course  said:**
> 
[/URL]

im an ex suse user, its a very beautiful and powerfull operating system.. ran fine on mine.. and its boot splash is 100000x better then ubuntu's (which drives me nuts all the time) but suse doesnt have as good of hardware support, at least for me
and installing software and tracking down dependencies is a long process

ubuntu is so much better..besides suse 's boot splash

---

### Post by r4ik on 2006-05-19
I am using SuSE on an AMD900 512mb and it works well.
Detected my hardware without any problems the only thing  i did whas turn off some services i dont need and installed another kernel.
Yast wont get a speeding ticket but every dist has its cons.
As soon as Dapper goes final i am planning a dual-boot and have a  look at both.
Time will tell what OS fits my hardware and skills the best.
Its the freedom of choise, i think i am a lucky person.

---

