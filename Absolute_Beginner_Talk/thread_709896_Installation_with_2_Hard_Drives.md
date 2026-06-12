---
title: "Installation with 2 Hard Drives"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by Whitelyte on 2008-02-27
I am new to Linux, and have limited knowledge about computers.  I know I need to put some time and work into this installation, but I need some tips.   I have three hard drives and would like to have the dual boot option.  I would like to keep windows on one HD, Unbuntu on the second, and use the third for data (FAT32).  The HD for Unbuntu is 40GB and currently in NFTS format.  How do I change the format to FAT 32?  I have down loaded Unbuntu and burned it to a disc and defragmented all the hard drives.  Could someone please let me know how to arrange the hard drives, and anything else I need to organize, so the installation of Unbuntu can go as smooth as possible.  My wife will be home in 6 days.  Thanks.

---

### Post by halitech on 2008-02-27
when you are installing Ubuntu, it will give you an option of taking over the entire drive (make sure you select the right drive) and it will format it for you. You also don't want the Ubuntu drive as FAT32, you want EXT3

---

### Post by bobpur on 2008-02-27
First of all, don't let this process intimidate you. It's really easy. The CD does everything. 
When you fire up the CD just follow the prompts, remembering which drive you want to use for Ubuntu. After clicking "install" on the "Live CD" screen, you will be prompted for this information. PAY ATTENTION to the prompts. Ubuntu takes care of the formatting. Oh Yeah! BACKUP your Windows drive. Nobody's perfect and you might accidentally end up with an all Ubuntu machine before you're ready:)
Sorry if this is a bit disconnected, but it's been a long day. The info is good, though.

Good Luck!

---

### Post by bobpur on 2008-02-27
It's me again!
Your 1st drive (hda) should be your Windows drive. If you have to do a clean install of everything, Windows should be installed first as it tends to overwrite the bootloader (GRUB) making anything else installed inaccessible. 
Your Ubuntu drive (hdb) can be installed next (after Windows).
I labeled your drives as hda and hdb as if they were the older drives with the big wide flat ribbon cable and the 4-pin molex connector. If they are the newer SATA drives, they would be sda and sdb. 
If you're using Ubuntu 7.10 you won't have to format your storage drive to FAT32. This version of Ubuntu can read and write to a NTFS partition. Am I right on this one? Anybody? I don't have my Ubuntu machine hooked up at the moment to verify this but I believe I'm correct. I'll have to get back to you on this one... in the morning.
I'll keep an eye on your post if you run into any problems.

---

### Post by Whitelyte on 2008-02-28
Thank you for all of the information.  I am going to use this information and give the installation a try on Sunday.  I did not expect such quick replys.  Take care and thanks for your time.

---

### Post by go_lanche on 2008-03-29
This has been really helpful to me, I am also wanting to do a three hard drive setup with a communal media storage drive. The problem I am concerned about is the fact that the drive I had reserved for linux is my master drive. Will this present any problems? Also, if I am worried about potentially overwriting my media drive can I just unplug it during the install and then plug it back in when all done with the ubuntu install? Thanks.

---

### Post by luceerose on 2008-03-29
If you are not installing an OS on the communal drive you've pretty much got zero chance of buggering it up. Just don't format the communal drive.

My only other advice is, if you are installing windows & ubuntu with dual boot, then install windows first & ubuntu 2nd.
It's just that ubuntu automagically detects windows & writes the grub file for you. It makes things very easy.
And if ever thinking of installing multiple Linuxes on one computer, installing the one you will mainly be using last (for the same reason as the windows thing above).
It's easy enough to edit grub and change it's 'Level 1', if you know how, but installing things in the right order will save you the trouble.

And when dual booting with windows, (iff windows is on the secondary drive), you should ensure the menu.lst file has;
map		(hd0) (hd1)
map		(hd1) (hd0)
near the bottom of the windows section

---

### Post by go_lanche on 2008-03-29
Thank you so much for the help.

---

### Post by dobrowski on 2008-04-25
I am trying to install Hardy Heron on my computer that also has three drives.  When I autoboot with the new CD, and try to install it gives me an error message (I'm at work so I don't recall exactly, something along the lines of /sbin/modprobe/).  Searching the forums it seems that this was a previous bug that was supposedly fixed with Gutsy or by entering "all_generic_ide" into the kernal parameter.  I tried doing that by pressing F6 after it asked me what language to use, but that appearantly didn't work since it froze on the splash screen.  

Am I going about this the right way by typing in that "all_generic_ide" phrase, or can I do something so that it just recognizes that there are 3 drives on its own?  

Thanks.

---

