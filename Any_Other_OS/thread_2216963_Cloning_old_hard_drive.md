---
title: "Cloning old hard drive"
date: 2014-04-14
forum: Any Other OS
---

### Post by quadrplax on 2014-04-14
Ok, so here is my situation: I have a really (really) old desktop computer, a Packard Bell 945 (or at least that's what it claims the model number is). It has a 333Mhz obviously single core Processor and 64MB of RAM. The hard drive is a 4GB IDE drive. I would plug it into my not-as-old PC that has IDE connectors, but it doesn't show up for some reason, so that would also be a solution. If that can't work, however, then I need a lightweight version of Linux to run that is compatible with a lightweight disk imaging program. I would prefer a VDI or VMDK. If there is software you know of for Windows 98, that would work too, as long as it meets those processor and RAM requirements. As a test, I was able to boot into PLoP Boot Manager off of a flash drive, which allowed me to boot into Ubuntu's GRUB menu, but from there, regular and recovery mode both crashed to the BiOS. Oh, and this is a one time thing so I don't want to go out and but an IDE to USB adapter or anything like that. Any suggestions? Afteward, I will be doing this with the file: [https://www.virtualbox.org/wiki/Migrate_Windows](https://www.virtualbox.org/wiki/Migrate_Windows)

Edit: Just found [this]("http://www.easeus.com/disk-copy/home-edition/spec.htm"), looks great except it requires 128MB of RAM :(

---

### Post by TheFu on 2014-04-15
They sell SATA/IDE--> USB converters for $10-$20. It is worth having 1.

Or try tinycore.

---

### Post by mips on 2014-04-15
What's wrong with dd? Will work on any lightweigh linux distro (usually included by default) and it's also mentioned in that virtualbox guide you linked to.
[http://en.wikipedia.org/wiki/Dd_(Unix)](http://en.wikipedia.org/wiki/Dd_(Unix))


Or you could use a livecd called clonezilla which has a ncurses interface.
[http://clonezilla.org/](http://clonezilla.org/)


For windows you also get dd & windd,
[http://www.chrysocome.net/dd](http://www.chrysocome.net/dd)
[http://sourceforge.net/projects/windd/](http://sourceforge.net/projects/windd/)


To find a lightweight linux look at [http://en.wikipedia.org/wiki/Lightweight_Linux_distribution](http://en.wikipedia.org/wiki/Lightweight_Linux_distribution) and click on the options on that page to get more details which would tell you the ram requirements.

Have a look at slitaz, tinycore & alpine, they should all work in 64MB of RAM. Slitaz is really cool and I'll put Tiny core second after slitaz.

---

### Post by quadrplax on 2014-04-15
I'm trying slitaz. I can get to the boot menu, but it seems gets stuck  on rootfs4.gz on all boot options. Media Check doesn't say anything is  wrong with the file. The light on the flash drive, however I don't know  if it's the same type of error in [my other post]("http://ubuntuforums.org/showthread.php?t=2213645&page=4")  (which is still unsolved). The flash drive I am using does not have the  light on unless activity is occuring, so it's not on when I'm in the  boot selection menu for example, so that might be the problem.

Edit: just to be sure, I left my signature on by mistake, but obviously it's irrelevant for this topic.

---

### Post by TheFu on 2014-04-15
Booting from USB is a relatively new idea.  Not all legacy systems will boot from USB and some that might are very picky about the flash drive. It is much better today, but in 2006, it was hit-or-miss.

---

### Post by quadrplax on 2014-04-15
As I said in the first post, I'm using plop boot manager, not my BIOS's (nonexistent) USB boot option.

---

### Post by quadrplax on 2014-04-16
Bump #1

---

### Post by sudodus on 2014-04-17
Please tell us what you have tried, and what help you want right now :-)

Would you be able to take the drive out of the computer and connect it to another computer?

64 MB RAM is very low today, and you need an extremely light linux version, maybe an old one like DSL.

---

### Post by quadrplax on 2014-04-17
> [COLOR=#000000] I would plug it into my not-as-old PC that has IDE connectors, but it doesn't show up for some reason[/COLOR]
> [COLOR=#000000]I'm trying slitaz. I can get to the boot menu, but it seems gets stuck on rootfs4.gz on all boot options.[/COLOR]
.

---

### Post by sudodus on 2014-04-18
> [COLOR=#000000] I would plug it into my not-as-old PC that has IDE connectors, but it doesn't show up for some reason[/COLOR]

Did you check with terminal window commands, if it was shown as a device (although maybe it was not mounted and therefore not visible in a file browser)?

```
sudo parted -l
```

> [COLOR=#000000]I'm trying slitaz. I can get to the boot menu, but it seems gets stuck on rootfs4.gz on all boot options.[/COLOR]

There could be some problems with drivers (or too low RAM). I would try DSL which is based on a very old linux kernel, I think 2.4.

---

### Post by quadrplax on 2014-04-18
The hard drive doesn't even show up in the BIOS. In fact, it makes the  regular one not show up as well, and swapping which IDE connectors each  drive gets does nothing. Also, according to Wikipedia, slitaz is  supposed to work in 16MB of ram on one of the settings and 48MB on  another, I have 64 to work with.

---

### Post by sudodus on 2014-04-18
I can't help you with the IDE drive. It might be damaged, but let us hope it is only some mismatch in the newer computer.

Yes, but probably there is some other issue with Slitaz, for example some hardware driver. It is still worth trying some of the other really small distros,

DSL, Tiny Core, Puppy. I would guess chances are best with DSL, but of course, I don't know.

---

### Post by quadrplax on 2014-04-18
Both IDE drives work fine in their proper computers. Also, remember my problem is that I wish to clone the drive, and that means there needs to be disk imaging software like dd available on whatever distro I use.

---

### Post by sudodus on 2014-04-19
I just booted it into an old Dell with a Pentium 4 and gave it only 64 MB RAM via the boot option. I entered

```
dsl mem=64M
```

You need not do that, let it grab all RAM available!

It runs with network (internet connection), graphical desktop etc, and ***I checked that dd is available***.

I ran it from an old CD with DSL version 4.4.10 with the linux kernel 2.4. You may find some newer version via the internet, but I think all DSL versions are based on 2.4, which is good for compatibility with old hardware. At least you should be able to find a version of DSL based on linux 2.4.

So please try DSL. I think it is the best alternative in this case :-)

---

### Post by quadrplax on 2014-04-21
I booted into DSL 4.4.10 (installed with Universal USB Installer). I got to the DSL logo screen, pressed enter, and nothing happens. I could get to the boot options, and I chose "dsl dma" because I accidently did that thinking it was "dsl 2" (text mode), and it (slowly) booted into the GUI. My question is how to use dd. It's not listed in "help" and when I type it, it goes to a blank line (no "dsl@box:~$") and nothing happens. At this point, if I type anything, it repeats it to me and then presents me with another blank line. So close :( Any help?

EDIT: "help dd" works, but help isn't that helpful. How do you use "dd" (I would have posted this in Absolute beginners section, but felt I shouldn't do that since it's not Ubuntu.) to clone a hard drive. I tried what a tutorial said:
```

dd if=/dev/hda conv=sync,noerror bs=64K | gzip -c  > /mnt/sda1/hda.img.gz


```

but it didn't work. It gave the following errors:

```

dd: invalid number '64K'
bash: /mnt/sda1/hda.img.gz: Permission denied

```

Not sure if I said this, but I'm trying to make the file on the second of 2 flash drives (the first one is for booting DSL) in the PC. I'd like some n00b help :)

---

### Post by sudodus on 2014-04-22
0. Run dd **as root** or with ***sudo***

1. Check very carefully that you get the correct drive letters and partition numbers with

```
sudo fdisk -lu
sudo blkid
df

```

Try either of these commands (assuming the internal drive (the source) is hda and the target partition is sda1

As root:

*Edit*: Mount the target drive

```

mkdir /mnt/sda1
mount /dev/sda1 /mnt/sda1

```

```
dd if=/dev/hda bs=4096 | gzip  > /mnt/sda1/hda.img.gz
```

or (the following command is probably slower)

```
dd if=/dev/hda | gzip  > /mnt/sda1/hda.img.gz
```

or with sudo:

```

sudo -s
mkdir /mnt/sda1
mount /dev/sda1 /mnt/sda1
dd if=/dev/hda bs=4096 | gzip  > /mnt/sda1/hda.img.gz
sync
exit

```

or (the without the bs specifier)

```

sudo -s
dd if=/dev/hda | gzip  > /mnt/sda1/hda.img.gz
sync
exit

```

---

### Post by quadrplax on 2014-04-22
Oh, stupid me forgetting about the fdisk command. I forgot to mention that I did do it with sudo before and it didn't work. Anyway, I think I may have broke something. I tried booting again, and accidentally pressed F1 first. This made the F2 or <enter> screen go away for a second and come back. I went to F2, typed "dsl dma" and the cursor went to the next line but nothing happened. I shut down the computer (with the power button) and it froze on the DSL logo screen. Help?

EDIT: nevermind, got it to work by typing in "dsl dma" without pressing F2

---

### Post by quadrplax on 2014-04-22
Ok, I got the error:
```
bash: /dev/sdb1/hda.img.gz: Not a directory
```
Here's some information about my situation: I plugged in the DSL drive and booted into it, then I plugged in another flash drive, this one has Ubuntu installed on it (like a HDD, not a Live CD). This one is 16GB. When I do the fdisk command, it shows /dev/sda1 (the DSL drive), /dev/sdb1-3 (the partitions on the 16GB) and /dev/hda1 (the 4GB HDD). No where is anything called /mnt/, it's all /dev/

EDIT: If I go to the /mnt/ directory myself, it shows the partitions (except /dev/sdb3, Linux-swap) I tried the command again, using /mnt even though that's not what it showed, and it said
```
gzip: Write Error
```

EDIT2: I went to the /mnt/sdb1 directory in emelFM afterwards. All the partitions were showing up blank before, but now in /sdb1 there is a file "hds.img.gz" but it's only 2.28 Mbytes, and the drive I am cloning has nearly 3GB worth of data

---

### Post by mips on 2014-04-22
You can't write to /dev/sdb1/ as it's not a folder. You need to mount /dev/sdb1 and then write the image file to a folder (under the mount point) in the mounted partition.

---

### Post by sudodus on 2014-04-23
Notice the difference between

**[COLOR=#ff0000]/dev[/COLOR]/sdb1/hda.img.gz**

and the path to the target file in posts #15 and #16

**[COLOR=#0000ff]/mnt[/COLOR]/sda1/hda.img.gz**

So mount /dev/sdb1 on /mnt/sda1

I added two command in post #16 (making the directory /mnt/sda1 and the mounting command).

Please try again :-)

---

### Post by quadrplax on 2014-04-23
This may be normal, but it is showing no signs of any progress now. I  opened /mnt/sdb1 to check on it in a sudo'd emelFM. There is a  hda.img.gz file there, growing in size. What's interesting is that I  don't hear the hard drive sound I always remember hearing with this PC.  Maybe it's only a write sound? It's going rather slowly (which I'd  expect with this old hardware) Weird, the forums glitched out when I tried to post this, saying it was a duplicate in the last 5 minutes. Also, something I find funny is that the hard drive says it's Win95 lol. I'll edit this once it's done.

---

### Post by mips on 2014-04-23
Are you writing to a flash drive?

---

### Post by quadrplax on 2014-04-23
It got to 2048MB and then it said "File size limit exceeded" in the terminal. The drive is 2.7GB, so that's not the whole thing. Just making sure, the problem here is the fact that you can't have a file over 2GB in FAT32. Also, I was wondering if there was a way I can continue this process after I reformat the drive (backing up the img file of course) without having to restart it, since just this took about 3 hours.

EDIT:
> Are you writing to a flash drive?
Yes, 16GB one, and I forgot to format the windows partition to NTFS so it could hold a file over 2GB.... *facepalm*

---

### Post by sudodus on 2014-04-24
The process is slow, but I think that you will finally succeed with an NTFS file system (provided the partition is big enough for the file).

---

### Post by mips on 2014-04-24
> **quadrplax said:**
> 
EDIT:

Yes, 16GB one, and I forgot to format the windows partition to NTFS so it could hold a file over 2GB.... *facepalm*

That's gonna be slow, if the pc is usb 1.x then even slower.

---

### Post by quadrplax on 2014-04-24
The partition is 4GB, and I'm using <1GB. The drive's capacity is 4GB and 2.7GB are used. The partition is now NTFS. I bet the ports are 1.0, the computer is from 1999 and only has 2 usb ports on the back. It took roughly 3 hours to copy 2GB in the first attempt. Speed isn't a concern, this is just a one time thing anyway, and it's not like I want to be using the computer for anything else. I guess I will start the process over. I can start it in 5.5 hours from now, but I'll check first if you guys say something else, I still have the 2GB first attempt. If I don't get any posts, I'll post when it's done, probably about 8 hours from now.

---

### Post by sudodus on 2014-04-24
I would not try to append to that 2 GB file from your first attempt.

Please start the imaging process from the beginning (writing to a new file name).

Good luck :-)

---

### Post by quadrplax on 2014-04-24
Ok, starting the process over now. I get the error
```
bash: /mnt/sdb1/hda.img.gz: Read-only file system
```
I hope it's not because it is NTFS, so close... :(
I tried to mount the Ubuntu (Ext4) partition instead and it said
```
mount: wrong fs type, bad option, bad superblock on /dev/sdb2
        or too many mounted file systems
```
When I tried to mount it, which doesn't sound very helpful. I don't care which partition I get it on, I just need this image file somewhere. Help with either error?

---

### Post by quadrplax on 2014-04-24
Update: Never mind, I remounted the drive with 
```

sudo mount -o remount,rw '/media/SGTL MSCN'


```
from [http://askubuntu.com/questions/47538/how-to-make-read-only-file-system-writable](http://askubuntu.com/questions/47538/how-to-make-read-only-file-system-writable) and now it's working again. Will mark as solved if it works, will find that out in a few hours...

---

### Post by quadrplax on 2014-04-24
At the end, it said the following:
```
1056037+1 records in
1056037+1 records out
```
It  looked like it had finished fine, the file was ~2400MB (I expected it  to be about 2700) in emelFM, so I shut down the computer, Took out the  flash drive, put it into windows, and had a 0KB "hda.img.gz" file! What  happened?!? I guess I have to do this for a third attempt tomorrow then. Help?

EDIT: in Right Click --> Properties, it is 2.36GB. I'm afraid to touch it now, until you guys say something, have a feeling I'll break it. I did, however, make a backup (or 3)

EDIT2: That must have been a weird windows glitch. When I refreshed the folder it went to its actual size, but it's getting late here. I'll tell you tomorrow if I have any luck with it.

---

### Post by sudodus on 2014-04-25
I suggest that you run a live full size linux system (for example Lubuntu, Xubuntu, Ubuntu, Kubuntu) from a CD/DVD/USB drive in the computer where you have Windows, and that you copy that compressed image file to a faster drive, for example hard disk drive.

Then I suggest that you 'install alias 'flash' the system into a USB pendrive.

***Reverse the dd-gzip process***

Be very careful, so that you do not overwrite the internal drive of the computer.

Check carefully the drive letters with commands like

```
sudo parted -l
sudo fdisk -lu
sudo blkid
df
```

Select **x** in the following command line depending on the output of the commands above.

```

sudo -s
zcat hda.img.gz | dd bs=4096  of=/dev/sd**x**
sync
exit

```

***Safer alternative***

or use ***mkusb*** to decrease the risk with dd. See the following link

[Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

In the directory, where you have hda.img.gz and mkusb, run the command

```
sudo ./mkusb hda.img.gz
```

and it will help you identify and select the target drive, where you want to expand the system from the very old computer.

---

### Post by quadrplax on 2014-04-25
That was just a weird thing where it said 0KB. I see no need to use Linux on my main PC, I'm using 7-zip. Copying the file around on my main PC only takes about one minute across USB 2.0 ports, the initial 6 hour copying time is probably because of how old the hard drive and USB ports are on the old PC. I have the file on the flash drive, my solid state drive, and my backup hard drive, and I got it in all of those places in well under 5 minutes. I am currently using remote desktop, and ran out of SSD disk space. When I get home, I will plug in my external drive and copy files to there. That will be about 5 hours from now. Then I'll extract the img and mount it (with gizmo) to see if it will work fine. If so, I'll follow the Migrate Windows tutorial. Otherwise, I'll keep you posted.

---

### Post by sudodus on 2014-04-25
I think you have succeeded now :-)

Anyway, when you are sure, please click on **Thread Tools** at the top of the page and mark this thread as **solved**

---

### Post by WoodenWalker on 2014-04-25
Have you tried looking into SystemRecoveryCD. I'm not sure what's required to run it, but it should be pretty lightweight.... It comes with DD on it, which is a great lightweight way to move data. May take a little while....but it will get the job done and use relatively low resources. That's what I use at work.

---

### Post by sudodus on 2014-04-25
How light is SystemRecoveryCD? I mean what is the RAM limit for it to boot and run for example dd? Will it work in a computer with only 64 MB?

---

### Post by quadrplax on 2014-04-25
I extracted the drive, it totaled 4.02GB, I'm guessing the .02 are the MBR and stuff, as the whole drive showed up as 4GB in Win98. Interesting thet the img file stores all the unused space on the drive too. Anyway, when I tried to mount it via Gizmo, it gave this error:
```
The image "hda.img" does not appear to be formatted yet.
Would you like to format it now?
```
If I chose no, windows says: 
```
You need to format the disk in drive I: 
before you can use it.
Do you want to format it?
```
If I choose cancel: 
```
I:\ is not accessible.

The volume does not contain a recognized file system.
Please make sure that all required file system drivers are loaded and the volume is not
corrupted.
```
The drive shows up in the Hard Disk Drives catagory. It is "Locak Disk (I:)" and does not have the total space information. I made some copies of the file for some tests.

Test #1: I accept when Windows asks to format the drive
Result: It gives me the default formatting menu (deja vu from when I reformatted flash drive to NTFS xD), which wipes the drive.

Test #2: I accept when Gizmo asks to format the drive
Result: It formats automatically, and quickly, and results in an empty drive.

The next thing I'm going to do is use Ubuntu on my testing laptop (the one in my sig) to do what sudodus suggested in post #31. I encountered a problem that Ubuntu refuses to mount the NTFS partition. Beacuse of this, I tried to boot up DSL and copy the file from the NTFS partition to the Ext4 one, but then I remembered that I can't mount the Ext4 partition there. So, in DSL I can't use Ext4 in DSL/Win7, but I can't use NTFS in Ubuntu. Great. Help?

Edit: Tried Ext2Fsd, doesn't show any partitions other than the ones Windows already sees.

---

### Post by sudodus on 2014-04-26
If the NTFS partition is clean, it should be possible to mount from Ubuntu. Try in Windows to run

```
chkdsk /f i:
```

and after that Ubuntu should be able to mount it, at least manually.

-----
**Edit**: Check which drive you want to mount with parted

```
sudo parted -l
```
-----

Let us say that the internal drive is /dev/sda, the Ubuntu boot drive is /dev/sdb and this one is /dev/sdc (the clone of the  really (really) old desktop computer, a Packard Bell 945).

```
sudo mount /dev/sdc1 /mnt
```

if the Windows partition is not the first one, try to mount the second partition ...

```
sudo mount /dev/sdc2 /mnt
```

and browse to **/mnt** to find the directories and files that you want.

---

### Post by quadrplax on 2014-04-26
The Windows command worked, and I can now open the NTFS partition. I got  an error when I tried to mount the NTFS partition, saying it was  already mounted, and If I unmounted it from the file explorer, it  disappears and can't be remounted. Luckily, I don't have this problem  with my external NTFS HDD, so now I'm using that instead. I put the  "of=" in the Ubuntu partition of my second Ubuntu flash drive (see sig).  It appears to have wiped that drive...would have been good to know it  does that...guess I'm going to be reinstalling Ubuntu today...Anyways,  good thing I didn't put in on external hdd like I was planning to.  Nothing lost, just a pain to reinstall. Right now I'm waiting for the  command. I can't find signs of progress anywhere.

---

### Post by sudodus on 2014-04-26
See ```
man dd
```

```
       Sending a USR1 signal to a running `dd' process makes it print I/O statistics to standard error
       and then resume copying.

              $ dd if=/dev/zero of=/dev/null& pid=$!
              $ kill -USR1 $pid; sleep 1; kill $pid

              18335302+0  records  in
              18335302+0  records out
              9387674624  bytes (9.4 GB) copied, 34.6279 seconds, 271 MB/s

```

If you did not add '& pid=$!' to the command line, you can instead run (from another terminal window)

```
ps -A|grep dd
    2 ?        00:00:00 kthreadd
 1770 ?        00:00:00 winbindd
 1776 ?        00:00:00 winbindd
 3207 ?        00:00:00 e-addressbook-f
 8732 ?        00:00:00 dd

```
identify the process ID number of dd (*not* kthreadd ...)
in this example 8732

 and run the command

```
sudo kill -USR1 8732
```

to get three lines of output telling you how far it has proceeded.

---

### Post by quadrplax on 2014-04-26
Ok, it finished (much faster than than the original copy lol) and oddly, the "10 GB FILE SYSTEM" aka the Ubuntu partition moved from devices to Computer and appears empty. I'm going to reboot now, see if that does something. It is now called "10 GB Unrecognized". Ok, I rebooted, and now there isn't a 10 GB anything showing up, just the windows partition on it. From fdisk -lu, it shows up fine, in fact the only difference between the Linux partitions on each drive is that one is sdc2 and the other is sdb2. I'll run some more commands to see if there are any problems. Aha, parted -l shows that the one I copied the img to has no file system, where as the one I booted to just now shows up fine as Ext4. blkid confirms this, completely skipping over /dev/sdc2. Next thing I will try is attempt to boot this potentially corrupted drive. That results in:

```

error: unknown filesystem.
grub rescue> _

```

I'd like to know if there's anything I should do before re-install. If I do re-install, I'll assign a larger Windows partition, but it will probably still wipe the drive...help?

---

### Post by quadrplax on 2014-04-26
Sorry, I'm nooby, I don't understand post #39, could you only put the commands to run in the code boxes? That confuses me...

---

### Post by sudodus on 2014-04-26
```
ps -A|grep dd
```

identify the process ID number of dd
in this example 8732 (in your real life something else)

 and run the command

```
sudo kill -USR1 8732
```

to get three lines of output telling you how far it has proceeded.

*Edit*: But it is only meaningful, while dd is running

---

### Post by sudodus on 2014-04-26
Please explain what you want to do with the system that you extracted from the compressed dd image!

I thought that you wanted to recover some personal files, maybe documents and photos. In that case, boot a live Ubuntu system and mount the partition, that you think contains the files.

If it is a Windows system, you cannot expect that it will boot and run in another computer. Microsoft has made that impossible.

But maybe you want to do something else. It will be easier to help if you tell us what you want to do.

---

### Post by quadrplax on 2014-04-26
[https://www.virtualbox.org/wiki/Migrate_Windows](https://www.virtualbox.org/wiki/Migrate_Windows)
I want this for two reasons:
1. There are 4 or 5 nice old games and stuff on there you have to buy that I don't have the CD of
2. I have a 64-bit OS and would like to be able to run some 16-bit applications

---

### Post by sudodus on 2014-04-26
From that link:
> 
Disclaimer: Migration of Windows guests from a physical host  into a VirtualBox VM is not supported. These instructions are provided  as-is in the hope that they are helpful.

I think it is very difficult to migrate Windows installed directly into a computer into a VirtualBox system. Possible, yes, but extremely advanced, because you must make the virtual machine 'look like' the real computer.

---

### Post by quadrplax on 2014-04-26
It provides step-by-step instructions. If there is some other way you know for me to be able to do this (use 16-bit applications and the software and the software on the PC) that would work too.

---

### Post by sudodus on 2014-04-26
See these links, which describe something similar to what you want to do

[Windows OEM disk loaded on VirtualBox]("http://ubuntuforums.org/showthread.php?t=2119831&highlight=curbie")
[Backing up OS, programs, and system settings]("http://ubuntuforums.org/showthread.php?t=2119527&highlight=curbie")
[Starting a used secondary hard drive]("http://ubuntuforums.org/showthread.php?t=2118357&highlight=curbie")
[Newbie Xp and Ubuntu questions]("http://ubuntuforums.org/showthread.php?t=2114414&highlight=curbie")

---

### Post by quadrplax on 2014-04-26
I don't own any unused copies of Windows, I tried using the reinstillation disk of XP and the product key said it was invalid. The only PC in my entire house I was the OEM of and have an OEM disk for is this one, Windows 7 _64-bit_

---

### Post by sudodus on 2014-04-27
It is possible, but I think quite difficult. I hope you can get help from some people who have migrated Windows guests from a physical host  into a VirtualBox VM (I haven't done it). Maybe it would help to start ***a new thread with a good descriptive title to attract those interested and capable ***of helping you.

Good luck :-)

---

### Post by quadrplax on 2014-04-27
Ok, well I don't feel like messing with this idea for another month or so right now, so I'll mark this thread as solved, and maybe I'll start another topic some time in the future.

---

