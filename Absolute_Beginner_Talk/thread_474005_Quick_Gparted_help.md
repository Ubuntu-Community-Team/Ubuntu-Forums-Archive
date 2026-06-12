---
title: "Quick Gparted help"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by fwuffycloud on 2007-06-14
I just created a partition with Windows and Ubuntu, and i made my windows partition 11gb (enough to install it), but now i have started adding files i need to make it bigger, and i need to know if i modify the Windows partition using Gparted, will it format the partition and delete all the files on it?

Or is there a way to make it bigger without deleting all my files? (because there is about 100gb of empty space that isnt partitioned).

Thanks.

---

### Post by fwuffycloud on 2007-06-14
bump, Just need a quick answer, because i'm out of space on Windows and i only really know how to use Gparted to edit partitions.

---

### Post by dannyboy79 on 2007-06-14
I can tell you that gparted CAN grow a NTFS partition. All you should have to do is grow it larger BUT you need to shrink your Ext3 partition first so that there's unallocated space between the 2. It is SUPPOSE to work BUT whenever you move around partiitons and whatnot it's always a good idea to back them up JUST IN CASE, but yes, in theory it can be done. The one thing that CAN'T be done YET, is use partimage to restore a NTFS parititon back onto a NTFS partition that was created using gparted livecd. I couldn't get NTLDR to recognize the parititon but that's for another post. Partimage warns you that writing to NTFS is still in testing mode.

---

### Post by fwuffycloud on 2007-06-14
Hmm ok, If say i wanted to grow my Windows partition to 70gb's, would you mind guiding me through shrinking the ext3 partition and growing the Windows one?

I dont know partitions too well, and i really dont want to lose everything again (already managed to lose Windows altogether this week, its in the healing process :P)

Thanks.

---

### Post by dannyboy79 on 2007-06-14
just use gparted to shrink the ext3 partition, make sure you shrink it so that the space is in the middle as I said. if you're worried about losing anything, than use partimage to backup the partitions somewhere, partimage even can compress the images as well as split them so they can be burned onto disc so you don't waste vaulable space.

---

### Post by fwuffycloud on 2007-06-14
Right ok, i'll give it a go.

I'll post if i get any problems.

Thanks a lot.

---

### Post by fwuffycloud on 2007-06-14
I'm in Gparted, but there is a padlock next to ext3, and wont let me modify it.

Also, i noticed that my Windows partition is in FAT32 instead of NTFS, is it important that it is NTFS?

---

### Post by bren on 2007-06-14
you cant modify it because it is your current root/boot partition

if you boot from live cd then you can change it

bren

---

### Post by fwuffycloud on 2007-06-15
Ah right that makes sense,

Shall try that later tonight, gotta head off to college soon.

Thanks for the replies.

Cloud

---

### Post by freebird54 on 2007-06-15
The fact that your Windows is FAT32 is not a problem.  It can be resized - though I think not to as large a size as an NTFS one  (should not affect your numbers though).  To leave room between partitions, you select the size, then set where (and how much) the empty space will be.  Then pick new size for the Win partition.  Do it in the right order! :)

One of the easiest ways to modify the partitions is to boot from the Live CD to get at GPartEd without having any drives mounted - it is in System->Administration->Gnome Partition Editor (if you didn't already know that!)

Enjoy,  good luck - and remember - the one time you DON'T backup defore playing with partitions is the one time the power goes off in the middle....

---

### Post by fwuffycloud on 2007-06-15
Hey,

I just tried shrinking the ext3 one (as stated above), 

but it came up with an error telling me to check file system for faults and fix them (if possible).

So i'm not too sure what to do.

thanks.

---

### Post by fwuffycloud on 2007-06-15
errr.....slight problem. I managed to get all the partitions resized. Then the computer froze when I tried to shut down so I had to reset it and instead of booting up I got  a GRUB error 15!
This is really worrying.

---

### Post by fwuffycloud on 2007-06-15
ah, sorry, no problem...think I've got it sorted now. ^_^

---

### Post by dannyboy79 on 2007-06-15
you think you got it sorted??? if you need any help just ask. Grub error 15 is most likely because grub can't locate the files for continuing booting, like the kernel or similar. You can either change your /boot/grub/menu.lst to call out the correct drive and partition for whereever /boot/grub/ is mounted (changing around (hd0,0)   ) OR
just reinstall grub and you should be fine!

---

