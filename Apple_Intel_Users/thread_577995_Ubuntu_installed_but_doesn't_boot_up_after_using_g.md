---
title: "Ubuntu installed but doesn't boot up after using gparted"
date: 2007-10-16
forum: Apple Intel Users
---

### Post by jamieno10 on 2007-10-16
Hi

I have a mac pro with 4 hard-disks, 7.10rc & rEFIt. I have Mac OS and Ubuntu on two of them while the other two is currently 'free-space'.

I now want to convert the other 2 to ext3 so that I can mount and use them in ubunutu. I used gparted and the partitioning works fine; I cam mount and write to the disks.

However, I can't get ubuntu to boot up if I now reset my machine. I uderstand that its something to do with sync-ing the MBR and GPT? I did that in the rEFIt menu and I got a legacy OS icon appearing in addition to linux and mac os. I booted the LiveCD and saw that all my HDD were detected. 

I was wondering if it would be possible to resolve these problems before I reboot, i.e. right after I've partitioned my two other HD?

Thanks

---

### Post by pxwpxw on 2007-10-16
are you using grub bootloader and what happens when you try to boot from the rEFIt TUX icon, did it ever boot and how? . Some more details wouild help.

---

### Post by jamieno10 on 2007-10-17
Thanks.

I am using GRUB. 

From the rEFIt menu, only mac os starts up, the other icons (linux etc) just hangs at a black screen.

---

### Post by pxwpxw on 2007-10-17
Could you please post  from Macosx
```

 diskutil list
 sudo gpt -r show disk0

```
That should hopefully give a listing of all drives, except it will call them disk0,disk1....

Then  tell me which drive ubuntu and macosx are on.

Use the Live cd to get a copy of /boot/grub/menu.lst  from  the ubuntu installation, and post it.

And while in the live cd, also get and post 
```

 cat /proc/partitions

```
That will give the linux partition names.

---

### Post by jamieno10 on 2007-10-17
Hi,

I use gparted to repartition my 2 other HDD (sdab and sdc) from freespace to ext3, installed GRUB and re-sync the tables with rEFIt (installed in mac os) at bootup. Linux doesn't boot & computer hangs.

The details you requested are attached.

Mac OS is on disk4 and Ubunu on disk1.

Running sudo gpt -r show disk 0 also gives - dev/disk0: Supicious MBR sector 0

cat /proc/partitions is in partition.txt. The partitions are as I expected, but doesn't show up in mac os x.

Please help. Thanks.

---

### Post by jamieno10 on 2007-10-17
I should add that I've tried:

sudo grub

find /boot/grub/stage1 (and it finds the correct partition)

root and setup (hd0,1)

rEFIt menu now shows an additional icon: Linux from partition 2.

All options (linux from HD, Legacy OS, linux from partition 2) except LiveCD and Mac OS do not work.

---

### Post by pxwpxw on 2007-10-17
That looks difficult due to the multi disk setup.
When you can post /boot/grub/menu.lst that  will show if there might be an easy answer.
Also how many TUX linux icons is rEFIt showing, and do you know where grub was installed.

Edit: had not read your post above.

You will need to post menu.lst to help sort it out.

running grub setup has only confused the issue and installed to the wrong sector in this case

Could you also clarify have you ever booted the installed ubuntu i.e. before whatever you did with partitioning.

---

### Post by jamieno10 on 2007-10-17
Thanks.

I can't find /boot/grub/menu.lst from the liveCD. Its not there.

There are now 2 tux icons (linux from HD, the original one) & (linux from partition 2; after I re-installed grub from the liveCD).

Grub should be on hd0,1

Any advice? If not I'll re-intall everything and this time use manual partition in ubuntu installer to set all the HDD. Do you think this will work?

---

### Post by pxwpxw on 2007-10-17
I am reading now, will post shortly.

---

### Post by jamieno10 on 2007-10-17
Just read your edit.

I've booted up Ubuntu succesfully a number of times before using gparted.

I had intended to use the manual partition, but it complained about the EFI parts having the same name and since I am not well-versed in such matters, I just used the guided partitioning (using the largest cont. free space).

---

### Post by jamieno10 on 2007-10-17
If I need to reinstall, what would be best to do so that I can mount all my HDD and be able to boot and reboot into ubuntu successfully

One of the problems when I choose to do manual partitioning during ubuntu installation is that it complains the the mount points for EFI are the same for all the disks.

When I do a guided install using the largest continuous free space, this issue doesnt come up even though the EFI mount points are the same and remain there. For example, I have mac OS x on sdd and ubuntu on sda and both have the EFI partition.

Advice would be most appreciated!

Thanks

---

### Post by pxwpxw on 2007-10-17
> **jamieno10 said:**
> Just read your edit.

I've booted up Ubuntu succesfully a number of times before using gparted.

I had intended to use the manual partition, but it complained about the EFI parts having the same name and since I am not well-versed in such matters, I just used the guided partitioning (using the largest cont. free space).

Well, if you booted before, there is no problem with the multi disk situation, what we need to know is what booted, and what you did that  stopped it booting, so maybe you could recall the before and after situation. In particular exactly what did you do with gparted  and what else has changed.
Can you restore it to the booting situation?

---

### Post by pxwpxw on 2007-10-17
I had this writtne before I saw previous post, may be irrelevant, read with caution, may help your thinking, my bed time.

No dont reinstall like that, probably compound the problem.

But I cant see why it would not work as is. There may be a problem with using the GUID partitioning scheme on that disk.
Dont really know.

You have an arrangement I have not tried, so this is guesswork.

If you had just installed macosx and ubuntu on sda1 in the normal way, that would work. That has been done. 

But you should also be able to use separate disks, some do, and it seems a good idea - however the GUID scheme on sda cannot be synced by rEFIt on another disk (sdd?), how much this matters I am not sure.

 With separate disks for macosx and linux, you should be able to select macosx or linux from 2 icons in the Apple Icons boot selection, without going to rEFIt, but I would leave the macosx disk as it is and keep refit. 

It should not be a problem to run macosx from sdd as is, with or without refit.

If you do reinstall linux, I would suggest re-install the linux disk sda as an  MSDOS partitioned drive, not apple or guid/gpt  (using the macosx diskutility to make it an MBR/MSDOS partition scheme disk, and the installer to make the partitions).

If you use manual partitioning you need to know what you are doing, you may need to use the Alternate install CD. And  grub should be installed to the MBR in this case, which is usually the default.

I dont know if your existing install is broken or not, you should be able to mount sda2 and see all your linux including the files in /boot - you found /boot/grub/stage1 using the grub in the live cd but sometimes that can be misleading. It could be as simple as editing menu.lst and reinstalling grub.

If /boot/grub/menu.lst is missing that would indeed be a major problem, so I would at least have another look with the live cd to see what you have.

I cant really say much more at this stage, not too sure of what is going on.

---

### Post by jamieno10 on 2007-10-17
Thanks.

I was surfing around in rEFIt bug forum and found another person with a similar problem in that it doesn't sync properly if there are multiple disks. Not sure if this is general.

I usually install rEFIt first before installing ubuntu (to one HDD only, the others remain as freespace) and there doesn't seem to be any problems. So does the ubuntu partitioning tool during install sync the tables?

Do you think that by manually mounting the other 2 HDD as ext in lieu with making sda as root (installing grub there as well) during ubuntu install would get around the need to sync?

However, I do not know how to deal with the FAT32 (EFI) partition that exists on each disk. Do I not mount it? How does the 'guided' partition handle that?

The last resort would be to use gparted and then not reboot. Would data on these disks be accessible by just unplugging them and using them as external HDD with a suitable casing?

Any advice would be most appreciated.

---

### Post by pxwpxw on 2007-10-17
Sorry, but I fail to understand what you did with gparted or why that should affect the linux disk, or what the position was when the linux install worked.
The gptsync done by refit on the Macosx drive is entirely irrelevant to the separate linux disk.
You should get a simple install done on the linux disk, preferably just using the guided whole disk, and without touching gparted or attempting to mount anything in the install
If you have a problem with the existing GPT/MBR partitioning on the linux disk, you can use MBR scheme.

Then you can treat the extra drives as the next issue, and there should be no problem in separately chooisng a partitioning system for them, provided you do not mix it up with the linux partition.

You dont want the EFI partitions on any drive except the macosx one, but you get it as default  when the drive is partitoned by the Macosx disk utility default partitioning scheme GPT/MBR compatible aka GUID - but you can choose alternative MBR scheme, which would be fine for your linux disk.

Dont have enough info to comment further at this stage.

---

