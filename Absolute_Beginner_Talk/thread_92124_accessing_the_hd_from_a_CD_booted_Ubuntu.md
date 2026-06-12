---
title: "accessing the hd from a CD booted Ubuntu"
date: 2005-11-18
forum: Absolute Beginner Talk
---

### Post by dantech on 2005-11-18
I was trying to access my files on the hard drive from a Unbuntu booted CD. I have overheard that Samba is the program I need but havent found any solid answers. Can someone give me basics on how to get bmp's, mp3's, and mpg's from my windows hard drive and also how to be able to save stuff on the hard drive that Ive downloaded while booted into Unbuntu?

---

### Post by Mustard on 2005-11-18
I take it you are using a liveCD?

From the sounds of it you are attempting to do a little too much with what is essentially a 'preview' of Ubuntu, rather than an permanent and fully functional install Ubuntu.

An example of a mount command would be..

```
mount -t ntfs /dev/hda1 /media/windowsdrive  #this is just a sample and most likely will not be relevant to your setup
```

Another issue is that if your windows drive is ntfs, then you won't be able to write to it from linux.  Linux can write to a fat32 filesystem, but in a general sense cannot write to ntfs (without using experimental software).

---

### Post by MichaelM on 2005-11-18
What file system is your hard drive? If it's NTFS, you can't write to it from Linux. However, you can run ```
sudo mount <device name> <mount point> -t ntfs -o nls=utf8,umask=0222
``` This will mount it so that you can access it.

If it's FAT32, you would instead run ```
sudo mount <device name> <mount point> -t vfat
```

---

### Post by schdefan on 2005-11-18
Check out the starterguide
[http://help.ubuntu.com/starterguide/C/ch05.html]("http://help.ubuntu.com/starterguide/C/ch05.html")

---

### Post by Decon1 on 2005-11-18
NOTE********** I have a SATA HDD.

Ok RANK Noob here and I asked the question in a post just under yours!

Now then the answer they gave me flat did not work.....Soooooo I started messin'.  Here's what I did.


First..Open the Terminal - Apps, Accessories, Terminal and type in: sudo mkdir /media/windows

Then:
1. Select System,  then Administrator, then Disks.

2. One of the disks on the left side will show that it has some amount of file size.  Mine is 69.25.  No matter.  Select that disk.

3. Click on the Partitions Tab. In access Path type: /media/windows and click on change.

4. 2 lines down, Status, the Enable button will be highlighted.  Click it.  It will change the Status from inaccessible to accessible.

5. Click on "Browse", wait a few seconds and you have access to your HDD!!

Cool huh?

Now then, you will notice a HDD Icon on the Desktop under the CDROM icon.  Oddly...clicking on that brings up a window saying No Access because you're not the "owner".  There are many other way to get to the HDD but NONE of them work.  Only the above method works???

I am still going to try the commands above to mount from the terminal. Application, accessories, Terminal

OBTW it took nothing to add my Hp DeskJet 895Cse open my documents and print

Everything else works slick off the disk I can't believe they made this so tough??  Yes I know they want you to install it but Sheesh give a guy a chance to check it out!  Many of the other flavors that do not work anywhere as well as this immediately mount my drive on boot, ie. Knoppix, Mepis, Slax.

GL to us both! LOL!  I have this old Toshiba LapTop that's not doing anything :)

Regards,
Decon

---

### Post by jimw on 2005-12-03
[QUOTE=Mustard]I take it you are using a liveCD?

From the sounds of it you are attempting to do a little too much with what is essentially a 'preview' of Ubuntu, rather than an permanent and fully functional install Ubuntu.

An example of a mount command would be..

```
mount -t ntfs /dev/hda1 /media/windowsdrive  #this is just a sample and most likely will not be relevant to your setup
```

Another issue is that if your windows drive is ntfs, then you won't be able to write to it from linux.  Linux can write to a fat32 filesystem, but in a general sense cannot write to ntfs (without using experimental software).[/QUOTE]


I'm using the 5.10 install, dual-booting with Windows 98, which has FAT32.  What do I do to be able to read and write to that partition?  In Mandrake, which I had been using, it was set up that way by default, and I don't know enough to be able to guess how to do it.

Thanks.

JimW

---

### Post by aysiu on 2005-12-03
I think what's confusing is that you're using a Ubuntu installer CD. If Ubuntu's installed, it's no longer a CD. If it is a CD session... it's probably the live CD.

I don't see (even conceptually) how you can read and write Windows with the installer CD (unless "read" and "write" means repartitioning).

---

### Post by jimw on 2005-12-04
[QUOTE=Decon1]NOTE********** I have a SATA HDD.

Ok RANK Noob here and I asked the question in a post just under yours!

Now then the answer they gave me flat did not work.....Soooooo I started messin'.  Here's what I did.


First..Open the Terminal - Apps, Accessories, Terminal and type in: sudo mkdir /media/windows

Then:
1. Select System,  then Administrator, then Disks.

2. One of the disks on the left side will show that it has some amount of file size.  Mine is 69.25.  No matter.  Select that disk.

3. Click on the Partitions Tab. In access Path type: /media/windows and click on change.

4. 2 lines down, Status, the Enable button will be highlighted.  Click it.  It will change the Status from inaccessible to accessible.

5. Click on "Browse", wait a few seconds and you have access to your HDD!!

Cool huh?

Now then, you will notice a HDD Icon on the Desktop under the CDROM icon.  Oddly...clicking on that brings up a window saying No Access because you're not the "owner".  There are many other way to get to the HDD but NONE of them work.  Only the above method works???

I am still going to try the commands above to mount from the terminal. Application, accessories, Terminal

OBTW it took nothing to add my Hp DeskJet 895Cse open my documents and print

Everything else works slick off the disk I can't believe they made this so tough??  Yes I know they want you to install it but Sheesh give a guy a chance to check it out!  Many of the other flavors that do not work anywhere as well as this immediately mount my drive on boot, ie. Knoppix, Mepis, Slax.

GL to us both! LOL!  I have this old Toshiba LapTop that's not doing anything :)

Regards,
Decon[/QUOTE]


Thanks a lot for posting this.  I'd had a whole lot of files on a data partition from when I was using Mandrake, and couldn't get at them.  Using your solution, I changed the path, and now I can get at all those saved files.

Much appreciated

JimW

---

