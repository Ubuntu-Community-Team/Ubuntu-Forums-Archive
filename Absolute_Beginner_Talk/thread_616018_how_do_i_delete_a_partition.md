---
title: "how do i delete a partition?"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by kevin11951 on 2007-11-17
my computer has 2 os's, windows, and ubuntu, im done! no more windows! so... is there a way to delete the windows partition, but leave the ubuntu partition alone (but still increase its size to fill the hdd)?

---

### Post by shad0w_walker on 2007-11-17
Did you install from the LiveCD? If you did, just boot up from that and run gparted from the System > Administration menu. It will let you configure your partitions and you can delete the windows one and expand your Ubuntu one safely. Just be sure you have backups of anything important before you resize. It is fairly safe but if its important might as well play it safe. Good luck.

---

### Post by kevin11951 on 2007-11-17
thank you! i will try, be right back!

---

### Post by Inxsible on 2007-11-17
> **kevin11951 said:**
> my computer has 2 os's, windows, and ubuntu, im done! no more windows! so... is there a way to delete the windows partition, but leave the ubuntu partition alone (but still increase its size to fill the hdd)?
you can do that provided your root partition is NOT between you windows and your home or other ubuntu partitions.

Because to merge the partitions you will need to format the partitions which means you will lose your ubuntu if your partitions look like this

Win | Ubuntu Root | Ubuntu home | swap

---

### Post by CatKiller on 2007-11-17
You can move the start of an ext3 partition with vaguely recent versions of GPartEd. I don't know which version is on the Ubuntu cd, but if that version can't then the [GParted live cd]("http://gparted.sourceforge.net/") can. So no need to reformat.

---

### Post by ajgreeny on 2007-11-17
Just delete the windows partition with gparted.  You will probably need to restore grub if the live CD installer did its default of putting it on the windows partition.  Just follow this to do so.

Boot into the ubuntu live CD
open a terminal and run :
    sudo grub
This gets you to a simple grub command line.
Then:
    find /boot/grub/stage1
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. Replace the question marks in the following command with the output of the this last command :
    root (hd?,?)
[like : root (hdo,1) ,probably]
then:
    setup (hd0)
This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    quit
Finally reboot, and hopefully you will now have a working grub bootloader.

---

### Post by Inxsible on 2007-11-17
> **CatKiller said:**
> You can move the start of an ext3 partition with vaguely recent versions of GPartEd. I don't know which version is on the Ubuntu cd, but if that version can't then the [GParted live cd]("http://gparted.sourceforge.net/") can. So no need to reformat.
The GParted in Feisty wasn't able to do that. I am not sure about Gutsy.

well in any case, its great that the GParted Live CD can do it :)

---

### Post by kevin11951 on 2007-11-18
wow! thanks for all your help, i will try a few suggestions, but isnt it possible to just run lie grub-reconfigure or something like that, to make it reset grub (i did that when i got rid of am OS on its own hdd)

---

