---
title: "ubuntu on jump drive"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by brdohman on 2008-04-08
I created a jumpdrive with ubuntu on it, and formatted it to have 2 sections, one of them being the casper-rw.  But I need undo my installation and make it a useable jump drive again.  The casper-rw part takes up about 3gb of my 4gb jump drive. 

My problem is that I can't reformat the casper-rw portion to make it a usable drive again.  The casper-rw portion does not show up under the windows disk management, When I connect it to an ubuntu machine, it loads the main portion, + the casper-rw portion, but I can't figure out how to reformat it so that I can just have 1 jump drive again, with no partions and be able to use more then 700k of the space.

thanks

---

### Post by bumanie on 2008-04-08
Have never done this before, but the general principle behind formatting a hard drive with say, gparted live cd is to have the drive/partition you are wishing to format unmounted. Windows will only see ext2/3 as unknown file system and that's it. As I said never tired this, but I would download and burn a copy of gparted live cd [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) 
Then set the computers' bios to boot from cd-rom. Boot into wndows, insert your usb drive. Then insert gparted into your optical drive and reset the computer with the reset button. Once gparted has loaded and inspected your drives, your thumb drive should be recognised, hopefully it is not mounted and you can then format with gparted. If the thumb drive is not recognised it's because it is still seen  as being mounted. In that case boot back into windows (remove the gparted cd first) go through the 'safe device removal' routine without removing the thumb drive.Then reset again with gparted back in your optical drive. Hopefully gparted will see your thumb drive's file system which hopefully will be inactive.
Hope this works. It is only my ideas based on experience and may not work. Follow these instructions at your own risk. (I would have no problems trying what I have said, but I often try things out. If something breaks, I say, "Oh, well, will have to reinstall now"). As you are only dealing with a thumb drive, doing harm should not be an issue as long as you choose the correct device to format.
Good luck. Hope it works.

---

### Post by az on 2008-04-08
> **brdohman said:**
> I created a jumpdrive with ubuntu on it, and formatted it to have 2 sections, one of them being the casper-rw.  But I need undo my installation and make it a useable jump drive again.  The casper-rw part takes up about 3gb of my 4gb jump drive. 

My problem is that I can't reformat the casper-rw portion to make it a usable drive again.  The casper-rw portion does not show up under the windows disk management, When I connect it to an ubuntu machine, it loads the main portion, + the casper-rw portion, but I can't figure out how to reformat it so that I can just have 1 jump drive again, with no partions and be able to use more then 700k of the space.

thanks
You don't need any other cd.  The only time you need a live cd to partiion is when you are working on your root partition.  You can't partition a mounted drive.

Boot into Ubuntu without the usb drive plugged in.  Once you are at the desktop, plug it in.  When the casper-rw partition mounts, right-click on the icon and unmount it.  Use cfdisk to change the partition type from 83 to 06

sudo cfdisk /dev/sdb (or whatever the usb device is on your machine - BE CAREFUL and select the correct device.)

Once that is done, format the partitoin as fat16

sudo mkdosfs -F 16 /dev/sdb1

And you are done.

You can create a loop filesystem called casper-rw on the fat16 partition and use that as a persistent home, apparently.  The file must be named casper-rw as well as the ext2/ext3 filesystem within the loop file.

---

