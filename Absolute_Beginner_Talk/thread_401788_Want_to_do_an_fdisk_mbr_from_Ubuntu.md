---
title: "Want to do an fdisk /mbr from Ubuntu"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by josephpford on 2007-04-05
Ok, so I know I can't do an "fdisk /mbr" on Ubuntu, but that's what I'd _really_ like to do...  At any rate, here's the issue:

I've had Ubuntu 6.10 installed for about 4 months.  I've decided to dual boot.  I watched this video to learn how to create dual boot:

[http://video.google.com/videoplay?docid=-6104490811311898236](http://video.google.com/videoplay?docid=-6104490811311898236)

Note: I had previously tried, and failed, to get dual-boot to work.  At that point, I decided to just stay with Ubuntu 6.10 without windows and see what happens.  At any rate, I need Windows now.

So I started by putting in my IBM restore disks.  This proceeded to not ask me anything except the basic "can we format your harddrive" question.  There were no questions on partitions, boot records, etc.

When I rebooted, I got the good ol' GRUB Error 17.  I've done a bit of research on these forums and there is TOO much information on Error 17, none of which helps me (so far).  I've tried the following Tutorial:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

But on this step:

find /boot/grub/stage1

I got this error:

Error 15: File not found

Now I'm lost.  Help!

[email]josephpford@gmail.com[/email]

Thanks
Joe

P.S.  All you uber-smart nerds rule!

---

### Post by LaurelLynn on 2007-04-05
Dear josephpford,

Very **important** question:

When the recovery disk asked you if you wanted to ¨format your harddrive¨ did you say yes???

Laurel Lynn

---

### Post by josephpford on 2007-04-05
Yes.  In fact, I actually used the IBM recovery disk set twice.  Once just trying to format and then over-write Linux, and after I got the GRUB error, I tried using some program to completely erase the harddrive (called cfdisk if I remember correctly).  My goal then was to completely eradicate all grub, linux and windows files.  

Then, I put the IBM disks back in and restarted the whole install process again.  Again I said "yes" to format the HD.  However - I didn't ever actually see the "standard' Windows format (blue screen with yellow bar scrolling).  Everything with IBM has to be behind-the-scenes you know....

Thanks for the quick reply!!!!

---

### Post by TransitMan on 2007-04-05
Once you get the re-install of Windows done, then put in your Ubuntu disk, and proceed to setup a partition on your drive for Ubuntu, like the video showed you.
Then after you get that done, install Ubuntu. 
Once Ubuntu is installed, it will over-write the /mbr with the grub information and you should be good to go on your dual boot.

---

### Post by josephpford on 2007-04-05
What an excellent idea.  I'll do that!

---

### Post by LaurelLynn on 2007-04-05
@$&@#*$&@($) Brand Name Computer Makers! Pardon my un-Ladylike outburst. For years they have been cutting down on service calls by removing recover tools. Now they have only one service respose...reinstall everything.

If you have a Live CD of Ubuntu boot that at the command prompt  I would try:

sudo  fdisk /mbr

---

### Post by RaZer0r on 2007-04-05
doesn't ibm has a normal windows xp cd delivered with the desktop? in my case they did. if you get your windows installed ubuntu automaticaly detects the windows partition and will modify the grub for you when you reinstall, but it seems you havent got windows installed nor ubuntu?

---

### Post by josephpford on 2007-04-05
LaurelLynn - AMEN!!!  I totally agree.

I tried sudo fdisk /mbr and I got

Unable to open /mbr

I also tried sudo fdisk \mbr and I got

Unable to open mbr

I did NOT get a "standard" windows disk.  In fact, I got no disks at all, and instead they partitioned my harddrive so it had all that standard stuff on a seperate partition.  But I blew that away (on purpose) when I first installed Ubuntu 4 months ago.  I ordered CDs at that time because I was guesing i would need Windows again at some point...  So no... I do not have a standard windows disk.

---

### Post by LaurelLynn on 2007-04-05
The disk they gave you is probably a partition backup using something like Norton Ghost. It SHOULD include a backup of the boot record, but it sounds like it may not.

Let me think for a moment.

---

### Post by josephpford on 2007-04-05
OK, you know what, I've changed my mind.  Here's what I want to do with a Ubuntu Live 6.10 disk:

Totally 101% blow away my partition table, MBR, Windows, Linux, EVERYHING.

can it be done?!?!?

---

### Post by LaurelLynn on 2007-04-05
The first 446 bytes of the partition contains the bootloader, Windows should have written of it. ¨fdisk /mbr¨ is meant to restore a basic dos style bootloader which loads from the first partition.

The next 66 bytes are your partition table.

Reinstalling Ubuntu should work as it will put in its own MBR with GRUB.

As to getting Windows back you may have to install it after Ubuntu to get it to install at all. The problem is how to protect the Ubuntu install, and then how to tell GRUB to boot windows.

The question is how to hide Ubuntu from the IBM installer. That would be alot simpler with two drives. Then you could unplug the first one with Ubuntu, install windows, and plug in the Ubuntu drive first. As long as your bios is set to boot the Ubuntu drive first it will boot. From there we can edit GRUBS configuration file and add the Windows disk.

Without that you could choose manual partition during the Ubuntu install.  Make the first partition and NTFS partition, then a /root Ext3 partion, a /home Ext3 partition, and a small swap partition.

Boot to Ubuntu and backup the MBR from a terminal:

sudo dd if=/dev/hda of=MBR bs=512 count=1

My experience is that the IBM installer will **probably** ignore the linux partitions and choose the NTFS one.

If nothing boots when it is done boot the Live CD and from a terminal:

sudo dd if=MBR of=/dev/hda bs=512 count=1

Ubuntu should be back.  l´ll be back when I look up how to change the GRUB config to boot windows.

Laurel Lynn

---

### Post by LaurelLynn on 2007-04-05
According to the how-to at:
 [http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/19644-how-add-windows-2k-xp-grub.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/19644-how-add-windows-2k-xp-grub.html)


You:

sudo mount /dev/hda2 /media/hda2
sudo gedit /media/hda2/etc/grub.conf

and add the following:

[B]title Windows XP
               map (hd0) (hd1)
               map (hd1) (hd0)
               rootnoverify (hd1,0)
               chainloader +1[/B]

If windows is on the first partition that looks right to me.


If you get an error message, you either have to ¨sudo umount /media/hda2¨ (it might be /mnt/hda2), or you need to make the directory to mount to ¨sudo mkdir /media/hda2¨ first.

Laurel Lynn

---

