---
title: "File system help"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by man-man on 2006-10-08
This probably gets asked a lot, but Google wasn't as helpful as normal (I'm probably just searching for the wrong thing ;) 

Anyway, what file systems are there that I can use to dual boot Ubuntu and WinXP and let both read + write to the disc? I know Fat32 will do this but there is also the issue of max. disc size being 137gb - so no good unfortunately :( 

Basically I'm looking for a way to either get Windows to write to the Linux file structure, or for Ubuntu to write to NTFS. I've read some stuff about the second option but I dont know how easy and/or reliable they are. 

Any advice or helpful links you can give would be great :mrgreen:

---

### Post by Kateikyoushi on 2006-10-08
Ext is your friend, reliable and writeable from windows and free.

[LINK]("http://www.fs-driver.org/")

---

### Post by aysiu on 2006-10-08
The max disc size for FAT32 that Windows can make is 30 GB, I think, but Linux can make much larger FAT32 partitions. I used to have my external hard drive (160 GB) as one big FAT32 partition.

Ext3 works just fine with the link Kateikyoushi posted.

FAT32 will work fine without extra drivers, as long as you don't have files bigger than 4 GB.

---

### Post by jaboua on 2006-10-08
Yes, writing ext from windows works fine. If you install the "ntfs-3g" driver, linux should also be able to write to NTFS without problems (you have to mount it as ntfs-3g filesystem though, not as ntfs - just remember that when you set up /etc/fstab ;)). Both solutions has worked for me before.

---

### Post by man-man on 2006-10-08
Wow, you guys are quick :) 

So would the easiest option would be to have the disc in the linux format (i have got my facts right - ext3 is the linux file system right?)

Will windows figure it out on its own or do i need to fiddle with the settings?

---

### Post by jordanmthomas on 2006-10-08
Actually, there's lots of Linux filesystems, but ext3 is the best in my opinion.

If you install the drivers from [http://fs-driver.org](http://fs-driver.org) it will ask you to assign a drive letter to your new partition and then you're good to go.

---

### Post by man-man on 2006-10-08
fair enough :) 

hmm.. now i realise i dont know how to set that up ](*,) 

what im thinking of here is having a partition each for linux and windows to install into then the rest of the disc in ext3 format to put all my files in. Is that right?

So.. if i install Ubuntu, set up the partitions in the process then install XP and put it in the partition i made, would that work?

---

### Post by jordanmthomas on 2006-10-08
Yes, but installing XP would wipe out Ubuntu's boot loader (GRUB)

It can be recovered, though.  Personally, I would partition, install XP, and install Ubuntu after XP.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
^^if you decide to put XP on second

---

### Post by man-man on 2006-10-08
okey dokey, so can i partition the disc during windows install? 
or is it a command line job?

---

### Post by jordanmthomas on 2006-10-08
You can use the Ubuntu CD to partition before installing anything
System --> Administration --> Gnome Partition Editor

It's nice and graphical.
I'm pretty sure the Windows installer will let you partition, but it won't be graphical.

---

### Post by man-man on 2006-10-08
and there i was thinking that windows was going to be the one with a shiny button to do these things with

maybe they only include nice graphics for stuff they want to encourage you to do - a normal install of windows that doesnt involve any other OS doesnt need partitions setting up

---

