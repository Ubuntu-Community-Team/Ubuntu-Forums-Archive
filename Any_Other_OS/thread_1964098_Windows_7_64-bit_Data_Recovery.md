---
title: "Windows 7 64-bit Data Recovery"
date: 2012-04-23
forum: Any Other OS
---

### Post by ConMac on 2012-04-23
):P  I'm new to this forum and I hope someone can lend some assistance.  My issue is that I have a dual-boot system, Windows 7 on one HD, and XP on another HD.  I recently had some RAM fail which I successfully swapped out and tested with Memtest86+.  However, now my Windows 7 is unbootable, and I have tried everything.  My XP boots up just fine, always did even with the bad RAM.

I have burned two UbuntuLive CD's:  one 32-bit and one 64-bit.  I need to copy/backup the "My Documents and Settings" folder from Windows 7 to a USB external HD.  I have run the two backups and copies to the external HD.  When I boot back into XP and look at the external HD, the folders with backups have over 11GB of data in them, each contain a number of zip files.  I presume this is correct.  But when I open up the folders containing the copies, there is nothing in there.

My questions are:

Does it make a difference if use the 32-bit or the 64-bit Ubuntu Live CD?
Why can't I see the files copies on the external HD?  It this normal?
What is the best method to copy these files to the external HD?.

And help would be greatly appreciated!  :p

---

### Post by CharlesA on 2012-04-23
If you are just copying the files, nothing should be zipped up.

What error are you getting with Win7?

---

### Post by collisionystm on 2012-04-23
As stated by Carlos, nothing should be 'zipped'. You simply boot the live cd, open the file browser ( click on the home folder ) and browse to your drives. You copy and paste the files from one drive to the other.

---

### Post by ConMac on 2012-04-23
The zipped files are in the folders that contain the backup.  The folder that I thought I was copying the files to has nothing in it.  To copy a file, I went to the top of the screen, browsed over the Documents and Settings folder, hit copy, then I went to the external HD and hit paste.  Is that not correct?

The error message I get from Win7 is that it is unable to boot normally/  I've tried everything recommended by the WinSeven Forum, and others (eg:  rebuilding the MBR, bootrec, etc.).

Also, should I use 32-bit or 64-bit? Thanks for the help!

---

### Post by oldfred on 2012-04-23
If your computer is newer and boots with the 64bit version, then it does not matter. 

Best to see what is installed where, run bootinfo script and post link to its output: 
You can download this into your Ubuntu liveCD or USB or download it as a full liveCD.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

### Post by CharlesA on 2012-04-23
> **ConMac said:**
> The zipped files are in the folders that contain the backup.  The folder that I thought I was copying the files to has nothing in it.  To copy a file, I went to the top of the screen, browsed over the Documents and Settings folder, hit copy, then I went to the external HD and hit paste.  Is that not correct?

Sounds right. It still shouldn't be zipping up the files.

Does dragging and dropping the files onto the external do the same thing?

---

### Post by ConMac on 2012-04-24
[http://paste.ubuntu.com/943964/](http://paste.ubuntu.com/943964/)
[http://paste.ubuntu.com/943974/](http://paste.ubuntu.com/943974/)

I tried the Boot Repair disk, and even though it said the repair was successful, it still doesn't boot into Win7.  These are the links associated with the effort.  I also copied and pasted the Documents and Settings folder using Boot Repair to my external HD.  But when I boot into XP and look at this file, all I see is a 52-byte System File.  Why am I unable to copy this folder?  Thanks for the input!

---

### Post by oldfred on 2012-04-24
Your install of Windows 7 looks like it has all the correct bits in the right places from the script. But script does not show all the internals in the PBR - partition boot sector.

Your Windows 7 install starts at sector 63, which was common for XP and even Vista. But 7 changed to using 2048. Early versions of gparted often changed 7 to 63 and then 7 would not boot as the internal data in the  PBR did not match. It was normally fixed with chkdsk and fixboot, but sometimes users could not fix it so, we usually suggest using Windows 7's own tools to resize 7.

Did you change the partition that Windows 7 was installed in, or just install it over an older XP or Vista partition so the start at sector 63 is correct.

If not I would run chkdsk and fixBoot from a Windows 7 repair CD or USB. And they seem to be inter-related, so running more than once may also help.

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)
fix boot loader With screen shots from full Windows install media
[http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
# is comment do not copy or type comments
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r  #(have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector or see bootsect.exe commands
chkdsk c: /r
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

---

### Post by ConMac on 2012-04-24
I installed Win7 and XP on seperate partitions.  I put Win7 onto a 150GB partition that I created.  Everything was working fine until the RAM failure.  I continued to boot into Win7 after the first signs of the RAM going, so that must have corrupted something.

I figured out why I couldn't copy those files from my Documents folder:  I had to open up the file, high-lite everything; then copy and paste.  Piece 'o cake.

Thanks for the input, I let you know which of these options fixes the problem.  Cheers!

---

### Post by ConMac on 2012-04-24
I tried all those options, and they completed successfully, except one:  When I ran the bootrec.exe /scanos, the results were:  "Total identified Windows installations:  0"  Does this mean that Win7 is corrupted beyond repair?

---

### Post by oldfred on 2012-04-24
I do not know Windows that well, but I would think it would find both your installs. Did BCD update or you may be able to manually rebuild a BCD entry with bcdEdit. Some of the Windows sites have details on what goes into a BCD boot entry.

---

### Post by CharlesA on 2012-04-24
Could always try to boot off the install cd and do a repair and see what happens.

---

### Post by ConMac on 2012-04-26
None of the above suggestions worked, so I restored a system backup that I made two weeks before this issue began using EaseUS Todo Backup.  This great bit of software installed a boot option that permitted me to recover my system...and so far it is stable (keeping my fingers crossed!).  Thanks again for all your help!  Cheers!!

---

