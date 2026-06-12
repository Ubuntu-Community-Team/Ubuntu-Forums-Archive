---
title: "help! dapper-amd64 install probs, dual boot/BootMagic/XP variety"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by wgaprotest on 2006-08-05
[SIZE="2"][FONT="Arial"]k, on 2nd try it did install, but there was no grub in the right place, so I'm trying a 3rd time now that I *think* I understand about mount points. I don't understand some of the other posts about putting parts of ubuntu in extended partitions, as being a fairly-expert user of PartitionMagic 8 and BootMagic, I'm used to leaving the extended partitions alone i.e. don't touch.

Here's my setup and what I'm trying to do:
I have a 300G sata drive with 4 primary partitions: 
[LIST]
[*]a 55MB dos/BootMagic primary Fat16 partition that I believe should be the /boot partition (it has about 22MB empty space left for linux files like grub, but is at the maximum size already for this fat16 type
[*]next, a 35G ext3 partition where I want to put most of the Ubuntu from the amd64 version of the LiveCD, and am trying to use it for the '/' root partition 
[*]then a 22G Media Centre NTFS partition, which I won't need to mount, as it only has OS and app files - followed by 4 logical NTFS partitions labeled Data, Drivers, Backups, and Media (147G). I will want access to at least 2 of these logical partitions from ubuntu. 
[/LIST]

Then I also have an older 20G IDE drive that's set up as a slave to the DVD-writer. I was trying to put my minimal swap drive (I have 2G of RAM, so won't need much swap) and /home parition there; they're already formatted by the dapper installer to ext3 from the second install, but I chose to select reformat for the sda2, hd? for swap and hd? for /home on this, the 3rd try.

Of course in step 4 of the installer I always choose "manually edit the partition" because I don't want my win MCE or other NTFS partitions touched, and can still boot to these through BootMagic just fine.

In step 5 I told the installer (this last time, after which it's giving me the "invalid file system for this mount point" error to put the /boot in sda1, the / in sd2, and swap in hd?

With my previous attempt I hadn't understood mount points hardly at all, and the install did go all the way through after telling me there were errors in one of the partitions (probably the /boot, and that's why I got no grub or any other linux file in sd1). Nor did the sd2 mount at all, although the swap and /home both did in the 2 hd partitions.

What in the world should I do? should I hide all the other partitions for now with pqmagic, except for sd2? so that i can get into my previous install? once I can get into the installed linux, perhaps then I can copy the grub and whatever else i need (I haven't the foggiest) into the sd1 so it'll boot from BootMagic. Then I can mount other drives from the command line. No, I don't have the whole PartitionMagic 8 in the win MCE partition anymore, as I like working with the smaller dos version in BootMagic. I suppose i could reinstall it in MCE again, but it wouldn't be able to read the linux partitions anyway. obviously the live CD, which I'm in now, won't let me mount or do much.

And what about these mentions of putting parts of the dapper in the extended partitions? What's that all about?

I'd really appreciate some help.[/FONT][/SIZE]

---

### Post by steve.horsley on 2006-08-05
> And what about these mentions of putting parts of the dapper in the extended partitions? What's that all about?
An extended partition is a primary partition (so it must be one of the first 4 partitions) that acts as a container for all the "logical" partitions. So in your case, you have 3 normal primary partitions that contain normal stuff - FAT, ext3 and NTFS. Then you have your extended partition that probably fills the rest of the hard disk. Inside this extended partition are partitions 5, 6.... Hope that helps.

> invalid file system for this mount point
I guess this is because it doesn't like putting grub on a FAT partition. I suggest not trying to do anything fancy with GRUB - just let it put the grub files on the / partition (which will go on sda2).

Are you using the live CD installer? If so, you can take a little precaution first: Make a copy of your bootsector so you can put it back later if needed. Use the CD and use these commands:
> sudo mkdir /media/sda1
sudo mount -t vfat /dev/sda1 /media/sda1
sudo dd if=/dev/sda of=/media/sda1/BOOTPART.IMG bs=512 count=1
then if you need to restore it later, use the live CD and the commands:> sudo mkdir /media/sda1
sudo mount -t vfat /dev/sda1 /media/sda1
sudo dd of=/dev/sda if=/media/sda1/BOOTPART.IMG
Fyi, the argument meanings are: 
if: input file
of: output file
bs: block size
count: number of blocks to copy

The live CD installer **will** overwrite your existing bootloader code. The "alternate" text-mode installer CD gives you the option to put GRUB in you root partition instead if you prefer, in which case you will have to arrange for some other bootloader to boot that partition for you.

Linux needs at least 2 partitions - / and swap. It is common to use more, although the default Ubuntu install only makes those two. Most common is to use separate partitions for / and /home. /home is where all the user files go - equivalent to all the My Documents folders on Windows. This is worth doing so that you can reformat and reinstall the o/s on / if you want without losing all the user data in /home. 

Your system partition should be 5-10 Gig but since you can't use any space you leave (if you were to shrink sda2, you can't have a 5th promary partition to give the space to, and it's not in the right place to expand the extended partition) you may as well leave it at its current size. You might consider creating a separate home logical partition if you have free space there though.

Hope this helps.

P.S.
You may want to install a 32-bit Dapper despite the 64-bit CPU, because some stuff that you don't have source code to doesn't work on 64-bit very easily - audio and video codecs, flashplayer frinstance.

---

### Post by wgaprotest on 2006-08-05
k, made a couple of changes since my first post, so according to windows' admin tools/disk management I can finally see what you mean by:

"An extended partition is a primary partition (so it must be one of the first 4 partitions) that acts as a container for all the "logical" partitions. So in your case, you have 3 normal primary partitions that contain normal stuff - FAT, ext3 and NTFS. Then you have your extended partition that probably fills the rest of the hard disk. Inside this extended partition are partitions 5, 6...."

The problem was that, under the linux install program (from the liveCD), it showed sda1 [dos/BM (p)], then the former sda2 [where I wanted the Linux / root [35G, ext3, also primary)], then the sda3 (MCE, 22G, ntfs [p]), then a large extended [primary], and THEN all the logical drives (data, drivers,backups and media). to be clear, it did show extended as being totally separate from the logical drives; NOT encapsulating them as you write. 

However, I'd read somewhere that the linux should be on a logical drive, and had tried to make sda2 logical, but couldn't for some reason. 

So I tried moving the sda2 (which I'll now call Linux), so order under linux installer was dos/BM, MCE, extended, and then I could make the Linux logical, so the list went on as extended (p), linux (l), data(l), drivers (l), backups (l), media (l). The linux installer was still showing the extended as primary and SEPARATE from the logical drives, although windows is showing it as encapsulating the logical ones as you state. Confusing. 

The 3rd try at install last night, after writing the post, with this new order of partitions, still gave me the 'invalid file system for this mount point' message, and the only thing that would "work" for an install last night with this new order of partitions was if I simply didn't try to manually edit my partitions, and let the ubuntu installer put everything on the IDE drive, configure the partitions, etc. Of course, it doesn't actually "work" because the IDE is a slave to the DVD writer, so its certainly not bootable and my MBR for windows is still fine. 

I will certainly try to take your advice about backing up my MBR, but I'd tried becoming root and mounting drives on the liveCD, but it wouldn't let me. I don't know if it'll allow me to follow your advice as a simple liveCD user.

During the linux 3rd install/manual edit partitions I had tried to shrink the linux partition by 512MB to have the linux-swap follow the / partition, which I understood to be where the /system files would go, and tried to put the /boot in the dos/BM. I had read that all OS's, including linux and win, could read fat... 

Perhaps I'm mis-understanding the difference between '/' and '/boot'? 

How can I chain from the dos/BM to the linux?

And why is the linux installer showing my partitions differently than in Windows?

I'm still no closer, despite your wonderful help and another person's wonderful help with explaining about mounting and mount points (from the linux questions/ubuntu forum). Nor do I believe that simply buying another Sata drive to devote to Linux will help me (and I'd rather save my scarce funds for CrossOver Office and/or a different tuner than the wonderful PowerColor PCI-E x1 tuner I've got, as it's run by ATI's Theatre 550 Pro software and I'm afraid it won't work under linux), as I'll still have the problem of chaining from the dos/BM to the 2nd Sata. And it'll mean going into the box... I'm seriously thinking about getting out my old PII, putting my current IDE slave back in it, and devoting IT to linux, but am afraid that won't help me with this beautiful beast (Vista-capable/SLI/all 64-bit/PCI-E home theatre PC).

---

### Post by steve.horsley on 2006-08-05
You may have trouble with GRUB in that it seems to not cope well with mixed IDE and SATA drive setups. I have seen a number of posts here where installations don't boot properly aparently because of this. So I don't adavise trying to put Ubunto on the IDE drive.

> I will certainly try to take your advice about backing up my MBR, but I'd tried becoming root and mounting drives on the liveCD, but it wouldn't let me. What was the problem? You really should have a backup, and know how to restore it using the live CD if the PC stops booting at all.

> Perhaps I'm mis-understanding the difference between '/' and '/boot'?  /boot is a folder off of the root folder. It is used to store stuff used for booting - OS images etc. Sometimes people use a separate partition, but Ubuntu doesn't by default - it keeps it on the main / root partition. Don't mess about with this - it's slowing you down. Just go for 2 or 3 mount points - swap you need, / you need (at least 5G), and /home is optional. Both / and /home should be ext3 or reiserfs. All 3 can be either primary or logical partitions. Your choice, whrever you have space.

> However, I'd read somewhere that the linux should be on a logical drive, and had tried to make sda2 logical, but couldn't for some reason. Linux doesn't mind. This allows you to use primary partitions for other things if you are so inclined. So if you have space inside the sda4 extended partition, create another logical partition and house Linux there. You can't make sda2 logical. sda1-4 are primary partitions, by definition. sda5+ are logical partitions inside the extended partition, by definition, and can only exist if one of the four primaries is an extended partition.
> How can I chain from the dos/BM to the linux?
Tricky. The live CD installer doesn't give you any choice except to put the bootloader on the MBR. The alternative installer gives you the option to install into the root partition instead. This is where you should install it if you want to use a different bootloader - than tell that bootloader to load the Linux partition when you choose Linux.

> And why is the linux installer showing my partitions differently than in Windows? How, in a drop-down list, would you indicate that a load of the items listed happen to be inside another item in the list? It's a tricky one.

---

### Post by wgaprotest on 2006-08-05
Well, for all your wonderful efforts, steve (good points all, particularly about the graphical/droop down list), and the other stuff I've ben reading on these forums, I'm going to have to take a break from these attempts to install linux for a day or so. 

I tried to implement six's solution about using NTloader, as my setup was almost like his, but I didn't get past deleting one of the logical partitions that hadn't even been used yet. Then Partition Magic told me there was a bad sector, cylinder, or such, and I'd have to delete EVERYTHING because my HDD was in danger of massive failure. And I don't think I'll even try to restore the MCE from the Acronis backups I have because I suspect the recent problems I've had with win may be due to the recent WGA Notify hell I've gone through, and is the very reason I'm struggling with Linux. I won't bore you with the details, as they're in another long post I put into a thread as to why Ubuntu might be able to compete with Vista.

Signed,
Busy-zipping-recorded-tv/burning-DVD's

---

### Post by steve.horsley on 2006-08-06
If you have partition magic, the the easiest way to install is to use PM to make some space - unallocated space, and then tell the Linux installer to use the free space. The installer will make the partitions it wants and then install onto them. Easy Peasy. You can reserve space with PM by temporarily allocating another partition, to prevent the installer from using that space.

---

