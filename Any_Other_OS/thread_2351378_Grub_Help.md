---
title: "Grub Help"
date: 2017-02-02
forum: Any Other OS
---

### Post by frank105 on 2017-02-02
Okay - so I know this is way off base here but this forum has always been nice to me and helped me with trickier things than this...

So here we go:
HP Pavilion x2 12-b020nr 
Intel Core M3, 4 GB RAM, 128GB SSD with Win10.

I installed Remix OS on a separate partition on my HD.  (Bear with me - this is a GRUB question)

Okay - I messed around a bit and ended up messing up my Grub boot... so now it won't boot Windows 10 correctly. 

Now my Win10 install is fine and dandy but just won't boot normally.  I can boot to it by interrupting the boot with 
Esc, 
then F9 (Boot Device Option)
Boot from EFI File (Instead of the default OS Boot Manager)
Select File to Boot = EFI
Boot
Select a File = bootx64.efi

I have used a Win10 install USB and tried startup repair and system restore and... everything else I can think of...  But my laptop will not boot correctly into Win10 when selected.  

I tried to find GRUB.CFG files etc - but they all seem to be from other previous Linux installs that I did.  None of them show the Remix OS.

So - how do I find the correct location of GRUB?
How do I edit or update the file?
What is the simple way?  Can I boot into Mint or Elementary OS that I have on a thumb drive and do like a Grub update or search command?

Oh - and my hard drive file structure looks like 

[IMG]https://dl.dropboxusercontent.com/u/18409659/Capture.PNG[/IMG]


Okay - so again I ask PLEASE since I know this doesn't really relate to Linux.  I feel really close to finding the right answer I just can't put my finger on it. 

Thanks in advance,

Frank

---

### Post by howefield on 2017-02-02
Thread moved to the "*Any Other OS*" forum.

---

### Post by oldfred on 2017-02-02
Does not look like a typical Windows UEFI install. Seems to be missing a couple of misc partitions.

 May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 

      
 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions)
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference)
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

Also Windows likes lots of free space. Or 30% unused inside the NTFS partition. When you get to 10% free a defrag may take forever as it has no working room.

---

### Post by frank105 on 2017-02-03
Thanks OldFred.  

I knew this was the place to come for the answer.  But the solution that fixed it for me was:
boot manually into Windows as I described in the OP
In windows - used the Remix OS uninstaller. 
deleted the partition I used for Remix
Added back the partition for Remix
Reinstalled Remix.
Reboot.

Thanks again for the pointers.  
Frank

---

