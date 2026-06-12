---
title: "[SOLVED] GRUB and eliminating bootable partitions."
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by JillSwift on 2007-12-12
I'm about to eliminate two bootable partitions on my hard drive (Both Windows).
I'm keeping one partition bootable (Ubuntu).

It just hit me this will probably effect GRUB.

Can someone help me understand how it will effect GRUB's setup, and what to do about it?

[FONT=Georgia][SIZE=1][COLOR=DimGray]Attached is my current partition map as displayed by GPartEd. The first two are the partitions going bye-bye. The third will be expanded to fill the empty space. The fourth is the bootable Ubuntu partition and will be expanded to take up that last 2gb of unallocated space.[/COLOR][/SIZE][/FONT]

---

### Post by Herman on 2007-12-12
Deleting Windows partitions won't affect GRUB much at all, since no part of GRUB writes to any part of any Windows file system. All GRUB does is 'chainload'  (pass control over to) Windows bootloader at the Windows boot sector, (the first sector of the Windows parrtition).
So, deleting Windows won't affect GRUB at all. You might like to also delete your Windows entries in /boot/grub/menu.lst, since your Windows won't exist anymore, but that's optional, it's just to tidy up.

Congratulations, you are making a good move there! :)

Regards, Herman

---

### Post by JillSwift on 2007-12-12
So it'll still be (hd0,3) to boot from? I rather thought that wold change >.>;

---

### Post by Duck2006 on 2007-12-12
> **JillSwift said:**
> I'm about to eliminate two bootable partitions on my hard drive (Both Windows).
I'm keeping one partition bootable (Ubuntu).

It just hit me this will probably effect GRUB.

Can someone help me understand how it will effect GRUB's setup, and what to do about it?

[FONT=Georgia][SIZE=1][COLOR=DimGray]Attached is my current partition map as displayed by GPartEd. The first two are the partitions going bye-bye. The third will be expanded to fill the empty space. The fourth is the bootable Ubuntu partition and will be expanded to take up that last 2gb of unallocated space.[/COLOR][/SIZE][/FONT]

No it will not effect grub, are you wonting to add the deleted partition to your home or just use then for storage?

---

### Post by JillSwift on 2007-12-12
> **Duck2006 said:**
> No it will not effect grub, are you wonting to add the deleted partition to your home or just use then for storage?Adding the deleted partition to /home =^_^=

[FONT=Comic Sans MS]ET Grow /home![/FONT]

---

### Post by Duck2006 on 2007-12-12
> **JillSwift said:**
> Adding the deleted partition to /home =^_^=

[FONT=Comic Sans MS]ET Grow /home![/FONT]

That should work ok just add it to the extended partition sda3, then to the sda5.

---

### Post by Herman on 2007-12-13
> So it'll still be (hd0,3) to boot from? I rather thought that wold change >.>; It looks like you are going to use GParted, which is very good. That is the best partition editor you can use, all the 'Parted based partition editors are good.  
As long as your partition number for Ubuntu does not get changed, you won't have any trouble booting with GRUB, and even if it does get changed, it's easy to edit your /boot/grub/menu.lst file to cope with that, there are lots of people here who can help you with that.
GParted won't change your Ubuntu partition number or any other partition number if you only resize the partition or move it around.

You can also copy a partition and paste it somewhere else on your hard disk, and if you do that then the new copy of the partition will have a new partition number. Sometimes that's faster than moving the partition. If you know what to do to edit /etc/fstab and get GRUB working again it can save time in some circumstances.

If you use some other partition editor other than GParted then I can't predict what will happen. Some partition editors are not really designed for use with Linux as their main priority.

Regards, Herman :)

---

### Post by JillSwift on 2007-12-13
Yep yep. GPartEd is for me. Mostly becasue it's saved many folks bacon when I've used the GPartEd live CD.

It's growing my home partition as I type, =^_^=

---

