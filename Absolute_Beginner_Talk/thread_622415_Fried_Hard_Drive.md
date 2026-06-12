---
title: "Fried Hard Drive?"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by johnfarrow on 2007-11-24
I tried to remove 7.10 and start over. It messed up the hard drive so bad that I can't reinstall XP or Win2000 because it now says I dont have a hard drive. It will let me install 7.10 again . I even used the CD that came with the Segate 500 gig drive and that wouldn't work.

Is there a Linux program that I can use to reformat the hard drive so I can reinstall XP?
_

---

### Post by Dr Small on 2007-11-24
Check out the gParted Live CD:
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by taurus on 2007-11-24
Boot from Ubuntu LiveCD and use gparted (System -> Administration) to erase all the partitions.  Then, format that harddrive to vfat or ntfs.  Now, boot with a bootable windows cd and see if you can install it on that harddrive now.

---

### Post by pdlethbridge on 2007-11-24
Are you booting from cd or harddrive?
Have you tried using XPs fixmbr?
Have you tried to Format the harddrive totally as fat 32 using ubuntu?

---

### Post by johnfarrow on 2007-11-24
I will give that go.  Thank you guys.

---

### Post by Taboo Mirage on 2007-11-24
Hello.

The reason that you may not be able to reinstall Windows on your drive is because it is using the SATA interface, at a guess.  Windows XP does not always have drivers preinstalled to read from SATA interfaces due to its age; you have to bear in mind that SATA drives were not commonplace when it was released.  This is likely the reason why XP isn't seeing your drive; it is unlikely the installer not seeing the drive at all is because of what you're done in terms of partitioning.

There is a way around this.  During the installation procedure on the WIndows XP disk you may notice that it requests you to hit a button in order to install third party drivers from a floppy disk.  This provides you an option of installing the necessary drivers for your device from floppy.  You can likely obtain the drivers you require from the manufacturer's website.

There is another way of installing the necessary drivers without using a flopy disk, should you not have a drive.  It is possible to slipstream the drivers into a Windows installation by copying the contents of an installation disk to a drive, including the drivers into your install and re-burning the new setup as an ISO.  There are applications such as nLite which can help with this process.

I suggest further searching about this process if you'd like further information.

Take care.

---

### Post by johnfarrow on 2007-11-24
I can boot to ubuntu from the hard drive.  It starts up right after it says there is no hard drive.  I can't get XP started to run the fix mbr (wish I could).  When I put the reinstall disk in, it tries to install and then give up and reboots.  I am going to try that Gparted from ubuntu idea now

---

### Post by johnfarrow on 2007-11-24
You are correct about it using SATA.  But when I try to use the reinstall system disk, it doesn't ask for the drivers before it reboots

---

### Post by Taboo Mirage on 2007-11-24
You stated in your first post that you couldn't reinstall Windows because it says that you "dont have a hard drive."  I assumed this to mean you couldn't begin an installation of Windows whatsoever due to the setup application on the disk not seeing the hard drive at all.  This would indicate a driver issue.  However, you then state that "it tries to install and then give up and reboots" in your next post.  Is the Windows installer giving you access to the partition information for your hard drive or not?  If no, you should pursue the driver route.  The option to install 3rd party drivers is presented to you immediately after you boot from the Windows setup CD.  I believe it asks you to press F8 to install the drivers from floppy media.

---

### Post by johnfarrow on 2007-11-24
I was wrong about the f6 option and I will persue that issuse and try to get a SATA driver from Dell.  I do not get to see any partition info from the XP installation disk.

I appreciate your assistance and will post back when I obtain the driver.

Thank You

---

### Post by johnfarrow on 2007-11-25
I was able to get the SATA driver floppy set up and I was able reinstall XP.  Of course I lost all the previous XP info/programs.  Also lost 7.10.

I am now afraid to try to install 7.10 again so I can dual boot.  I really like Ubuntu a lot, but I do taxes and other stuff where I really need  XP.

I certainly do thank all who offered help.

---

### Post by johnfarrow on 2007-11-25
what are the thoughts on installing Ubuntu on an external bootable hard drive and then selecting which drive to boot up on startup?

---

### Post by Taboo Mirage on 2007-11-25
Hi.

Thanks a lot for your update.  I'm glad that issue was pinpointed and you now have a usable system again.

In regards to your issue now, providing you correctly configure your partitions, there is nothing dangerous about dual booting.  It is probably the preferred method of many people who wish to use Windows alongside Linux.  

As you're starting off with a completely fresh install, I'd suggest that this is probably the perfect time to set up Ubuntu alongside Windows at this stage as you risk minimal data loss.  The basic structure of your drive should be as follows:

1x NTFS partition for Windows.
1x ext3 partition for Linux, mount point /
1x ext3 partition for Linux, mount point /home
1x Linux Swap Partition

Basically, you now need to resize your Windows partition to make space for your Linux partitions.  [This page](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html) gives some very extensive details about the actual partitioning process and how to prepare your Windows partition for resizing.  **I recommend backing up any sensitive data on your Windows partition before embarking on this.**  This warning applies in the future too when you're thinking about doing *anything* with your partitions.  Always be on the safe side!

Of course what you're saying is also a viable solution; you can boot from an external drive also.  [This](https://help.ubuntu.com/community/BootFromUSB) might be of use to you in this respect.

Take care.

---

### Post by johnfarrow on 2007-11-25
If I go dual boot do I need to do the "Manual" partition?  What percentage of 200Gig would be allocated for Mount point/ , mount point/home and swap?

---

### Post by Taboo Mirage on 2007-11-25
Yes, manual partitioning.  The sizes entirely depends on which OS you'll be wanting to dedicate most space to.  It'll also help if you know what each of these partitions does.  So:

NTFS - Your Windows partition.  If you plan on using this most then you'll obviously be wanting to dedicate the most space to it.

EXT3 / - This is where the Linux OS will be installed to.  You should reserve maybe 10-15 GB here depending on what you intend to be installed on Linux.

EXT3 /home - This is where your /home directory will be installed to.  Basically this is responsible for storing all of your user data so it should be the largest area. 

Swap - This is the area which is used as virtual memory.  It should be roughly twice what your RAM is.  For example, 2GB.  For most purposes it certainly shouldn't exceed 2GB.

So, let's take a pure example of a 100GB hard disk.  You could partition it like this:

NTFS - 70GB
EXT3 / - 10GB
EXT3 /home - 18GB
Swap - 2GB

Hope that makes things a little more clear.  The sizes of NTFS and /home really depend on which OS you're going to be storing more files on.  You will need to shrink your NTFS partition currently to make room for the Linux partitions.  You WILL need to defrag your drive before doing this as per the HOWTO I linked to earlier.

---

