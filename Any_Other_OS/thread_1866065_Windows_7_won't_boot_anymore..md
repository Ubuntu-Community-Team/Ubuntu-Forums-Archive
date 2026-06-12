---
title: "Windows 7 won't boot anymore."
date: 2011-10-20
forum: Any Other OS
---

### Post by u-slayer on 2011-10-20
Okay so I reshuffled some system partitions (don't ask) and then restored grub by using the grub-install command. Grub works great and it can load ubuntu just fine. However when I try to boot windows 7 I just get a black screen.

I popped in the Win 7 install disc and ran startup repair.

It now shows my Win 7 install in the list of operating systems but it says the Location is (Unknown) Local Disk.

When I try to run startup repair again it just says "could not detect a problem"

So I loaded the command prompt and I tried to run

bootrec.exe /scanos
It can't find windows.

So I ran
bootrec.exe /fixmbr
and wiped out the grub MBR
 
Then I tried
bootsect.exe /nt60 all
and it says it sucessfully updated on the third partition

However, when I reboot I just get a black screen when trying to load windows and "bootrec.exe /ScanOs" still can't find windows even though I ran that bootsect.exe command

What else can I do to get windows running?

---

### Post by oldfred on 2011-10-21
Moved to other OS.

download & run this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

if only minor repairs this will also run script and possibly make some repairs.

Yanni has created a easy way to download boot repair & run script:
HOWTO : easily create a Boot-Info summary
[http://ubuntuforums.org/showthread.php?p=11164270](http://ubuntuforums.org/showthread.php?p=11164270)
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by u-slayer on 2011-10-21
```
 sh '/home/ubuntu/Desktop/boot_info_script.sh' 

boot_info_script version: 0.60        [17 May 2011]

/home/ubuntu/Desktop/boot_info_script.sh: 353: Syntax error: "(" unexpected (expecting "fi")

```

---

### Post by u-slayer on 2011-10-21
I also tried your boot-repair program.


All it did was restore grub, but windows still shows a black screen when I try to boot it.

---

### Post by oldfred on 2011-10-21
When you installed you created a separate /boot partition. (Not normally needed for desktops but ok). But when you used boot repair you did not tell it you have a separate /boot so it did not install grub to the MBR correctly. Your MBR is trying to boot from sda2, but the boot files are in sda1.  Try again but tell boot repair your /boot is on sda1.

You also have sda3 issues. The partition table says it is Linux, but the PBR - partition boot sector says it is NTFS but does not have correct data in it. A NTFS partition has to have correct data matching partition table and be configured to boot your Windows as that is what Windows uses to know how to boot.

You need to change partition table entry (only, not reformat) to 07 so it is NTFS. You may be able to use Disk Utility from the liveCD or if you boot from Ubuntu from that. Or from liveCD use command line:

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

change sda3 to type 7
sudo sfdisk --change-id /dev/sda 3  7

---

### Post by u-slayer on 2011-10-22
Okay, I did what you said but it still doesn't work. On the bright side the window repair tool no longer marks the partition location as unknown.

Here is my latest paste bin:


I'm thinking it's time to admit defeat and just reinstall windows from scratch.

---

### Post by oldfred on 2011-10-23
Your Windows NTFS boot partition needs fixing. Its info has to match the partition table which it says it does not. Do not run fixMBR & you may need to run chkdsk and/or run each again in opposite order as both fixBoot & chkdsk update parts of the boot sector, but sometimes seem to depend on each other to be first.

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r  (have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector or see bootsect.exe commands

---

### Post by u-slayer on 2011-10-24
None of your advice worked, so I thought that the linux partition itself might be the problem. I wiped out the linux and moved the windows partition to partition 1. Then I ran the windows dvd and startup repair and now everything works great.

---

### Post by Styx on 2012-02-13
Hello,
i know the tread is old but since i have a very similar problem, i just wanted to post one thing that i found out.
First things first.
I dit install Win7 then i pluged out the cd-drive an plugd in a sec-master SATA-HDD. I installed kubuntu on this one. But to be able to install i had to change the other OS option in the bios. 
Now i am only able to boot win7 if i disable the option and kubuntu if i anable it. I haven know solution ...jet.

sorry for my english

---

