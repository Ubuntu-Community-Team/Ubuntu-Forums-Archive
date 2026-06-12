---
title: "Wireless Network - not detected"
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by DizMan on 2006-06-25
Hi there.

I've downloaded the DVD and booted Ubuntu a couple of times via the live CD function.

I have got a wlan integrated on my main board (ASUS P5GD2 deluxe). This is used to communicate with my Zyxel router (and other pcs). I'm using WEP encryption and no broadcasting of SSID. 

I ran the network utilities from the live cd, but it did not find my wlan card - only my regular giga lan card (also integrated on the main board). I hit the "help" button. In the help there was 4 buttons in the network dialog - and I had only 3. The one missing was "Add" - which i presume i could use to add the missing wlan card.

In the Device mangager I actually found the device. There was a lot of info e.g. that it is produced by Marvell.

Well without the net my Ubuntu affair will only last a weekend i'm affraid.

My question is: Is my lack of wlan support due to the fact that i'm running Ubuntu from the live CD? Will it be there if I install Ubuntu and run it normally?

Q2: I can see all my NTFS drives, but it seems they are not mounted. Can I get some software, so they can be read from Ubuntu - or do I have to convert them to FAT32 (i won't convert my XP system partition).

A nice thing though. I put in my USB memory stick. And ta-da - a file mangager window opened right away. I browsed my pictures and read some word and excel docs via Open Office (i think it was). No problemos what so ever. It looked just like the original docs. Impressive. So when my internet is up and running I think I'll discover that I really can use Ubuntu for my daily work... (especially when I get the Citrix Client to work as well so I can log in to my work computers).  :-D 

Hope to hear what to do!

---

### Post by neoflight on 2006-06-25
[QUOTE=DizMan]Hi there.

I've downloaded the DVD and booted Ubuntu a couple of times via the live CD function.

I have got a wlan integrated on my main board (ASUS P5GD2 deluxe). This is used to communicate with my Zyxel router (and other pcs). I'm using WEP encryption and no broadcasting of SSID. 

I ran the network utilities from the live cd, but it did not find my wlan card - only my regular giga lan card (also integrated on the main board). I hit the "help" button. In the help there was 4 buttons in the network dialog - and I had only 3. The one missing was "Add" - which i presume i could use to add the missing wlan card.

In the Device mangager I actually found the device. There was a lot of info e.g. that it is produced by Marvell.

Well without the net my Ubuntu affair will only last a weekend i'm affraid.

My question is: Is my lack of wlan support due to the fact that i'm running Ubuntu from the live CD? Will it be there if I install Ubuntu and run it normally?

Q2: I can see all my NTFS drives, but it seems they are not mounted. Can I get some software, so they can be read from Ubuntu - or do I have to convert them to FAT32 (i won't convert my XP system partition).

A nice thing though. I put in my USB memory stick. And ta-da - a file mangager window opened right away. I browsed my pictures and read some word and excel docs via Open Office (i think it was). No problemos what so ever. It looked just like the original docs. Impressive. So when my internet is up and running I think I'll discover that I really can use Ubuntu for my daily work... (especially when I get the Citrix Client to work as well so I can log in to my work computers).  :-D 

Hope to hear what to do![/QUOTE]

impressive....i dont think there will be any difference as far as hardware detection goes with respect to the installed and livecD cases....

search for your particular device in this forum or google and see  if you could get any specific info....or you could post somewhere in the hardware section...

good luck

---

### Post by az on 2006-06-25
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Maybe you need ndiswrapper.  You would need to install the system, then install ndiswrapper and your windows driver to see if it worked...


Ndiswrapper is an application that can take your window's wireless driver and use it in linux.  It is included, but not installed on the live cd.

---

### Post by RandomConjecture on 2006-06-25
And you can mount your NTFS drives just fine--read only support, mind you. Actually, I was surprised that Ubuntu (just switched from Debian) auto mounts my NTFS partition. Probably didn't for you if you're talking about external drives. 

If you can see all your NTFS drives...just mount them. In terminal: mount <partition name>. If you're talking about USB drives...they're probably sda1, sdb1, and so on. If you're talking about internal harddrives, they should be something like hdb1. (It goes hda, hdb, etc.) If you want them to mount automatically, you need to edit your /etc/fstab file. Try typing "sudo nano /etc/fstab" in the terminal. There's a column labeled <options>. You'll want to change 'no auto' to 'auto' on the drive you want automatically mounted. Don't auto mount an external drive.

Oh, also, probably ought to make sure they're NOT mounted. When a drive is mounted in linux, it gets mounted somewhere. the fstab file will tell you where. You then have to go to that location to browse the files. I believe they default to folders with /media in Ubuntu.

---

