---
title: "start Windows XP with Ubuntu start disk"
date: 2005-11-18
forum: Absolute Beginner Talk
---

### Post by Wolf1994 on 2005-11-18
Hello.

My PC have two hard disks C: 4Gb - WinME and D: 40 Gb - WinXP. I want to clean disk C: and set on one Ubuntu. But there's one problem. WindowsXP ( D: ) starts from C:. How I can install Linux-Ubuntu and keep WindowsXP working? And additional problem - is disk with Ubuntu file system percepted by Windows as ordinar Windows disk? Will Ubuntu keep letter C: to left Windows - D: - becouse many programs installed in D:\... path...

---

### Post by Mustard on 2005-11-18
It's a bit hard to tell from what you have written exactly how you would go about it.  It's quite a strange setup.  You say XP boots from C: but is installed on D: ?

---

### Post by SSTwinrova on 2005-11-18
Ok, let's work on rephrasing what you said. You have 2 hard drives in your computer: a 4 GB which Windows ME is installed on and recognized as drive letter C: and a 40 GB which Windows XP is installed on and recognized as drive letter D:. By "starts from C:" I'm assuming you mean that the 4 GB drive is set as the master on the IDE chain and contains the MBR.

Assuming the above is correct, now let's start answering your questions. If you only let the installer reformat the 4 GB drive, XP should be left untouched. Ubuntu will install Grub into the MBR which should hopefully also detect your installation of XP and add it to the boot menu. (If not, that's just a minor tweak to get it working). If you stick with the default filesystem Ubuntu uses, Windows XP will (by default) **not** be able to access that drive. The two most often recommended solutions would be to create a FAT(32) partition which both OSes can read/write to and use that to share data, or I believe there is a program/plugin for XP which can add the ability to access the ext3/4 filesystems.

Now, onto the whole drive letter issue. I honestly don't know what Windows will do with the drive letters, but regardless you should be able to force Windows to always mount it's filesystem as drive letter D:. Go to Control Panel > Administrative Tools > Computer Management > Storage > Dick Management (there's a quicker way but I can never remember it) and then right-click on a partition and choose "Change Drive Letter and Paths..." if Windows sets it to something else.

---

### Post by Wolf1994 on 2005-11-19
Thanks for your answer.

But I still have questions.
> Ubuntu will install Grub into the MBR which should hopefully also detect your installation of XP and add it to the boot menu. (If not, that's just a minor tweak to get it working).
Can newbie perform this minor tweak with no help of masters - because if I done these actions my WindowsXP will be unaccessable and I will be left without Internet asccess for help as well?

> The two most often recommended solutions would be to create a FAT(32) partition which both OSes can read/write to and use that to share data
I prefer first solution. And again want to ask - can newbie create FAT(32) partition in Ubuntu without help?

> Now, onto the whole drive letter issue. I honestly don't know what Windows will do with the drive letters, but regardless you should be able to force Windows to always mount it's filesystem as drive letter D:. Go to Control Panel > Administrative Tools > Computer Management > Storage > Dick Management (there's a quicker way but I can never remember it) and then right-click on a partition and choose "Change Drive Letter and Paths..." if Windows sets it to something else.
You mean that Windows can be loaded with wrong drive letter and then I can fix it?
By the way, I tried to perform this operation now and was unsuccessfull - Windows refused to change letters of both C: and D: drives. What a problem in is?

---

### Post by SSTwinrova on 2005-11-19
With instructions and the specific lines to add, you shouldn't have an issue doing it at all. I, unfortunately, have no experience with tweaking Grub though, so hopefully someone else will be able to tell you what you'd need to add for an XP entry in case one isn't added automatically.

Pretty sure that the Ubuntu installer can make a FAT32 partition if you manually configure it. I've never had to worry about this issue before, so can't give you any more specific instructions than that.

Good point about Windows being **loaded** with the wrong drive letter. Every installation of Windows I've worked with has been the sole one on the computer and has always been C:, and I've used the instructions I gave you just to remount data partitions.

This is about the end of my knowledge, so hopefully someone else will be able to come in and give you more help.

---

### Post by Wolf1994 on 2005-11-20
SSTwinrova, thanks for your answer. I think many qustions may be resolved when I try liveCD with Ubuntu - just to take a look...

---

### Post by forbes on 2005-11-20
To keep things simple you could try this.

[LIST=1]
[*]Boot into your XP install.
[*]Copy any important personal files onto from your C: to your D:
[*]Make sure your xp pagefile is on the D: drive
[*]turn off system restore on the C: drive
[*]Delete everything from your C: drive except the boot files in the root of the C: drive.  boot.ini, ntldr, cmldr and probably a few other important ones  ** google for win xp boot files **
[*]defrag the C: drive
[*]use a partition tool to resize the C: drive to 50MB.  Symantec's Partition Magic is the classic tool to do this, but there are several free tools out there.  (Does Breezy live CD have gparted on it?  Should work as your Win ME partition will be FAT/FAT32)
[*]Install Ubuntu into the 3.95GB space left between C: and D:
[*]GRUB will install but should correctly recognise and add your XP as a boot option.
[*]Win XP will still see the C: drive at the start and recognise the D: as before.
[/LIST]

Quick and dirty, but it will work.  Just need to make sure you keep all the boot files needed by XP on the C: and you're careful when you format the blank space in the install.  You could even make the C: slightly bigger and give yourself an area to swap files easily between OSes.

**Backup anything important you don't want to lose, before resizing, deleting and creating partitions.**

HTH

---

### Post by forbes on 2005-11-20
After thinking about this a bit more, you will need to edit your boot.ini file to take account of the changes to the partition table.

Or after you resize the C: partition, you could move the D: partition down and have the free space at the end of the drive for Ubuntu.  This way you wouldn't even have to edit your boot.ini

---

### Post by Wolf1994 on 2005-11-20
Thank you. Seems its an exit from my situation. I need a time to consider everything and to summon my spirit to perform above actions.

But I have last question:
> You could even make the C: slightly bigger and give yourself an area to swap files easily between OSes.
If my WindowsXP have FAT32-file system - is it means that I can avoid swap file and refers immediatly from Ubuntu to Windows-disk?

---

