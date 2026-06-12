---
title: "Problems with Dual Boot on two Hard Drives"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by Village on 2007-01-26
Hi there, 

For a while now I've been trying to fully set up my computer to run both Ubuntu and Windows. I have them on two separate hard drives and I have followed the instructions from [http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902) . I have a dell Dimension 4550, this is where my problems start. 

My set up is;
Ubuntu on hdd1
Windows on hdd2 (I believe that the Dimension 4550 automatically partitions  this with a  Dell Service partition at first, see post linked above)

If I set my BIOS to OFF for the Primary IDE controller then I go strait to GRUB. If however I change it to Auto then I get this message;
> 
Primary Had disk drive 1 not found

strike the F1 key to continue, F2 to run the setup utility

I hit F1 or it makes it to GRUB on its own if I select Windows I get the following message;

> Error 21: Selected disk does not exist message
 
This is my sudo fdisk -l ;
> 
Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       23944   192330148+  83  Linux
/dev/hda2           23945       24321     3028252+   5  Extended
/dev/hda5           23945       24321     3028221   82  Linux swap / Solaris
alex@alex-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=8601ca78-c262-4017-b686-39f49c8d933d /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=6ba7751a-3ff5-41f6-8223-9dc22cc1c196 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
alex@alex-desktop:~$ 

I'm stuck, I've been trying for about a month now to get this set up (been a bit busy so its proablly been several hours actuall effort)

I'm trying to use Ubuntu as my day OS and Windows for games. 

Any advice most welcome.

Village

---

### Post by ieee488 on 2007-01-26
Is not installing Grub to MBR that important to you?  Because that linked thread is about doing that.

For regular dualbooting you can just leave Windows XP in HDD1.

---

### Post by Sef on 2007-01-26
I don't see your Windows partition at all.

Open the terminal (Applications > Accessories > Terminal) and type this command:

```
sudo fdisk -l
```

Then post it here.

---

### Post by geek_Man on 2007-01-26
I finally gave up trying to get GRUB to work on my other drive, so I just installed it to the first one and it works fine.

---

### Post by Village on 2007-01-28
Here's my sudo fdisk -l

> Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       23944   192330148+  83  Linux
/dev/hda2           23945       24321     3028252+   5  Extended
/dev/hda5           23945       24321     3028221   82  Linux swap / Solaris
alex@alex-desktop:~$ 
alex@alex-desktop:~$ 
alex@alex-desktop:~$ 


I'm trying to keep both OS's separate, but if you think changing the MBR would fix it then I'm all ears.

Both OS's are on different Drives and I followed the instructions by unplugging each of the drives during their individual installation. 

Village

---

### Post by ieee488 on 2007-01-28
What that output is saying is that there is only one hard drive in your system, and it has the Linux.

The second hard drive is not showing up at all.

---

### Post by Village on 2007-01-28
Is there someway that I can get it to see the second hard drive? Do I need to edit a file somewhere?

Thanks for the diagnosis. 

Village

---

### Post by geek_Man on 2007-01-28
Download the Super GRUB Disk and burn it to disc. Then you should try installing GRUB to the first hard drive. And if it doesn't work out, then fix it with SGD. I was trying to keep the two OS's completely seperate too, but then I just decided to put GRUB on the first drive and I've no regrets.

---

### Post by Village on 2007-01-29
> **geek_Man said:**
> Download the Super GRUB Disk and burn it to disc. Then you should try installing GRUB to the first hard drive. And if it doesn't work out, then fix it with SGD. I was trying to keep the two OS's completely seperate too, but then I just decided to put **GRUB on the first drive** and I've no regrets.

Put GRUB on the first drive? Just so I have this 100% right; I currently have Linux and therefore GRUB on HDD1 and on HDD2 I have a completely clean windows. 

Do I need to download and install this Super GRUB on my Linux drive? or on my Windows, Does Super GRUB have a few more options?

Also do you know a good howto for it?

Thanks

Village

---

### Post by geek_Man on 2007-01-29
Yeah, put GRUB on the the first drive to boot. What was the thing about "I currently have Linux and therefore GRUB on HDD1 on HDD2"? Y'know, just so that we're clear. Download SGD with whatever you're using, Ubuntu or Windows. Super GRUB Disk can install GRUB, fix GRUB, restore your Master Boot Record, install Lilo (but that's in beta), boot Linux directly (without GRUB), boot Windows, and I'm sure the list goes on. A good webgsite to go to is [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/). You can download it there and I'm sure it's got info. A good place to go to is [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm) for info on GRUB. Good page to look at. Good luck, hope this helped!

---

### Post by Village on 2007-01-29
Sorry it was a typo. Edited now.

What I mean is Ubuntu is on HDD1 (with GRUB, I presume by default) and Windows is on HDD2. 

Is there a way to edit my current install of GRUB without needed to go down the super GRUB route?

I can if I have to, but I'm sure there must be a way of just informing GRUB and BIOS that there's a second HDD and to start that one up when necessary. 

Village

---

### Post by geek_Man on 2007-01-29
Yeah, you can change without SGD. What did you want to do?

---

### Post by Village on 2007-01-29
What ever is easiest, and I suppose that would be use the current GRUB on my Ubuntu HDD.

I guess I need to edit it somehow, and put the right stuff in it to make it realise that the 2nd HDD does exist. 

Do you think this will also solve the problem of having to hit F1 at boot up (see first post).

Thanks for your help on this so far, I really mean that!

Village

---

### Post by geek_Man on 2007-01-29
One question, can you boot into Windows? And if you can, how? I just realized that no one helped you out with getting your other drive to show up. Can you access it from within Ubuntu? As soon as we sort this out I'll show you how to get GRUB squered away. BTW, you're quite welcome! I love to be able to help.

---

### Post by Village on 2007-01-30
I can boot into Windows, but only if I take my Linux drive out and put the Windows Drive into HDD1 (From being in HDD2). 
Right now if I try to select Windows on the GRUB list I get a message saying;

> Error 21: Disk does not exist

or something like that.

Anyway to help here's my Menu.lst

> 
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		1

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

title              Windows XP
root               (hd1,1)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=8601ca78-c262-4017-b686-39f49c8d933d ro
# kopt_2_6=root=/dev/hda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


---

### Post by geek_Man on 2007-01-30
Hmm, like you literally have to disconnect your Linux drive or just swap there places in the bios? And is that all of your menu.lst file?

---

### Post by Village on 2007-01-30
Open the box, take drives out and swap them around. 

Also that should be all of the menu.lst

---

### Post by geek_Man on 2007-01-30
Sorry I'm asking all these stupid questions, but can you put both drives in and boot from your Linux drive?

---

### Post by Village on 2007-01-30
There's no such thing as a silly question;

I can have both Drives wired in, (Linux on HDD1 and Windows on HDD2) and then it will boot to Linux, but can not get to Windows.

Or I can take the drives out and put Windows in HDD1 and it will boot to Windows.

---

### Post by geek_Man on 2007-01-30
Okay, open up your menu.lst file and add the following to the very bottom: ```

title   Windows
root   (hd1,0)
makeactive
chainloader +1
```

I don't know if that will work right away, but give it a try. You can try changing the part where it says "root (hd1,0)" to something else if it doesn't work. Basically, in "root (hdx,y)" x is the hard drive and y is the partition. GRUB starts counting at zero, so hd1,0 is the second hard drive and the first partition. The hard drive in the above code should be right, but I don't know for sure about the partition. But give that a try.

---

### Post by Village on 2007-01-30
Sorry that didn't work. I just put it in at the very end, after

> ### END DEBIAN AUTOMAGIC KERNELS LIST

I had it set up as root (hd1,1) because of something I read in an earlier thread. (see first post)

---

### Post by geek_Man on 2007-01-30
Okay, what error did you get? Another thing, put a couple newlines in between the "### END DEBIAN AUTOMAGIC KERNELS LIST" and the Windows part.

---

### Post by geek_Man on 2007-01-30
Oh yeah, did you add the ```
map                (hd0) (hd1)
map                (hd1) (hd0)
``` in between the makeactive and chainloader part?

---

### Post by Village on 2007-01-30
Ok it now looks like this:

> 

### END DEBIAN AUTOMAGIC KERNELS LIST


title   Windows
root   (hd1,0)
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader +1


Im jjust about to try a restart. Previously it still came up with Error 21, and it still wanted me to press F1

---

### Post by geek_Man on 2007-01-30
And you have both drives in right?

---

### Post by Village on 2007-01-30
After Re-start I still had the same problem, as before.

Still had to press F1 and it still came up with 

> Error 21: Selected Disk does not Exist

But it will load Linux as before

---

### Post by Village on 2007-01-30
Yes Both drives are plugged in. 

HDD1 - Linux
HDD2 - Windows

---

### Post by ur2good on 2007-01-30
I am a total newbie...but I did what you are trying to do without problems...but I did it differently.  I had windows XP on HDD1, and was using a second drive (HDD2) as a slave to backup stuff on the main drive.  Using the Ubuntu disc received through the mail from from Ubuntu (Dapper Dan), I placed the cd into the player and started the machine...the process asked me where, what, and when...there were no problems.  I now can boot from either drive depending on which system I want to use.  Therefore, my suggestion would be to make sure the your boot sequence in the CMOS is CD-Rom before HDD...switch your drives so that windows is HDD 1 and make your linux HDD2...be sure to check the pin configuration on the HDD to let them be primary and slave.  Hope this helps

---

### Post by ieee488 on 2007-01-30
Ur2good,

That's the way I have my system set up too.

But the OP is wanting to do it differently. If you go to the thread linked in his first post, you'll see what he is trying to do.

---

### Post by ur2good on 2007-01-30
iee438....what I got from the thread is that what he wants is for the HDDs to each have one system...and for it to work...I have always felt that if what you are doing doesn't work, you should try what does work (unless you just like beating your head against the wall).  I was reluctant to try to help because I really know nothing of the command line stuff that these guys are talking about...but I thought I would offer, because that is what I would like someone to do (help me make it work)...sorry if I intruded

---

### Post by Vox754 on 2007-01-30
This is your problem:
[QUOTE="Village"]Both OS's are on different Drives and I followed the instructions **by unplugging each of the drives during their individual installation**.[/QUOTE]

I can understand why you did this: you wanted to keep your systems as separated as possible.
However, that may not be the best solution.
When you install Ubuntu it automatically detects your disks, and writes the appropriate "fstab" file, allowing you to mount them without much trouble.
This is easy in Ubuntu because it was developed as a friendly distribution; the same cannot be said of Windows.

For the next time you decide to make a dual boot, people usually mention:
1. Install Windows first.
2. Windows is proprietary so it attempts to gain control of your computer by all means necessary, like it was the only OS; therefore...
3. Install Windows in the first disk, in the first IDE channel, and as master. This may be satisfy Windows.
4. Once you have pleased Windows and it is working right, then go for the humble Ubuntu.
5. Install Ubuntu in the second disk. Do not unplug any other disk while installing. Let the wise Ubuntu recognize all your hardware and write the appropriate configuration files.
6. You should have a working dual-boot system.

Sorry I can't give you any more help.

---

### Post by torgrot on 2007-01-30
I also have the Dimension 4550.  I have a few questions, when you added the second hard drive did you set the jumpers on it to cable select?  Prior to starting the Ubuntu installation were you ever able to see the second drive from Windows?  Dell uses cable select for their drives.  If you didn't replace the Dell cable then you will need to set the jumpers on both drives to cable select.  The last drive on the cable will be your primary and the drive connected to the middle connector will be the slave.  

When I added my second drive, I set the jumper to slave and it took me several days to finally figure out what I had done wrong.


George Grote

---

### Post by Village on 2007-01-30
Vox745:
I was trying to follow an earlier thread (see here: [http://ubuntuforums.org/showthread.php?t=179902)](http://ubuntuforums.org/showthread.php?t=179902)).

Torgrot: 
Both drives are set to Cable Select. The Linux drive was purchased separately, the other (smaller Windows Drive) came with the Computer.


Does anyone know a way to fix this little problem without havening erase Ubuntu (and more importantly the files I have on the computer)?

Thanks

---

### Post by torgrot on 2007-01-30
After you have the jumpers set correctly, connect the Ubuntu hard drive to the connector on the end of the cable and the window drive to the connector in the middle of the cable. 

Go into the BIOS and set both drives to AUTO.  Save your settings and boot. I can't stress enough that both drives need to be set to AUTO, if they are set to enabled the drive geometry is stored in the BIOS and it will be incorrect when you move the drives on the cable.

Boot Ubuntu and try sudo fdisk -l again and see if both drives are not listed.

I am not home at present so I can't post what mine looks like  but as I recall I have two partions on the windows drive, one of those being the utility partion that Dell installs and the other is the Windows partion which should show up as being ntfs.

If both drive are shown shut down and attempt to boot Windows.

---

### Post by Village on 2007-01-30
Both drives are set to Auto, here's what it looks like:

> 
Primary Drive 0 - Hard Drive
Primary Drive 1 - Unknow Device
Secondary Drive 0 - CD-Rom Reader
Secondary Drive 1 - CD-Rom Reader


I have two DVD drives, no CD, but I guess this is just BIOS. 

Like I said in an earlier post, I used to have this set up and working with 2 drives, Linux and Windows, Linux in HDD1, Windows in HDD2. 

Its after the necessary re-installation that the fun started.

Village

---

### Post by torgrot on 2007-01-30
Your BIOS still doesn't recognize the drive on the middle connector of the cable.  This really looks like either the cable on the drive is not connected properly or the jumper is not set correctly.  I have essentially the same setup and it works flawlessly.  That the BIOS doesn't recognize the drive is what leads me to believe that it is a hardware problem.   I know you have done this a thousand times already, but please open the case take out the drives and verify that the jumper are set correctly and the cable are connected properly.

---

### Post by ieee488 on 2007-01-30
> **ur2good said:**
> iee438....what I got from the thread is that what he wants is for the HDDs to each have one system...and for it to work...I have always felt that if what you are doing doesn't work, you should try what does work (unless you just like beating your head against the wall).  I was reluctant to try to help because I really know nothing of the command line stuff that these guys are talking about...but I thought I would offer, because that is what I would like someone to do (help me make it work)...sorry if I intruded

Sorry. I didn't mean to be critical.

I just thought that since the OP is choosing to do it this way he must have a reason for doing so.

I absolutely agree with you that I would do it the more traditional way which is to install GRUB in Windows.  :D   It works wonderfully.

---

