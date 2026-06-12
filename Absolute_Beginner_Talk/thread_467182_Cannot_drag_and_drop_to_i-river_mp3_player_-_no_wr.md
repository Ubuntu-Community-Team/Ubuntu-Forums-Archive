---
title: "Cannot drag and drop to i-river mp3 player - no write permission."
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by heyho on 2007-06-07
First off, hello, this is my first post - I've managed to sort all of my other feisty problems using the search function on this forum, but this is really bugging me!

My machine is a fujitsu-siemens amilo notebook, running dual boot xp media and feisty + KDE.  I am liking my 1st linux experience a lot!

The problem I have is that if I try to drag and drop files or folders into my i-river player (iFP-190TC), I just get the message along the bottom of the window "You cannot drop items in a directory in which you do not have write permission".

I'm almost sure that the first couple of times I tried this, the files were transfered, but nothing actually ended up on the drive.  The firmware in the player allows it to be seen as a normal removable storage device, however even when wiped/formatted, 3 folders always reappear - music, voice and tuner - in case it may be of relavence.  It is using FAT32.

I have checked permissions using the GUI, and tried to change permissions via the GUI and terminal, but this did not work.  Although I have permission, it is impossible to alter permissions.  The properties tab is unable to determine the size of the drive - it just says "calculating", and continues to count up and up into terrabyte territory!  It's only a 256MB player!

I also have a 4GB flash drive, and this works a treat, no problems at all.

Sorry if the info is a bit jumbled, I think I've mentioned everything relavent.

Paul.

---

### Post by PatrickMay16 on 2007-06-07
Very strange...
Could you give me the output of the command **fdisk -l**? (that is l as in lower case L.)

Also, try unmounting it from nautilus, and then mounting it again in nautilus. Then try copying files over again.

---

### Post by heyho on 2007-06-07
Thanks Patrick, here are the results:

Disk /dev/sdb: 262 MB, 262144000 bytes
9 heads, 56 sectors/track, 1015 cylinders
Units = cylinders of 504 * 512 = 258048 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?     1543921     3808821   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(1543920, 4, 5)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(3808820, 4, 35)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?      334702     4176028   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(334701, 3, 51)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(4176027, 2, 42)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?     3710083     7551409   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(3710082, 2, 26)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(7551408, 0, 25)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?           1     7216720  1818613248    d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(0, 0, 1)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(7216719, 2, 8)
Partition 4 does not end on cylinder boundary.


Hopefully, soon this will also mean something to me!

---

### Post by PatrickMay16 on 2007-06-07
That is very strange looking. I think maybe formatting it might help. Or, deleting the partitions on it and creating a new partition (and of course formatting that partition as fat) but I dunno how safe that is. Hmm...

Does it work when you try to copy files onto it using windows?

---

### Post by heyho on 2007-06-07
I've never had any problems using it in windows - it's only since I've been using ubuntu that I've encountered this.

I did try to format it using windows  yesterday, which took ages and ended at 100% progress with the "format failed message".  I think that maybe it's not a straightforward mass storage device. 

I'll check the iriver site for firmware.  It's a shame, as it's my only problem so far, and it's a cracking little player.

Thanks for your input Patrick - I'll persevere.

---

