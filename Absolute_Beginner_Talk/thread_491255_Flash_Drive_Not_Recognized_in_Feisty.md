---
title: "Flash Drive Not Recognized in Feisty"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by wmichaelb on 2007-07-03
I tried to download a file this morning to a flash drive that works fine on my Windows machine (Memorex traveldrive USB 2.0 1 GB), but Feisty ignores it altogether. The system seems to recognize five USB ports, and I have used a printer connected to one of them successfully. I tried setting the  BIOS on the PC Chips M861G motherboard to "enabled" for DOS support for legacy USB, but it made no difference. Running lsusb in a terminal yields the following: 

Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  

I've searched, but can find nothing that shows a successful resolution to this problem. Does anyone have a suggestion? 

The other details of my system are shown below. Thanks!

---

### Post by Inxsible on 2007-07-03
Plug in the drive and then do this
 
```
sudo fdisk -l
``` -l is lowercase L. Post the results here

---

### Post by wmichaelb on 2007-07-03
I ran sudo fdisk -l as noted, and found the following:

Disk /dev/hdc: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        5086    40853263+  83  Linux
/dev/hdc2            9682        9964     2273197+   5  Extended
/dev/hdc3   *        5087        9681    36909337+  83  Linux
/dev/hdc5            9885        9964      642568+  82  Linux swap / Solaris
/dev/hdc6            9682        9884     1630534+  82  Linux swap / Solaris

Partition table entries are not in disk order

By way of explanation, I previously ran Dapper. But my motherboard died, and Dapper would not boot with the replacement. I decided to update to Feisty and reinstalled. The installation put in an additional partition that protected the original Dapper install, so well in fact that I've not been able to read the files! (but that's another story). The system actually has only a single 80 GB IDE HD. 

Thanks!

---

### Post by Inxsible on 2007-07-03
> **wmichaelb said:**
> I ran sudo fdisk -l as noted, and found the following:
 
Disk /dev/hdc: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
 
Device Boot Start End Blocks Id System
/dev/hdc1 1 5086 40853263+ 83 Linux
/dev/hdc2 9682 9964 2273197+ 5 Extended
/dev/hdc3 * 5087 9681 36909337+ 83 Linux
/dev/hdc5 9885 9964 642568+ 82 Linux swap / Solaris
/dev/hdc6 9682 9884 1630534+ 82 Linux swap / Solaris
 
Partition table entries are not in disk order
 
By way of explanation, I previously ran Dapper. But my motherboard died, and Dapper would not boot with the replacement. I decided to update to Feisty and reinstalled. The installation put in an additional partition that protected the original Dapper install, so well in fact that I've not been able to read the files! (but that's another story). The system actually has only a single 80 GB IDE HD. 
 
Thanks!
 
Did you connect your Memorex TravelDrive before running this command ? If yes, your drive is not being read at all. Possibly drive failure?
 
EDIT : You said the drive works in Windows....so it must not be the drive. Whats the file system on the drive ?

---

### Post by Fitzcarraldo on 2007-07-03
*wmichaelb*, open a Terminal window and type:

```
dmesg
```

and see what messages are displayed at the end.

Then insert the pen drive, wait a few seconds and then type the above-mentioned command again and see what messages are displayed.

If you see messages like "attempt to access beyond end of device" or "p1 exceeds device capacity" then it is likely that the problem lies with the firmware in the USB pen drive. You can probably solve such a problem by following the procedure given on the following Web page:

[http://www.sabayonlinux.org/wiki/index.php?title=HOWTO:_USB_pen_drive_will_not_automount](http://www.sabayonlinux.org/wiki/index.php?title=HOWTO:_USB_pen_drive_will_not_automount)

I had a similar problem with my pen drive. It would mount fine with Windows XP and Ubuntu 6.06 LTS, but not with another variant of Linux. I've also come across several people on another forum, as well as colleagues at work, with the same problem: their pen drive would not automount with one or more Linux distros, and the technique I have given on the above-mentioned page has solved the problem. Although I have seen this problem with various different manufacturers' pen drives, I suspect that it could be because the chip with the firmware is from a common supplier. Basically, it's a bug in the firmware.

---

### Post by wmichaelb on 2007-07-03
Fitzcarraldo: I ran dmesg both with and without the pen drive. I pasted both into Open Office Write, and used Edit/compare to find any differences. There were none. Yet I can cheerily print from the USB printer all day. 

Phase of the moon? Wolfbane pollen concentration? Windows vapor from the next room?

---

### Post by Fitzcarraldo on 2007-07-03
What happens when you run GParted with the pen drive plugged in? Can you see it in GParted?

If GParted is not already installed on your PC, you can install it by typing the following into a Terminal window:

```
sudo apt-get install gparted
```

and then:

```
sudo gparted
```

to launch it. The box at the top right hand corner of the GParted window lets you select the different disks connected to your PC. Don't try to format or partition anything, though! Just look to see if GParted sees the USB pen drive.

---

### Post by wmichaelb on 2007-07-04
Fitzcarraldo: What GParted shows me is this:

Partition                     Filesystem              Mount Point              Size                 Used           Unused        Flags

/dev/hdc1                  ext 3                        /media/disk              38.96 GiB         4.34 GiB     34.62 GiB   
/dev/hdc3                  ext 3                        /                               35.2 GiB            4.99 GiB    30.21 GiB       boot
  V /dev/hdc2             extended                                                 2.17 GiB
     /dev/hdc6             linux swap                                                1.55 GiB
     /dev/hdc5             linus swap                                                627.51 MiB

In my limited knowledge of Linux, this looks to me like the current Feisty installation, and the older Dapper installation in an extended partition. But the system does not see the pen drive in any way, shape, or form. 

So I plugged it into my Windows machine, in which it worked the last time I used it, and behold...no pen drive there either! So the drive itself may be dead. I have all the data on it on the HD on the Windows machine, so that's no loss; but I do need to get another.

Thanks for all your time and patience; I should have checked it on the Windows machine _again_ and _immediately_!
before engaging this community.

---

### Post by Fitzcarraldo on 2007-07-04
As it looks like the pen drive is dead, it would do no harm to try to low-level format it and, if that is successful, to format to FAT32 with GParted, just to see if it works (which I doubt). There is nothing to lose.

[http://www.sabayonlinux.org/wiki/index.php?title=HOWTO:_USB_pen_drive_will_not_automount](http://www.sabayonlinux.org/wiki/index.php?title=HOWTO:_USB_pen_drive_will_not_automount)

---

### Post by TonyDoc on 2007-07-04
I've got a similar issue with one of my two memory sticks.  The newer 2GB one automounts perfectly, the older 64MB one mounts with Dapper, Suse 10.0 and Windows, but not Feisty.  I really don't want to low level format it.  Any other possibilities?

Tony

---

### Post by wmichaelb on 2007-07-06
Fitzcarraldo: I installed the HDDGuru software that you were kind enough to cite, but it doesn't find the pen drive either. There's a sale on this week at Micro Center, so I'll simply stop there and pick up another one.

Thanks for all your time and suggestions!

---

### Post by wmichaelb on 2007-07-06
TonyDoc: Try

[http://ubuntuforums.org/showthread.php?t=237881&highlight=flash+drive](http://ubuntuforums.org/showthread.php?t=237881&highlight=flash+drive)

If that doesn't help, you may be stuck with the low level format approach:

http://www.sabayonlinux.org/wiki/ind...ot_auto[/url] mount

as per Fitzcarraldo's reply above. 

Please reply and let the rest of the community know how things turn out. Good luck!

---

### Post by quinnten83 on 2007-07-06
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117781]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117781")

i tried witht he suggestion here when my external HD wasn recognized.
it works for me, you might want to try it.

---

### Post by wmichaelb on 2007-07-06
Just for the record, I purchased a new Sandisk 1 GB drive today, plugged it in, and Feisty recognized it immediately and automatically. Onward and upward!

---

### Post by macogw on 2007-07-07
This is weird.  I have a Memorex TravelDrive 4GB and it works perfectly in Feisty

---

### Post by kartik2104 on 2007-07-07
hello!
i m new to ubuntu and also to any sort of linx, just yesterday i installed ubuntu 7.04 on my 20 gb hard disk , my processor is 2.8 dual core and a 512 mb ram ,
how can i pair my phone up wid my system?
fiesty is not detecting my bluetooth device automatically, what shall i do?
do manage my mobile phone and use the LAN acess via blue tooth shall i have to install any softwares if yes then please send me the links from where i can download them.

---

### Post by macogw on 2007-07-07
> **kartik2104 said:**
> hello!
i m new to ubuntu and also to any sort of linx, just yesterday i installed ubuntu 7.04 on my 20 gb hard disk , my processor is 2.8 dual core and a 512 mb ram ,
how can i pair my phone up wid my system?
fiesty is not detecting my bluetooth device automatically, what shall i do?
do manage my mobile phone and use the LAN acess via blue tooth shall i have to install any softwares if yes then please send me the links from where i can download them.
This has nothing to do with this thread.  Make your own thread.  And look for bluetooth in Synaptic.  There are GUIs to get it working.  Of course, if your computer doesn't have a Bluetooth card, having software isn't going to do anything.

---

