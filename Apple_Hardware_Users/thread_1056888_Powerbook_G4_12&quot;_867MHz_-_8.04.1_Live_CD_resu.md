---
title: "Powerbook G4 12&quot; 867MHz - 8.04.1 Live CD results"
date: 2009-02-01
forum: Apple Hardware Users
---

### Post by uncoolbob on 2009-02-01
Hi all,

I'm about to take the leap from OS-X 10.2.8 to Ubuntu 8.04.1 (on my G4 powerbook, as above plus 40GB drive + 768MB RAM + Airport Express card). Looking forward to being back with Linux again, but I had a few issues with the Live CD, and have some questions...

[LIST=1]
[*]The wireless didn't work but it looks like it will on a real install since it needs to write to disk and reboot.  This absolutely has to work.
[*]Ditto for USB memory stick - looks like some filesystems are compiled read-only for the Live CD.
[*]From my reading on the forum, suspend to RAM isn't going to work because of the Nvidia card.  Will it be simple enough to get suspend to disk working?  (Seems to be plenty of threads on that here.)
[*]I couldn't get a second display working with the Live CD.  During boot it did recognise it and print some logging to it, but then the desktop came up on the laptop screen (second screen was white with some black dots) and no amount of "Detect Displays..." in the screen resolution settings panel would fix it.  Will this be easy enough to fix?  I have to have the big screen (the powerbook is mostly used as a desktop, since the battery is long dead)).
[*]Is JRE 1.5 or higher available?  I forgot to check while booted.
[/LIST]

Sound seems to be working fine, which is excellent.

I'll probably go for a full reformat of the drive, with two partitions and dual boot with OS-X 10.5 in the smaller (15GB should do it - I'll skip the developer tools) partition.  Dumb question, but do I need the Apple Disk Utility CD to perform this?  Should the OS-X partition be the first one?

From what I read here I need to install OS-X first, but hopefully I can remove it later if I never use it.

Have I missed anything else obvious?

many thanks for any help you can offer,

cheers
Bob

---

### Post by mkvnmtr on 2009-02-01
You will need to install the mac os first. I would ues disk utility on the disk to create the partition for mac and leave the rest as free space. On my G4 Ibook every thing works but I have never tried to add another monitor. The driver for my wireless is in hardware drivers waiting to be enabled and have firmware down loaded. When you install you can choose the method to install Ubuntu in the largest free space and it will form the partitions you need for swap, yboot and root. I would assume you will be able to get your monitor working but it might take some questions here on the forums. Later you can reformat the mac partition to use as you wish. Even though I rarely boot into mac I still have about 6G with a very stripped down mac os installed.

---

### Post by uncoolbob on 2009-02-04
Thanks for the info mkvnmtr.  I'm just wondering, is there a custom OS-X install option or do you do a normal install and then remove things (and then resize your partitions)?  The recommended disk space for 10.5 is 9GB and I guess one should leave room for the updates.

---

### Post by uncoolbob on 2009-02-19
I'm back, and typing from Ubuntu, with wireless working fine.  Hibernate didn't work when I tried it (only once) and I know not to try to get sleep working.

So far the fan hasn't come on (has now, see update below) and I've been reading that the kernel module therm_adt746x is needed.
I get the same error as others (e.g. [http://ubuntuforums.org/showthread.php?t=192577&page=2](http://ubuntuforums.org/showthread.php?t=192577&page=2))
when I try to load the module:

sudo modprobe therm_adt746x

FATAL: Error inserting therm_adt746x (/lib/modules/2.6.24-19-powerpc/kernel/drivers/macintosh/therm_adt746x.ko): No such device

I reckon there's a problem with there being no /sys/devices/temperature on my system.

Any ideas?

UPDATE: fan came on midway through a massive package update.  could be something upgraded/fixed or maybe it just runs hotter than os-x, which is fine with me.

---

### Post by uncoolbob on 2009-02-20
Just some more observations...

Thanks to mkvnmtr's advice everything went smoothly.

The first install of OS-X (10.5) went fine but when I did the first "software update" it complained of lack of disk space (5GB needed for post-install optimizations!).  I had only given OS-X a few GB spare space, but fortunately you can extend the partition into the unused space with with Disk Utility, without even rebooting or booting from CD.

Then when it came to installing Ubuntu (from the live CD) I just selected "guided, use largest available free space" and the dual boot with OS X all worked out fine.

Audio was perfect straight out of the box.

It looks like Sun Java 6 is problematic - no PPC version available.  Some discussion here: [http://ubuntuforums.org/showthread.php?t=470292](http://ubuntuforums.org/showthread.php?t=470292)
I will see how I get on with openjdk and the IcedTea browser plugin (so far failed with thinkbroadband speedtest).

Adobe Flash is the other sticking point.  Gnash installs OK and plays animations OK (e.g. adverts!) - as others have mentioned on the web - but so far no joy for audio (e.g. embedded mp3 players).

I assume that due to the lack of proper graphics support (thanks a lot Nvidia!) the drawing of windows is rather clunky.

Fan is working just fine.  Sorry for the false alarm above.

I will tackle the dual monitors another day (not even tried yet).  I also forgot to try USB media.

---

### Post by mkvnmtr on 2009-02-20
Flash and java are just not going to be first class on powerpc equipment. Try enabling the medibuntu repositories and using the IBM java. You will need to uninstall the other java you have tried first. You will probably want the other programs in the medibuntu repository for DVD viewing and such. On my Ibook I have never heard the fan come on in Mac or Ubuntu except once in Ubuntu. I have had it 6 years and use it a lot. It got hot once and stopped working. I have found no programs to help. I can't even get lm-sensors to read the temps. On mac I had some programs to read temps. What I do is if it seems a little warm to the touch I turn a fan on to blow across my desk. That seems to do it. On another laptop it makes an 18 difference. Even with the lack of good flash I like Ubuntu better than my mac os and I really liked Mac.

---

### Post by uncoolbob on 2009-02-21
thanks, will enable the medibuntu repository in a minute.

have got the external display working (but not dual head or anything fancy, as this would require the closed source nvidia driver).  I kept it simple, here is my xorg.conf, from the Device section onwards. "CrtcNumber" is the critical option (although I had to also set FlatPanel = 0 to make it work).  I set up the resolution using the System->Preferences->Screen Resolution GUI, and remembered to press the auto-adjust button on my monitor to centre it properly!

```

#Section "Device"
#       Identifier      "NV Internal"
#       BusID           "PCI:0:16:0"
#        Driver          "nv"
#EndSection

Section "Device"
        Identifier      "NV External"
        BusID           "PCI:0:16:0"
        Driver          "nv"
        Option          "CrtcNumber" "0"
        Option          "FlatPanel" "0"
EndSection

Section "Monitor"
        Identifier      "Internal Monitor"
EndSection

Section "Monitor"
        Identifier      "External Monitor"
EndSection

Section "Screen"
        Identifier      "Internal Screen"
        Monitor         "Internal Monitor"
        Device          "NV Internal"
EndSection

Section "Screen"
        Identifier      "External Screen"
        Monitor         "External Monitor"
        Device          "NV External"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
#one of the following two lines only
        Screen          "External Screen"
#        Screen          "Internal Screen"
        InputDevice     "Synaptics Touchpad"
EndSection

```

Unfortunately you can't have two Device sections running off the same driver and PCI slot (hence commented out region), so I'll have to figure out a clean way to specify a different xorg.conf file (or fallback or something) when booting without the external monitor.

One downside: the internal LCD still displays junk from the graphic card memory and I don't think you can turn down/off the backlight?

---

### Post by uncoolbob on 2009-02-26
Just for the record (might help someone)

I booted into OS-X for the first time yesterday, except it didn't boot into OS-X until I fixed /etc/yaboot.conf - it had the wrong /dev/hdaXX for the OS-X boot partition.  Then (after sudo ybin -v) it was fine of course.

You can find the correct hda number by either mounting it from the GUI Places menu, running df at the commandline, then unmounting it again before running ybin.  Or it looks like you can find out which partitions are available from /etc/blkid.tab

---

### Post by mkvnmtr on 2009-02-26
On powerpc I find that I can't do things that need the most current java or flash. That doesn't really matter to me because I seldom have a desire to view a flash video and I use no script by default. The upside is I can do so much that I never thought to do on Mac. I very seldom boot my mac. I usually just use my acer that is up and running Mint if I wish to view something that I can't see on powerpc. I think you will enjoy using Ubuntu but I would never consider anything but a dual boot. I even keep a windows partition on other computers. Heck it is paid for I might find something easier to do in the other os.

---

### Post by uncoolbob on 2009-02-28
Just figured out how to get gdm to start X11 using the relevant xorg.conf file (depending on monitor attached or not):

[http://ubuntuforums.org/showthread.php?p=6813144#post6813144](http://ubuntuforums.org/showthread.php?p=6813144#post6813144)

USB stick works fine too.

Linux has really come a long way in the ~5 years I've been away from the desktop.  (Have been administrating servers all the time though.)

---

### Post by mkvnmtr on 2009-02-28
On powerpc we are lacking a little but on my other computers there is nothing that I feel doesn't work. I just reread one of your questions and it is a little late but you can do a costom install on the mac and leave out all the stuff you don't want.Language garage band and some other stuff saved me over 2 Gb. I think my whole mac partition is only like 6 Gb and I have nearly half free.

---

