---
title: "How to Uninstall Windows XP from Dual Boot"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by nebhead77 on 2007-06-27
This is my first post so go easy on me.  

I'm finally taking the big leap and I want to remove my Windows XP partition and leave Ubuntu fully intact.  I've been using Ubuntu for several months now, without the need to switch back to Windows.  That's right!  I'm a true convert!

To set the stage, I installed Ubuntu 6.10 Edgy several months ago which automatically setup the dual boot for me.  Later I upgraded to Ubuntu 7.04 Feisty.  

I *would* just load up the liveCD and run GPartEd and delete the partition, but I'm worried that it might cause some serious issues when I reboot. (i.e. GRUB Failure, etc.)

How should I proceed to uninstall Windows XP?

---

### Post by freebird54 on 2007-06-27
Well - it is still one of the easiest ways to dump XP!  You won't get any failures unless you try to boot to Windows after it is gone.

To avoid leaving references to the 'dear' departed, you could also

```
sudo cp /boot/grub/menu.lst /boot/grub/menu/lst.backup070627
gksudo gedit /boot/grub/menu.lst
```

and remove the entire 'block' of instructions from the file that refer to Windows (like so)

```

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


[B]# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hde1
title           Microsoft Windows XP Professional

root    (hd0,0)
savedefault
makeactive
chainloader     +1[/B]

title           Ubuntu Feisty Test System
savedefault
configfile      (hd1,5)/boot/grub/menu.lst
```


Just highlight the equivalent to the bolded part, delete it, and save and exit.  Next time you start Grub, it won't know about Win....

Edit:  BTW - the block will be at the bottom of the file, and may very well be the last entry.  If it is, you can also lose the four lines referring to the divider...

---

### Post by Miakehl on 2007-06-29
Would this method of removal skip the GRUB loader on boot or would you still have to choose Ubuntu from a list?

---

### Post by freebird54 on 2007-07-01
Well - yes and no  :)

Assuming you do nothing else, you will still be presented with a list of available options, and you would normally select the first one, or wait...

The others that would show include the 'Recovery Console' boot option, and possible previous kernel versions if yo have any...

Of course, like nearly everything else in Linux, you have choices here...

You could, for instance, remove the timeout by setting its value to 0 - meaning nothing is displayed, and you boot directly.  Problem can be - what *IF* you need to Recovery Console someday?

So - maybe a short timeout, like 2 or 3, then you see it, but don't have to do anything about it...

Or you can set it to NOT SHOW, but be there.  This gives you time to hit ESC and activate other choices in case of need....

Or


(you get the idea, right?)  Enjoy your freedom of choice.. :)

---

### Post by weedenbc on 2007-08-08
Follow-up question:

I am currently dual-booting with Windows on the first partition and Ubuntu on the 2nd and would like to get rid of windows.  Is grub installed on the windows partition?  In other words, by removing that partition is it going to have an effect?

Also, will removing that partition change the order and mapping of partitions in Ubuntu?  RIght now my structure is as follows in order from first partition to last on the HD:

/dev/sda (my only HD)
/dev/sda1 (windows ntfs partition)
/dev/sda3 ((ubuntu ext3 partition)
/dev/sda2 (extended patition)
/dev/sda5 (linux swap within the extended)
/dev/sda6 (fat32 within the extended)

---

### Post by skymera on 2007-08-08
i would hash is out of grub menu or just delete it
and format the windpows partition to unused space,.
then rxpand linux into it.

---

### Post by cobrn1 on 2007-08-08
What are you planning to do, use GParted to delete the windows partition (sda1). This won't delete grub, however, it may change the numbering of the subsequent partitions, ie, I'm not sure if the ubuntu one will still be known as sda3, or if it will become sda2...

Some one will need to confirm this for you.

My advice is to download something called the super GRUB disc, and if GRUB goes tits up you can just bung the disc in, follow the menu and restore GRUB... easy. Download and burn the .iso

---

### Post by weedenbc on 2007-08-08
Yes, I really need the space that the windows partition occupies so I was thinking of just deleting it with GpartD and rebooting.

But maybe I can just shrink it down to like 10 megs or something so that it will keep the same order of partitions.  It won't be as clean but at least I will get the space back.

---

### Post by freebird54 on 2007-08-08
To get maximum resizing room, go into windows, open a CMD (or DOSPrompt) and enter:

```
FORMAT C:\ /Q
```

which should do a quick format (after asking for confirmation) allowing you to size it down ALMOST to nothingness if you wish.

Hope this helps! :)

---

