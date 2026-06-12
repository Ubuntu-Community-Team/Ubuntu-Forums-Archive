---
title: "Anyone good with GRUB?"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by ithuwakaga on 2007-05-07
Hi,

I have 3 hard drives, one with Ubuntu (/sda) on it, one with Windows (/sdb), and one with Debian (/sdc).  I recently installed Debian, and I want to boot into it from the GRUB in the Ubuntu HD.  My line looks like this;

```
title           Debian GNU/Linux, kernel 2.6.18-4-686
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.18-4-686 root=/dev/sdc1 ro
initrd          /boot/initrd.img-2.6.18-4-686
savedefault
```

I've set up my device.map to make /dev/sdc1 as (hd2,0), but my problem is that I get an error that says "/bin/sh: can't access tty; job control turned off" and I'm given a command prompt.

Any ideas?

---

### Post by Bachstelze on 2007-05-07
Try with hdc instead of sdc.

---

### Post by ithuwakaga on 2007-05-07
I'm using all SATA hard drives instead of IDE, isn't hdc strictly for IDE?

---

### Post by Bachstelze on 2007-05-07
Then I think the best thing to do would be to install a GRUB for Debian on the boot sector of it's partition and then chainload it from your "main" GRUB. Where did you install grub during Debian's installation anyway ?

---

### Post by freebird54 on 2007-05-07
Did you get the lines from the Debian install's menu.lst?  Just wondering...

When I went to a triple boot, I used the configfile option to pass control over to the 'other' installation - as it also means that changes in the 'other' install are reflected properly in the grub entries without manual intervention.  Here's what my "extra' entry looks like..
```

title           Ubuntu Feisty Test System
savedefault
configfile      (hd1,5)/boot/grub/menu.lst
 
```

This might be a good answer for your setup too?  (with minor changes for actual drive/partition of course)  It also allows Debian's 'automagical' changes to /boot/grb/menu.lst to happen as required.

Hope this helps!

---

### Post by ithuwakaga on 2007-05-07
Well what I did is I installed Debian alone (I took out the other hard drives), copied Debian's menu.lst file exactly into my Ubuntu GRUB's installation, changing everything that said "sda" into "sdc" and "(hd0,0)" into "(hd2,0) (After I modded the device.map file in Ubuntu too)".

I'm a complete noob when it comes to triple boot.  Was there something wrong in that process?

---

### Post by freebird54 on 2007-05-07
Well - perhaps - but not much.  I still think that the configfile option is by far the easiest/simplest/most compatible with what you did.

The problem came from Debian not knowing about the other systems, and your other systems not knowing about Debian.  However - they do not NEED to know with the configfile method - it will just hand control over to the 'standalone' Debian install to boot itself - which it should know how to do :)

I have done that (had only the relevant drive hooked up) before, and it DOES prevent most problems - so go for it!

---

### Post by ithuwakaga on 2007-05-07
That actually makes a lot of sense.  I think I have one more question and I'll give this a try;

In the codeline "configfile (hd1,5)/boot/grub/menu.lst", is it referring to the menu.lst in the GRUB that you're booting from?  Or the GRUB on that particular hard disk?

So what I'm really asking is if my Debian line should be "configfile (hd0,0)/boot/grub/menu.lst" or "configfile (hd2,0)/boot/grub/menu.lst"

---

### Post by tchoklat on 2007-05-07
it refers to the location of the menu.lst in the distro you are trying to boot!

---

### Post by ithuwakaga on 2007-05-08
It kinda works.  It starts booting into Debian, but in the end it displays a "/bin/sh: can't access tty: job control tunned off".  A google search displays very little helpful results (or none that I can really understand... =o).

Any thoughts?

---

### Post by confused57 on 2007-05-08
You might want to boot into Ubuntu, open a terminal, post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

What's in your device.map in Ubuntu:
```
gedit /boot/grub/device.map
```

You might want to mount your Debian install from Ubuntu(or from a live cd):
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

which would be something like this:
```
sudo mkdir /media/debian
sudo mount -t ext3 /dev/sdc1 /media/debian
```
then you might want to see what your menu.lst looks like in debian:
```
gedit /media/debian/boot/grub/menu.lst
```
and maybe your /etc/fstab:
```
gedit /media/debian/etc/fstab
```

---

### Post by ithuwakaga on 2007-05-08
The results of fstab -l is

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19079   153252036   83  Linux
/dev/sda2           19080       19457     3036285    5  Extended
/dev/sda5           19080       19457     3036253+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        8510    68356543+  83  Linux

```

Sdc1 is the Debian drive, and when I formatted it I used the linux swap file in sda.  I'm pretty sure that isn't the problem though.

Device.map is fine, I configured that to what seems viable to me.

```
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)   /dev/sdc
```

Here's what my menu.lst file looks like in Debian.

```
## ## End Default Options ##

title		Debian GNU/Linux, kernel 2.6.18-4-686
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.18-4-686 root=/dev/sdc1 ro 
initrd		/boot/initrd.img-2.6.18-4-686
savedefault

title		Debian GNU/Linux, kernel 2.6.18-4-686 (single-user mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.18-4-686 root=/dev/sdc1 ro single
initrd		/boot/initrd.img-2.6.18-4-686
savedefault

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu, kernel 2.6.20-15-386 (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-386 root=UUID=5b44d672-455e-4907-9958-eabd15c170cb ro quiet splash 
initrd		/boot/initrd.img-2.6.20-15-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu, kernel 2.6.20-15-386 (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-386 root=UUID=5b44d672-455e-4907-9958-eabd15c170cb ro single 
initrd		/boot/initrd.img-2.6.20-15-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot
```

And lastly, my fstab file in the Debian distro.

```
proc            /proc           proc    defaults        0       0
/dev/sdc1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

Note: I have already mounted /dev/sdc on /mnt/Debian.  I'm not totally sure if that will affect anything, but I could be wrong.

---

### Post by confused57 on 2007-05-08
I don't see anything wrong with your configuration files for Debian not to boot.  You might want to read over Herman's tutorial for booting multiple linux distros:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

I always use the chainloader method to boot multiple distros, but I'm not sure that will work, since configfile didn't.
If you want to try it you could use the live cd to install Debian's grub to the root partition:
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

running "find /boot/grub/stage1" should return "root (hd0,0)" and "root (hd2,0)"...to set up Debian's grub on the root partition:
root (hd2,0)
setup (hd2,0)

then you'd need an entry similar to this to boot Debian:
```
title   Debian
rootnoverify (hd2,0)
chainloader +1
```

First, you might want to read through the symlink method of booting other distros, especially investigating your other Linux OS.

Another possiblity is to download the Super Grub Disk(5-7 Mb download):
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
you may want to do this before trying anything else, just to see if it can boot your Debian partition.

Sorry I can't give you something specific to try, but hopefully one of these methods will work...all the links I've given you are from Herman's website, he's probably one of the most grub knowledgable people on the forum.

---

### Post by freebird54 on 2007-05-08
That does not look as if it were setup on the 'only visible' drive!  Not saying that there is a problem with that - in fact it all looks quite correct.  I am left with a suspicion that someting was incomplete with the Debian install- but am not sufficiently conversant with Debian usage to tell what it may be.  (trying to get Debian installed successfully is the reason I'm  on Ubuntu!)

Have you anything to lose by trying a re-install of Debian?  Have you double-checked the CD for integrity/bad burn etc?

---

### Post by ithuwakaga on 2007-05-08
Alright thank you.  I'll look into it tomorrow and tell you how it goes.

Edit: I've actually reinstalled Debian several times to no avail.  It boots fine when I set the Hard Drive alone, so it can't be Debian.

---

### Post by freebird54 on 2007-05-08
> I've actually reinstalled Debian several times to no avail. It boots fine when I set the Hard Drive alone, so it can't be Debian.

Verry strange.  How does it find a swap partition when there is no other drive? Anyway - I would then guess that when Debian gets booted, that *IT* must see the drives in a different order than Ubuntu does when it boots.  Have you tried specifying UUID for the drives rather than the 'standard' references?  That could clear up the confusion for you...

I attach an example below

```

title        Ubuntu, kernel 2.6.20-15-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=fe7bf845-7ce9-4733-b6de-f70f2b62076d ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault
```

I wouldn't think that Debian would have any trouble with the UUID option.

---

### Post by ithuwakaga on 2007-05-08
Oops, I forgot to mention that when I booted Debian alone, that was the time when I had installed the swap file on that hard drive as well.  When I reinstalled it with the hard drives attached, it allowed the default to use the swap file on sda.  So I don't think that's the problem, since both times (with Debian as sdc) they came out with the same results.

Also, I've never heard of chainloading until just now.  What is it exactly?

---

### Post by freebird54 on 2007-05-08
Basically it is passing the baton to the next bootloader in line!  Most often Linux users will see it in the Windows dual boot scenario - when control must be passed to the Windows bootloader (say NTLDR for XP, for example) for it to successfully fire up.  This will also work for any other valid bootloading system - it is just a 'hand-off' to the next loader...

---

### Post by ithuwakaga on 2007-05-08
Here's an interesting find... it seems that just recently my latest Debian reinstall put in it's OWN GRUB version, and right now I'm using that.

This hasn't caused any major complications, but I need to resolve it to continue.  Anyone know how to make /sda's GRUB the boot manager rather than /sdc's?

---

### Post by freebird54 on 2007-05-08
I suspect that the re-install of Debian wrote its grub on sda last time, and that is why it is in use.  What ever drive is seen first will get the first shot at control!  Overall, it should not matter much who put it there - just ensure that the right set of drives in the right order are there when it goes in!  Have you tried the UUID method of drive designation yet?  Or have the problems been solved now?

I attach a link to a 'Grub resource' that might help you see the system as grub sees it - (hint - try the null command).

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by ithuwakaga on 2007-05-08
Ok, so I tried something a little different, which I think produced more helpful results (the light is at the end of the tunnel, yay!).

This is the code I put into my /boot/grub/menu.lst

```
title        Debian
root         (hd2,0)
kernel       /vmlinuz root=/dev/sdc1 ro quiet splash
initrd       /initrd.img
savedefault
```

The nice thing is it changes the resolution to what Debian uses.  But it gives these lines of code...

```
(Shows the above code)
Ok, booting the kernel...
kinit: name_to_dev_t (/dev/sda5) = sda5(8,5)
kinit: trying to resume from /dev/sda5
kinit: no resume image, doing normal boot...
mount: mounting /dev/sdc1 on /root failed: no such device
mount: mounting /root/dev on /dev/.static/dev failed: no such file or directory
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /proc on /root/proc failed: no such file or directory
target filesystem doesn't have /sbin/init

(Talks about BusyBox, I forgot to write this part down.)

/bin/sh: can't access tty; job control turned off
```

All my drives are set up the way I need them to be.  Plus, the GRUB problem (that I spoke of earlier) I fixed in the GRUB command prompt just by reinstalling it, so it's doing exactly what I want it to do.

---

### Post by freebird54 on 2007-05-08
Try escape'ing from grub, and do the null command (and hit <tab>) which should show you what the drives 'look like' to the system at that time.  It does not appear to think that sdc1 exists - or that it has another designation.  It can't run if it can't find it's files!
Here's a more detailed link (from the same pages) on how to operate Grub from its own command line..  [http://users.bigpond.net.au/hermanzone/p15.htm#How_to_get_GRUBs_Command_Line_to_investigate_a_computer](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_get_GRUBs_Command_Line_to_investigate_a_computer)

This section of the link should give you info you need to resolve the 'missing drive' problem...

---

### Post by confused57 on 2007-05-08
It probably won't make a difference, but I noticed your bootflag on sdc1 wasn't "on", or didn't appear to be.
I believe you can turn the bootflag on, using the gparted live cd:
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

You might be able to do so, using gparted on the Ubuntu live cd?

---

### Post by ithuwakaga on 2007-05-09
GRUB sees the hard drive, I did a grub>  find /vmlinuz and it showed both (hd0) and (hd2) as Linux kernels, which is correct.

Honestly, I'm kind of stumped.  This should be WAY easier than it has been, but unfortunately it kinda isn't.  I suppose if you had any other ideas, feel free to share them.  Neither I nor Google really has a clear answer.

Sorry.

---

### Post by freebird54 on 2007-05-10
Did you try it with UUID's yet?  If you aren't familiar with generating them, try

```
sudo vol_id -u /dev/sdc1
```

then pick up the result and paste it into grub as shown in my earlier post (root= etc)

This is best remaining possibility I know of right now....

You are right - it is NOT supposed to be difficult, and usually isn't!  Something got misidentified in there somewhere...

---

### Post by ithuwakaga on 2007-05-11
I'm starting to believe it's the hard drive that shows the problem.  I know that it had a problem with the MBR but I thought it went away when I installed GRUB onto it.

Anyway, I'm thinking I'll just reinstall Debian in a partition on my working hard drive.  Hopefully that'll eliminate the problem altogether.  Thank you so much Freebird and Confused, I'm really glad there are people as helpful as you two on the forums.

---

