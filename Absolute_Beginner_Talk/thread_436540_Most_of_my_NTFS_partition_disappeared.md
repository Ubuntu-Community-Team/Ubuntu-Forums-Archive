---
title: "Most of my NTFS partition disappeared"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by raycosm on 2007-05-07
As you can probably tell, I'm an absolute beginner. I decided to try out Ubuntu because I kept hearing such great stuff about Linux. I haven't backed up my Windows install, and if possible I want to try to get this fixed without wiping the hard drive and reinstalling Windows.

I recently installed Feisty 7.04 on a Toshiba Laptop with a 80 gb HDD with about 14 gb used up. In installation I chose moved the slider to about 20% or so. I then clicked next, and when it finished doing what it did, I clicked back, and then I panicked because it didn't give me a slider option, it just gave me the option to use the whole disk, use the largest contiguous part, or manually partition, and cancelled after the installer did stuff with partitions, because I accidently gave my current Windows partition about 15 gb, when I was trying to give Ubuntu about 15 gb. That was somewhere between the 4th and 6th step in the installation. I restarted to check if Windows still worked, and it did, but it had about 15 gb. So I booted back up the LiveCD and repartitioned Windows to around 45 gb, and then used the installer (I selected to use the largest contiguous part) and installed Ubuntu on the remaining space.

[IMG]http://i103.photobucket.com/albums/m136/raycosm/HDDCgparted.png[/IMG]


[IMG]http://i103.photobucket.com/albums/m136/raycosm/HDDC.jpg[/IMG]

Now, even though my NTFS partition is 45 gb, I can only access 15 gb.

---

### Post by psusi on 2007-05-07
It looks like expanding the ntfs partition did not work.  If you have not done so already, I suggest that you backup anything important.  After that, run a chkdsk /f in windows, and reboot to let it check the disk.  If it finds nothing wrong and it appears to otherwise be working just fine, then I'd suggest booting off the livecd, and running ntfsresize manually on the volume from the command prompt to expand it, since it looks like the partition size was increased, but the filesystem was not resized.

---

### Post by ammatos on 2007-05-08
Hello Ray - Though a Newbie to Ubuntu, I'm an OldGoat when it comes to computers.  According to the info provided, I think  there is something wrong with the partition table.  Windoze has a tendency to go koo-koo when there is something wrong with the LAST partition on a HD.  If you note,  Linux sees an "unkown" area at the end, while Windoze sees a healthy partition.  Both can't be correct. 

So the simple guess is that you screwed the MBR on the HD.  resolution - boot from floppy or U-Stick, run (Windows) Fdisk /mbr.  This should give your 80G drive its correct Boot Record.  If you have important data on XP, suggest you back up &/or image the readable section first.  /MBR should do it, buuuuuuuuuuuuuuut - if there is something of import - better safe than sorry.

Another observation is that you have an XP primary partition, a Linux primary partition, an  Extended/Logical  partition for the Linux swap, followed by another Linux primary partition.  It's late nite so I'm not 100% sure on this but, I don't think Windoze likes this arrangement of an Extended/Logical  partition followed by a primary.  If you follow-up on this and it is so, you'll need to delete the 204M Primary, expand the Extended partition to the end, so that it includes both the Linux Swap and the 204M Logical drives.

The other thing you may wish to do, is make that little 204M section into DOS, Windoze likes a simple DOS partition to terminate a drive.  And both Windoze & LinDuck can read it.  You may wish to use this drive to mount HD utilities (& others) on it, so you can simple boot from a floppy, and run DOS utilities from it.  If the Boot Record is not salvageable and you have to remount XP, etc. Theeeeeeeeeen, mount the LAST partition, as the First Primary, put DOS boot files on it - and you don't need a DOS Boot Floppy.

You Menu program would then give you the option to boot into DOS, XP, or Linux.
 
Hope this proves useful,

a.

---

### Post by LaurelLynn on 2007-05-08
Dear raycosm,

I pretty sure your problem was that enlarging the partition only changes the partitions size. It has no effect on the file system that was formatted onto the disk.

According to my copy of "Knoppix Hacks" the way to enlarge the file system is to boot to windows and run "chkdsk", unfortunately, it is very emphatic that you have to do it **before** trying to mount it under linux (probably to make sure windows ask to run it at boot).

I would give it a try though. If it doesn't ask to run chkdsk on startup, run it from dos window. It should spot the extra space as lost blocks and try to restore them.

---

### Post by psusi on 2007-05-08
> **ammatos said:**
> Hello Ray - Though a Newbie to Ubuntu, I'm an OldGoat when it comes to computers.  According to the info provided, I think  there is something wrong with the partition table.  Windoze has a tendency to go koo-koo when there is something wrong with the LAST partition on a HD.  If you note,  Linux sees an "unkown" area at the end, while Windoze sees a healthy partition.  Both can't be correct. 

In windows parlance, "Healthy" just means it is not a broken raid.  Both windows and linux agree that the partition type is unknown.  

> So the simple guess is that you screwed the MBR on the HD.  resolution - boot from floppy or U-Stick, run (Windows) Fdisk /mbr.  This should give your 80G drive its correct Boot Record.  If you have important data on XP, suggest you back up &/or image the readable section first.  /MBR should do it, buuuuuuuuuuuuuuut - if there is something of import - better safe than sorry.

There is nothing wrong with the MBR.  Fdisk /mbr will only remove grub and reinstall the dos boot loader, which is not what he wants.  Also most people these days do not have an old dos boot floppy laying around.  

> Another observation is that you have an XP primary partition, a Linux primary partition, an  Extended/Logical  partition for the Linux swap, followed by another Linux primary partition.  It's late nite so I'm not 100% sure on this but, I don't think Windoze likes this arrangement of an Extended/Logical  partition followed by a primary.  If you follow-up on this and it is so, you'll need to delete the 204M Primary, expand the Extended partition to the end, so that it includes both the Linux Swap and the 204M Logical drives.

The other thing you may wish to do, is make that little 204M section into DOS, Windoze likes a simple DOS partition to terminate a drive.  And both Windoze & LinDuck can read it.  You may wish to use this drive to mount HD utilities (& others) on it, so you can simple boot from a floppy, and run DOS utilities from it.  If the Boot Record is not salvageable and you have to remount XP, etc. Theeeeeeeeeen, mount the LAST partition, as the First Primary, put DOS boot files on it - and you don't need a DOS Boot Floppy.

You Menu program would then give you the option to boot into DOS, XP, or Linux.
 
Hope this proves useful,

a.

Windows has no problem with this partition layout.  It is a little strange, but will work just fine.  He just needs to resize his ntfs partition to use up the whole partition.

---

### Post by raycosm on 2007-05-08
> **psusi said:**
> It looks like expanding the ntfs partition did not work.  If you have not done so already, I suggest that you backup anything important.  After that, run a chkdsk /f in windows, and reboot to let it check the disk.  If it finds nothing wrong and it appears to otherwise be working just fine, then I'd suggest booting off the livecd, and running ntfsresize manually on the volume from the command prompt to expand it, since it looks like the partition size was increased, but the filesystem was not resized.

And how would I run ntfsresize so I can get the file system resized?

---

### Post by LaurelLynn on 2007-05-08
I thought resizing in Gparted should be doing the same thing as ntfsresize.  Qparted does, but admittedly only in more recent versions.

raycosm from the windows disk management tool (which you displayed earlier), you should be able to right click on the partition and run chkdsk from the popup menu (my windows memory is fading but I remember you can scan the disk for errors somewhere in there).

It is worth a shot at least.

If you need it, "ntfsresize" is a tool you can run from a terminal window's command line:

$ sudo ntfsresize -s size /dev/hdXXXX

But you will probably have to install it. My system has no manpage for it and it  is not in the repositories I am using with Synaptic and apt-get.  I've only used that command from Knoppix which is also Debian based so a ".deb" file should be available from somewhere. You can probably run it with the same size you used in Gparted.

I still think chkdsk will find the lost blocks, that is one of the things it is for.

---

### Post by raycosm on 2007-05-08
> **LaurelLynn said:**
> I thought resizing in Gparted should be doing the same thing as ntfsresize.  Qparted does, but admittedly only in more recent versions.

raycosm from the windows disk management tool (which you displayed earlier), you should be able to right click on the partition and run chkdsk from the popup menu (my windows memory is fading but I remember you can scan the disk for errors somewhere in there).

It is worth a shot at least.

If you need it, "ntfsresize" is a tool you can run from a terminal window's command line:

$ sudo ntfsresize

But you will probably have to install it. My system has no manpage for it and it  is not in the repositories I am using with Synaptic and apt-get.  I've only used that command from Knoppix which is also Debian based so a ".deb" file should be available from somewhere.

I've ran CHKDSK before, and it told me there was nothing wrong, I'll just try again right now and see.

And I just finished right now, I didn't get back to my computer in time to see the results, but when I rebooted it, it said the drive was clean, if that means anything.

---

### Post by LaurelLynn on 2007-05-09
The partition is fine, it's table entry in the MBR - Master Boot Record is why it is taking up 45GB. The problem is the disk was formated at about 15GB, that is how large the file system is.  Enlarging the entry in the MBR only makes changes to partition size. Something has to extend the formatting to include the new space. The version of Gparted bundled with the OS aparently is not sufficiently NTFS aware to do this.  Updating Gparted in Synaptic might install a version which can.

If not the newest versions of QtParted (the KDE version of Gparted), are sufficiently NTFS aware to resize the filesystem.  Even if you are running Gnome as your desktop you should still be able to install QtParted using Synaptic or apt-get. The two programs have similar interfaces.

Windows utilities though are much more likely to fully understand the NTFS filesystem.
On the windows side:

Chkdsk is the only tool I can think of that comes with XP that is designed to repair filesystems. It checks for bad or lost blocks, broken file links, etc...

Chkdsk won't tell you everything it did  when you ran it (should be an option for a more verbose listing). The real test is to look at the hardrive in explorer, and see it the free space has gone up.

If not, there are 3rd party applications, some free, that repair windows file systems. One of them should be able to spot the empty space and add it to the filesystem.

The last, and least desireable option, is to copy the contents to another partition with backup software of you choice (windows based apps may be more reliable for this). Then reformat the partition, and copy the files back.

Tar could be used for this, but I'm not sure if it would retain the NTFS file attributes.  I've used tar to backup user files from NTFS partitions. Operating system directories are another matter. Proper functioning of some of the files depends on their attributes.

At least those are all the options I can think of. If anything else comes to mind, I'll come back latter and add it to this thread.

---

### Post by psusi on 2007-05-09
QtParted and Gparted are essentially the same, only the UI code is different.  Gparted should have resized the filesystem, but for some reason it didn't.  IIRC, if you don't specify the size to ntfsresize, it will expand the filesystem to use the whole partition, so you just need to run sudo ntfsresize /dev/hdxxx to fix it.

---

### Post by raycosm on 2007-05-12
It tells me that the command "ntfsresize" is not found, and I have no idea how to install it or whatever. QtParted tells me that there's no device found, and that I'm maybe not using root user.

---

### Post by psusi on 2007-05-12
Did you forget to boot from the livecd like I said before?

---

### Post by kelvin spratt on 2007-05-12
download Gparted live from there web site burn to disc, then you will not have any system influence, then you can do what needs probally just needs re formating to be done on that partition and then you will be able to see the partition on linux, remember windows only sees windows partitions

---

### Post by raycosm on 2007-05-12
I finally got it, by using the Live CD and shrinking my Windows partition by one byte, GParted did the the rest and managed to resize the file system to fill up the partition.

Thanks to everyone for the help.

---

