---
title: "Installing Ubuntu on a second HDD?"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by jacatone on 2007-02-08
Have an older HP Pavillion with two HDD's. Win98SE on C drive and D drive was used as a backup. How would I reformat this D drive and install Ubuntu 6.06 on it. Once installed, how would I access between the two drives and would I be able to access Windows from Ubuntu or is that only in separate partitions? Many thanks.

---

### Post by Denn1s on 2007-02-08
just insert the live cd into the drive, you may wat to try the alternate install if your laptop has not enougth ram. During the instalation you will be asked in wich hard disk you want to install ubuntu, if the disk is a slave, drive d: must likely be in linux hdb (it may not be), linux will also install grub wich is a boot menu that will ask you wich OS you want to start when u turn your computer on.

To access linux drive from windows you may want to use [this]("http://www.fs-driver.org/") driver                                 EDIT: i believe this will not work under win98...

To access windows drive from linux, just follow [this]("http://ubuntuguide.org/wiki/Dapper#Windows") guide

---

### Post by Hitchhiker42 on 2007-02-08
I'm kinda new here, but this was my exact situation. Ubuntu will handle the reformatting of D:\ for you automatically. If you choose to take up the entire drive, it will erase everything, so make sure you've gotten all your files off first. Also, make sure that it's set to reformat your slave drive, *not* your master drive.

Check out this site for info on how to see Windows, as well as loads of other useful information: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Seeing Ubuntu from Windows is proving to be a bit trickier, but I believe there's a program out there that will do it for 98. I'll post the link in this thread as soon as I can, as it's on my computer, whose rather old CPU finally kicked the bucket (Haven't replaced it yet). :(

---

### Post by boogiepop88 on 2007-02-08
when you boot from the ubuntu live cd and start the installation you can pick manually edit the partition table from the list of of formatting options. select your d drive and format it in ext3, and also make sure to create a partition twice the size as the amount of memory you have choose linux swap from the dropdown menu for that partition. When Ubuntu installs the grub bootloader will attach itself to windows MBR and give you a boot option of which OS to pick. Reading from windows: Ubuntu should see your windows HDD, cause i believe 98 should be formatted in fat32. which you can read and write to i believe.

---

### Post by boogiepop88 on 2007-02-08
i was late :P



you bring up a good point with 98, i've never tried it. What are your system specs on your 98 machine? If they are rather low, you might have a smoother running desktop with xubuntu.

---

### Post by Hitchhiker42 on 2007-02-08
@Denn1s
I don't think ext2fs will work for 98, because of some differences in the way 9x handles files. (However, if I'm wrong, I'd love to know, so I can use it on my machine *grins*)

---

### Post by xpod on 2007-02-08
If your giving Ubuntu the whole second drive you dont need to do any partitioning or messing around yourself as you can just point the partitioner towards "hdb" and tell it to "erase entire hdb"etc  and it will do everything for you.

Your windows 98 should be found and mounted automatically if it`s fat32.
The XP i once had on a fat32 drive was as far as i recall anyway.

---

