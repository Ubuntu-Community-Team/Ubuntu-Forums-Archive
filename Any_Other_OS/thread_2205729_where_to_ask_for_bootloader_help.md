---
title: "where to ask for bootloader help"
date: 2014-02-15
forum: Any Other OS
---

### Post by shady2 on 2014-02-15
Not sure to go to other distros or what . Briefly my problem is with bootloader. After installing LXLE there is a glitch or two yhat I want to correct. There are two windows OS  on same hard drive. Please instruct which section to place my ? .Thanks !!!

---

### Post by Bashing-om on 2014-02-15
shady2; Hi !

Posting in General Help is a good as any and better than most !
OK, Let's get some info to work with.

What results when you attempt to boot ubuntu ? -> Are you setting the boot priority in bios to boot the hard drive that ubuntu is installed on ?

Can you boot to the grub boot menu ?
Else, going to have to work from the liveDVD.

[INDENT][INDENT]in the process 
[INDENT][INDENT][INDENT]of learning
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by shady2 on 2014-02-16
Will boot Lxle. I get the boot screen. Option is there for winows. Dont know how to set the priority. Previous attempt to fix bootloader added an extra entry. If I select windows it goes real quick booting to c:windws. I see the quick flashby and no chance to select f:windws. Want it to go direct to c: if no selection is made.
Many thanks !!!

---

### Post by oldos2er on 2014-02-16
Moved to Other OS/Distro Support.

---

### Post by shady2 on 2014-02-16
ok . 
Attempt to run (sudo fdisk -1) in terminal emulator , got nothing. Window dissapeared after entering password.

---

### Post by Bashing-om on 2014-02-16
shady2; Well.

Can you boot Lxle to a terminal ?
Post the out put of terminal commands - between code tags - :
```

sudo fdisk -lu ##that is with a lower case "L"##
sudo parted -l
sudo parted /dev/sda unit s print
lsblk -f

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

This shows us what we are working with. We can restore the linux boot loader, grub, however if the Windows' boot loader is corrupted, Will have to have a Window's repair disk to effect the repair.

We will see
[INDENT][INDENT][INDENT]what tale is told
[/INDENT][/INDENT][/INDENT]

---

### Post by shady2 on 2014-02-23
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    29075759    14537848+   7  HPFS/NTFS/exFAT
/dev/sda2        29077502    78155279    24538889    f  W95 Ext'd (LBA)
/dev/sda5        63549423    77898239     7174408+   7  HPFS/NTFS/exFAT
/dev/sda6        77898303    78155279      128488+   7  HPFS/NTFS/exFAT
/dev/sda7        29077504    54245375    12583936   83  Linux
/dev/sda8        54247424    63537151     4644864   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 2000 MB, 2000683008 bytes
255 heads, 63 sectors/track, 243 cylinders, total 3907584 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006fb3b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63     3907583     1953760+   c  W95 FAT32 (LBA)
go@go-PM800-8237:~$ 



this is result of (f disk -l)

I just noticed on the boot screen where you can choose your option, down at the bottom there appears to be options for editing also. What about changing the default from there.
Also have not figured out how to save when using terminal. Does not recognize done or save!!!

---

### Post by shady2 on 2014-02-25
just did commands you posted.                                                                                                        [COLOR=#000000][FONT=Ubuntu Mono]sudo fdisk -lu ##that is with a lower case "L"##[/FONT][/COLOR]sudo parted -l
sudo parted /dev/sda unit s print [COLOR=#000000][FONT=Ubuntu Mono]lsblk -f[/FONT][/COLOR] .

Ok. copy paste is messy. 
Cant get results to paste in. I run the commands and copy turns it blue. then paste into something and error. Under flag is indicated boot is in the windows partition. Is this possible? I thought the Lxle would have taken it over. 
Now I see that the options at boot logon screen are there for emergency only.
 
Someone at the LXLE forum say "boot default can't be edited". Could it be a flaw in that distro ?
I have done a lot of reading on this to figure it out. I am thinking I followed the steps correctly and now GRUB DEFAULT=4 (win xp) and it does not work. Boots to LXLE.

---

### Post by oldfred on 2014-02-25
Each of Bashing-om's commands is a separate terminal command. And anything after a # is a comment so you do not need to copy or write that into terminal.
Or just this as one line in terminal, and each of the other comands
sudo fdisk -l

and we often add comment as the -l may look like number one 1, I -Cap eye, depending on fonts used.

---

### Post by shady2 on 2014-02-25
I am only getting the part about  [QUOTE] ([COLOR=#000000]anything after a # is a comment so you do not need to copy or write that into terminal.) The rest ??
 I am really not understanding why we insist on using commands for everything and why there is not aprogram to simplify this.
 [/COLOR][COLOR=#000000]Someone at the LXLE forum say "boot default can't be edited". Could it be a flaw in that distro ?[/COLOR]
[COLOR=#000000]I have done a lot of reading on this to figure it out. I am thinking I followed the steps correctly and now GRUB DEFAULT=4 (win xp) and it does not work. Boots to LXLE.[/COLOR][COLOR=#000000](Keditor?)[/COLOR]

---

### Post by oldfred on 2014-02-25
I use Ubuntu not so I do not know what screens you may see. 
But with terminal the commands are the same for all flavors of Ubuntu and many others based on Ubuntu. 
Usually copy & paste into a terminal is not an issue as long as you copy & paste one line at a time.

If you have two Windows installs grub will only normally boot one of them. Windows only boots from the one NTFS active partition or as we see it the one with the boot flag. Then Windows adds additional Windows entries to boot.ini for XP or BCD for all versions since XP. Second installs of Windows do not have any boot files.
       
Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by shady2 on 2014-02-26
I read this```
[http://www.multibooters.co.uk/multiboot.htm]("http://www.multibooters.co.uk/multiboot.html")
``` Not a lot or enough there to answer my questions. Mostly deals with windows. How can I migrate boot mgr to its own little partition ? Looking for links . ! thinking that maybe boot mgr is in wrong place for editing from my ubuntu OS.

---

### Post by oldfred on 2014-02-26
That should explain why you only get one Windows in grub as only one Windows partition has boot files. Unless you install boot files into your second install of Windows and it is a primary partition can you boot both copies of Windows from grub.

But if Windows does not load that is a Windows issue. Grub only boots working Windows and you may need Windows repairCd or flash drive to fix Windows.

Post this, but it can only fix minor issues with Windows. Then we may be able to suggest something.
       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by shady2 on 2014-02-26
[CODE][[COLOR=#000000]Post this, but it can only fix minor issues with Windows. Then we may be able to suggest something.[/COLOR]
[COLOR=#000000]Post the link to the Create BootInfo report. Is part of Boot-Repair:[/COLOR]
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
[COLOR=#000000]Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:[/COLOR]
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[COLOR=#000000]You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.[/COLOR]/CODE]

URL is-    [http://paste.Ubuntu.com/7003285/](http://paste.Ubuntu.com/7003285/) 

about ready to abandon win xp. seems like it's broken. Will wait for reply. Hopefully we can fix where it won't mess things up if/when I go to reinstall it.

---

### Post by shady2 on 2014-02-27
So now I see where I have made at least 2 mistakes. On installing Lubuntu, made it logical instead of a primary. Secondly did not make separate partition for boot (also a primary- I think). Found a pretty good video on you tube  that shows how to pretty well.
   Suppose I could offer URL if yu like for anybody reading this looking for same answers. Thoughts ???       previous post includes the link yu requested.

---

### Post by oldfred on 2014-02-27
Your XP looks normal, maybe it only needs chkdsk from your XP disk?

Linux in logical partitions is fine. It is Windows that only boots from primary partitions. And actually only the first install of Windows has to be primary as all additional installs but their boot files into that first partition which Windows calls active partition, but we see boot flag.

Only some old BIOS that have a limit of where on drive boot files can be may need a boot partition or a smaller / (root) fully within the first 137GB of a drive.

Try using Boot-Repair to reinstall grub2 to MBR and use a Windows repair console to run chkdsk on your XP install. 

Not sure how you got an old grub legacy menu.lst into your Linux boot partition? Perhaps that is also part of issue. If so then run the total purge of grub & grub2 and reinstall grub2 from scratch using Boot-Repair. May sure Internet is working as you have to download new copy of grub2.

---

