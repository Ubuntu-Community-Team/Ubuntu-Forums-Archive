---
title: "Help needed. Ubuntu unable to boot"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by remoir on 2006-11-25
I have been using ubuntu for a while. But suddenly today Grub failed to run. ( Grub error 17)

I searched around the forums for the error. Tried to run the below commands from 

[http://www.ubuntuforums.org/showthread.php?t=224351&highlight=grub+live+cd](http://www.ubuntuforums.org/showthread.php?t=224351&highlight=grub+live+cd)

sudo mkdir /mnt/root [OK]

sudo mount -t ext3 /dev/hda5 /mnt/root [Can't execute]

The error i got was: ext3 not detected on my Linux disk partition.

When i tried to view my partitions using GNome Partition, my /dev/hda5 was of unknown type. 

What can i do to make it ext3 without formatting it ?

Also is that any command line i could use to check out the available diskspace left on that partition ? 

Appreciate any suggestions. 

Thanks :p

---

### Post by K.Mandla on 2006-11-25
The *df* command generally lets you see how much space is left. 

Are you sure you're using the right partition for the mount command? I'm only guessing, since the default installation puts the swap on /dev/hda5, and that would account for the "ext3 not detected" error. What does your partition table look like?

---

### Post by seshomaru samma on 2006-11-25
Did you try reinstalling Grub with the first set of commands in the link you provided? (sudo grub ,find /boot/grub/stage1...etc...)
If so , did you get any errors?

---

