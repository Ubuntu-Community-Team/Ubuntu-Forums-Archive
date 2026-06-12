---
title: "Formatted HD and installed Ubuntu, but now I want to dual boot with Windows"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by BigManJoe on 2006-08-23
Since no iPod apps are working in Linux for me (possibly my firmware version), I want to duel boot Windows so I can access my iPod. The thing is, I already installed Ubuntu with no intention of installing Windows again or dual booting, so is it possible for me to get everything set up without uninstalling Ubuntu (because I've done alot and don't want to lose my stuff)?

I still have the XP Pro CD that came with the computer and I think you can do partitioning things in there.

---

### Post by Ziox on 2006-08-23
> **BigManJoe said:**
> Since no iPod apps are working in Linux for me (possibly my firmware version), I want to duel boot Windows so I can access my iPod. The thing is, I already installed Ubuntu with no intention of installing Windows again or dual booting, so is it possible for me to get everything set up without uninstalling Ubuntu (because I've done alot and don't want to lose my stuff)?

I still have the XP Pro CD that came with the computer and I think you can do partitioning things in there.

Have you tried to use VMWare? That application allows you to use Windows within Ubuntu, and since all you are doing is moving files from the computer to iPod, then I suggest using it.  

As for dual-booting with Windows...I've heard that some people are successful with installing Windows after Ubuntu has already installed. However, most people (including myself) found that the easiest way to dual boot windows and Ubuntu is install Windows first (because it always takes up the beginning of the hard drive), then install Ubuntu...

---

### Post by BigManJoe on 2006-08-23
OK, I'll check out VMWare. I've never heard of it until now (I've only been using Linux for 2 days), so I'll look around the wiki and see what I can see.

Thanks.

---

### Post by seshomaru samma on 2006-08-23
VMware is a great option
Another option is to resize your Ubuntu partition and reinstall Windows in a new partition. Windows will overwrite your MBR which will mean you will not be able to access Linux , so you will have to reinstall Grub . Reinstalling Grub is quite easy , you can find many threads about it. If you encounter difficulties , post them and we will help.

---

### Post by catlett on 2006-08-23
It is not hard to install windows after ubuntu. First download and burn Gparted Live to a cd. It is a partitioning program that runs off of a live cd. You boot to the cd like you would an installation cd. So go here and download it. [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) 
Now burn it to a cd. You can use gnome baker. If you do not have it installed then run this command ```
sudo apt-get install gnomebaker
```
When you boot into gnomebaker, if you have all the space formatted then you will have to shrink the last partition. Windows will need 2 or 3 gb for install. You should give it 5gb or 10gb if you have it to spare.
Anyways shrink the partition and then create a fat32 primary partition. It has to be a primary partition. Apply your actions and exit when done.
Now run the xp installer. It is very simple. Just select the fat32 partition when it asks which partition to install to. You can keep it fat32 so Ubunrtu can read/write to it and you can easily share data between the 2 OSs or you can have the installer format it to NTFS.
After the install, grub will be gone. Windows will overwrite grub with it's bootloader (ntdlr) and you will not be able to access ubuntu. This is where I come in :D  After many messed up installs and banging my head off the wall, I found a way to restore grub after it has been over written. I made it into a little how to on the forum. Just go here and follow the instructions [http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351) This will  restore grub to the mbr. It should detect windows and add it. If it doesn't, just post and I'll give you the entry to use.

---

### Post by BigManJoe on 2006-08-23
Awsome. Thanks so much catlett. It seems like a long process so I'm considering just installing iTunes and backing up my music on my parents laptop, but I'll give this a go. Thanks!

---

### Post by catlett on 2006-08-23
It's a bit of a process. It isn't as hard as it may seem though. Just a question. Your ipod didn't interface with anything on linux? Do you have a windows ipod or an apple ipod (they have different types of filesystems)
Did you try gtkpod? It is the closest thing to itunes as far as interfacing with you ipod (not as far as a music store frontend)
Just in case you didn't see it ```
sudo apt-get install gtkpod
``` Here is it's web site [http://www.gtkpod.org/about.html](http://www.gtkpod.org/about.html)

Good luck. Post here if you have any issues. I'll be off to bed and work, so I won't be back online for another 18 hours (6pm EST or GMT -4 Thursday) but I'll check here to see if you need any help. Good luck and take care.

---

### Post by BFPerkins on 2006-08-24
> **catlett said:**
> It is not hard to install windows after ubuntu. First download and burn Gparted Live to a cd. It is a partitioning program that runs off of a live cd. You boot to the cd like you would an installation cd. So go here and download it. [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) 
Now burn it to a cd. You can use gnome baker. If you do not have it installed then run this command ```
sudo apt-get install gnomebaker
```
When you boot into gnomebaker, if you have all the space formatted then you will have to shrink the last partition. Windows will need 2 or 3 gb for install. You should give it 5gb or 10gb if you have it to spare.
Anyways shrink the partition and then create a fat32 primary partition. It has to be a primary partition. Apply your actions and exit when done.
Now run the xp installer. It is very simple. Just select the fat32 partition when it asks which partition to install to. You can keep it fat32 so Ubunrtu can read/write to it and you can easily share data between the 2 OSs or you can have the installer format it to NTFS.
After the install, grub will be gone. Windows will overwrite grub with it's bootloader (ntdlr) and you will not be able to access ubuntu. This is where I come in :D  After many messed up installs and banging my head off the wall, I found a way to restore grub after it has been over written. I made it into a little how to on the forum. Just go here and follow the instructions [http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351) This will  restore grub to the mbr. It should detect windows and add it. If it doesn't, just post and I'll give you the entry to use.

Completely new to all this, so forgive the ignorance. I tried your grub re-install, but now my PC wont boot up, not to XP Fedora or Ubuntu. I am as I said new to linux, and have no idea about any of this. What I'm getting when the PC tries to load off the HDD is a load of garbled characters, then the PC hangs. Any ideas?

---

