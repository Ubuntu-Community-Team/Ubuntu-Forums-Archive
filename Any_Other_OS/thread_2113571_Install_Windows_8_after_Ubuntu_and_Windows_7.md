---
title: "Install Windows 8 after Ubuntu and Windows 7"
date: 2013-02-07
forum: Any Other OS
---

### Post by chromium1 on 2013-02-07
I am currently running a dualboot with Windows 7 and Ubuntu 12.10. I want to install windows 8 on another partition, but im not sure how the bootloader will work. Right now when i turn on my PC im presented with grub with a ubuntu and windows 7 entry, but when i install windows 8 which bootloader will take over. Will the windows 8 bootloader find automatically find windows 7 and ubunty, or will grub find windows 8?

---

### Post by darkod on 2013-02-07
Installing win8 will install windows bootloader to the MBR. It can't boot ubuntu so you will have to restore grub2 to the MBR after that from live mode. So, have your ubuntu cd at hand.

Another important fact: Windows combines boot files from two or more installations and puts them on the partition with the boot flag. If you want win7 and win8 boot files to be separate, first create ntfs partition for win8 in advance (from win7 for example, or ubuntu), put the boot flag on it instead of the win7 partition, and only then start the win8 installer.

That way grub2 can show both entries for win7 and win8. Otherwise there will be only one entry for the combined windows files, and then a second screen to select between 7 and 8.

Also, for this to work the new partition for win8 has to be primary too.

All of the above is for msdos partition table and legacy boot. If you are using uefi boot I don't know how exactly it will go, I don't use uefi.

---

### Post by naano on 2013-02-07
In general, whichever OS is installed last will overwrite the other bootloaders. So if you install Ubuntu first and Windows second, the Windows install will overwrite grub. If you want grub back, it's as simple as booting the live disk and using Boot Repair: 
[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")
If you would rather use the Windows boot loader, you can add an entry using EasyBCD or some other tools so that Windows can "see" your Ubuntu install. This works the same way with Windows 7 and 8, though 8 has the new snazzy tile boot menu. You can check out some more info here: [URL="http://lifehacker.com/5840387/how-to-dual+boot-windows-7-and-windows-8-side-by-side"]http://lifehacker.com/5840387/how-to-dual+boot-windows-7-and-windows-8-side-by-side
[/URL]
As for your case, Windows 8 will likely see your existing Windows 7 partition when you install and boot up, but not your Ubuntu partitions (unless it's NTFS). The thing you need to be most careful with is hidden partitions, the 4 primary partition limit of MBR drives(if applicable), other stuff. Best of luck!

---

### Post by Mark Phelps on 2013-02-07
Even if you create an NTFS partition for Win8, it will still most likely write its boot loader files into the Win7 partition -- that's what it did to me when I did the same thing.

When you boot, the Win8 boot loader will have an entry for Win8 and another one for Win7.

When you install GRUB, the os_prober will see the boot loader in the Win7 partition but will know that it's Windows 8 -- so the entry will say Windows 8 Loader.

When you select that, you will the the Windows os selection screen and then will have to select Win8 or Win7.

---

### Post by darkod on 2013-02-08
> **Mark Phelps said:**
> Even if you create an NTFS partition for Win8, it will still most likely write its boot loader files into the Win7 partition -- that's what it did to me when I did the same thing.


It did that even when you moved the boot flag before installing it?

It shouldn't, unless they made changes again (read messed up :) ). On the other hand, just creating a partition is not enough unless you move the boot flag before you start the installer. It will put the files where the boot flag is.

---

### Post by chromium1 on 2013-02-08
Ok so i need to do this?:

-create an ntfs partition for windows 8 (using win7)
-move boot flag to the win8 partition
-install win8 on that partition
-after win8 install, boot into live ubuntu and run boot repair

Im confused about moving the boot flag. What does that really mean and how do it do it?

---

### Post by darkod on 2013-02-09
Correct.

The easiest way to move the boot flag would probably be from ubuntu live mode using Gparted. You right-click the win7 partition first, select Manage Flags in the submenu that opens, and remove boot flag.
Then you do the same on the win8 partition to activate the boot flag there. Save changes and close Gparted.

Reboot with the win8 dvd and start the install.

---

### Post by chromium1 on 2013-02-09
OK I have really bad news...my PC won't boot into an os.
I decided to remove Ubuntu because I didn't want it  anymore( I just wanted to dual boot win8 and win7) . so i used easybcd to write the MBR to the win7 boot loader, then I deleted my Ubuntu partition and swap partition. I then deleted my dell recovery partition to get some more space (which I now regret,). I then needed to merge the unallocated space I created, so i used easues partition manager to move my c: drive to the left and have the unallocated space beside each other. When the PC rebooted after applying the changes, I get this error:

PXE-E61 : media test failure check cable
PXE-M0F : Exiting PXE ROM
Insert bootable media and press any key to continue

I'm really scared right now, please help.

---

### Post by darkod on 2013-02-09
Welcome to windows. The more you try to do, especially with moving partitions around, the more problems can happen. You have too much faith in windows, you shouldn't have tried so many changes at once.

On another note, you are aware that this is the ubuntu forum right? I don't want to sound harsh, and this is not a punishment for removing ubuntu, but since the topic has turned into windows issues, moving partitions, recovering them back, etc, I think you might find people who can help you more on the windows forums. They know more details about the windows tools.

Obviously the repartitioning went wrong. I don't think easeus offers support for their free products, maybe their forum can help.

The only thing I can think of using ubuntu in live session is trying to recover your partition with testdisk. But note that it might not be recoverable since you actually did try to move it with easeus. For example, if you delete a partition it is easier to recover than trying to move it. Deleting a partition doesn't remove/move data but moving a partition might actually try moving the data, which is more complicated to recover.

Anyway, if you want to give it a shot:
[www.cgsecurity.org/wiki/TestDisk_Step_By_Step](www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

There are probably windows programs to try recover data but I don't know any, that's why I suggested the windows forums for more detailed info. Also, may programs that can recover files actually read the whole hdd and recover what they find but the files don't have the original names. So it can happen that you need to wait several hours and then spend further several hours checking which file is what and naming them accordingly.

---

### Post by Mark Phelps on 2013-02-09
> **darkod said:**
> It did that even when you moved the boot flag before installing it?

It shouldn't, unless they made changes again (read messed up :) ). On the other hand, just creating a partition is not enough unless you move the boot flag before you start the installer. It will put the files where the boot flag is.

Good point ... I didn't move the boot flag (because basically, I didn't CARE where it wrote the boot loader files).  So had I moved it, it probably would have done as you said.

On another note, I did a Win8 install to a Win XP, Win7 PC and, as expected, it wrote the Win8 boot loader files to the XP partition -- where the boot flag is located.

However that said, if you now have MULTIPLE partitions with boot loader files, only ONE of them can have the boot flag -- and the ones that don't might not be bootable anymore.

---

### Post by Mark Phelps on 2013-02-09
> **darkod said:**
> There are probably windows programs to try recover data but I don't know any, that's why I suggested the windows forums for more detailed info. Also, may programs that can recover files actually read the whole hdd and recover what they find but the files don't have the original names. So it can happen that you need to wait several hours and then spend further several hours checking which file is what and naming them accordingly.

Actually, to recover data from Windows filesystems (including the original directory and file names), you need to read the following:

In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from Runtime Software in MS Windows.
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to the website below, you can compare the features and (at least for me) the extra cost wasn't worth it:

[http://www.recovermyfiles.com/data-recovery-software-purchase.php](http://www.recovermyfiles.com/data-recovery-software-purchase.php)

Your data ... your money ... your choice.

---

### Post by oldfred on 2013-02-09
Moved to Other OS since only Windows issues.

---

### Post by darkod on 2013-02-09
> **Mark Phelps said:**
> 
However that said, if you now have MULTIPLE partitions with boot loader files, only ONE of them can have the boot flag -- and the ones that don't might not be bootable anymore.

Depends on your point of view (and bootloader used). Grub can always detect and boot the boot files, if they are not messed up in any way. So they will always be bootable for grub. The only way to have several windows versions as separate entries in grub is to have separate boot files.

If you plan to use windows bootloader (or later go back to using it), you are right, it will automatically boot the partition where the boot flag is, and only that one. It will not have a submenu to select between several windows versions. That's the downside of separate windows boot files if you go back to windows bootloader.

---

### Post by chromium1 on 2013-02-09
thanks for the quick reply.
So is there no possiblity of me getting my full system back and running?
If i cant, would this be the right thing to do:
-use ubuntu livecd and copy all my files to a usb flash drive
-reinstall windows 7

Is it possible that my hard drive is completely destroyed, to the point that i cant install an operating system?

---

### Post by chromium1 on 2013-02-09
sorry for my windows posts but now i need some ubuntu help again.
If i boot using a ubuntu 10.10 livecd will i be able to see my windows 7 partition and copy my files to a usb drive. Also do guys think that the files will be corrupt because of how i moved the partition with eausues?

---

### Post by Dr. C on 2013-02-09
> **chromium1 said:**
> sorry for my windows posts but now i need some ubuntu help again.
If i boot using a ubuntu 10.10 livecd will i be able to see my windows 7 partition and copy my files to a usb drive. Also do guys think that the files will be corrupt because of how i moved the partition with eausues?

This is a simple way to tell what is happening. While the hard drive may be un-bootable there is a very good chance that the files are still there. Ubuntu does read NTFS so unless the files were encrypted with Bitlocker there is a very good chance that this should work.  

By the way I recovered files from a badly corrupt Windows XP system (BSOD and malware) by using an Ubuntu live CD and copying the files to an external USB drive.

---

### Post by chromium1 on 2013-02-09
Ok I booted into Ubuntu with an old 10.10 livecd, and I am currently successfully copying my files off the hard drive. (Not sure if they are corrupt yet though) . anyways once I'm done I want to maybe fix the partitions, is there a partition manager built into Ubuntu?

---

### Post by Dr. C on 2013-02-09
> **chromium1 said:**
> Ok I booted into Ubuntu with an old 10.10 livecd, and I am currently successfully copying my files off the hard drive. (Not sure if they are corrupt yet though) . anyways once I'm done I want to maybe fix the partitions, is there a partition manager built into Ubuntu?

Yes. It is called GParted and it is on the live CD.

---

