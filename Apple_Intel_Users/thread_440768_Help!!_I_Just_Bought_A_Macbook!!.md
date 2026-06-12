---
title: "Help!! I Just Bought A Macbook!!"
date: 2007-05-11
forum: Apple Intel Users
---

### Post by mshale on 2007-05-11
Ok, I just bought a Macbook.  I would like to know how i could transfer all of my files, settings, programs, etc (basically i want to copy my existing HD to the macbook.  As of right now, i have a toshiba satellite and am tripplebooting win xp, ubuntu, and kubuntu.  What i want to do is replace windows with OSX and have it on my new mac.  I also bought an external HD so could i possibly use Gparted to copy the linux partitions to the external, then use gparted to copy from the external to the mac HD?  Or would just swapping the HD b/n the two lappys the best way to go (if they are compatible, i don't know if they are)??

Thanks for all of your help!!

---

### Post by benanzo on 2007-05-11
I'm not certain what you want to do.  Do you want to have a dual-boot with OS X and Ubuntu on the new MacBook?  If that's the case I assume you mean that you want to move your existing Ubuntu (from your Toshiba) to your MacBook, right?

Here is a great guide on how to backup/restore your system without just imaging the partitions. [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

---

### Post by mshale on 2007-05-12
> **benanzo said:**
> I'm not certain what you want to do.  Do you want to have a dual-boot with OS X and Ubuntu on the new MacBook?  If that's the case I assume you mean that you want to move your existing Ubuntu (from your Toshiba) to your MacBook, right?

Here is a great guide on how to backup/restore your system without just imaging the partitions. [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

I believe that is exactly what i need. Thanks so much!! sorry that i didn't search, i had no clue as to what to search for.  I have a separate partition for all of my music and pics and stuff like that, is there a way that i can back that up together with the ubuntu files?  actually it would probably be better to do a separate backup for that.  Thanks again for your response :)

---

### Post by benanzo on 2007-05-12
Glad to help.

Just a word of warning, now that I understand your intentions, you will need to be careful if you want to move your / (root) partition to the new machine because much of the device-specific information is statically configured for your Toshiba, and will likely not work on the new MacBook.  One example is if the Toshiba used and ATA disk you're /etc/fstab is most likely going to list your / (root) parition as /dev/hda1 (or similar) but when you try to boot on the MacBook which uses a SATA disk, your disk will not be found at boot time because the / (root) has changed to /dev/sda1 (or similar).

My advice would be to backup just your /home/user directory and any global configuration files for your software (ie /etc/smb.conf if you use samba) and any other non-system files on the external disk.  Then just install (K)Ubuntu from scratch and restore your /home/user directory when it's done.  That will give you back all your settings etc.

---

### Post by mshale on 2007-05-12
Thank you for your warning.  Since you have given me an example of the kind of hard drive the mac uses, i now know that i could just shove the toshiba hdd into the mac and hope for the best (kidding).  I'm jsut saying that on my toshiba, ubuntu lists all of the partitions as sdas so it should all be compatible!  thanks for all of your help, if you have any more advice please fell free to give it!!

---

### Post by mshale on 2007-05-12
ok, so I've been doing some research, and it seems that it is quite difficult to have OS X, xp, and ubuntu on the same machine.  can i not just use gparted and partition the drive like i need it?  i love gparted.  it would be a shame to not be able to use it.  ok, so maybe windows isn't such a priority, if i don't install xp, could i still use gparted?  Any advice or input on personal experiences would be greatly appreciated. 

I've searched for howtos, but there are so many that give advice on a plethora of different routes to take.  I need a howto that will get me going, not do everything for me, just get the basic stuff up and running (like help with wifi, get isight working, and just get ubuntu working in general).

Thanks So Much!

---

### Post by ronocdh on 2007-05-13
> **mshale said:**
> ok, so I've been doing some research, and it seems that it is quite difficult to have OS X, xp, and ubuntu on the same machine.
Posh! It's a freaking snap with Feisty. Here's a brief overview:
[LIST=1]
[*]Install OS X and make sure it's set up in a way that makes you happy.
[*]Download the Boot Camp installer from Apple
[*]Burn a Windows XP drivers CD from the Boot Camp utility
[*](DO NOT USE BOOT CAMP TO PARTITION)
[*]Partition your drive using the terminal in OS X. Decide on the space you want for each OS, then slice it up. (I recommend you use FAT32 for Windows for easy sharing. OS X can read/write to ext3 with an installable filesystem you can find on SourceForge.)
[*]Install [rEFIt]("http://refit.sf.net").
[*]Install Windows XP to the 4th partition. Then install the drivers using the CD you burned in Boot Camp.
[*]Install Ubuntu on the last remaining partition. It will ask to use the same MBR as WinXP. Tell it, "No problem, dude, go right ahead."
[*]You win! Setting up drivers in Ubuntu would take a longer list. ;)
[/LIST]

Here are some guides to get you going (and they offer considerably more detail than I just have!):
[LIST]
[*][http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu)
[*][http://ubuntuforums.org/showthread.php?t=198453](http://ubuntuforums.org/showthread.php?t=198453)
[*][https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)
[/LIST]

Cool? Post back with any more questions!

---

### Post by godd4242 on 2007-05-13
If you want you can enable NTFS (Windows partion reading) in Ubuntu after you do everything ronocdh said. Share your files in between Ubuntu and XP if you haven't set it up already, just synatpic, NTFS and there should be one NTFS-config or somesuch.

---

### Post by sethdotcom on 2007-05-13
I really really want a macbook so bad

The only mac I own is an old Imac G3 400mhz , 768mb, OS X 10.3, 10GB hardrive 

but it is still a nice capable little machine,
your lucky

what are your specs of your new macbook?

---

### Post by mshale on 2007-05-14
Thanks for all of your help.  Just one last little question.  Am I going to have to make an extended partition so that the number of primaries doesn't ecxeed 4 (i still have to have a swap right?)

> **sethdotcom said:**
> I really really want a macbook so bad

The only mac I own is an old Imac G3 400mhz , 768mb, OS X 10.3, 10GB hardrive 

but it is still a nice capable little machine,
your lucky

what are your specs of your new macbook?

Here is a list of specs of the macbook so you can drool sethdotcom ;)

Intel Core 2 Duo (2.0 GHz)
2 GB RAM
80 GB HDD (will be replaced with my 120 GB after I receive it!)
Double layer Super Drive
iSight mirror so that i can take a pic of what is infront of me
It's also coming with a 120 GB external HDD for free
$400 in my pocket cuz i knew a guy and worked at a certain place.  I got the whole deal for just over $600 :guitar:

---

