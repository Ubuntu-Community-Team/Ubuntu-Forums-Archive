---
title: "Vista + Ubuntu then reinstall Vista ==&gt; Ubuntu won't boot"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by duydaniel on 2007-08-08
Hi all

I had Ubuntu and Vista dual boot before. Then a file in Vista seems to have some error so I decided to reinstall Vista. BADLY, after reinstall, the boot loader seems not working any more. The computer boot directly to Vista...

I really don't want to reinstall Ubuntu since I have set up everything nicely. Please help. :confused:

---

### Post by Al3xK3aton on 2007-08-08
Use Vista's System Restore to go back to the way it was before.

---

### Post by overdrank on 2007-08-08
> **duydaniel said:**
> Hi all

I had Ubuntu and Vista dual boot before. Then a file in Vista seems to have some error so I decided to reinstall Vista. BADLY, after reinstall, the boot loader seems not working any more. The computer boot directly to Vista...

I really don't want to reinstall Ubuntu since I have set up everything nicely. Please help. :confused:

Hi and yes windows writes the mbr and ubuntu will not be seen. this link will help you reinstall the grub. 
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by duydaniel on 2007-08-08
> **Al3xK3aton said:**
> Use Vista's System Restore to go back to the way it was before.

Thanks for that, but I am afraid that I have reinstalled Vista. I don't know if the so-called system restore can do anything.

I will try this when I am home> 
Hi and yes windows writes the mbr and ubuntu will not be seen. this link will help you reinstall the grub.
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Thanks again.

---

### Post by cobrn1 on 2007-08-08
You could, of course, always try using the super GRUB disc, as this makes it really easy to fix. See the link in my sig.

---

### Post by MQMike on 2007-08-08
What you need to know is:

Is Vista handling the bootloading of both Vista and Ubuntu?
Or, is GRUB doing it?  (When you turn on the PC, do you see the GRUB boot menu showing you choices of Vista and Ubuntu?)
You need to know what partition Ubuntu is on . . . is it on the first, second, third partition?  Where is Vista?

If GRUB is handling it, then try re-installing GRUB to the Master Boot Record of the hard drive.

***   The definitive dual-booting guide: Linux, Vista and XP step-by-step
[http://apcmag.com/dualboot](http://apcmag.com/dualboot)

How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)
(including how to reinstall GRUB)

---

### Post by duydaniel on 2007-08-08
Hi

I believe the GRUB haddled the boot before. After I reinstall Vista, the GRUB gone.
I meant, Bill Gates is now in control. :(
About the partition, it is quite tricky to me since both Vista and Ubuntu, call those partitions, differently. Maybe I am wrong.

The attached pic will show you.[COLOR="Blue"] I would appreciate if someone tell me which partition I would tell Ubuntu while I would restore the GRUB in order to restore correctly[/COLOR] :KS

Thanks.

---

### Post by PriceChild on 2007-08-08
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by tille on 2007-08-08
> **duydaniel said:**
> Hi

I believe the GRUB haddled the boot before. After I reinstall Vista, the GRUB gone.
I meant, Bill Gates is now in control. :(
About the partition, it is quite tricky to me since both Vista and Ubuntu, call those partitions, differently. Maybe I am wrong.

The attached pic will show you.[COLOR="Blue"] I would appreciate if someone tell me which partition I would tell Ubuntu while I would restore the GRUB in order to restore correctly[/COLOR] :KS

Thanks.



HAHAH UNDER BILL GATE'S CONTROL OMFG HAVENT HAD THAT FUN IN YEARS HAHAHAHAHAHAH :lolflag:

---

### Post by MQMike on 2007-08-08
I’d be afraid to guess based on Windows Computer screen there (although you did a nice job editing it!).

Using the Live Ubuntu CD, get into Ubuntu, and get a Terminal, and type the sudo fdisk –lu command, then tell us what it said (copy it if you can?).

You know the sudo fdisk –lu command at the Ubuntu Terminal prompt?  It gives you a list of your hard drives and filesystems.  (-lu is “l” as  in “list,” “u” as in “units.”)

---

### Post by MQMike on 2007-08-08
Here's what we are looking at doing:
To re-install GRUB, you'll need to fill in the details here, for the partitions (hdx, y).

First, you need to get a grub prompt (grub>) somehow.  
Your two choices are: (1) Use a rescue disk, like Super Grub Disk, from which you can boot into your OS, or press the “c” key to get a GRUB prompt.  Or, (2) Use your Live Kubuntu CD.  
Let's assume (2) here.  
Put your Live CD in the CD tray, re-boot your PC, startup your Live Ubuntu.  
Now get a terminal and proceed as follows:

Get a GRUB prompt as root by typing sudo grub  (then press Enter), and type the following (press Enter after each command):
grub>  root (hdx,y)          # (hdx,y) is the partition of your "main" Linux OS--SEE NOTE BELOW
grub>  setup (hd0)          # This assumes (hd0) is your “main” booting hard drive MBR
grub>  quit
$ exit

Close out all windows.
Re-boot to test it.

NOTE:  
We need to fill in the (hdx, y) with the actual Ubuntu partition.
From what you said, Windows was there first, probably on (hd0, 0) – the first hard drive hd0, the first partition (partition 0).  
And then Ubuntu is on the second partition? If so, the root (hdx, y) would then be root (hd0, 1).  If Ubuntu is on the third partition, it would be (hdx, y) = (hd0, 2).
(Note that the bootloader GRUB starts numbering drives and partitions from zero).

- - - - -

Edit the boot menu (/boot/grub/menu.lst)?

After doing all this, you may still have to edit the boot menu for GRUB, which is contained in Ubuntu at /boot/grub/menu.lst.  (.lst is an “l” as in “list.”)
You must edit it as root, and don’t forget to save your changes when you are done (File-Save, File-Quit).

The part you need to check/edit is the boot menu for Windows, which should look like:

title Windows XP or whatever you wish to call it
rootnoverify (hdx, y)
makeactive
chainloader +1

where:
(hdx, y) is your Windows partition.
x is the hard drive number.
y is the partition.
 (GRUB, the bootloader starts counting from zero.  So hd0 is the first hard drive, hd1 is the second hard drive, etc.;  the first partition is partition 0, the second partition is partition 1, etc.)


For all the details:
How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

---

### Post by duydaniel on 2007-08-08
> **PriceChild said:**
> [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Hi
After followed this guide, I restarted the system and got this screen which reads:

```
Windows failed to start. A recent hardware or software change might be the cause. To fix the problem:
1. insert your windows installation disc and restart your computer
2. Choose your language settings, and then click next.
3. Click "repairt your computer"


Other options:
If power was interrupted during startup, choose start windows noremally.

Safe more
Safe more with network
sefe mode with command promt
last known good configuration
start windows normally
```

And I am only be albe to move the highlight from safe mode to start windows normally. 
:confused:

Any idea? :confused:

---

### Post by duydaniel on 2007-08-08
> **MQMike said:**
> Here's what we are looking at doing:
2) Use your Live Kubuntu CD.  
Let's assume (2) here.  
Put your Live CD in the CD tray, re-boot your PC, startup your Live Ubuntu.  


can I insert a Kununtu CD then see Ubuntu?

My Ubuntu partition is /dev/sda7
but after tried the guide at [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
2 times, it still let Vista boot ==> then report "Windows Error Recovery" as my previous post. :confused:

---

### Post by duydaniel on 2007-08-09
I have tried the Super Grub many times with different selections ==> DID NOT WORK!!!
Anyone has been thru this problem and has a working guide? ](*,)

---

### Post by duydaniel on 2007-08-09
> **MQMike said:**
> Here's what we are looking at doing:
To re-install GRUB, you'll need to fill in the details here, for the partitions (hdx, y).

First, you need to get a grub prompt (grub>) somehow.  
Your two choices are: (1) Use a rescue disk, like Super Grub Disk, from which you can boot into your OS, or press the &#8220;c&#8221; key to get a GRUB prompt.  Or, (2) Use your Live Kubuntu CD.  
Let's assume (2) here.  
Put your Live CD in the CD tray, re-boot your PC, startup your Live Ubuntu.  
Now get a terminal and proceed as follows:

Get a GRUB prompt as root by typing sudo grub  (then press Enter), and type the following (press Enter after each command):
grub>  root (hdx,y)          # (hdx,y) is the partition of your "main" Linux OS--SEE NOTE BELOW
grub>  setup (hd0)          # This assumes (hd0) is your &#8220;main&#8221; booting hard drive MBR
grub>  quit
$ exit

Close out all windows.
Re-boot to test it.

NOTE:  
We need to fill in the (hdx, y) with the actual Ubuntu partition.
From what you said, Windows was there first, probably on (hd0, 0) &#8211; the first hard drive hd0, the first partition (partition 0).  
And then Ubuntu is on the second partition? If so, the root (hdx, y) would then be root (hd0, 1).  If Ubuntu is on the third partition, it would be (hdx, y) = (hd0, 2).
(Note that the bootloader GRUB starts numbering drives and partitions from zero).

- - - - -

Edit the boot menu (/boot/grub/menu.lst)?

After doing all this, you may still have to edit the boot menu for GRUB, which is contained in Ubuntu at /boot/grub/menu.lst.  (.lst is an &#8220;l&#8221; as in &#8220;list.&#8221;)
You must edit it as root, and don&#8217;t forget to save your changes when you are done (File-Save, File-Quit).

The part you need to check/edit is the boot menu for Windows, which should look like:

title Windows XP or whatever you wish to call it
rootnoverify (hdx, y)
makeactive
chainloader +1

where:
(hdx, y) is your Windows partition.
x is the hard drive number.
y is the partition.
 (GRUB, the bootloader starts counting from zero.  So hd0 is the first hard drive, hd1 is the second hard drive, etc.;  the first partition is partition 0, the second partition is partition 1, etc.)


For all the details:
How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

SOLVED ==> I appreciate it. Will make a guide from this soon!!! :guitar:

Plz, edit the title as SOLVED. Thanks

---

### Post by duydaniel on 2007-08-09
I don't know if some one could understand what I am talking about, but here is just like a conclusion of how to solve the boot problem.

What if you have dual boot Windows and Linux. Then somehow, you reinstall Windows and your PC then no longer provide you with boot options menu &#8220;GRUB&#8221; but boot directly to Windows. Here is what I have found work for me.

You need to boot from a Live Ubuntu CD. Then start the Terminal then type:

```
 sudo -f
```

in order to work as root.
Then check your hard disk partitions:

```
fdisk -l
```

l as in love not number one.
here is what my system pop up:
```

Disk /dev/sda: 120.0 GB, 120034123776 bytes

255 heads, 63 sectors/track, 14593 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1               1       11682    93835633+   5  Extended

/dev/sda2   *       11683       14593    23382604+   7  HPFS/NTFS

/dev/sda5            3188       11682    68236056    7  HPFS/NTFS

/dev/sda6               2        1148     9207513+   7  HPFS/NTFS

/dev/sda7            1149        3151    16089066   83  Linux

/dev/sda8            3152        3187      289138+  82  Linux swap / Solaris



Partition table entries are not in disk order

```

Now, as you have seen, I have 2 Linux partitions. Of course, Ubuntu was install on /dev/sda7 since the other was just SWAP partitions.
You need to identify your Linux Partitions in the form of (hdx,y) whereas x is the number in order of the hard drives. For example, if you have 2 hard drives, the first will be call &#8220;hd0&#8221; and the second will be call &#8220;hd1&#8221;. In the same way, y is the number in order of the partitions of that hard drive. For example, if I have Linux on my 2nd hard drive and it is on the 3rd partition, then it would be identify as (hd2,3).

In my case, I only have one hard drive so it will be call hd0
since x and y always start from 0, that meant the Linux partitions you see above /dev/sda7 should be identify as (hd0,6)

Thanks to MQMike for the following:
> 
Here's what we are looking at doing:
To re-install GRUB, you'll need to fill in the details here, for the partitions (hdx, y).

First, you need to get a grub prompt (grub>) somehow. 
...
Put your Live CD in the CD tray, re-boot your PC, startup your Live Ubuntu. 
Now get a terminal and proceed as follows:

Get a GRUB prompt as root by typing sudo grub (then press Enter), and type the following (press Enter after each command):
```
grub> root (hdx,y)
``` # (hdx,y) is the partition of your "main" Linux OS--SEE NOTE BELOW
```
grub> setup (hd0)
``` # This assumes (hd0) is your &#8220;main&#8221; booting hard drive MBR
```
grub> quit
$ exit
```

Close out all windows.
Re-boot to test it. 


please, fix and improve it... so that someone else, who gets trapped by Bill Gates would find it helpful.

---

### Post by MQMike on 2007-08-09
Hey  duydaniel  -- Congratulations!  Good work !
There&#8217;s many people who have this same problem here.  Perhaps you might be able now to help us help all them.  You might even refer them to this thread where they can see exactly what you did here to fix your setup.
Thanks for the feedback, duydaniel ,
--Mike


BTW,
For all the details:
How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)
(aka Qqmike)

Bigpond, GRUB:   [http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries)
(A classic dual-boot/GRUB reference by Herman)

---

