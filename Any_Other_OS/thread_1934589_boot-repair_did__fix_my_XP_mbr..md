---
title: "boot-repair did  fix my XP mbr."
date: 2012-03-02
forum: Any Other OS
---

### Post by davedaveh on 2012-03-02
boot-repair did not fix my XP mbr.
Here is the report:

[http://paste.ubuntu.com/865429/](http://paste.ubuntu.com/865429/)

Would anyone like to check it out and suggest a fix?
or do I throw in the towel?

Thanks

---

### Post by mastablasta on 2012-03-02
use (boot form) windows XP (install) cd to repair boot. you need to use repair console and then type fixmbr to repair the windows XP boot.

---

### Post by ajgreeny on 2012-03-02
If you have no XP install disk, you can install a Windows equivalent MBR to your sda drive by doing the following from a Live Ubuntu CD.
```
sudo apt-get install lilo
```
Ignore the warning then 
```
sudo lilo -M  /dev/sda mbr
```
Then you should be able to boot directly into Windows again if all goes well.

---

### Post by davedaveh on 2012-03-02
My OEM Power Spec Recovery CD has not worked.

I tried lilo, but got request to:

 run liloconfig(8)
and execute sbin/lilo

I don't know how.

Also, if I want to make another boot disk, I don't know how exactly to create boot disk image -- do I emulate floppy? that kind of thing.

Thank you for help.

I did manage to get lilo to say that mbr was updated, but still not booting.

fdisk -l still has no output

---

### Post by ajgreeny on 2012-03-05
Sorry but this is all outside my experience and I have no other ideas to help you, I'm afraid.

I do not have windows any more, so was passing this info on having read about it in the past.

---

### Post by oldfred on 2012-03-05
Moved to other OS as it is just XP.

Your boot script showed syslinux as the boot loader which should have worked. Then ajgreeny's suggestion of lilo should have worked also. With lilo you just want the MBR not the full lilo boot loader so the warning is normal. So do you get error messages from Windows?

All the Windows boot loaders do is check for boot flag and jump to that partition to continue to boot. Syslinux & lilo's boot loaders will do the same.

Are you booting from sda? You have no boot flag on sdb and the grub install in sdb does not have any system to boot from. Grub does not need boot flag, but it has to have a partition with the rest of the grub files to continue to boot. Did you have another drive installed when you installed grub to sdb?

---

### Post by davedaveh on 2012-03-05
Thank you all for your help.  It will take me a while to absorb this info - as of now, I cannot answer these last questions.

I do have good news though.  When I attempted the Ubuntu install, I was expecting to see my only option to be 'erase everything and start anew'.  I did get that once before.  This time, it gave option to install alongside XP. I did.  Linux is working fine and I am very happy to be able to do just about everything I used to do with Windows. {and more)

However, XP will not boot from Grub, but I am happy to have not deleted that partition because I retain all my old files.

I think I screwed this up because I was using other versions of Windows CDs to get to a prompt, but never could.
I think it is amazing that Linux can be used to fix WIndows MBR.  I did it once, but somehow screwed it up again.  But that's OK it was fun and educational. And ended up with a free and wonderful OS with a great support community.
For all I know I may get Windows to boot again on this drive.  Not that I need it, but still want to try. Steep learning curve for me.

Oldfred -- yes there was another (slave)drive in there which I since removed.  Was that sdb - that is, not another partition but a drive?  You're right - I shouldn't bother with XP anymore.  I just like to make use of what I have rather than ditch it and buy more stuff.  My computers are old!

---

### Post by wolfen69 on 2012-03-05
You need to choose recovery mode from the xp install disc and run **fixmbr**

---

### Post by davedaveh on 2012-03-06
Thank you for the reply - my troubles started because I only had a PowerSpec recovery disk - not XP startup.  The disk did not recognize my system. Alternative methods did not work either like xpquick and mbrfix.exe because they would not even boot, eventho I created an .iso CD.  Don't know why they did not boot...although the boot-repair CD booted, it could not fix my system, although maybe saved the partition. That signaled me that it was unfixable. (Do we believe that?)
My BIOS posted 'MBR' when trying to boot from HDD.
Problem is not solved, but I am running Linux now so it does not matter much.

---

### Post by oldfred on 2012-03-06
A fixMBR command just puts the Windows boot loader back into the MBR. That would be if you wanted to know you could directly boot Windows. 

You then would have to reinstall grub2's boot loader to boot Ubuntu also.

You may need fixBoot from a Windows XP disk which repairs the boot sector or Partition boot sector (PBR) which has more Windows boot code. Or you may need to run chkdsk which is one thing you cannot do from Ubuntu. 

NTFS partitions keep a backup of the PBR and testdisk can restore the backup if it is good. Testdisk is in the Ubuntu repository so you can easily download it.

repairs including testdisk info & link to testdisk
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
As described, it has an option to "Recover NTFS boot sector from its backup"
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

I have also used a Windows 7 repairCD to run chkdsk on my XP install and restore a PBR. If you have or know someone with Windows 7 you can make a repairCD.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by davedaveh on 2012-03-06
Thanks oldfred.
So if I want to pursue the problem of accessing XP on this drive, I would try one of those methods, then that would destroy grub, at which point I would run the ubuntu CD again and do the lilo mbr command to restore that?

I did not come across test disk in my research of this problem.  Checking it out now...

From what I have been reading, I see that it is possible to fix this, but I think it is way beyond me at present.  This info may be helpful to others though.

Thanks for delving deeper! I think it's amazing that the test disk page reminds one to be patient and proceed slowly and take time to absorb all this info.  Ha!  Right on.  (What the H is PhotoRec!!)  
Not something to do after having a few beers.

Thnanks for pointing me to this. It looks fascinating.  I'm looking into it.

---

### Post by critin on 2012-03-06
> You're right - I shouldn't bother with XP anymore.**  I just like to  make use of what I have rather than ditch it and buy more stuff.  My  computers are old**!

That's my philosophy too!  

Keep the XP, everytime I get frustrated or stumped with linux, all I have to do is turn on XP and I remember what I enjoy so much about ubuntu.   XP is boring...lol

---

### Post by davedaveh on 2012-03-07
Oldfred, or any other contributor -- 
Maybe you can decipher this output of fdisk, now that I learned I had to be root:
sda1 looks like it has a near duplicate partition named sdc1, but since it has no linux on it, should I assume it is a bad partition and delete it? 
If so, what is the command? (My guess:  sudo fdisk /dev/sdc1 -d)

(The sdb is a smaller slaved drive.)
As a reminder, I have Ubuntu working fine, but have lost the ability to boot XP eventho it is still in the boot loader menu.
Let me know if I am understanding this correctly please.



dave@dave-desktop:~$ sudo fdisk -l
[sudo] password for dave: 

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000408f1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   195350431    97675184+   7  HPFS/NTFS/exFAT
/dev/sda2       195350526   390721535    97685505    5  Extended
/dev/sda5       195350528   389150719    96900096   83  Linux
/dev/sda6       389152768   390721535      784384   82  Linux swap / Solaris

Disk /dev/sdb: 10.2 GB, 10248118272 bytes
255 heads, 63 sectors/track, 1245 cylinders, total 20015856 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000be0f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    20000924    10000431    c  W95 FAT32 (LBA)

Disk /dev/sdc: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x59818e20

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   320159384   160079661    7  HPFS/NTFS/exFAT

To clarify, there are only two hard drives in my system.

Thanks

---

### Post by oldfred on 2012-03-08
I would not delete partition. It looks like sdc is your other hard drive. I would review what data is in it.

It looks like sdb may be a  flash drive but 10GB is unusual or do you have a card reader with a card in it. Usually flash drives are mounted after hard drives so I am not sure what sdb is either. Some new hard drives have built in small SSD's to speed things up, also. Not sure how they are shown.

---

### Post by davedaveh on 2012-03-08
Oldfre,

This falls under the category of beating a dead horse....

I removed my 10 GB HDD and here is the fdisk output.  There is only one disk in there.  I'm pretty sure that the cause of my problem not bootiing XP is because of this extra (bad?) partition table.

dave@dave-desktop:~$ sudo fdisk -l
[sudo] password for dave: 

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000408f1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   195350431    97675184+   7  HPFS/NTFS/exFAT
/dev/sda2       195350526   390721535    97685505    5  Extended
/dev/sda5       195350528   389150719    96900096   83  Linux
/dev/sda6       389152768   390721535      784384   82  Linux swap / Solaris

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x59818e20

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   320159384   160079661    7  HPFS/NTFS/exFAT
dave@dave-desktop:~$ 

Is that the sort of fix that Test Drive would do if I actually ran it?  
Need more reading or advice first.

BTW, this drive is an old PATA drive - no bells or whistles.

Thanks

---

### Post by oldfred on 2012-03-08
If these are older IDE/PATA drives in an older system, BIOS may only let you boot primary master. Second drive is slave, but you have to have jumpers set correctly for both drives to work.

With older IDE drives you can often only boot from the primary master so grub has to be installed to that drive. But the Windows partition has to have the NTFS boot signature and you have to have all the XP boot files in the NTFS partition.

From Boot-Repair run the boot info script and post the link to the latest run of the script that Boot_Repair creates.

---

### Post by LostFarmer on 2012-03-08
> I think I screwed this up because I was using other versions of Windows CDs to get to a prompt, but never could. What version of Windows and what commands did you run ?

please run and post 'Boot Info Script 0.60' again.

The hdd you have in now, what brand/model/size ?   I can not understand if you only have 1 hdd, why fdisk says you have 2.

Get into the bios/cmos , what does it say about hdds ?

When you select XP from grub, just what happens ?

---

### Post by davedaveh on 2012-03-08
OK you guys - thanks for keeping this going.
I really do have only one HDD in there, after removing the 10GB slave.  The fact that there is an sdb there (in fdisk) is what makes me think that this is what is wrong with my dual boot scenario.  In trying to get to a prompt, I used a Win98 and a WinNT disk, and they might have put that 'false' partion in (or something). I do think it is wrong - that's why I think I should delete it.

I was using XP alonside Linux, and if I select XP in boot loader menu now, I only get blank screen with one blinking cursor in it.
The reason I lost XP was that I deleted linux, got the mbr back, then messed with the Linux partitions again, because they were too small when I reinstalled.
The HD in there is a 200GB Seagate PATA, I think, but it is screwed in and can't look now. But it is 200GB.  It has XP and Linux - 50%-50%.
I will run boot-repair again later to show you the output.
I have already tried the lilo and ms-sys mbr commands that I found in earlier posts by other Ubuntu gurus. lilo said it fixed mbr or updated it, but dual boot still failed.
People try to tell me to use the XP start up CD, but the only one I have is a PowerSpec Recovery CD that does not recognize my system since I have messed it up.  Still fun!  Thanks a lot for the help.

---

### Post by LostFarmer on 2012-03-08
If your computer will boot to a USB stick, you can try this site:[http://tuts4tech.net/2009/07/14/creating-a-usb-bootable-xp-recovery-console/](http://tuts4tech.net/2009/07/14/creating-a-usb-bootable-xp-recovery-console/)
The site does seem to be down right now.

it will not work on all computers, like mine but others it does work on.  You will need a XP or up WIN OS, I think but not sure.  Not sure what help it would be right now.


> that's why I think I should delete it  Fdisk says it is a HDD, you can not delete it.  I do not understand it .

I do need you to check the BIOS and see if it list 2 hdds. I have seen XP list a phantom partition but never linux fdisk list a phantom HDD.

---

### Post by davedaveh on 2012-03-09
BIOS says one HDD. (WDC WD2000BB-00GUA0)
I have DVD drive as secondary slave

I think what may have happenned is when I was trying to increase the size of the linux partition during an install, there was an error and the process was not completed.  This way, it was not Windows that tried to make the change to the mbr, but fdisk itself under linux. That could explain how fdisk is seeoing the wrong thing. Could that have happenned?

Here is the boot-repair output:

[http://paste.ubuntu.com/876181/](http://paste.ubuntu.com/876181/)

I don't know how, but this time the results look good (except for an error on swap)
However, I just tried booting XP and it is not working.

Apparently, running things more than once comes up with different results...
Fdisk is now showing the one drive.
Now I look crazy!!
BTW, what is wrong with swap partition?

Here is a new issue:
Running sudo lilo -M /dev/sda/ mbr said mbr was updated but when I rebooted to check, nothing is booting now.  Bad news.
Back to the Ubuntu Live CD! or should I run boot-repair again from disk?

OK I am adding this info after running boot-repair again.
result is [http://paste.ubuntu.com/876265/](http://paste.ubuntu.com/876265/)

What does "/Noxecute=OptIn" mean at the very end?

It said it fixed it, and it did fix my linux boot, but XP is still not booting from Grub.
There are some suggestions farther down in the report which I don't understand.

---

### Post by oldfred on 2012-03-09
Boot script looks normal to me. I so not see an issue with swap. 

Boot-Repair reports a lot of what it does and sees. I do not know those details. But I did note that your Windows partition is 91% full. Windows slows down at 20% free and just about stops at 10%, you should be waiting longer and perhaps houseclean some Windows info out of the Windows NTFS partition.

Have you run chkdsk on your NTFS parition. It again may be very slow.

---

### Post by davedaveh on 2012-03-09
Well, I finally am trying testdisk.  It is reporting so far that:

"Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)

It is continuing to analyze cylinders....

If this means some parts of the HDD ae bad, then I assume software cannot fix it.

Do you have a suggestion for what I should have testdisk do when it is done checking these cylinders?  Should I have it write an mbr? or is that dangerous.

---

### Post by oldfred on 2012-03-09
Boot script showed 255 heads, so something internal must be different?

Your pastebin has the info you need to rebuild if necessary, but I would backup partition table as then you can easily restore.

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

---

### Post by davedaveh on 2012-03-09
Thank you for that info.  But testdisk just finished analyzing and it said:
"Hard disk seems too small!  Check HDD size, jumpers, bios ETC."

tHEN IT SAID
The following partitions can't be recovered:
HPFS - NTFS 1634 44 28514 43 41 195350369

I guess that says it.

If I am to continue to pursue this problem,I'm unclear on how to create the partition backup to an external device and then load it from a live cd testdrive.

Test drive also said NTSF boot sectors did not match so I took a risk and had it rebuild (from backup?) and when done, XP almost booted from Grub (saw XP Splash screen momentarily), then went into Linux instead!
I still have access to Windows partition from Linux - are there any boot files I could change for Windows to work?
I guess there are still options.  Maybe I am getting closer.

---

### Post by oldfred on 2012-03-09
Testdisk shows all versions of old partitions, so that some are not recoverable is normal as they may overlap with other new valid partitions.

You may need to run chkdsk but have to do that from a Windows CD.

Script did not show boot files are they there, if script was not able to correctly mount the NTFS is just may not have seen them. You should have these files:

Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM

---

### Post by davedaveh on 2012-03-09
Thanks oldfred,

Testdisk was, needless to say, a little difficult to navigate the first time.
Where are you suggesting that I access these three files?
boot.ini I have seen, and it looks like it always does...
The others are binaries? and don't know how to see them or change them.

Do I do this from testdisk, or maybe RescueDisk, or from the Ubuntu platform, or live CD?

Again,  life would be simpler if I had the Windows CD.  I will try my PowerSpec recovery disk again, to see if the changes which were just made will have enabled it.

Just tried recovery disk - NOT.

I do have folders in my Windows drive called "My Old Disk Structure" and "System Recovery".  How can I use them to possibly replace the bad files?  
thanks.

---

### Post by erbeesr on 2012-03-10
If you have a Windows 98 bootup disc, at the a: prompt type fdisk/mbr (enter).  That will restore the boot sector.  If your XP OS is still intact the machine will boot up in XP like you had never installed Ubuntu.

---

### Post by Dlambert on 2012-03-10
EasyBCM works well too!

---

### Post by oldfred on 2012-03-10
Look here (my old XP in in /mnt/cdrive in Ubuntu):

/mnt/cdrive/WINDOWS/ServicePackFiles

or here:

meierfra. - How to fix XP when the boot files are missing + download
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)

But just replacing boot files assumes rest of system is ok.

---

### Post by LostFarmer on 2012-03-10
> XP almost booted from Grub (saw XP Splash screen momentarily), then went into Linux That would indicate your boot files are likely good. For some reason XP is doing a soft reboot.  It could be due to not enough free space.  Try-- as soon as you select XP from grub, start pressing the F8 key- if you get XP's boot menu try Safemode.

You may have to try and remove some of the personal file in C:\Documents and Settings\username\My Documents. move they to the linux  /home/user folder.  Delete file in C:\WINDOWS\Temp

If you get it to boot into safe mode- "start-all programs-Accessories-System tools-Disk cleanup" remove all

---

### Post by davedaveh on 2012-03-10
OK you guys are great!
That looks like a lot of fun, trying to replace those boot files.  Thanks for all the good advice.
I'll keep you posted in a couple of days.
Thanks alot.  It's nice that you Linux guys have such compassion for old beat up Windows OS.  :D
Thanks

---

### Post by davedaveh on 2012-03-10
I've had a chance to try your ideas:

WIn98 fdisk /mbr did not work.  Nor does safemode.

After testdisk boot sector 'fix', I almost lost the ability of my Linux to see the windows partition.  Got that back, and moved some files from it over to Linux partition, but now my Windows partition is read only, and could not delete the files I copied.  

I was also confused what to do when trying the boot.ini, ntldr, ntdetect.com replacement....my boot.ini was the same.  Should I replace those three files from the archive that meierfra provided as a fix for restoring a windows partition? If my windows partition is read only, I can't do that. (I made the /Win mount point and tried chmod 0777 -- didn't work). Is my problem mbr, windows boot files, or bad sectors (physical)?  or am I mental?)  :P

---

### Post by oldfred on 2012-03-10
I do not think the auto mount is read/write anymore and I think it used to be. 

You have to be careful but you can to this. Do not move other files around as this allows total read/write.

gksudo nautilus

I normally suggest read only for a Windows partition to prevent accidental issues.
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

### Post by davedaveh on 2012-03-10
Thank you,

Oldfred, when I typed that, strange things happened.  Terminal showed hash table warnings and that table still has one element at quit time.  'Eel-warning'
My GUI home directory only showed my desktop folder until this command was finished.
Then when I tried to swap out my win boot files, they could not be deleted or moved.
No damage done at least.
I'll send screen output later if it will help.  I'm on a different computer.
I'm not giving up yet but I am close.
You guys know a lot!

---

### Post by oldfred on 2012-03-11
I get a few minor errors in terminal but it seems to work for me. I think someone posted before about the errors and they are not as critical as they sound.

```
(nautilus:3496): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
eedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '3496'

```I have also seen this and always thought it was the same as gksudo is sim-linked to gksu. But that must not be true?
Edit:
Just checked and gksudo is just a link to gksu. Not sure why a difference then.

gksu nautilus

But that gives no error message.

---

### Post by davedaveh on 2012-03-11
I tried gksu nautilus and terminal hung -- reboot, back to normal.
When this command was invoked, my home folder only showed one folder (desktop)...
I discovered that the ntldr file on my windows drive is 250 KB, the one provided by meirafra is 236 KB.  Need access to windows drive to try the file swap.

Is that a good sign that my ntldr is bad? (ntdetects are the same size BTW.)

Now I just did a little research on nautilus, and I don't think my file browser in 11.10 Ubuntu looks like the Nautilus I saw when researching....my file browswer has no menus. (I'm using Ubuntu not Gnome.)

What up?

---

### Post by oldfred on 2012-03-11
My ntldr is 244.2KB from Aug 19, 2008. I recently updated the old XP so it should be current?

The new Unity is somewhat different. But Nautilus is basically the same. Some things have been moved around with different versions. Even the change to 11.10 went from gnome2 to gnome3 but kept Unity. I still am on 10.10 as my working system.

---

### Post by davedaveh on 2012-03-12
I need to make the windows partition writable.
I understand that I need to unmount it and remount it rw.
Now, I can't do either - "not in fstab" or "busy" or "already mounted"
When I umount /dev/sda, says "/dev/sda is not mounted (according to mtab)"

Puzzled

Previously I took the drive out and connected it via usb and was able to swap out the ntldr and ntdetect.com

That did not let XP boot, and also made my drive unreadable to the usb conection.
If I can fix that again (go back to orig boot files), I want to reconnect via usb and run chkdsk on that drive and maybe that would fix it.  Don't worry!!  Almost giving up!

Do I need to add /Win or /dev/sda1 to fstab?   How?

---

### Post by oldfred on 2012-03-12
If you do not have it in fstab:

sudo mkdir /media/windows
sudo mount ntfs-3g -o rw /dev/<device-name> /media/windows
if you get a message regarding Windows not being shutdown properly, then run the following command to force the mount
But better to run chkdsk from a Windows repair CD first, only use this if you have to copy data.
sudo mount ntfs-3g -o force,rw /dev/<device-name> /media/windows

If you have it in fstab:
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

Examples:
# Make permanent mount point (unmount if already mounted):
sudo mkdir /media/Data2
# Find your UUID:
sudo blkid
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
# Anytime you edit fstab always do this before rebooting. If no errors it just remounts everything, but if errors you have to fix before rebooting or you may not be able to:
sudo mount -a

UUID=01CC498FE4856480 /media/Data2 ntfs defaults,uid=1000,nls=utf8,umask=000 0 0
# or
Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
UUID=66E4DC83E4DC56C1 /media/Data2 ntfs defaults,uid=1000,windows_names,umask=000 0 0

---

### Post by davedaveh on 2012-03-12
Sorry,

I'm having difficulties:

Here is fstab:  (not there)

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=6cc209b6-f775-4d67-9c4c-28c578b29f39 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=d8846365-e289-45ca-8edb-44ca01453325 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


Here is mtab:  (I manually changed r to rw in the last line):

/dev/sda5 / ext4 rw,errors=remount-ro,commit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/dave/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=dave 0 0
/dev/sda1 /media/windows ntfs rw 0 0

And here are some mount trials:

ave@dave-desktop:/$ sudo mount -t ntfs -o rw /dev/sda1 /media/windows
mount: /dev/sda1 already mounted or /media/windows busy
mount: according to mtab, /dev/sda1 is already mounted on /media/windows

dave@dave-desktop:/$ sudo umount /media/windows
dave@dave-desktop:/$ sudo mount -t ntfs -o rw /dev/sda1 /media/windows
mount: warning: /media/windows seems to be mounted read-only.

dave@dave-desktop:/$ sudo mount -t ntfs -o force,rw /dev/sda1 /media/windows
mount: /dev/sda1 already mounted or /media/windows busy
mount: according to mtab, /dev/sda1 is already mounted on /media/windows
dave@dave-desktop:/$ sudo gedit /etc/mtab
sudo: gedot: command not found
dave@dave-desktop:/$ sudo gedit /etc/mtab
dave@dave-desktop:/$ sudo mount -t ntfs -o rw /dev/sda1 /media/windows
mount: /dev/sda1 already mounted or /media/windows busy
mount: according to mtab, /dev/sda1 is already mounted on /media/windows

BTW, it didn't like the "ntfs-3g"
and needed "-t"

At any rate, I can open /media/windows with gksudo nautilus, but have no option to delete/replace files..
I made some progress though!

---

### Post by oldfred on 2012-03-12
Your mount already showed it, so you could not mount again.

> /dev/sda1 /media/windows ntfs rw 0 0

Some have had issues with gksudo nautilus but gksu nautilus works. Not sure why but gksudo is just a link to gksu.

---

### Post by davedaveh on 2012-03-13
Still trying to mount windows partition rw:

I got some code from killerbees -- he suggested umask


dave@dave-desktop:~$ sudo umount /media/windows
dave@dave-desktop:~$ sudo mount -t ntfs -o umask=022,gid=046,uid=0 /dev/sda1 /media/windows
mount: warning: /media/windows seems to be mounted read-only.
dave@dave-desktop:~$ 

I have been going around around with this.  Recently installed samba because something asked for it.  I do not have ntsf 3-g installed, so could not use your earlier code suggestion.

I added a line to fstab because there was no mention of /dev/sda1 on it,
but it didn't like what I wrote:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=6cc209b6-f775-4d67-9c4c-28c578b29f39 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=d8846365-e289-45ca-8edb-44ca01453325 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda1	/media/windows  ntsf    rw,user,noauto,noexec 

Must I go the UUID route?  I will if necessary (although I might not get it right) -- there seem to be a lot of ways to address this, but I must be doing them incorrectly.

---

### Post by YannBuntu on 2012-03-14
Hello
Suggestion: from Disk-Manager (11.04 and 11.10 version is [here]("https://launchpad.net/disk-manager/1.1/1.1.1/+download/disk-manager_1.1.1-1_all.deb")), select your Windows partition, click the "Modify" button, and change the driver from "default" to "read-write".

For information, the title of this discussion is incorrect: Boot-Repair has fixed your MBR, but your problem is located after the MBR (in XP files).

---

### Post by oldfred on 2012-03-14
uid 0 is root, so you want root to have the ownership of your Windows files. Normally the user is uid=1000.

# Make permanent mount point (unmount if already mounted):
sudo mkdir /media/Data2
# Find your UUID:
sudo blkid
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
# Anytime you edit fstab always do this before rebooting. If no errors it just remounts everything, but if errors you have to fix before rebooting or you may not be able to:
sudo mount -a

Other examples, UUID is preferred only because it changes less. Some BIOS do not always mount drives in same order, or promote a flash drive to sda or other issues that changes a mount by device like /dev/sda1.

UUID=01CC498FE4856480 /media/Data2 ntfs defaults,uid=1000,nls=utf8,umask=000 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
UUID=66E4DC83E4DC56C1 /media/Data ntfs defaults,uid=1000,windows_names,umask=000 0 0

---

### Post by davedaveh on 2012-03-14
Thank you for your help in all this.

YannBuntu, thank you for suggesting that option, but I do not know how to install the file ending in .deb
Correction:  somehow it is already installed.  I did not see "modify" but clicked on "Edit Partition".  There were no rw options there.  Should I unmount first?

oldfred, here are some printouts of the results of our efforts:
Can you tell where my errors are?  

dave@dave-desktop:~$ sudo umount /dev/sda1
dave@dave-desktop:~$ sudo mount /dev/sda1 /media/Data2
mount: warning: /media/Data2 seems to be mounted read-only.
dave@dave-desktop:~$ sudo mount -o -rw /dev/sda1 /media/Data2
mount: /dev/sda1 already mounted or /media/Data2 busy
mount: according to mtab, /dev/sda1 is already mounted on /media/Data2


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=6cc209b6-f775-4d67-9c4c-28c578b29f39 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=d8846365-e289-45ca-8edb-44ca01453325 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
UUID=7CE01102E010C474 /media/Data2 ntfs defaults,uid=1000,ntfs=utf8,umask=000 0 0

is the umask incorrect?

---

### Post by oldfred on 2012-03-15
You only unmounted it once but tried to mount twice. You needed to unmount for before running the second mount. but if adding to fstab you do not manually mount or else you will have another conflict of a mount.

make sure you have no manual mounts and always run this after editing fstab. if no errors then it is reloaded & you new entry is used to mount the partition

sudo mount -a

Your umask=000 gives full permissions to everyone. Some may say a little too permissive.

---

### Post by YannBuntu on 2012-03-15
> **davedaveh said:**
> YannBuntu, thank you for suggesting that option, but I do not know how to install the file ending in .deb
Correction:  somehow it is already installed.  I did not see "modify" but clicked on "Edit Partition".  There were no rw options there.  Should I unmount first?

No, it's not installed by default, i think you mistake "Disk-Utility (=palimpset , which is installed by default) and Disk-Manager.
For Disk-Manager, just save the DEB on your Desktop, double-click on it, Ubuntu-Software-Center will propose to install it.

Here is what Disk-Manager looks like:
[[img]http://pix.toile-libre.org/upload/img/1331825186.png[/img]](http://pix.toile-libre.org/?img=1331825186.png)

---

### Post by davedaveh on 2012-03-15
Whew !

My odd-ysey continues...

Thank you for pointing out my mistakes.

YannBuntu, You are patient in directing me to the correct procedure.    This was after having a failed boot and booting into Recovery Mode.  There, I was lucky enough to take oldfred's suggestion of copying my backup fstab from root prompt -- otherwise all would be lost.

I just got fuse to mount my ntsf read-write!  And I have replaced my trial ntldr and ntdetect.com files with my originals, which was the purpose of this endeavor.  Still not done -- I plan to connect this drive via USB to another XP computer and see if it will run chdsk on this drive and hopefully fix it.  BTW, Disk Utility notified me that I have 22 bad sectors on this drive.  Wow.  This may have been the problem all along.  

Can't thank you enough for being so patient.  Hope my trials help someone else in the future.
I'll let you know if my usb external drive chdsk fix worked. You're thinking: doubtful!)  :-)

A half an hour later and i discover that windows usb external HD could not open the drive -- corrupt in some way. I was hoping that replacing my original XP boot files would revitalize it. I may as well give up on this now.  At least I eliminated other issues as being the reason -- but you can't do much about bad sectors on the drive. One last thing: Can windows tell if the drive had been mounted in Linux?  That is, should I unmount it before trying this again?

---

### Post by davedaveh on 2012-03-16
I marked the thread as 'solved' because I have learned so much about what is possible with Ubuntu and the forum.  I believe my hard drive is damaged, and have not restored windows as I had hoped, but I don't think it is reparable.  (Although I will keep trying anyway.)

Thanks everybody!

tools learned:

lilo mbr command from live cd
editing /etc/fstab and making .backup
and UUID options
testdisk
boot-repair  (Title should be changed to 'DID fix my XP mbr')
disk-manager

---

### Post by oldfred on 2012-03-16
Glad you resolved a lot of issues. If you want I can change title for posterity.

---

### Post by davedaveh on 2012-03-16
OK,good idea -- change the title.

---

