---
title: "Uninstalling Ubuntu"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by cate on 2007-04-25
My laptop is partitioned and is running Ubuntu Dapper and Windows XP. I want to uninstall Dapper due to lack of space on my Windows partition and problems setting up wireless network on Ubuntu (and unfortunately I must use wireless internet on this computer). I wanted to know how I would go about uninstalling it. I don't have a Windows boot CD, as Windows was already installed on my computer and the laptop didn't come with them.

Any ideas?

---

### Post by viciouslime on 2007-04-25
You could use partition magic to delete the ubuntu partitions and then expand the xp partition to fill the remaining space.

Have you tried the latest version of ubuntu, feisty? It is two versions on and very much more advanced than dapper, you will probably find wireless just works out of the box with it. You might wsnt to try installing feisty over the top first.

---

### Post by jocheem67 on 2007-04-25
You shouldn't forget that the grub bootloader will still be on your system. 

To get back to the windows bootloader you can fire up your vista cd and in the end go to the dos-prompt. There you can do a "fix mbr" to install back the original bootloader from windows.

You can also do this with a bootable dos floppydisk, as long as it has fdisk on it. You can get one at [www.bootdisk.com](www.bootdisk.com)..

Honestly this works flawlessly on xp, am not sure 'bout vista.

---

### Post by cate on 2007-04-25
I'm not using Vista, jocheem. I wouldn't touch that POS with a ten foot pole. ;)

I tried to delete the partition with PartitionMagic, but it wouldn't let me. It said something about it being locked.

I'm also not sure which bootdisk I'll need from bootdisk.com. Any ideas?

Don't worry, I'll be back to Ubuntu later. Right now I just really need the space back until I get my new external hard drive.

---

### Post by jocheem67 on 2007-04-25
Well, you can use a win 98 one , oem is okay...( just check them out ), maybe better the win98 se one...
If I remember well the command would be fdisk /mbr..
The little program fdisk should be present on the floppy, maybe you can do a google on fdisk and it's commands...

But, if you're using xp and got a cd , you could just use the cd...at the end ther's the screen asking you if you want to install a new copy of windows or repair an existing one. that's your option...
You get to a prompt, there you just do a "fix mbr".
Easy...

Not being able to delete a partition with part. magic.
Hmmmm....I'm using part. magic 8 and got no probs there. One condition: there shouldn't be a driver to read ext3 partitions loaded. The partition will be locked then.

Cheers.

---

### Post by thefoolisme on 2007-04-25
OK Jocheem, she has said she doesn't have the CDs.    :-)

I've used Partition Magic 8 before too without any issues.  If that doesn't work for you, perhaps you could make a gparted boot disk.  [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)  (Live CD or USB issue).  

The big issue here is fixing the MBR after deleting Ubuntu.  Since you don't have the CD, can you make MS boot disks?  [http://support.microsoft.com/kb/305595](http://support.microsoft.com/kb/305595)  That would require floppies.  Or at this site, you can create a bootable CD.  That is probably something you want to have anyway.  [http://www.answersthatwork.com/Downright_pages/Boot_Disks_and_Boot_CDs.htm](http://www.answersthatwork.com/Downright_pages/Boot_Disks_and_Boot_CDs.htm)

I do believe you can just keep Grub, but you'd have to edit it, and for that you would need a more experienced person than I.  Perhaps going through the grub information would point you in the right direction.

---

### Post by loanrangie on 2007-04-26
Where does the grub loader get filed ? i used partition magic and formatted and then deleted ext3 file system and then resized my ntfs file system. Then i will build a linux specific pc for myself to play with and the missus can use the xp pc that is familiar to her.

---

### Post by Tomosaur on 2007-04-26
Easiest answer is to load up the LiveCD and use the partition manager to format the space currently used by Linux (and the swap space).

I would advise against growing your windows partition to take over this space however, as I've had problems resizing NTFS partitions in the past. My advice would be to format using a 'Windows-Safe' file-system, such as NTFS or FAT32. Alternatively, you can format it as ext2 or ext3, and download the [fs-driver for Windows](http://www.fs-driver.org/). This will allow Windows to read and write to ext2 or ext3 filesystems.

EDIT: Grub is installed in two places - one is on the linux partition (the grub config files - so getting rid of that partition will get rid of the grub config files), and the other place is on the MBR, which is where all bootloaders are installed. There is only space for one bootloader on the MBR, and one bootloader is absolutely necessary to boot anything. To get rid of grub, you need to replace it with something. If you don't have the Windows Recovery Disk, you may be out of luck. However, you can get Grub for Windows too, so all is not lost, or you can try a totally different bootloader, whichever suits you. A quick google search should help you out.

---

### Post by jocheem67 on 2007-04-27
Okay I did some light research on restoring  an mbr...

I downloaded the win98 se oem disk from [www.bootdisk.com](www.bootdisk.com). Searched for commands usable with fdisk that's on the floppy..

Here's a site with some more explaining:  [http://www.pclinuxonline.com/wiki/dosmbr](http://www.pclinuxonline.com/wiki/dosmbr)...

It indeed is a " fdisk /mbr "  command from a booted win98 disk...

It's all very easy.

---

