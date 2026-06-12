---
title: "Partitioning troubles"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by jbor7755 on 2007-04-16
I am in the process of trying to set utp my Ubuntu installatino alongside Windows XP in my dell laptop.

I was dead keen to use the following partitions

25GB NTFS for Windows
25GB ext3 for Ubuntu
2GB Swap
about 48GB fat32 for shared files between Windows and Ubuntu

The problem is that I actually already have 2 partitions.  Apparently windows has a small (50 odd MB) partition for some files and the main NTFS partition.

I obviously can't have 5 partitions.  Is there a way of combining the swap and shared partitions???

Cheers

---

### Post by freebird54 on 2007-04-16
Not a problem.  IN the manual partitioning mode, first create an extended partition containing all the free space to be reconfigured.  Then, create whatever more partitions you wish within it.  Even Windows can access an extended partition if it doesn't have to boot off it - and Linux is designed to be flexible, so it will have no problem.

Hope this helps!

---

### Post by az on 2007-04-16
> **jbor7755 said:**
> I am in the process of trying to set utp my Ubuntu installatino alongside Windows XP in my dell laptop.

I was dead keen to use the following partitions

25GB NTFS for Windows
25GB ext3 for Ubuntu
2GB Swap
about 48GB fat32 for shared files between Windows and Ubuntu

The problem is that I actually already have 2 partitions.  Apparently windows has a small (50 odd MB) partition for some files and the main NTFS partition.

I obviously can't have 5 partitions.  Is there a way of combining the swap and shared partitions???

Cheers

You can have much more than just four partitions.  You can only have four primary partitions, but you can install any OS on a logical partition within an extended partitions.  The four (primary) partition limit has been irrelevant for about a decade and a half...

As well, forget about a shared partition between linux and windows.  Use the windows ext2/ext3 driver to access your linux partition through windows.  Your linux partition becomes another native partition that windows can use,

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by jbor7755 on 2007-04-16
Okay now I have another problem.

This small 50MB partition is fat16.

I decided to create a separate ext3 partition instead and use some left over space to give me more windows partion space.

However on continuing with the setup an error box came up saying: "unresolved errors in fat 16 partition, please go back to correct" or something like that.  I am not sure what is supposed to be wrong.

---

### Post by jbor7755 on 2007-04-16
here is what the message says:

"Go back to menu and correct error:
The test of the file system with type FAT16 in partition #1 of SCSI1 (0, 0, 0) (sda) found uncorrected errors"

I have the option to continue or go back and correct.

The problem being that I have no idea what I am supposed to correct (Ubuntu doesn't need to have anything to do with this partition - I have not asked for it to be formated)

---

### Post by freebird54 on 2007-04-16
Back out - boot Windows, and run **CHKDSK /F** from a command line :)  You have unresolved errors in the partition, and the partition program doesn't want to mess with a flaky setup.  Actually, the Linux tools could probably fix it too - but CHKDSK /F is a native tookit item.

I am NOT sure that a Win that old will run the Linux filesystem - so you might be safer to go with the original idea of a FAT32 shared space...

---

### Post by jbor7755 on 2007-04-16
The windows isn't that old (XP SP2).
It just seems to use this little partition (as well as the usual C drive - in NTFS). It has no drive letter assigned and is in FAT16.  Has no-one else seen this before?

I don't understand how there could be problems with it since windows XP was cleanly reinstalled yesterday.

---

### Post by freebird54 on 2007-04-16
Well - mine never did that!!  If it isn't indicative of W95, then ignore it I guess....

Sorry for the false alarm :oops:

---

### Post by jbor7755 on 2007-04-16
The result of chkdsk /f is:

"the type of the file system is NTFS.
Cannot lock current drive
Chkdsk cannot run becasue the volume is in use by another process.  Would you like to schedule this volume to be checked next time the system restarts?"

So it didn't even look at the little FAT16 partition

Opening Computer management and disk manager shows the presence of the FAT16, NTFS and the new Ubuntu and swap partitions (unknown).

I elected to run chkdsk at on reboot.  It doesn't seem to look at the FAT16 partition.

I don't understand this at all.  Ubuntu shouldn't even be looking at this partition (windows doesn't seem to).

FYI: I am using a Dell Inspiron 6000 laptop with 100GB hard drive

---

### Post by jbor7755 on 2007-04-17
Can anyone help me with this?

---

### Post by Bachstelze on 2007-04-17
Have you tried looking into that FAT16 partition so see what's in there ?

---

### Post by freebird54 on 2007-04-17
Sorry I disappeared - apparently I needed sleep!  It is a strange partition indeed that you have there - but the dosfsck command should be able to deal with it.  You could either

```
dosfsck -a /dev/sda1
```

which will **A**utomatically fix things (won't ask further - uses least destructive option to fix)  or

```
dosfsck -r /dev/sda1
```

which does the same job inte**R**actively (fixes after asking if it should fix for each thing it finds)

I am assuming from the error message you posted earlier that sda1 is the strange FAT16 partition.  You could check that with 

```
sudo fdisk -l
```

before running the dosfsck command.

Once it has fixed the partition, you should have no further problems with the process.  I too wonder what the heck it is.  Leftover Win 3.1?  Some sort of recovery partition?  Ah well - should be fixed whatever it is!

---

### Post by mahiyar on 2007-04-17
I have read somewhere that the small partiotin as is in all recent dell desktops is for the diagnostics programme and all. See this [http://www.goodells.net/dellutility/](http://www.goodells.net/dellutility/). This link within ubuntu gives the pros and cons of removing the dell utility partition [http://ubuntuforums.org/showthread.php?t=402341&page=2&highlight=dell+utility+partition](http://ubuntuforums.org/showthread.php?t=402341&page=2&highlight=dell+utility+partition)

---

### Post by Tundro Walker on 2007-04-17
My question would be...why did WinXP setup a 50mb partition?  In using WinXP, I don't recall it ever needing more than 1 partition, unless someone manually setup more than 1.  Are you using a pre-setup computer (EG: Dell) where Windows was preinstalled?  Perhaps the 50mb has the system files, and then the main partion you use was setup for application installs and such.

See if you can mount that 50mb partition in Ubuntu and check out what's on it.  

Using a Live CD to boot Ubuntu, you'd start with a terminal window and use...

```
sudo fdisk -l
```...to see what the [COLOR=Red]**/dev/hd??**[/COLOR] path is of that partition.  FDISK should return something like...

```
Disk /dev/hda: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
** /dev/hda1**   *           1        3582    28772383+  83  **Linux**
** /dev/hda2**            3583        3738     1253070    5  **Extended**
** /dev/hda5**            3583        3738     1253038+  82  **Linux swap / Solaris**
```Look for your /dev/hd?? that uses FAT16.  Then, do the following in the terminal...

```
sudo mkdir /media/win16; mount [COLOR=Red]**/dev/hd??**[/COLOR] /media/win16; ls -l -a -h /media/win16 > ~/Desktop/fat16.log
```...which will...[LIST=1]
[*]make a mount point called "/media/win16" for your FAT16 partition
[*]mount the /dev/hd?? (replace the ?? with whatever letter & number you found in fdisk for your FAT16 partition)
[*]list what's on it in detailed mode, showing everything (hidden files, etc)
[*]and (should) also dump the list to a file called 'fat16.log' on your home/user desktop[/LIST]Looking down the list, see what's on that drive.  It may be old, worthless junk.  Or, if your comp is a pre-built Dell, it may be all the WinXP system files.  If you need help deciding, just copy/paste the contents of the 'fat16.log' file in your next post, and hopefully some folks with Windows experience can help you decide if it's necessary to keep or trash.

---

### Post by jbor7755 on 2007-04-17
Thanks for all your help.  It is indeed a rescue/diagnostocs partition set up by Dell.  Comparing the Dell setup CD with an ordinary XP install CD showed that the Dell CD has an extra folder with some executables (apart from that - no differences).  Presumably these set up the small partition (without prompting the user during installation).

A bit anoying but it seems the best thing to do would be to do a clean reinstallation WITHOUT this partitiion (I have never needed it and I can do a rescue from the CD anyway).

I could either use the ordinary XP CD or I could make a copy of the dell CD without the extra folder and see how that goes.

Thanks again

---

### Post by metaphor- on 2007-04-17
is there any information on this partition which you need? why not just delete it and move the free space.

i prefer to use partition magic 8 for all that stuff, simple boot program which checks errors and partitions drives very quickly

---

### Post by jbor7755 on 2007-04-18
I wasn't certain so I decided to go with a clean reinstall.  All went well.  I now have windows on a 25GB partition, a 20 odd GB partition for Ubuntu and a "/share" partition in FAT32.  The operating systems have both booted up flawlessly.
All I need to do now is change GRUB so that it waits a little longer for the user to make up their mind which operating system they want to use.
Then of course get my wireless access (my only internet access) happening in Ubuntu and start updating and installing drivers.

No doubt I will be posting more questions soon.

---

### Post by freebird54 on 2007-04-18
I find that this link gives you something fun/easy to work with for Grub.

[http://ubuntuforums.org/showthread.php?t=228104](http://ubuntuforums.org/showthread.php?t=228104)

Saves some of the careful editing that goes wrong!

---

