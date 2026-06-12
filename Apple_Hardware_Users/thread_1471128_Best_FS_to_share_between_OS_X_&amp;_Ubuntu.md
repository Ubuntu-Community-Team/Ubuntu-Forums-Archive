---
title: "Best FS to share between OS X &amp; Ubuntu?"
date: 2010-05-03
forum: Apple Hardware Users
---

### Post by Jheric on 2010-05-03
So, my girlfriend wants to dual-boot OS X and Ubuntu.

We want to format her laptop as:

20gb - Mac OS (Mac OS Journaled)
20gb - Ubuntu (ext4)
158gb - Shared Partition (???)
2gb - Swap

The most common suggestion I see around on the net is to go with FAT32 for the shared partition. But I know FAT32 isn't journaled and has a max file limite of 4gb. I've also seen some limited mentions of adding ext3 support to OS X or adding additional HFS support to linux...

Can anyone give me a good solid recommendation for a -everyday use- partition to share between her two OS's?

(explanation: she'll be using OS X for video editing or music recording... thus why the 4gb file limit is greatly concerning to me.)

---

### Post by srs5694 on 2010-05-03
Personally, I'd use HFS+; however, Linux currently doesn't support read/write operation for *journaled* versions of HFS+, so you may need to use it unjournaled. (This limitation can reportedly be overcome in various ways, but I don't recall the details.) Using NTFS for this is a Bad Idea because it will become useless the moment the system crashes or experiences a power failure; after such an event, an NTFS partition must be checked by Windows, which of course you're not running. (If there's a reliable NTFS check utility for OS X, this might be less of an issue.) FAT32 is, as you say, a bad choice because of its 4GiB file size limit. (I don't recall offhand the file size limit for the older non-plus HFS.) Using ext2fs or ext3fs might be an option, but I'm not sure how good the OS X ext2/ext3 driver is.

One other point: I'd put the shared partition between the OS X and Ubuntu partitions; that will reduce head seeks when accessing the partition from either OS.

---

### Post by moviemaniac on 2010-05-03
I got fed up of the dang limitations of OSX regarding file systems and switched to a NAS ;)

---

### Post by untmdsprt on 2010-05-09
Ooo, this is what I'm wanting to do, but I'm debating why exactly do I need Ubuntu, why would I want to switch, etc.

What does your girlfriend want to do on the Ubuntu side?

---

### Post by paulinchen on 2010-05-09
As I said in another thread:

[http://ubuntuforums.org/showthread.php?t=1473069](http://ubuntuforums.org/showthread.php?t=1473069)

I think its the most comfortable way to make one home partition for both, lucid and leopard ...

---

### Post by vincebs on 2010-05-13
I can access my Mac partition from Linux, but my Linux partitions are currently in ext4 so I can't get to them from Mac OS. If there's a file system I can install Ubuntu on that Mac OS can access, then I'd be willing to reformat the partition.

So is there any file system I can install all of Ubuntu under that Mac OS can access? (not necessarily natively, if there's something i can install similar to MacFUSE that's okay too)

---

### Post by srs5694 on 2010-05-14
IMHO, it's a Bad Idea (note the capitalization) to give one OS regular and ongoing direct access to another OS's system files. Typically, each OS knows and respects its own access control systems (permissions, ownership, etc.), and knows what files it should and should not be mucking with. This isn't true across OSes, so if you give Linux access to OS X, or OS X access to Windows, or whatever, the chances of a user or system process accidentally trashing something vital on the foreign OS go up. Such problems might not occur right away, but if you leave it running like that for days, weeks, months, or longer, the odds of a problem just keep on climbing.

Instead, I recommend using a data-exchange partition. You can mount this partition in all your OSes and use it to exchange user data files. If necessary, it can be very big and can hold large amounts of data that you might want to access in multiple OSes -- digital photos, MP3s, word processing documents, etc. For a Linux/OS X configuration, my personal preference is to use HFS+ for this purpose, although that choice has its problems -- Linux can't provide read/write access to journaled HFS+ without jumping through some extra hoops, although the unjournaled form is better. There may also be a need to synchronize UIDs between the OSes or be very careful with permissions settings. FAT is a tolerable lowest-common-denominator filesystem for some purposes, but it tops out at a 4GB file size, which may not be enough for some purposes. NTFS is a bad choice if Windows isn't installed on the system, since (AFAIK) neither Linux nor OS X has good native filesystem checking tools for NTFS. Ext2fs/ext3fs might work, but I'm not sure how good the OS X ext2fs/ext3fs drivers are.

---

### Post by chernandburn on 2010-12-31
[FONT=Courier New][COLOR=Black]What's the complicated way of mounting an HFS+ r/w volume attached to a USB drive?[/COLOR][/FONT]

---

