---
title: "error : unknown filesystem. Grub rescue&gt; _"
date: 2014-08-25
forum: Any Other OS
---

### Post by Stephen_H_Clarkson on 2014-08-25
I've just installed elermentery OS alongside of my windows XP after installtion was complete is asked to reboot to complete, But after it re-started i got a black screen with this Message "error : unknown filesystem. Grub Rescue> _

Now i can't get into anything ? All i want is get at all my files on windows and move them somewhere safe ? 

Then i'm not bothered if i delete the lot and start afresh ?

Can anybody help me please ? I'm new to linux so please be kind to me and give me help in simple (Dummie) terms !

Thanks

---

### Post by oldfred on 2014-08-25
Moved to Other OS since Elementary.

You always should be able to boot the Desktop installer in live mode and mount partitions and copy data to another drive.

Best to do backups before starting major changes. If you resized XP from the installer, then the NTFS partition needs chkdsk. Often the Linux NTFS driver will not mount NTFS that needs chkdsk or is hibernated to prevent further damage. But you should be able to force a read only mode. Better to run chkdsk from your XP installer or any newer Windows repairCD or flash drive first. 

If at grub rescue> you should be able to manually boot.

 See post #10 by drs305 
[http://ubuntuforums.org/showthread.php?t=1916698](http://ubuntuforums.org/showthread.php?t=1916698)
grub rescue:
ls # Do you see (hd0), (hd0,1) ? If so, run the next command. If you see (hd0,5), use that instead of (hd0,1) in the next command. If grub menu is ok this works, if not you have to directly boot kernels.
configfile (hd0,1)/boot/grub/grub.cfg

# directly boot kernels, change both hd0,5 and sda5 to number that is correct:

 set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
linux (hd0,5)/vmlinuz root=/dev/sda5 ro
initrd (hd0,5)/initrd.img
boot

If you are not sure what partition you installed into you can search for your boot files:

 Adjust drive, partition to your install or try all the alternative the ls command shows:
ls (hd0,5)/  # Do you see 'vmlinuz' and 'initrd.img' ?
ls (hd0,5)/boot # Do you see the kernel and initrd image files ?
ls (hd0,5)/boot/grub # Do you see lots of *.mod files and grub.cfg ?

---

### Post by Stephen_H_Clarkson on 2014-08-27
Thanks  "Oldfred" But that's too complcated for me to figer out ! I said I need to be told in "dummie terms" There should be a book "Linux for Dummies"

Anyway what i've done is install another linux called Centos which over wrote Elermentery but left my Win xp on so all I had to do is a windows xp repair which allowed me to get all my files off which is what I wanted to do, what i did not want to do is lose my files so i'm well pleased i've not lost all my files.

In future i will do a back up if i ever do this again ! But i intend to use a spare HDD to install linux again so thanks for your help even if i did not use any of it ! I think the elermentery disc must be corruped ?

---

