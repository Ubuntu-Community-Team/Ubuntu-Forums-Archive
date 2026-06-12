---
title: "Mac Pro: Triple Boot Explained.  The Easy Way."
date: 2008-06-27
forum: Apple Hardware Users
---

### Post by emptyman on 2008-06-27
I spent days getting my Mac Pro to be able to triple boot Mac OS X 10.5, Windows XP (Vista would work fine), and 64-bit Ubuntu. I called Apple no less than 5 times.  Here's my experience and how to do it yourself.

I am using an 8-core Mac Pro.  I splurged for the extra RAID card.  It was in the way, and here's how I finally took it out.  If you don't have RAID, you can skip down.

To remove the RAID card, I had to remove much of the inside of the case.  DOING IT YOURSELF might violate your warranty.  Poster is not liable for anything you do to your Mac.  Follow the instructions on how to install a the Mac Pro Raid card here:

[http://manuals.info.apple.com/en/MacPro_RAIDCard_Installation.pdf]("http://manuals.info.apple.com/en/MacPro_RAIDCard_Installation.pdf")

Basically, pretend you are installing it, until you get to step 13.  Then disconnect the iPass cable and connect it to the original spot on the logic board.  Taking all of those pieces out was just to be able to get this plugged back in.  Take the RAID card out of the PCI slot, and put it all back together.

Very important!!!  After removing the RAID card, you have to reset the parameter RAM to get the drives showing up.  Boot while holding down option-command and p and r.


Yes, I know this is crap, that we can't use our $1000 RAID card.  If you would like to get it working with RAID, see FakeRaid.  Much luck to you, because BootCamp (still!) doesn't support RAID.  If you get it working PLEASE respond below.

With the card out and one big 750GB SATA drive in Bay 1, we are ready to install.

Boot off of the OS X disk.  Before installing, open Utilities -> Disk Utility and make 3 partitions.  Format the 3rd on MS-DOS (FAT32) for windows, and name it BOOTCAMP or something.  The second partition we are making is for Ubuntu.

Resume the installation, and install Mac OS X on the first partition.  I am using 10.5.  After the installation reboot, install [rEFIt]("http://refit.sourceforge.net/").  It's a boot manager for the Mac, which will allow us to choose the boot drive when we power on the machine or restart.  Insert the Windows CD and restart, holding down "c" to boot from the CD.

To install Windows, use the partition it suggests, which should be FAT32 and given the C: drive letter.  Format it with NTFS for best results.  Not sure what happens if you leave it FAT32.

Important!!! Do not do any partitioning of the drives here.  It will hose things and then you can start over.

After installing Windows (rebooting to finish install) insert the Ubuntu Feisty 64-bit Live CD.  Download it [here]("http://releases.ubuntu.com/7.04/"). 

Install from the CD.  When you get to the disk partitioning page of the wizard, choose Manual.  It will give you a list of current partitions.  You should be able to recognize the BOOTCAMP (msdos) partition, the Mac OSX partition (the first hfs+) and the Ubuntu blank partition in between.  Click on it, and remember its disk name for the last page of the wizard. (e.g. sda3).  Click Edit Partition, choose 'ext3' for the file system and '/' for the mount point.  Yes, format the partition.

Important!!! Don't just click off the end of the wizard.  On Step 6, Finalizing the Installation (or something), there is an Advanced button.  Make sure to click on it, and install the boot loader on the correct partition (remember from earlier).  Finish the wizard, remove the CD after installing, and reboot.

You're done!  No manual partitioning, no shell scripts or commands.  Apple Disk Utility did all the fun stuff, and now you can boot any of the 3 OSes!  Enjoy!

If anyone has additional information about getting this to work with RAID, please follow up.

---

### Post by wubi on 2008-06-27
Thank you!  This is exactly what I was looking for.  My one question would be when you partition your HD, you state for windows to use DOS FAT 32 and name it Bootcamp, what about the linux partition how would one format that partition?  Or at least which format other than DOS FAT?

I'm going to use this technique on my second HD by partitioning it in half, one for windows the other for linux.  Thanks!

---

### Post by emptyman on 2008-06-27
When partitioning on the Mac, go ahead and leave that drive as HFS+.  You will reformat it later during the Ubuntu install, into the 'ext3' filesystem.  So when you are installing Ubuntu, you will be choosing a partition labeled 'hfs+', just make sure it's the correct one (not your Mac OS).  

When I did my install I put all 3 partitions on the same disk, because there is something wonky about booting on the Mac, at least off of external drives.  I will be very interested to hear if you get this to work on 2 separate internal drives.

FWIW, a couple of guys at Apple suggested this as a good solution.  So I discourage using an EXTERNAL drive, but another internal should work just as well.

---

### Post by Phonan on 2008-06-27
The usual format for Ubuntu is ext3, but you can't do that with OS X Disk Utility. If you feel comfortable, just make the Windows partition DOS Fat 32 and the same for the Ubuntu partition. Then, on the Ubuntu install, you can format the partition to ext3, but make sure you are formatting the right partition! You don't want to format the partition with your windows installation and wipe it out.

Also, on your Windows install, I'd recommend NTFS over Dos Fat 32 because Fat 32 has a file size limit of 4 GB, whereas NTFS has no file size limits. However, if you use NTFS, it's much trickier to access files from your other OS's. You can pick a format for your Windows partition during the Windows install.

EDIT: Whoops, 2 minutes late; I must have spent a long time typing.

---

### Post by wubi on 2008-06-27
Thanks again for the tips.  I have successfully installed Ubuntu on the second (internal drive) were as REfit handles the boot menu.  My mac is on the first HD, but my issue lies on the 2nd HD.   When I go to install windows the installer says it cannot install into the partition.  This is why I want to wipe the 2nd HD clean and repartition it one as DOS FAT32 and the other as HFS then install again.  I just cant find a solution on getting the windows to recognize the partition.


So now I will leave HD 1 as Mac OS X leopard, and Wipe HD 2 to create 2 partitions.  then partition A will be hfs and partion B will DOS FAT 32.  Does it matter the order?

---

### Post by rathna on 2008-07-26
What if i required a /boot and a swap partition apart from the /(root) partition. Should i create 5 partitions? and on "Advanced" should i choose the /boot partition to install grub?

---

### Post by cyberdork33 on 2008-07-26
> **rathna said:**
> What if i required a /boot and a swap partition apart from the /(root) partition. Should i create 5 partitions? and on "Advanced" should i choose the /boot partition to install grub?yes as long as /boot is in the first 4 you are fine. and yes install grub to the boot partition

---

### Post by rathna on 2008-07-28
Err...I have been trying it all weekend and today and I got "No bootable devices....", so I tried this link, [http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677), and my display froze with the tux image.

I performed a manual shutdown and tried choosing my linux partition again. this time it went past the tux image but came back with "GRUB Loading stage2...". The display hangs in there. I found another relevant thread [http://ubuntuforums.org/showthread.php?t=638752](http://ubuntuforums.org/showthread.php?t=638752).

Anyway I have no idea what mint is, I've been trying only ubuntu. 

Right now, OSX and Windows works just fine.

Could someone please help me. Thank you.

---

### Post by cyberdork33 on 2008-07-28
please give output of 
```
sudo parted /dev/sda print
```and
```
sudo fdisk -l /dev/sda
```

If you have multiple drives there maybe other issues at work.

---

### Post by rathna on 2008-07-29
No, I have only one drive.
[HTML]
<pre>
ubuntu@ubuntu:~$ sudo parted /dev/sda print

Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags
 1      20.5kB  210MB   210MB   fat32        EFI System Partition  boot 
 2      210MB   75.2GB  75.0GB  hfs+         Untitled                   
 3      75.2GB  75.4GB  128MB   ext2                                    
 5      75.4GB  79.5GB  4096MB  linux-swap                              
 6      79.5GB  97.9GB  18.5GB  ext3                                    
 4      97.9GB  120GB   22.1GB  ntfs         Untitled                   
Information: Don't forget to update /etc/fstab, if necessary.


ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2cd72cd6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  EFI GPT
/dev/sda2              26        9148    73269248   af  Unknown
/dev/sda3   *        9148        9163      125000+   c  W95 FAT32 (LBA)
/dev/sda4           11905       14594    21595568    7  HPFS/NTFS
</pre>
[/HTML]
Thank you cyberdork for looking into my query.

---

### Post by cyberdork33 on 2008-07-29
> **rathna said:**
> No, I have only one drive.
Thank you cyberdork for looking into my query.
Your partition tables do not appear to be synced. The first thread you linked to shows how to fix that. Please try to sync again and note any odd messages, or if it executes fine, then repost these commands' output again.

---

### Post by rathna on 2008-07-29
Ok, this is what I did for syncing:

After I installed linux, I rebooted the system, navigated to the partition tool within refit, Said "y" when I was asked if I should "Update the MBR". It updated it successfully and there were no odd messages.

When I go back to the partition tool, I'm told everything is in sync.

---

### Post by cyberdork33 on 2008-07-29
OK I see now, it was my mistake in reading the table.

So verifying, 
sda3 is for /boot ?
sda4 is windows (or a sharing partition)
sda5 is swap
sda6 is root

Does that sound right? If that is the case, then you will want to install GRUB to the /boot partition (sda3). This should also be the root partition for GRUB. so, booting into the live cd, run 'sudo grub' 

```
grub> find /boot/grub/stage1
``` should return (hd0,2). Then do
```
grub> root (hd0,2)
grub> setup (hd0,2)
```

as is instructed here:
[http://orgs.man.ac.uk/documentation/grub/grub_3.html#SEC9](http://orgs.man.ac.uk/documentation/grub/grub_3.html#SEC9)

---

### Post by mike-g2 on 2008-08-06
Hi,

I'm about to try and do this, but I had a few questions.  Previous posts on this topic ([http://macprolinux.blogspot.com]("http://macprolinux.blogspot.com") indicated that 

[INDENT](a) one needed to compile a custom kernel

(b) that cpu frequency scaling wasn't working.  
[/INDENT]
Can you confirm whether or not these problems still exist?

Thanks.

Mike

---

### Post by cyberdork33 on 2008-08-07
> **mike-g2 said:**
> Hi,

I'm about to try and do this, but I had a few questions.  Previous posts on this topic ([http://macprolinux.blogspot.com](http://macprolinux.blogspot.com) indicated that 
[INDENT](a) one needed to compile a custom kernel

(b) that cpu frequency scaling wasn't working.  
[/INDENT]Can you confirm whether or not these problems still exist?

Thanks.

Mike
I don't think you need to compile a custom kernel. I would only do that if ther eis something specific that you need to change in the normal kernel. 2.6.23 is old now anyway.

I don't know anything about the cpu freq scaling.

---

### Post by ben22 on 2008-08-21
Hi,

I followed your instruction (installation of mac os first, rEFIt, windows, ubuntu).

When starting from windows partition I get the error hal.dll not found.

Another fact is that when I choose Windows from rEFIt, then gurp loads and there I have to choose windows again. My assumption is that something went wrong with the bootmanager.

Any hints?

cheers,
ben

---

### Post by cyberdork33 on 2008-08-21
> **ben22 said:**
> I followed your instruction (installation of mac os first, rEFIt, windows, ubuntu).

When starting from windows partition I get the error hal.dll not found.
If you change the partitions at all after installing windows, you will get this error. Create your partitions before you install windows.

> **ben22 said:**
> Another fact is that when I choose Windows from rEFIt, then gurp loads and there I have to choose windows again. My assumption is that something went wrong with the bootmanager.
This is because by default, windows installs its bootloader into the MBR (really the only place it can go). Ubuntu, by default, installs its bootloader to the MBR also, but you can specify during the install to install it instead to your Ubuntu partition. Then it will show up in refit and windows will boot directly from there.

There is alot of information on multi-booting in the Macbook Pro wiki page. you can follow it for the actual installation as it is the same for all Macs.
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)

---

### Post by ben22 on 2008-08-21
when I start windows from rEFIt now, windows starts and then crashes. I see a blue screen for a moment, but cannot determine the error message.

Hers is the report from partition inspector

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    226377767  Mac OS X HFS+
 3      226377768    304502768  Basic Data
 4      310788136    390721927  Basic Data
 5      304502769    306455894  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    226377767  af  Mac OS X HFS+
 3 *    226377768    304502768  83  Linux
 4      310788136    390721927  07  NTFS/HPFS

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

Partition at LBA 226377768:
 Boot Code: GRUB
 File System: ext3
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 83  Linux, active

Partition at LBA 310788136:
 Boot Code: Windows NTLDR
 File System: NTFS
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 07  NTFS/HPFS

Partition at LBA 304502769:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 5, type Linux Swap


how can I determine the cause for not being able to boot windows?

---

### Post by emptyman on 2008-08-26
> **ben22 said:**
> when I start windows from rEFIt now, windows starts and then crashes. I see a blue screen for a moment, but cannot determine the error message.

...

how can I determine the cause for not being able to boot windows?

If everything else is working, I would do what you can to keep it that way.  Reinstall Windows on its partition is I think the safest, easiest thing to do.  Seems like worst case you would have to reinstall ubuntu as well, but I doubt it.

If I misunderstood the question, then nevermind.  I'll just offer this, I find that the delicate balance is in getting them installed in their partitions, in the right order.  I never had any success modifying things once I had it partially done but incorrectly.  I always had my best results starting over from a clean slate.  In this case if the Windows Paritition is known to be good, I would consider reinstalling Windows, reformatting the partition.  If it's not known to be good, you might consider starting completely over -- partitioning, OS installs, etc.  The whole thing takes a few hours front to end, and that's the BEST I could hope for if I were to try and fix a broken configuration.

My 2 cents.

---

### Post by muymoo on 2008-08-27
Have you read this how to: [here]("http://forum.onmac.net/showthread.php?t=2793").  It worked for me.  I left out the Vista partion but kept the 3 OS's and a storage partition (I would highly recommend this one).  It is very important install XP as the first OS in the MBR.  Make sure to read the whole thread though.  It is full of updates.  I had the same problem with hal.dll missing, but by doing this in the Mac OS X Terminal:
```
sudo fdisk -e/dev/rdiskO
```

then type p to print MBR

then type 

```
f "partition # you want to install XP on"
```

this will flag it as active.

type q to quit

restart and either your windows should work, or you will need to reinstall it on the now active partition.

---

### Post by dreamof3d on 2008-08-29
My Mac Pro has all four HD bays populated. I used bootcamp to install Windows XP 64, Bay 3. For the Ubuntu install, I simply powed off the machine after iserting the Live CD, opened the case and gently eased out every hd but bay 4 about an inch so they could not be written to. Fired up my Mac pro holding the c key, and let Ubuntu 64 take the whole disk with the default settings. Rebooot after install, shut down and gently push back all other drives. Reboot holding the option key, and Viola, all 3 os's at a mouse click. Now that is an easy, safe way. No worries about harming any other MBR etc.  :guitar:

---

### Post by papoose on 2008-12-21
> **dreamof3d said:**
> My Mac Pro has all four HD bays populated. I used bootcamp to install Windows XP 64, Bay 3. For the Ubuntu install, I simply powed off the machine after iserting the Live CD, opened the case and gently eased out every hd but bay 4 about an inch so they could not be written to. Fired up my Mac pro holding the c key, and let Ubuntu 64 take the whole disk with the default settings. Rebooot after install, shut down and gently push back all other drives. Reboot holding the option key, and Viola, all 3 os's at a mouse click. Now that is an easy, safe way. No worries about harming any other MBR etc.  :guitar:

That was exactly my idea, except that in my case I have no windows installed its just three drive one osx one file drive and finaly one ubuntu drive. It worked well except for one glitch everytime I start on osx it tells me the drive is unreadable and ask me if I want to format it. Obviously I ll just ignore it but its nagging to have to do that upon each restart of os x... So I finally installed refit which does help me select upon startup but I still get the window asking if I want to format the drive. As far sa the ubuntu install is concerned once I boot on it there is no apparent problem... any idea?

---

