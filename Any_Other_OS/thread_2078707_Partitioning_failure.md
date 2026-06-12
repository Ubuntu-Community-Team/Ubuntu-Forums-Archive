---
title: "Partitioning failure"
date: 2012-10-31
forum: Any Other OS
---

### Post by Jbshare on 2012-10-31
Hi.  I attempted to install Ubuntu for my roommmate on his HP netbook.  Everything was going wonderfully until it got to the hard drive partition.  I tried resizing the largest part (from 230gig to 160gig, leaving 70 for Ubuntu) but it said it was unusable.  So I re-resized that part back to its original size and quit, since when I looked it up on my computer it said to shrink the space in Windows first.  However, when I tried accessing Windows, it said that the operating system has been corrupted.  I know I screwed up (and even more, I should have made sure he had everything backed up) somewhere, is there any way of salvaging his Windows computer?  He is a professional photographer and many of the photos he needs are on there, and there only.

---

### Post by zipher on 2012-10-31
There are various programs that can look at HDD and 'see' or 'restore' corrupted files, especially jpegs I believe......
..... but, before digging yourself in any deeper make sure that you are very organised and focussed about exactly what you are trying to achieve.

I am currently ploughing my way throughnsome similar problems so I wish you good luck.

---

### Post by zipher on 2012-10-31
[http://ubuntuforums.org/showthread.php?t=1737018&highlight=hdd+forensic](http://ubuntuforums.org/showthread.php?t=1737018&highlight=hdd+forensic)

The above thread is quite a good lead.

---

### Post by oldfred on 2012-10-31
Welcome to the forums.

Moved to Other OS since Windows issues.

Windows does not like to be resized from outside. Always best to use Windows MMC to shrink Windows. But even then the first thing Windows does is run chkdsk on reboot to update its new size. 

Boot a Windows repairCD or USB and run chkdsk and maybe other Windows repairs. Run chkdsk before and after any other repairs and if errors until there are not errors as it does not always fix everything on one pass.

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

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

### Post by Jbshare on 2012-10-31
Thank you all for your responses.  I wish this computer responded half as positively.  

So I tried inputting all of those things into the Command Prompt. Nothing changed.  Here is a picture of what the screen shows when it is asked about hard drive partitions.  Note that /dev/sdb2 should not have 3gigs used, it should be around 90.  I don't know why it is like this.  Also it should not be a ext4 file, but rather an ntfs one.  I think.
[IMG]http://s15.postimage.org/pb6tpaed5/PA310341.jpg[/IMG]

---

### Post by oldfred on 2012-10-31
Screen shot did not some thru. Use paperclip icon to attach screenshots.

If you reformated it, STOP using drive. Only use liveCD.

First see if testdisk sees old partitions. But it may need photorec to recover files if partition is gone.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

---

### Post by Jbshare on 2012-10-31
I'm sorry the screenshot did not carry.  Here is the link, just click on it.  [http://s15.postimage.org/pb6tpaed5/PA310341.jpg]("http://s15.postimage.org/pb6tpaed5/PA310341.jpg")

Can you please explain, in a more clear fashion, exactly what to do?  Best case scenario, I restore Windows to the way it was before and can then go from there.

Thank you so much for your help.

---

### Post by oldfred on 2012-10-31
If sdb was your Windows drive you overwrote the sdb2 partition which was the main install. Your sdb1 is the typical hidden boot/repair partition, but sdb2 is now Linux format.

Better to take a screenshot and attach with paperclip. 

What is sda?

Post this:

sudo parted /dev/sda unit s print

If sdb was Windows drive you have overwritten it, but Ubuntu is a lot smaller than Windows and you may be able to recover some of the data, if you did not have a good backup.

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

---

