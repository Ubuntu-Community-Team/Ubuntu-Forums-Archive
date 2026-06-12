---
title: "[SOLVED] Installing dual boot, resizing problem"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by Alan Stancliff on 2007-10-04
I downloaded the ISO and burned a bootable CD about a week ago. I have a Windows XP Pro installation and several hard drives. I also watched the Alan Pope video for installing a previous version. I want to have a dual boot system.

The problem is that when I get into the installation, I am not given the option to resize the partition. The directions in the Alan Pope video and several other documents I've seen are different enough from the distro I have that the only option I can see is to use an entire drive rather than partition.

Is there a step-by-step set of instructions specifically for the normally intelligent but Linux-ignorant newbie to set up a dual-boot with Windows already installed and a live CD for what I suppose is Feisty Fawn? A link would be appreciated.

Also, I don't really know what file system I should use on the Linux part. Does the installer figure that out for me?

---

### Post by hyper_ch on 2007-10-04
Well, in the installation process you come at one point to the stage "Partitioning". There you have to select "manual" partitioning and then you should be able to resize partitions.

Before you actually resize windows partitions, defragment them first 2-3 times in windows and also make sure you have BACKUPS.

I recommend to create 3 partitions for linux (well, could be more - depending on your needs):

- 1x SWAP (filesystem SWAP) about the double size of your ram
- 2x EXT3
    --> 1x a partition about 10-20GB (depending on how much space you can afford) and make it mount as "/" ("root")
    --> 1x a partition the rest of the free space for storing your personal files, music files etc...  and make it mount as "/home"

You also have to know you can only have 4 primary partitions on a harddisk. You can evade that limit by creating an extended partition in which you can create logical volumes then.

---

### Post by spiravdaeg on 2007-10-04
> **Alan Stancliff said:**
> I downloaded the ISO and burned a bootable CD about a week ago. I have a Windows XP Pro installation and several hard drives. I also watched the Alan Pope video for installing a previous version. I want to have a dual boot system.

The problem is that when I get into the installation, I am not given the option to resize the partition. The directions in the Alan Pope video and several other documents I've seen are different enough from the distro I have that the only option I can see is to use an entire drive rather than partition.

Is there a step-by-step set of instructions specifically for the normally intelligent but Linux-ignorant newbie to set up a dual-boot with Windows already installed and a live CD for what I suppose is Feisty Fawn? A link would be appreciated.

Also, I don't really know what file system I should use on the Linux part. Does the installer figure that out for me?

Alan, it took me a bit, but I figured out that the easiest way to dual-boot a pc for both Microsoft OS and Ubuntu was to use the tools in the OS's the way they are designed to be used.

In your case, like mine, you already have Windows  on the hard drive. 
Like the first responder said - defragment the Windows hard drive before doing anything.
I had Vista, but the same method is used. First boot up your XP, go to 'computer management' and then 'disk management' - you can bring up 'help' if you need to, to find these if you don't locate them via your start menu/programs....

Use the disk management to resize your hard drive. A lot here depends on how loaded it already is. On a virgin install, not much added yet, Microsoft OS.....around 50% of the hard drive will be made available. Same is true of a loaded hard drive - around 50% of available space will be made available. Once resized - do not format to any FAT or NTFS file system. Rather the opposite. Delete all on that portion of the drive. Delete the volume if needed to be sure that the drive has nothing on it Microsoft-wise. Believe it or not, you're still not committed to Linux yet. Nor have you altered the drive beyond Microsoft use should you decide to say "forget it". All you'd have to do is delete the volume - unallocated - and simply reallocate back to Windows.

Okay, that done, reboot with the Live CD/Ubuntu in the optical drive. Come up to a working desktop. I found it works better than trying to install from the CD. Use the icon on the Ubuntu desktop that says 'Install'.  Pretty much agree to all until you come to the part about where to put Ubuntu. Choose the option that puts it in 'take over the unallocated space'.

Manual is difficult, and you sure don't want to take over the whole hard drive. 

Let Ubuntu install Ubuntu, GRUB and do its thing. Rebooting, removing disk and such at the time it asks. On the first boot, you will be faced with a new boot choice screen - choose your new Ubuntu (not recovery mode) and go through the process of entering all the necessaries. Once on the desktop - go to System, Administration, and Synaptics Package Manager. Bring up Synaptics and do a search for 'start-up manager' or 'SUM'. Install same. This will give you the easy ability to choose which OS you want to have as the default boot-to OS.

Actually a bit more to it all - but in a nutshell - that's about it.

Good luck.

---

### Post by spiravdaeg on 2007-10-04
Alan, I want to be sure you understand that when I talked of the volumes post-resize of the hard drive - I mean the volume that does NOT have XP on it. Kind of a big "duh", but after I posted, I reread and wanted you to be sure to understand that you do basically nothing to XP, or the portion of the hard drive with XP on it. It is the new portion of the hard drive that you are concerned with, solely. The idea is to just create the space, a void as far as any partitioning or formatting is concerned, for Ubuntu to 'see' and install to. 

Partitioning is a bit of a nightmare for a Linux Newbie. As I am myself. I've done it, successfully with Xandros, Puppy, SimplyMEPIS and other distros - but I have to be honest and admit that it is this one point that is least explained and understood by most all migrating from Windows. About the only partitioning done by Windows is just one, or a worst two partitions (a hidden one if OEM Windows is installed). All the ext this, swap that and the odd terminology probably puts more people off Linux from the git-go than anything else. That's why Ubuntu is becoming so popular in my opinion. Let it do its thing on some blank space and 'Voila' - all the weird stuff is done and correctly. 

Again, good luck - I will tell you, once in and you get to experimenting with all Linux can do compared with Windows, you'll love it. Its a whole new world of being a pc-user. Freedom.

---

### Post by fumduck on 2007-10-04
[http://apcmag.com/5162/the_definitive_dual_booting_guide_linux_vista_and_xp]("http://apcmag.com/5162/the_definitive_dual_booting_guide_linux_vista_and_xp")

[http://www.psychocats.net/ubuntu/partitioning]("http://www.psychocats.net/ubuntu/partitioning")


Good luck

---

### Post by Alan Stancliff on 2007-10-04
Thank you Hyper_CH, Spiravdaeg, and Fumduck for being there and being so willing to help. I am going to try again in the next day or so.

I'll be back with followup questions if necessary

---

### Post by Alan Stancliff on 2007-10-05
> **spiravdaeg said:**
> Alan, I want to be sure you understand that when I talked of the volumes post-resize of the hard drive - I mean the volume that does NOT have XP on it. Kind of a big "duh", but after I posted, I reread and wanted you to be sure to understand that you do basically nothing to XP, or the portion of the hard drive with XP on it. It is the new portion of the hard drive that you are concerned with, solely. The idea is to just create the space, a void as far as any partitioning or formatting is concerned, for Ubuntu to 'see' and install to. 

Partitioning is a bit of a nightmare for a Linux Newbie. As I am myself. I've done it, successfully with Xandros, Puppy, SimplyMEPIS and other distros - but I have to be honest and admit that it is this one point that is least explained and understood by most all migrating from Windows. About the only partitioning done by Windows is just one, or a worst two partitions (a hidden one if OEM Windows is installed). All the ext this, swap that and the odd terminology probably puts more people off Linux from the git-go than anything else. That's why Ubuntu is becoming so popular in my opinion. Let it do its thing on some blank space and 'Voila' - all the weird stuff is done and correctly. 

Again, good luck - I will tell you, once in and you get to experimenting with all Linux can do compared with Windows, you'll love it. Its a whole new world of being a pc-user. Freedom.

Well, as it turns out, the Disk Manager utility in Win XP doesn't resize partitions. That feature was introduced with Vista. But I had an old installation of Norton PartitionMagic already installed. I am wary of Norton stuff. But I tried it anyway.

The good news was that it didn't ruin the partition. The bad news was that it didn't work. 

I have a pretty new image backup from Acronis True Image 10. At this point, it seems that maybe I should get Acronis Disk Director or maybe BootitNG. I sure don't seem to be able to see how to shrink that partition from the Feisty live boot disk. I'm actually leaning to Acronis Disk Director because I can get it using a discount coupon that came to me in the ATI box.

It seems intuitive to me that shrinking my C drive by about 20 gigs (which I can easily do) and leaving the new section unpartitioned as you suggest is the way to go.

By the way, I appreciate how you came back and posted a second time to make sure I did not remove my windows C drive. You guys seem really eager to help.

Let me know what you all think.

---

### Post by Alan Stancliff on 2007-10-05
Okay chaps,

I have the drive partitioned and the second part at the end has 23.53 gigabytes of unallocated space, no file system. I'm going to bed soon, but tomorrow after work, I'll try to install Ubuntu again. I got the Disk Director, and it seems to have worked pretty well. It only cost me $20 US.

---

### Post by Alan Stancliff on 2007-10-06
I am afraid I've really messed up the situation. I hope someone can help me. I'll probably need to start another thread.

Basically, what I did is create a huge Linux partition and my Windows partition is too small. Please check out my new thread on this

**[SIZE="3"][COLOR="RoyalBlue"]UPDATE[/COLOR][/SIZE]**
This issue has been solved. To see how I solved it,[***_ check out this related thread_***]("http://ubuntuforums.org/showthread.php?t=568706").

---

