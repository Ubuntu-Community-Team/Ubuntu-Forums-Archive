---
title: "Difference in a copy in gparted and using partimage?"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by Hillbilly Tilley on 2006-08-09
I was wondering if there is a difference in backing up a partition with partimage or making a copy of the partition with gparted?

I need to make the ntfs a1 partition larger, so I divided the a2 partition into which made an a4 partition.  I then copied a2 to a4 which was made by splitting the original a2 into.  Now I will delete a2 which will hopefully allow me to enlarge a1 with the space that was freed up by deleting a2.

Do you think this is possible?

My only reservation is when I delete a2 I will be left with an a1 and an a4.  Will I need to rename a4 to a2 so everything will be back to the original addressing?  If so how do I do this?

Thanx for all the help!

---

### Post by tagra123 on 2006-08-09
You will need to edit the /etc/fstab  and change the necessary lines



If the partition was hda1 and is now hda4 you will need to change that.

If moving the root partition I think you also need to edit /boot/grub/menu.list.

If you've wiped out the MBR try this (this is usually necessary after installing Windows when Ubuntu is already installed  (Windows overwrites the MBR):

There is an automatic command for grub to find:

Start grub 
From the terminal type

grub

grub will start -- then type 

find /boot/grub/stage1

setup (hd0)   # hd? -- whatever the above command returns this will install to the MBR

quit

You will be back at the command line

Reboot the computer

---

### Post by orb9220 on 2006-08-09
When you delete a2 it will be unallocated space. When you go to risize a1 it will encompass the space making it a larger a1.

Now what was on a2 that you moved to a4? If it was yout / root account then grub will no longer be able to boot to linux.

---

### Post by gesho on 2006-08-09
yeah, that is possible, I have done exactly the same thing couple of weeks ago.

my experience is that of all progs, gparted works the best, though not without flaws. sometimes it might give you error message, sometimes "busy partition", sometyimes appear as if it worked, when it did not. 

here are some tips:

- have you live disk around

- try to do all manipulations from live disk, your hard drive unmounted. this might mean that you will need good connection to install gparted. in my kubuntu live it was not included in live disk (in gnome it might).

- always check gparted work by 
fdisk -l
sometimes gparted reports things done, but they are not. sometimes it reports errors, but all is fine.

- after all work is done you might need to edit 
/etc/fstab
this is not much trouble.

- try to avoid more then four partitions, because above 4 goes into extended logical partion, not parimary. If you have more then four partitions, you will have to do more resizing, that is resize both mother extended partition and individual partition in it. you will see all this in gparted diagram.

tagra told you about grub. either you correct it when boot fails from grub menu (press "e"), or from live disk, file is
/boot/grub/menu.lst
remember that count of partitions starts from 0, names start from one.
ie /dev/hda1 is the same as hda(0,0)
/dev/hda4 might be (if all slots in between occupied) the same as hda(0,3). you might need to play this around.

I also had to reinstall grub and I had to do it from live. 
for that you need to indicate that boot directory is on hard drive (not live). for this, I mounted hard drive 
mount /dev/hda /mnt
and then indicate 
sudo grub-install --root-directory=/mnt/boot /dev/sda
you might need to play with directory, the idea is that grub should go into /mnt/boot/grub
it might be I only typed --root-directory=/mnt

all in all: if you have live disk, connection and never press delete/format, all will work out.

---

### Post by gesho on 2006-08-09
ps: you might also want to have ntfs/fuse in place to have write access to ntfs from linux. most likely this won't be needed, but still, feels safer.

---

