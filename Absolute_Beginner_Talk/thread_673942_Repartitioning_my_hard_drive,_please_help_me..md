---
title: "Repartitioning my hard drive, please help me."
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by mwalkr on 2008-01-21
I'm trying to repartition my hard drive to give the space back to Windows Vista, which I admit certainly has it's downfalls, but I'm no computer whiz and I don't have the energy or the time for all the manual configuring necessary to make ubuntu usable.  I installed Ubuntu 7.10 from a live cd on the recommendation of my boyfriend, whom I assumed knew what he was talking about and would be able to help me get it working.  Alas, he's as ignorant as I, and my new Vaio is now bogged down with 2 OS's which I don't need.  I'm currently dual booting with windows vista and ubuntu, and ubuntu is apparently the default for some reason or other.  After installing ubuntu I encountered several problems, the most annoying of which have been total lack of sound, and the total lack of a desktop, which my boyfriend somehow managed to remove.  I'm completely lost in ubuntu and I just want it gone.  In Vista I've gotten as far as finding the disk manager, I can see the four separate partitions that have been created, but I have no way of knowing which partition is for which operating system. Does anyone know how the ubuntu partition would be labeled?  I believe the default partition that ubuntu created provided it with 53% of my hard disk.  The four partitions I have are labeled as follows: 7.51 GB Healthy (EISA Configuration), C: 97.13 GB NTFS Healthy (System, Boot, Page File, Active, Crash Dump, Primary Partition), 78.30 GB Healthy (Primary Partition), and 3.37 GB Healthy (Primary Partition).  I'm thinking the C: 97.13 GB NTFS partition is probably Ubuntu, but I'm not sure, and this repartitioning business seems dangerous.  I really need this computer to be in working order as I'm in the midst of my first semester back at school.  If anyone out there can make sense of my incoherent babble and lend me a hand I'd be forever grateful.

---

### Post by The Cog on 2008-01-21
It may be safest to leave things as they are until your stsudies are done or you have a good safe backup. A mistake that loses your studies would be a disaster. Come to think of it, that's a good reason for having a backup anyway.

NTFS is the Windows filesystem. You definitely want to keep that one.

Before doing anything else, boot into Ubuntu and run the command
**sudo fdisk -l**
(that's a lower case L at the end)
and write down the output. We can tell you from that which partitions are what. I'm not sure Windows can do that.

Before doing anything with partitions, you need to put the Windows bootloader back on. I believe this can be done with the command **fixmbr** from the console on a windows recovery disk. Once the PC boots straight into Windows without the GRUB menu, only then should you think of removing partitions.

---

### Post by forestpixie on 2008-01-21
ok - the c:\ ntfs drive is most definitely not the ubuntu install is likely to be the vista one

can you boot ubuntu, open aterminal - applications >accessories paste this command and post the output

```
sudo fdisk -l
```

do you have the vista disc to fix the bootloader - if not you should apparently be able to make one from within vista.

What you need to do is  fix the vista bootloader, delete the linux partitions and then resize vista to use the free space.

There are tools to repair the vista boot - I'll have a look around, but it'll be easier if you've got the disc

edit - this page will help if you do have the disc [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

ok this could help too [http://ubuntuforums.org/showpost.php?p=3794970&postcount=2](http://ubuntuforums.org/showpost.php?p=3794970&postcount=2)

you can it seems do the fix from within ubuntu - near the bottom of this post

---

### Post by bumanie on 2008-01-21
"I'm thinking the C: 97.13 GB NTFS partition is probably Ubuntu"
That most definitely won't be the ubuntu partition as it uses the ext3 file system. Windows, since at  east xp uses ntfs.
The initial EISA partition is a partiton made by the computer manufacturer with various tools available, may be even a recovery files.
"78.30 GB Healthy (Primary Partition), and 3.37 GB Healthy (Primary Partition)"
The 78.3gb partition is probably the ubuntu file system and home folder etc. and the 3.37gb partition is likely to be the ubuntu swap file.

---

### Post by mwalkr on 2008-01-21
The laptop didn't come with a recovery disk for windows. There seems to be some sort of recovery program within Vista. Do I understand correctly that I should be able to burn a recovery disk from Windows Vista?

I ran the sudo fdisk -l command.  It reads as follows:


Device Boot   Start       End     Blocks          ID    System
/dev/sda1         1          981    7873536      27    unknown
Partition 1 does not end on cylinder boundary
/dev/sda2 *      981   13660   101844727   7  HPFS/NTFS
/dev/sda3     13661   23881   82100182+   83  Linux
/dev/sda4     23882    24321   3534300       5   Extended
/dev/sda5     23882    24321   3534268+    82  Linux swap / Solaris



Sorry about the format there.  I tried to line it up in my text box, but it won't post that way.  I hope it's intelligible.  I think I may know which partitions are which now looking at this, but I'm still wary of doing any resizing.  The Cog may be right that I should just leave it alone until the semester is over.  On a related question:  as I mentioned, I have no desktop in ubuntu.  I can only run commands.  Would it be problematic for me to reinstall ubuntu over the existing ubuntu in order to get my desktop back, or is there a better way?

---

### Post by chach man on 2008-01-21
ubuntu has probably installed on an ext3 partion. the easyest way i can think of looking at it would be to either burn a Gparted live disk which would show you all of the partions on the disk graphically  (easiest thing to do).

or make a DOS NTFS floppy disk which would only be able to see the ntfs file system(s) but if it is the windows install you would be able to confirm that the windows install is in fact on the ntfs partition.


I believe that in order to burn the vista recovery disks all that information is stored on a seperate partition my guess is it would be the 3.37 GB partition. and the ext3 is the 78.3GB ubuntu partition.

Im assuming you bought this computer from walmart or some other like store that preformated the harddrive for you...correct???

it looks like these 3 are ubuntu / linux related but i wouldn't put money on it/ try to delete them 
/dev/sda3 13661 23881 82100182+ 83 Linux
/dev/sda4 23882 24321 3534300 5 Extended
/dev/sda5 23882 24321 3534268+ 82 Linux swap / Solaris

---

### Post by forestpixie on 2008-01-22
sda1 - the vista recovery partition
sda2 - your vista
sda3 - ubunut
sda4/5 - extended partition with swap inside it

when you get to the prompt after booting ubuntu you could edit the menu.lst so that vista is default, and then learn to get on with ubuntu as well :)

Yes you should be able to burn the recovery  disc from within vista - absolutely no idea how but I guess there'll be a option in the menu somewhere. I would suggest doing that - then at least when you get a vista problem you might be able to sort it out.

Once you've got that you'll be able to write the vista boot again and could lose the linux partitions with the vista resize tool.

I personally would look at getting ubunut to boot so you can at least make an informed choice :D

---

### Post by The Cog on 2008-01-22
As others have said: Partition 1 is a recovery partition of some sort, and partition 2 (NTFS) is your Windows partition. Don't touch these. 

You can reinstall Ubuntu using custom partitioning and specifying the right mount points: sw for sda5 and / for sda3, or you can delete partitions 5, 4, 3 (in that order) and then tell the installer to use the free space.

You could make windows the default inthe bootloader menu reasonably safely. From your (text) login, use the command 
**sudo nano /boot/grub/menu.lst**
(that's lower-case LST short for list at the end)
find a line that says **default 0** and change the 0 to (probably) 4, then save. Don't change anything else in that file.

If you want to play with Ubuntu, you might try this command:
**sudo dpkg-reconfigure xserver-xorg**
and just take the default for any question you're not sure of. It might fix the GUI, it might not, but it won't hurt to try.

To change back to windows only, you can delete partitions 5, 4, 3 and then enlarge partition 2, but make sure the bootloader has been replaced with a windows one first. 
Vista can enlarge its running partition (I've done it) using the disk management thingy.

---

