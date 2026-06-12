---
title: "Help with modifying grub (menu.lst)"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by Ben325e on 2007-03-07
I've got ubuntu going great thus far, even my fglrx drivers are going well.  I'm to the point where I want to set up dual boot.  

I've got two hard drives - 200gig SATA with XP, and 120gig IDE with Ubuntu.  I installed Ubuntu with the XP drive disconnected, so grub is on the ubuntu drive, and I've got the ubuntu drive set up in bios as the primary boot drive.

My computer is an HP pavillion, and HP has a recovery partition on their drives, so the XP drive is already partitioned, so pasting the following in the menu.lst won't quite cut it because of the recovery partition.

[I]title Windows XP
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1[/I]

If I run that, it will send me to the recovery partition, which will set things in order to put a clean install of XP on my SATA drive.... Don't wanna do that.

I ran fdisk -l in the terminal to see what drives were where, and here's what showed up:

[B][I]Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         776     6233188+   b  W95 FAT32
/dev/sda2   *         777       24320   189117180    7  HPFS/NTFS

Disk /dev/hdd: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        3264    26218048+  83  Linux
/dev/hdd2           14331       14593     2112547+   5  Extended
/dev/hdd3            3265       14050    86638545   83  Linux
/dev/hdd5           14332       14593     2104515   82  Linux swap / Solaris
[/I][/B]

In my researching the topic I found this:

[I][B]If you have a HP that has system recovery on it (I'm not sure which models do), you'll want to modify menu.lst file in the following way:

title Windows XP
root (hd1,1)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

The only difference here is the second line. HP puts the system recovery on (hd1,0), so if use that it will go straight to recovery.[/B][/I]

So, I think I should have my menu.llst appended like in the preceding bold paragraph, but I'm not sure, because fdisk-l says that my windows partitions are sda1 and sda2.

On my previous install (yesterday) I used the "hp pavillion" way, and grub ended up not being able to find any of my drives, so I had to change to the XP drive in my bios just to get an OS to boot up.

Any clues as to how I should set up my menu.lst? I've already uncommented the #hidden so that I don't have to hit esc to see the grub list, but that's as far as Ive got!

I'd be very grateful for any help in getting this setup!  Thanks,

Ben

---

### Post by LotsOfPhil on 2007-03-07
I think we need to see the output from sudo cat /boot/grub/device.map

---

### Post by nick24 on 2007-03-07
I thought you said Ubunut is in sd0(sda) and XP in sd1(sdb) , in order to dual boot I think both OS's should be on the same disk. I could be wrong but from my experience thats what I think. I have Ubuntu and PCLinuxOS on one disk (primary disk) and XP by itself on a  second drive( slave). even though Grub lists it in the menu I cant boot in to windows because NTLDR is not in the MBR. ie it doesn't exist in the first disk. I hope this helps

---

### Post by Ben325e on 2007-03-07
(hd0)   /dev/hdd


There's the output from the grub device.map....  not too profound, is it?

---

### Post by LotsOfPhil on 2007-03-08
Let me warn you that I am guessing here. Do this at your own risk, etc. With that said, it's what I'd do.

Add this line to the /boot/grub/device.map
```
(hd1) /dev/sda
```

Then I think you'll be good to go. Of course you still need
```

title Windows XP
root (hd1,1)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

```

in /boot/grub/menu.lst

---

### Post by LotsOfPhil on 2007-03-08
I don't think grub knows about the sda disk. We are just telling it (I hope) and calling it "hd1" in grub lingo. Grub doesn't distinguish between SATA (sdxxx) and IDE (hdxxx).

---

### Post by dannyboy79 on 2007-03-08
> **nick24 said:**
> I thought you said Ubunut is in sd0(sda) and XP in sd1(sdb) , in order to dual boot I think both OS's should be on the same disk. I could be wrong but from my experience thats what I think. I have Ubuntu and PCLinuxOS on one disk (primary disk) and XP by itself on a  second drive( slave). even though Grub lists it in the menu I cant boot in to windows because NTLDR is not in the MBR. ie it doesn't exist in the first disk. I hope this helps

not true at all. if you can't boot into your windows install from grub than you have a problem with your menu.lst. if you're booting your ubuntu disk first and you installed grub into that mbr, than you didn't change the winbloz mbr, therefore ntldr should still be in the mbr of the winbloz disk. grub can boot any os from any hard drive on any parititon except some os's can't be booted from logical partitions, they need to be booted from the primary partitions. grub can always either directly boot the os or chainload the os.

---

