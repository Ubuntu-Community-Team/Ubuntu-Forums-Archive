---
title: "Boot PROB"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by staf4t5 on 2007-05-24
I have WinXP sp2 installed currently on my machine but i want to install ubuntu on another disk without affecting my current windows installation boot.ini...How do i do this???:frown:

---

### Post by starcraft.man on 2007-05-24
[This]("http://users.bigpond.net.au/hermanzone/p2.htm") is a really good guide to creating a dual boot with fat shared, its for the alternate disk and shows ya all the steps :).

Alternate disk can be gotten [here]("http://releases.ubuntu.com/7.04/") btw. I just prefer it to the automatic one on the main page.

However, it will replace with GRUB. Why do you want to preserve the boot loader from windows? You can use fixmbr command any time after you replace it with GRUB to get it back. Easy enough no?

If you absolutely want to keep the windows boot files, you'll have to make sure you install the GRUB bootloader to the partition/alternate HDD and then manually edit the boot.ini to get into Ubuntu. It's more trouble than the windows bootloader is worth IMO.

---

### Post by KIAaze on 2007-05-24
So you want to have Windows and Ubuntu on two separate hard disks, right?

In that case plug in both hard disks and install Ubuntu on the one you want to have it on.
**It's important that the Windows disk is also plugged in so that you can dual-boot with Grub later.**

I don't know if the master-slave order matters however...
The problem is that Windows boot must be on the first hard disk/partition in order to boot.
So I suppose that the Windows disk should be configured as master.

Please also have a look at this post in case you want to make the dual-boot work after having installed the OSes separately on the HDs:
[**How to dual-boot Ubuntu and XP after installing them separately on two HDs**]("http://ubuntuforums.org/showthread.php?p=2702832#post2702832")

---

### Post by staf4t5 on 2007-05-24
The problem is my main drive is ntfs winXP and my ubuntu is on another drive but as soon as i remove the ubuntu drive i cant access my windows one because it refuses to boot...

---

### Post by psusi on 2007-05-24
Why are you unplugging the drive with ubuntu on it?

---

### Post by staf4t5 on 2007-05-24
Thanks for the help guys...:)

---

### Post by starcraft.man on 2007-05-24
> **staf4t5 said:**
> The problem is my main drive is ntfs winXP and my ubuntu is on another drive but as soon as i remove the ubuntu drive i cant access my windows one because it refuses to boot...

Ummmm, you remove and take an internal HDD with you often? Why? The easiest means I have always seen for getting a dual boot, is to put both OS on the same HD and offload all data onto a second (USB or internal) drive. I also usually have a small buffer for data (around 50 GB) on the OS drive thats shared.

Is there a reason your opposed to both on the same drive? XP install really only takes 12 (or less) GB and Ubuntu is 6 + 2 GB swap (or less swap, usually double your ram = swap size).

Edit: Har, psusi beat me to the question with a quick post >.>.

---

### Post by staf4t5 on 2007-05-24
oh cos its in an external case and sometimes i need to swap it for data on my other drives because my pc has only one IDE cable and the rest are SATA but i still have IDE drives that i can still use..

---

### Post by staf4t5 on 2007-05-24
I tried putting XP and ubuntu on the same drive once and lost my 120 gig ntfs partition with everthing on it when trying to resize it...The installation froze up and i dont want to risk it again...

---

### Post by ayenack on 2007-05-24
Why not just change the boot order in BIOS each time you boot. Disable one drive and enable the other. So you install XP on your first drive with the second drive disabled in BIOS then do the same in reverse for Ubuntu. Then you can choose which drive to boot to in BIOS by enabling/disabling a drive. Long way round but should work. You could recover your XP install with your XP disc (if you have one) and set it up as before. You might need to install a few drivers after the recovery, graphics and so forth but all your data should still be there.

Best of luck. ayenack.

---

### Post by staf4t5 on 2007-05-24
My MB does not support that i guess i will probably just have to disconnect my XP drive manually...Thanks

---

### Post by ugm6hr on 2007-05-24
If I've understood your current setup is:
External HD for Ubuntu
Internal HD for XP
Occasionally disconnect Ubuntu drive (and still need to use XP).

If that's the case, you can use the Windows bootloader to access GRUB on a different partition.  GRUB will then only access Ubuntu.  That way, the Windows bootloader will start whether Ubuntu drive is connected or not, and give an option of XP or Ubuntu (if Ubuntu drive disconnected - Ubuntu option will generate an error).

How to do it - I have looked up how I did it with a prior Linux installation, since I just use GRUB alone now.  Essentially, you install GRUB to a partition supernode rather than the Master Boot Record of the HD (I did this with Puppy Linux LiveCD - but supergrub disk is perhaps better, but less user friendly), and edit the menu.lst to default to loading Ubuntu.  You then copy the supernode to the Windows partition, and put an entry in boot.ini to access it.  EDIT* you can in fact just use the Master Boor Record I think - I suppose it's easier with Ubuntu, since it defaults to using that anyway - see Option 2*

Here's how - it might need editing for your setup:

**Option 1**:

1. Install Ubuntu linux in its own HD partition and when it comes to installing the bootloader grub, install it to the super node of the linux partition rather then the MBR (where it would write over the windows bootloader).  I think this will only be possible if you use the "Alternate CD", altho you could use the Live CD and then use a different CD to install GRUB independently.

2. After installing GRUB, using the LIve CD again (or any Linux LiveCD):
Assuming that your linux partition is /dev/sdb2, use the dd command to made a direct copy of the supernode to file.  In Terminal:

dd if=/dev/sdb2 of=boot.lnx bs=512 count=1

3. This will create file called boot.lnx in your current working directory, which is usually your user home directory. Copy this to the root directory of your windows partion (c:\).

4. Now boot into windows and edit the BOOT.INI (either from Linux as root, or in Windows you will need to be an administrator to do this - right click My Computer properties -> Advanced -> Startup -> Edit manually).

5. Assuming the Root directory of your windows partion is c:\, and you have copied the boot.lnx file here, append to the end of the file:

c:\boot.lnx="Ubuntu Linux"

Note the boot.ini file, should now look something like this:

[boot loader]
timeout=10
default=multi(0)disk(0)rdisk(0)partition(1)\WINNT
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows XP" /fastdetect
c:\boot.lnx="Ubuntu Linux"

**Option 2** (perhaps easier - altho I've not used a setup like this):

1. Install Ubuntu as normal to the new hard drive, and install GRUB to the MBR of the same drive.

2. Using the Live CD before rebooting, assuming that your linux hard drive is /dev/sdb, use the dd command to made a direct copy of the BMR to file.  In Terminal:

dd if=/dev/sdb of=boot.lnx bs=446 count=1

3. Continue from 3 above

And that should do it.  In theory....  

The good thing about this (especially Option 2) is that either hard drive will boot independently or together - so you can remove whichever one you want.

That's a bit disjointed, cos I've just cut and pasted a previous help doc that I had, and tried to edit it for your situation.

---

### Post by ayenack on 2007-05-24
Try this [site]("http://ubuntuguide.org/wiki/Ubuntu:Feisty") for info on Super Grub may be of help. Scroll down to [1.19.7.2  Super Grub Disk]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Super_Grub_Disk").

---

### Post by staf4t5 on 2007-05-25
thanks ayenack and ugm6hr got it working finally....:mrgreen:

---

### Post by rweaver4 on 2007-05-27
Could you explain to a simpleton step by step what is meant by:

"Assuming that your linux partition is /dev/sdb2, use the dd command to made a direct copy of the supernode to file. In Terminal:

dd if=/dev/sdb2 of=boot.lnx bs=512 count=1

3. This will create file called boot.lnx in your current working directory, which is usually your user home directory. Copy this to the root directory of your windows partion (c:\)."
Thanks
rweaver4

---

### Post by KIAaze on 2007-05-27
Well, what you have is already a step-by-step explanation to me. ^^
1)```
df -h /
```
The first term is your GNU/Linux filesystem.
2)```
dd if=/dev/sdb2 of=boot.lnx bs=512 count=1
```
3)Plug in USB key.
4)Copy "boot.lnx" to the USB key
5)Reboot into windows
6)Copy "boot.lnx" from the USB key to C:\

[U][B]And here's an explanation of it:
[/B][/U]
_What's my GNU/Linux partition?_
Well, it's simply the partition where you installed Ubuntu.
A partition is simply a part of a hard-disk.

To find out on what partition you installed Ubuntu, simply type:
```
df -h /
```
You'll get something like this:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3             3.0G  1.7G  1.4G  56% /

```
Here, the GNU/Linux partition is /dev/hda3 for example.

_Explanation of the "dd" command:_
According to the manual (man dd), "dd" is a command to "convert and copy a file".
However, it is more powerful than the simple "cp" command to copy files.
It allows you to do a bit by bit copy of a part of a disk and save it in a file, or vice-versa, read a file bit by bit and copy it to the disk. (I think this is due to the fact that in Unix, everything is a file, including system devices :) )

The "dd" command is mostly used to back up the MBR and/or restore it:
[How to back up the MBR]("http://en.wikipedia.org/wiki/Mbr#Unix-like_systems")

_What's a supernode?_
I don't know, but I suppose that it's something like the MBR (Master Boot Record):
A Master Boot Record (MBR), or partition sector, is the 512-byte boot sector that is the first sector ("Sector 0") of a partitioned data storage device such as a hard disk.

_Last part:_
> 3. This will create file called boot.lnx in your current working directory, which is usually your user home directory. Copy this to the root directory of your windows partion (c:\)."


Well, this looks quite clear to me.
To do this, you may need a USB key on which to store the "boot.lnx" file on.
Then just reboot into windows and put the file in C:\.
I have no idea why this works when you put it in C:\ however. :/

---

### Post by ugm6hr on 2007-05-27
@KIAaze:
Cheers for stepping in.  I didn't know about the df command to be honest - that's why I like these forums - I learn something while helping someone else.  Good, eh?

@rweaver4:
I'm assuming you know how to find Terminal (I think it's in Applications somewhere).
Then just type the commands as listed.  You don't need to "find" the files at all.
i.e. substitute the output from *df -h /* into *dd if=**/dev/sdb** of=boot.lnx bs=446 count=1*

If you have Windows on NTFS partition - then it will probably be easier to use a USB stick like KIAaze suggested to transfer it to the C:\ drive (from within Windows).  The rest of the steps are all in Windows anyway.

---

