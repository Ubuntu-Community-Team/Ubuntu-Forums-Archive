---
title: "Resize Partitions?"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by mulkwolf on 2007-02-22
OK... Im totally new to this...  Installed Ubuntu... everything is fine.  wanted to have option of microsoft until Im more fluent in linux.... Obviously made a wrong choice in size when resizing the windows partition.  now left with minimal free for windows... plenty for ubuntu.  how can I resize the large empty partition in ubuntu and add to the windows?

Thanks

---

### Post by mykalreborn on 2007-02-22
you can use gnome partition editor. you can install it via synaptic: System>Administration>Synaptic Package Manager. enter root's password and then search for gparted and install it. you must make sure you don't wan't to resize the root partition. that is because to resize a partition you have to unmount it (=not use it anymore, basically), and you can't unmount the root partition. also you should be careful about what you do because you can make undoable things to the hard drive.
you can go here:[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/). the website for gparted. it has some info and some more. 
also you can download the gparted live cd. this is what i did. you run it from the cd and don't have to worry about mounting or unmouning. ([http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php))
or you can get the live usb if you want. ;) ([http://gparted.sourceforge.net/liveusb.php](http://gparted.sourceforge.net/liveusb.php))
also you should know that fat32 is a whole of a lot manageble in linux than ntfs. if you don't have to deal with dvd isos or files larger than 4 GB in general you should stick with fat32.
take care!

---

### Post by mulkwolf on 2007-02-25
thanks for the gparted lead....  Did have a bit of trouble understanding how to simply resize the ntfs by taking from the linux partition... A little googling and have come across a program FS-Drive that allows windows to read/write to the linux partitions.  I decided this is good for now.  I'll leave a much larger partition for linux......
Thanks,
:)

---

### Post by undertakingyou on 2007-02-26
The option you came up with should work well.  The only concern is that windows doesn't do well without the pagefile space that it wants.  Really kills the already difficult performance.  You may want to resize anyways.  To do that with gparted you just have to shrink the front of the ext3 partition and then extend the back of the NTFS partition.  Sounds like you'll have everything running good though.

---

