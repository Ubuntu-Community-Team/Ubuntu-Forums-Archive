---
title: "Help adding winxp to lepard and ubuntu already installed"
date: 2008-08-08
forum: Apple Hardware Users
---

### Post by guzzos on 2008-08-08
Hello there, I have a Macbook 4,1 with Leopard already installed.  I also installed Ubuntu 8.04 with it's respective swap space. I am also using rEFIt to switch between them.  Is there a way to install Windows XP without affecting my current configuration (without erasing or reinstalling Leopard or Ubuntu).

Any help is really appreciated.

---

### Post by HBBFrum on 2008-08-09
I think Apple has limited the ability of their computers to host multiple operating systems to just having two.

I was able to install XP and Vista on my mac, but in a single partition... You could try using Ubuntu to create a partition within a partition :/... No idea how that would turn out though...

---

### Post by cyberdork33 on 2008-08-09
> **HBBFrum said:**
> I think Apple has limited the ability of their computers to host multiple operating systems to just having two.
That is completely untrue... have a quick look in the forum here and you will see different...

> **HBBFrum said:**
> I was able to install XP and Vista on my mac, but in a single partition... You could try using Ubuntu to create a partition within a partition :/... No idea how that would turn out though...
That doesn't even make sense. You would have to make a separate partition to install both XP and Vista...

---

### Post by HBBFrum on 2008-08-09
> **cyberdork33 said:**
> That is completely untrue... have a quick look in the forum here and you will see different...

That is why i said I think, I just rarely see it like that...


That doesn't even make sense. You would have to make a separate partition to install both XP and Vista...[/QUOTE]

You think I wasn't surprised when I saw that I have them both installed on one partition? I have linux on my dell without a partition, which kinda worries me... and makes me think maybe I do have a partition.

But anyways, when I installed vista into the XP partition, unless it automatically split the partition in half... I don't know, I just can't remember anything about having to repartition.

---

### Post by guzzos on 2008-08-09
Well thanks anyway for your input.  I tried to use the disk utility in Leopard to create a partition using extra space available in my OSX startup partition but I get the following message from disk utility:

"Partition failed with the error:
MediaKit reports no such partition"

I have no idea what this message means.  My current volume scheme is as follows:

Partition 1
	Name       : “OSX”
	Size       : 100.0 GB
	Filesystem : Mac OS Extended (Journaled)
        Do not erase contents
 
Partition 2
	Name       : “DISK0S3”
	Size       : 18.6 GB
	Filesystem : MS-DOS (FAT32)
	Do not erase contents
 
Partition 3
        Name       : “Linux Swap”
	Size       : 2.4 GB
	Filesystem : Mac OS Extended (Journaled)
	Do not erase contents

Any help will be highly appreciated.

---

### Post by cyberdork33 on 2008-08-10
Install [rEFIt]("http://refit.sourceforge.net/").

run /Applications/Utilities/Partition Inspector.app

Copy and paste the partition info here.

---

### Post by guzzos on 2008-08-10
This is the information from partition inspector.  Before you analyze this mess I will tell you the whole story. I had my Macbook working with rEFIt to switch between OSX and Ubuntu.
Everything was working fine until I decided to install WinXP.

 I followed this instructions to install WinXP  ([http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp)).  Of course this failed because the new partition I made with the spare space in my OSX partition was not the second one (At least that is what I understood) because I already had ubuntu installed.

After installing WinXP, it failed to continue installation and removed my Ubuntu from the rEFIt menu, so I ended up with only my OSX partition working.

As everything got messed up except for the primary partition OSX, I decided to erase all partitions to have just one and start all over the triple boot tuturial from ([http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp))

My problem now is that I cannot delete any partition using disk utils nor via terminal mode.  I tried to merge the last two partitions with "diskutil mergePartitions" and I got and error that sounds like "Could not read partition map (-9988)".

Now what I want is to get rid of all those partitions to start a clean install.  I will appreciate your help but I won't blame you if you decide to abandon this tragedy.

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    140656679  Mac OS X HFS+
 3      140918824    268582951  Basic Data
 4      268582952    307383303  Mac OS X HFS+
 5      307645453    312580999  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    140656679  af  Mac OS X HFS+
 3 *    140918824    268582951  0c  FAT32 (LBA)
 4      268582952    307383303  af  Mac OS X HFS+

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 140918824:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 0c  FAT32 (LBA), active

Partition at LBA 268582952:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 4, type Mac OS X HFS+
 Listed in MBR as partition 4, type af  Mac OS X HFS+

Partition at LBA 307645453:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 5, type Linux Swap

---

### Post by guzzos on 2008-08-10
Hello Cyberdork33, forget about the previous post. I finally found a way to get rid of my partitions and get just one big OSX one to start a clean triple boot setup.  My new partition scheme is as follows: 


*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    312057519  Mac OS X HFS+

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1    312581807  ee  EFI Protective

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+




In case you see something wrong in this report, let me know.

THXS

---

### Post by cyberdork33 on 2008-08-10
> **guzzos said:**
> Hello Cyberdork33, forget about the previous post. I finally found a way to get rid of my partitions and get just one big OSX one to start a clean triple boot setup.  In case you see something wrong in this report, let me know.
Nope that looks good. Clean slate. Something defintely went wrong with your attempt. I would recommend following one of the guides in the wiki instead of that guide since it is a bit older. Anyway, I would start out with diskutility to create the various sizes of the space you want to have for each OS and then go from there. That will help Windows and OS X cooperate with your other partitions better.

---

