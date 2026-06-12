---
title: "need help with partitioning for install in a dual boot system"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by BlueSilverMageDragon on 2007-12-31
what i have is this:

     /dev/sda
          /dev/sda1          ntfs          /media/sda1               125024MB     5900MB
          /dev/sda5          ntfs          /media/sda5               125024MB     3200MB
          free space                                                             8MB
     /dev/sdb
          /dev/sdb1          ntfs          /media/sdb1                250048MB     51800MB
          free space                                                             8MB

it asks for a mount point with a minimum size of 2GB and a swap partition of at least 256MB.  if i press enter without doing anything else it gives me the prompt "no root file system is defined" and the book i bought is for Ubuntu 6.10 and this is 7.10 (it doesn't seem to explain what i am looking for, unless i missed it).  i also have 2G ram on an amd 64-bit +3800 dual core.  i can do advanced things because i am lucky i think and i need to become a beginner before trying to become intermediate let alone trying to do advanced things.

   anyhow... my question is simple... what partitions do i need to make and what size should they be if not too small or too big?

i do already love linux even though i haven't even got it setup yet and i also take my hat off to all of the ubuntu community... great help and care from you all... thanx to all (even before i get what i know will be great help)

---

### Post by BlueSilverMageDragon on 2007-12-31
i also forgot to say that i know that i want to put my ubuntu on the /dev/sda5 partiong but i need sub-partitions it seems

---

### Post by eternicode on 2007-12-31
Well, the first step, of course is to back everything up.  All your important stuff anyways ;)

You will need to repartition the drive in order to install.  Unless you let the Ubuntu installer do the work for you (which is not as safe IMO).

Linux needs at least one linux-format (ext2, ext3, reiserfs, etc -- not FAT32 or NTFS) partition, and wants one swap-formatted partition.

From the partitions you posted, it looks like sda5 (a 125GB partition?) has about 3.2GB freespace.  If this is the case, and you just want to give Ubuntu the minimum hard drive space (and maybe expand later), then you probably want a swap partition of 256MB-512MB (with 2GB RAM, 256MB swap should be plenty) and the rest of the freespace for the root partition (where Ubuntu will install).

I would suggest using GParted (should be already on your Ubuntu LiveCD, if that's what you're using).  In GParted, sda should be already selected (from the menu in the upper-right corner of the window).  If you want 256MB swap and all the rest for Ubuntu, then you want to:

1) Shrink sda5 from the right.  In the "space after" textbox, make sure you have at least 8 MiB.
2) Create a new 256MiB swap-formatted partition from the unallocated space
3) Create a new ext3-formatted partition that takes up the remaining unallocated space.
4) click "Apply"

When it's done, it will re-scan your drives.  Make note of which new partition is swap and which is ext3 (sda6 vs sda7).

In the installer, when it shows you the partitions, it should have a column "Mount Point" and a column "Format".  Make sure the "Mount Point" column for the ext3 says "/" (root), and the "Format" checkbox is marked.  It should automatically setup your swap.

Actually...With 2GB RAM and a dual-core, you may not even need swap.  But better to have it and not need it, than to need it and not have it ;)

Post back with any questions (or to point out something I might have missed :p ).

---

### Post by BlueSilverMageDragon on 2008-01-01
hey... didn't forget about you but i've had too many things going on today to complete the install and i reinstalled windows xp a few times to see if doing it differently with partitioning would help but i am trying to do this blindly it seems.  anyway... i am working on it and i did want to say that the partition is 125GB because i split a 250GB hd (i actually have two due to a mistake in thinking one was bad and it wasn't so now i have two), so plenty of space for everything... lol.  the 3200MB refers to used space and so i have almost all of that partition available.

thanx for your help... i'll tell when i get it done here too

---

### Post by BlueSilverMageDragon on 2008-01-05
just to let you know... i reworked my hard drives so that i have windows all on one and ubuntu on the other... now my problem is... how do i get a selection type window or such to pick if i want ubuntu or windows to boot up?

---

### Post by eternicode on 2008-01-05
I'm assuming it currently boots straight to Windows? Do you know which drive Ubuntu installed GRUB to?

The easy answer would be to install grub to the master boot record of the primary hard drive.  However, if you want to use Windows' default bootloader, some other work will be required.  Alternatively, you could install grub on Ubuntu's hard drive (which is probably already the case) and make that HDD the primary one (the one which the BIOS boots off of)

---

### Post by BlueSilverMageDragon on 2008-01-05
what i did was after not being able to "know" what to do to setup a dual boot system... newb... lol.  what i have is two 250GB harddrives and finally put all my windows stuff to one and then took it off the system and booted ubuntu on the second which made it the first (i think).   after reconnecting the harddrive with windows it boots to ubuntu (which i don't mind) but i need to know how to go to windows for some things until i get everything situated on my ubuntu then i will erase windows from my memory... (the computer's too).

    thank you already for any help

---

### Post by Moop on 2008-01-05
You could probably boot into windows by changing which harddrive boots first in the bios. It's kind of a pain to enter bios setup everytime you want to switch OS's but it's a short term solution. You should have left the windows hardrive connected when you installed Ubuntu, you would have had a choice which OS to boot. 

You could also add XP to grub.  

[https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs]("https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs")

---

### Post by bumanie on 2008-01-05
Having setup the OSes in the way that you have, makes me think that you will have to enter bios each time you boot the computer and choose which drive to boot, depending on whether you want windows or ubuntu. 
Alternatively, if you have nothing important on the ubuntu install yet, you could reinstall it. i would suggest setting up a /root; a /swap as well as a /home partition if you decide to reinstall ubuntu.

---

### Post by BlueSilverMageDragon on 2008-01-05
i will reinstall ubuntu and let you know what happens... (i think you already know that but you can listen to a newb play around in confusion... lol)

---

### Post by bumanie on 2008-01-05
> **BlueSilverMageDragon said:**
> i will reinstall ubuntu and let you know what happens... (i think you already know that but you can listen to a newb play around in confusion... lol)

I should have said to make sure you have both hard drives plugged in when you do this. In theory, grub will recognise windows and should give you the option of which OS to boot.

---

### Post by eternicode on 2008-01-05
You don't have to reinstall Ubuntu for the sole purpose of reinstalling grub.

You just have to add Windows to the grub menu

[http://www.linuxquestions.org/questions/showthread.php?p=1911658#post1911658](http://www.linuxquestions.org/questions/showthread.php?p=1911658#post1911658)

---

### Post by BlueSilverMageDragon on 2008-01-05
i changed my setup and i reinstalled ubuntu on the second hard drive with both hard drives active and now it just starts windows without a choice.  the hard drives are the exact same so it makes it hard to change boots in bios too... i tried and i couldn't see that any change was made or not so i still a newb windows AND ubuntu pretender... so i do need the help and i do appreciate any help i can get... (i hope i remember all that i am given here too... but i'm not holding my breath for that to happen... lol):lolflag:

:guitar:guitars are easier for me to play than computers... but i try

---

### Post by BlueSilverMageDragon on 2008-01-05
ummm... i guess i should say that i would like to know how to get a choice before the OS starts up...

---

### Post by BlueSilverMageDragon on 2008-01-06
thanks to eternicode and bumanie for your help... i reinstalled ubuntu with both hard drives and windows connected and it still gave me trouble but i change a few plugs in the hardware of my computer and it started ubuntu... i had to download many new updates then... it all worked out for me and i have a choice now when i start up my computer. yeeeeaaa :popcorn:

now i can learn ubuntu with ease... (:confused:) but i am sure i will get where i want with everyone's help... thanks again!!!

---

### Post by eternicode on 2008-01-06
Glad you got it sorted out :)

Sorry it was such a hassle, though ;)

But I'm sure your learning curve is off to a great start ;)

---

