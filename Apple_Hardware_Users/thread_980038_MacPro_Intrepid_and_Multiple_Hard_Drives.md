---
title: "MacPro Intrepid and Multiple Hard Drives"
date: 2008-11-12
forum: Apple Hardware Users
---

### Post by blackrim on 2008-11-12
I am actually trying to install the new 8.10 on my macpro now with some difficulty. Any help out there (for 8.10 not 8.04).

The situation is that I have a free internal drive on which to install it (I have 4 hard drives and am devoting one to ubuntu). I installed ubuntu entirely on the fourth drive (pulling the other three for paranoid reasons) and when I reboot and hit "option" ubuntu is not recognized as a feasible booting option. If I boot into the live cd and mount that drive all is well.

So drive config is :
1 Mac
2 Time Machine (Mac)
3 Other stuff (Mac)
4 Ubuntu (at least in theory)

Any ideas? I would prefer to stay away from Boot Camp and don't need anything pretty like refit unless completely necessary. 


Thanks

---

### Post by cyberdork33 on 2008-11-12
I believe that the first problem that you are going to run into is that the Ubuntu installer seems to mess up the partition table, which is the reason you don't see anything as 'bootable'. rEFIt has a tool to sync the partition tables, but it can only performs this function on the primary hard drive.

You can see info about this here:
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

After you get that situated, you also run into problems since you do not want Ubuntu on the primary hard drive. Apple designed the hard drive controller to act very oddly in that the hard drive that is "booted" is seen as the "first" drive by the system. (i.e. even though it is partition 4, it will be seen as /dev/sda). This can cause some issues with proper configuration of the bootloader and fstab.

I talk about this a little in two articles:
[http://www.rickycampbell.com/the-intel-mac-partitioning-system-efi-and-gpt/](http://www.rickycampbell.com/the-intel-mac-partitioning-system-efi-and-gpt/)
[http://www.rickycampbell.com/booting-windows-linux-and-osx-on-your-mac-without-using-grublilo-to-boot-windows/](http://www.rickycampbell.com/booting-windows-linux-and-osx-on-your-mac-without-using-grublilo-to-boot-windows/)
The second should help you with figuring out the last point I made above about the bootloader.

This might also be helpful:
[http://wiki.debian.org/DebianOnIntelMacPro#line-187](http://wiki.debian.org/DebianOnIntelMacPro#line-187)
[http://macprolinux.blogspot.com/](http://macprolinux.blogspot.com/)

Unfortunately, there are not a lot of regulars here with a Mac Pro.

---

