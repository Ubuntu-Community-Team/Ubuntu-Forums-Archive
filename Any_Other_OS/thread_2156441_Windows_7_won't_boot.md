---
title: "Windows 7 won't boot"
date: 2013-06-21
forum: Any Other OS
---

### Post by sixsamuraisoldier on 2013-06-21
I installed linux mint(15, aka olivia), and i played around in it, had fun. THING IS, some of my programs need windows to run and i had stuff on windows, also, i need windows n there. BUT, WINDOWS IS GONE! I have bootinfoscript 061 and it wont let me run it. I manually added windows 7 to grub, but it wont run, when i press enter, all it does is reload the grub page.

---

### Post by Frogs Hair on 2013-06-21
Moved to Other OS/Distro Support

---

### Post by kiyop on 2013-06-21
Please calm down. :)
You might have installed grub2 code onto the windows system partition. I hope your windows partition is not corrupted.
Can you boot any live linux such as boot-repair ? Please refer to [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
If you can, boot with boot-repair.

If you cannot, at Grub2 menu, press "c" key. Then you will be in Grub2 command mode.
The prompt may be "grub>".
If so, execute
```
ls
```
and find something like (hd0,msdos1) or so. "msdos" may be replaced with "gpt" or so.
And search by
```
ls (hd0,msdos1)
```
It will give you the information on the partition.
If it is ntfs, try
```
ls (hd0,msdos1)/
```
and search the file /bootmgr.
If there is /bootmgr,
```
insmod ntfs
set root=(hd0,msdos1)
insmod ntldr
ntldr /bootmgr
boot
```

Alternatively,
```
insmod ntfs
insmod ntldr
search -f --set=root /bootmgr
ntldr /bootmgr
boot
```

Refer [http://askubuntu.com/questions/135272/how-to-boot-into-windows-7-when-grub-is-installed-in-the-windows-partition](http://askubuntu.com/questions/135272/how-to-boot-into-windows-7-when-grub-is-installed-in-the-windows-partition)

---

### Post by QIII on 2013-06-21
Hello!

We can see pretty quickly whether or not you nuked your Windows partition if you will post the results of
```
sudo blkid
```

and

```
sudo fdisk -l
```

---

### Post by sixsamuraisoldier on 2013-06-21
ok, thx guys ill get back to you, havent tried it so far....

---

### Post by sixsamuraisoldier on 2013-06-21
> **kiyop said:**
> Please calm down. :)
You might have installed grub2 code onto the windows system partition. I hope your windows partition is not corrupted.
Can you boot any live linux such as boot-repair ? Please refer to [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
If you can, boot with boot-repair.

If you cannot, at Grub2 menu, press "c" key. Then you will be in Grub2 command mode.
The prompt may be "grub>".
If so, execute
```
ls
```
and find something like (hd0,msdos1) or so. "msdos" may be replaced with "gpt" or so.
And search by
```
ls (hd0,msdos1)
```
It will give you the information on the partition.
If it is ntfs, try
```
ls (hd0,msdos1)/
```
and search the file /bootmgr.
If there is /bootmgr,
```
insmod ntfs
set root=(hd0,msdos1)
insmod ntldr
ntldr /bootmgr
boot
```

Alternatively,
```
insmod ntfs
insmod ntldr
search -f --set=root /bootmgr
ntldr /bootmgr
boot
```

Refer [http://askubuntu.com/questions/135272/how-to-boot-into-windows-7-when-grub-is-installed-in-the-windows-partition](http://askubuntu.com/questions/135272/how-to-boot-into-windows-7-when-grub-is-installed-in-the-windows-partition)
it says error:no such partition
and
 on the /bootmgr ones, it says ther is no /bootmgr
and, at boot, says load kernel first

---

### Post by sixsamuraisoldier on 2013-06-21
> **QIII said:**
> Hello!

We can see pretty quickly whether or not you nuked your Windows partition if you will post the results of
```
sudo blkid
```

and

```
sudo fdisk -l
```
to teh first one:
[sudo] password for sixsamuraisoldier: 
/dev/sda1: UUID="f69d354e-3c16-43e9-b94e-47f50ab982a4" TYPE="ext3" 
/dev/sda2: UUID="9b50eff3-f889-4faa-9622-bd50ee28c91b" TYPE="ext4" 
/dev/sda3: UUID="5724e06e-711e-4dcb-a12f-76a4a6b77f3b" TYPE="ext2" 
/dev/sda4: LABEL="HP_TOOLS" UUID="DCFE-B773" TYPE="vfat" 
/dev/sr0: LABEL="AOE2" TYPE="iso9660" 

and to the second one:Disk /dev/sda: 500.1 GB, 500107862016 bytes255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xde1c2d32


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      409599      203776   83  Linux
/dev/sda2          409600   917823487   458706944   83  Linux
/dev/sda3   *   917823488   976559816    29368164+  83  Linux
/dev/sda4       976560128   976771119      105496    c  W95 FAT32 (LBA)

---

### Post by sixsamuraisoldier on 2013-06-21
please help :(
im desperate

---

### Post by QIII on 2013-06-21
Hmmm...

You may want to turn off your computer, sit down at another and get back to us.

Did you do good backups before you installed?

---

### Post by sixsamuraisoldier on 2013-06-21
> **QIII said:**
> Hmmm...

You may want to turn off your computer, sit down at another and get back to us.

Did you do good backups before you installed?
i had absolutely NO backups,
doe sthis mean that im screwed,i cant get a windows 7 re-install, but i DO have a repair disk...
PLEASE what can i do to get windows 7 again?

---

### Post by QIII on 2013-06-21
Please get to another computer.  The more you use that one, the less likely it is for you to recover your files -- if that can be done.

Please let me know when you are at another computer.  Please do not use the one you installed Mint on for now!

---

### Post by sixsamuraisoldier on 2013-06-21
ok, im on another computer
PLEASE help :( im distressed and DESPERATE

---

### Post by QIII on 2013-06-21
OK.  First thing is not to panic and not to give up hope.  You are not the first who has run into this and won't be the last.

Let me tell you what you did, if you haven't guessed already:  When you installed Mint, you installed it over the top of your Windows.  Windows is gone.  Depending on whether or not you chose to format the partitions you created when you installed, many of your files *may *be recoverable.  If you formatted, you would probably have to get professional help.  That runs into the thousands of dollars sometimes.  Probably not an option.

The best way to recover Windows files, if they are still recoverable, is with Windows tools.  I cannot vouch for any of these, I don't know if they contain malicious code and I don't know if any of them runs "live" (that is, without booting from the hard drive), but the following website references a number of free data recovery tools:

[http://pcsupport.about.com/od/filerecovery/tp/free-file-recovery-programs.01.htm](http://pcsupport.about.com/od/filerecovery/tp/free-file-recovery-programs.01.htm)

You may not be able to use them.  The most popular data recovery tool for Linux is probably this:

[http://www.cgsecurity.org/wiki/TestDisk_Livecd](http://www.cgsecurity.org/wiki/TestDisk_Livecd)

The beauty of that web site is that there is a forum.  I have used TestDisk/PhotoRec a number of times with great success.  The one thing that is probably gone, in any case, is any music you may have in Apple's music app, whatever that's called.  The database format is proprietary and the files are a hodgepodge of bits and pieces that are impossible to put back together.

Try to recover your important files before you do anything else.

As for whether you can get Windows up and running again, I don't know.  The "recovery" disks most OEMs depend on an image present on the hard driver (usually called D:\Recovery or some such) that your recovery disk invokes to reinstall the system.  So I can't really tell you if you can get going again from that.

Most important thing:  recover your files!

---

### Post by sixsamuraisoldier on 2013-06-21
i need to get to WINDOWS, i dont care about the files...
PLEASE help, i NEED my programs soon im dead :(

---

### Post by QIII on 2013-06-22
If you want to blow away your files and don't care, then try to use your recovery disk.  The programs will be gone.  You'll have to reinstall everything.

---

### Post by kiyop on 2013-06-22
Thanks QIII for explaining that the OP made the mint installer overwrite the Windows system partition.
:(

I hope that nobody do such a bad and wrong thing in future.

---

### Post by sixsamuraisoldier on 2013-06-22
> **QIII said:**
> If you want to blow away your files and don't care, then try to use your recovery disk.  The programs will be gone.  You'll have to reinstall everything.
i said i have a REPAIR disk, NOT windows 7, i cant reinstallit :( is there any way to recover windows?

---

### Post by Sef on 2013-06-22
> [COLOR=#000000]is there any way to recover windows?[/COLOR]

Read about test disk in post 13.

---

### Post by kiyop on 2013-06-22
> **sixsamuraisoldier said:**
> i said i have a REPAIR disk, NOT windows 7, i cant reinstallit :( is there any way to recover windows?
What is the REPAIR disk? Is there any manual about the REPAIR disk? If there is, have you read the manual?
If the REPAIR disk can recover Windows by using itself (and only /dev/sda4), it may work, although I am not sure (because I do not have its manual ;))

I think you had better ask at Windows 7 forums (such as [http://answers.microsoft.com/en-us/Search/Search?SearchTerm=windows+7+repair+disk&CurrentScope.ForumName=Windows&CurrentScope.Filter=&askingquestion=False](http://answers.microsoft.com/en-us/Search/Search?SearchTerm=windows+7+repair+disk&CurrentScope.ForumName=Windows&CurrentScope.Filter=&askingquestion=False) ) rather than here.

---

### Post by oldfred on 2013-06-22
Some manufacturers will let you order a replacement Windows 7 install/recovery disk. Some charge a lot, others just shipping, so you may want to contact your vendor and see what they offer.

Users are supposed to make their own recovery DVD set as hard drive will eventually fail and you will have to reinstall. But backup may be better.

 The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by sixsamuraisoldier on 2013-06-22
> **Sef said:**
> Read about test disk in post 13.

i meant recover windows as in start to boot it up and use the OS again, NOT te files, the files i dont care about, i just want the OS to boot up. Is there no way to do this?

---

### Post by ronniew on 2013-06-22
When Windows doesn't boot, you've just discovered the best piece of antispyware available. :)

---

### Post by oldfred on 2013-06-22
Because operating systems need all their files and if any one file is overwritten it will not work. Since you totally overwrote Windows there is no way to recover it fully and make it bootable. You will have to reinstall.

If you just want to recover data, you can recover a lot of it, just not all, since Linux is a lot smaller and generally has files everywhere on drive. Windows generally has files at beginning of drive so only some data is actually written over. But the chances of recovering a bootable Windows are just about impossible.

---

### Post by sixsamuraisoldier on 2013-06-22
so im screwed?

---

### Post by oldfred on 2013-06-22
You should be able to get a copy from your system vendor at perhaps minimal cost.

Does your system have the serial number on the bottom of the machine still?

---

### Post by dwaite on 2013-06-22
If you have a copy of your Windows key somewhere (it might be printed on one of those repair disks) you could download a Windows .iso from the Microsoft website, then create a new install disc or USB (UNetBootin on Mint will do this) then do a Windows clean install. The kicker is you have to have your own key, because you won't get one off the website.

---

### Post by Copper Bezel on 2013-06-23
Yeah, I was going to say, this is normally fairly simple - if your machine shipped with Windows, then there's a Windows product key on a sticker somewhere on the case. That's whether it's a laptop or a desktop machine and so on. You can download the Windows ISO, so long as you make sure that you get the same edition you had to start with - see here: [http://www.pcworld.com/article/248995/how_to_install_windows_7_without_the_disc.html](http://www.pcworld.com/article/248995/how_to_install_windows_7_without_the_disc.html) . Once you get Windows installed, you might have some driver issues to deal with, but searching by your machine's model number usually brings up all the drivers you need.

This will, of course, nuke your Mint install. Next time, be sure to select "Install alongside Windows 7." = /

---

