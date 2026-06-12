---
title: "USB drives won't mount!"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by jpblock82 on 2007-11-21
Help me folks, I'm Linux super-noob...don't know crap about all these commands, etc)...but I have faith in anything that is anti-MS. 

So I did a dual boot with XP Pro already installed and put Ubuntu 7.04 on top of that.  From there I went ahead and installed all the updates then installed 7.10.  I never used the PC for anything else until all the updates/upgrade were complete.

My problem is, I cant get any USB drives to mount (doesn't show up in Computer at all).  
In Users/Groups, the box is checked to auto mount USB devices.  What's odd is I can use my USB keyboard and mouse.

I actually had these my mouse and keyboard installed during the install...would that have caused issues??

Here's my lsusb with nothing USB plugged in:

jeremy@jeremy-3100:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

and here we go with my Maxtor 80GB:

jeremy@jeremy-3100:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

no change at all....???

and now with my Logitech wireless keyboard/mouse:

jeremy@jeremy-3100:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c513 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  

Weird huh??  Someone help...I wanna give up Windows all together!!

---

### Post by taurus on 2007-11-21
Plug in your USB drive.  Then, open a terminal and post the output of this command.

```
sudo fdisk -l <-- lower case letter l, not number 1
```

---

### Post by jpblock82 on 2007-11-22
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5287    42467796    7  HPFS/NTFS
/dev/sda2            5288        9541    34170255   83  Linux
/dev/sda3            9542        9729     1510110    5  Extended
/dev/sda5            9542        9729     1510078+  82  Linux swap / Solaris

---

### Post by jaybombalous on 2007-11-22
You should have a 'sdb' if your usb drive is plugged in. Are u using the 2.6.22-generic kernel?

---

### Post by jpblock82 on 2007-11-22
nope...not any sbd...how do I check as to what version kernel I'm running??

i went into the about GNOME option...it shows v. 2.20.1...it this what I'm looking for???

---

### Post by nikoPSK on 2007-11-22
hmm, did you have it plugged in on install of ubu (no clue if that makes a difference, probably doesn't mine worked right away thou...)

---

### Post by jpblock82 on 2007-11-23
Nope, definitely wasn't plugged in during install.  Is it possible to reinstall the OS over the existing??  If so, anything special I need to know or should do?

---

### Post by jpblock82 on 2007-11-23
Forgot to mention...

uname -a results:

Linux jeremy-3100 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

So yes, I'm running the 2.6.22 Kernel.

---

### Post by kpkeerthi on 2007-11-23
> **nikoPSK said:**
> hmm, did you have it plugged in on install of ubu (no clue if that makes a difference, probably doesn't mine worked right away thou...)

No. You don't need to have your USB drive plugged in during install to have it working afterward.

---

### Post by kpkeerthi on 2007-11-23
jpblock,
Are you sure that this USB drive is in a working condition? Did you check this with other OS (Windows) or by running Ubuntu/Other distribution in "Live" mode?

---

### Post by ugm6hr on 2007-11-23
> **jpblock82 said:**
> and here we go with my Maxtor 80GB:

jeremy@jeremy-3100:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

no change at all....???


Does the HD work in XP? It appears that the HD is not even recognised at the hardware level, so presumably stands no chance of being mounted.

Might be worth doing a diagnostic check on the HD (not sure how on a USB HD, but have a look at the Maxtor website).

---

### Post by kpkeerthi on 2007-11-23
Plug in your USB drive (again) and post the last 10 lines by running
```

dmesg

```

---

### Post by jpblock82 on 2007-11-23
Here's the dmesg results:

[43763.044000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[43763.236000] Failure registering capabilities with primary security module.
[43770.380000] usb 3-1: new high speed USB device using ehci_hcd and address 32
[43771.252000] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[43771.364000] usb 3-1: new high speed USB device using ehci_hcd and address 33
[43772.236000] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[43772.348000] usb 3-1: new high speed USB device using ehci_hcd and address 34
[43772.756000] usb 3-1: device not accepting address 34, error -71
[43772.868000] usb 3-1: new high speed USB device using ehci_hcd and address 35
[43773.276000] usb 3-1: device not accepting address 35, error -71
[43773.600000] usb 1-4: reset low speed USB device using ohci_hcd and address 4
[43774.284000] usb 1-3: reset low speed USB device using ohci_hcd and address 3
[43781.776000] eth0: no IPv6 routers present

and the external HDD works just fine in xp.  Help me out here friends, I want to love ubu, but this is the only thing holding me back.  I'll pop in the live cd and come right back with the results.

---

### Post by jpblock82 on 2007-11-23
I'm in the live cd now.  I plugged in 4 different usb drives, and into different ports and none would mount.  Any other suggestions???

---

### Post by jpblock82 on 2007-11-28
So that's it????  No one has any other ideas?????

---

### Post by nikoPSK on 2007-11-28
so does it work in windows?

---

### Post by jpblock82 on 2007-11-28
Works in Windows just fine.  Kinda weird that I used the Live CD and it wouldn't work from there either. help me help me!!!

---

### Post by crf on 2007-11-28
hi,

When the computer starts, and the grub menu comes up, is there a choice to what kernel you can use?

If there is, try booting with an older kernel, and seeing if your usb drives are found.

I think you can also install other kernels using synaptic (with the name linux-image ... ) .

---

### Post by nikoPSK on 2007-11-28
Well, that's extremely odd, if it works in windows it should work in linux. What ver of ubuntu are you using?

---

### Post by StephUb on 2007-11-28
Is that a USB stick or a USB HD?
Is it formatted in FAT32 or NTFS ?
I asked that because i got an USB HD in NTFS and i got it to work on both win XP and Ubuntu .
However, you need to remove it safely from windows (thing i never did when only on windows) otherwise ubuntu won't mount it. As soon as you remove hardware safely from windows, my USD HD NTFS is readable from Ubuntu.

---

### Post by nikoPSK on 2007-11-28
I prefer ntfs over fat... but yes, what are it's specs?

---

### Post by jpblock82 on 2007-11-29
-Tried that with the GRUB menu...i have "14" and "16" as options....neither get the USB to kick in though.  

-I'm running Ubu 7.10 (started with the 7.04 CD, got all my updates, then did the 7.10 upgrade)

I've tried flash drives, and my external HDD.  Everything is using a FAT32 file system.  I have 5 different flash drives, all I've tried in Ubu, which all work just fine in XP.  Same with the external HDD...And yes, I ALWAYS eject my drives with the "safe eject" option in Windows; cuz you just never know.  

I'm still really bummed out that not even from my 7.04 LIVE CD that it wouldn't work.... :(  

I even got my ATHEROS WIFI chipset working and I'm using the WICD utility!!  
Getting external storage to work is my last hurdle. 

Just an update, here's my lsusb with a 1GB flash drive (FAT32), my dell keyboard, and a logictech wired mouse:

jeremy@jeremy-3100:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 413c:2105 Dell Computer Corp. 
Bus 001 Device 003: ID 046d:c03d Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  

Strange huh????

---

### Post by fidge on 2007-11-29
I had the same trouble but it was fine after booting into vista/xp and safley removing the drives.
good luck

---

### Post by jpblock82 on 2007-11-29
Guess I'll give that a try....

---

### Post by jpblock82 on 2007-11-29
Ok, so I booted in to XP, plugged in my 80GB Maxtor, did a safe eject and unplugged it.  Restarted, and booted into Ubu and nothing....???

---

### Post by StephUb on 2007-11-29
If your HD is NTFS, 7.04 isn't able to read it out of the box. 
I don't know about the update 7.10 but the classic install 7.10 make NTFS read/write.
Tried to look if you have NTSF3g?

---

### Post by dimbulb1024 on 2007-11-29
Make sure when you use it in Windows that you unmount them first before unplugging them. I had this problem and found that once I unmounted them in Windows they would then mount in Linux, where as if I didn't unmount before unplugging the device would never appear on Linux.

---

### Post by nikoPSK on 2007-11-29
yes, be sure to always right click, then unmount, for mass storage devies, sd cards, everything (I don't know if cds...).

---

### Post by jpblock82 on 2007-11-29
I do correctly eject my drives....ALWAYS.   So I'm reinstalling Ubu 7.04.  I popped in the Live CD and removed the exisiting ext3 partition and I've created a new one, it's at 70% right now.   I'll let you guys know if it works when done...but if it doesnt, what then???  Ubu is crap and to give up???  I hope not...I really like it, and want to make it work.

I'm just concerned still for the fact that, why wouldn't any of my USB drives mount when running the LIVE CD????

Ho hum, I'll let you guys know how it turns out...

---

### Post by lespaul_rentals on 2007-11-29
Run:

```
sudo apt-get install ntfs-3g
```

Then:

```
sudo apt-get install ntfs-config
```

Then:

```
sudo ntfs-config
```

Select Yes at the window.

---

### Post by jpblock82 on 2007-11-29
> **lespaul_rentals said:**
> Run:

```
sudo apt-get install ntfs-3g
```

Then:

```
sudo apt-get install ntfs-config
```

Then:

```
sudo ntfs-config
```

Select Yes at the window.


After the 7.04 re-install, I followed the above exactly, and did a reboot.  I then plugged in my 80GB USB drive and .................. 

nothing happened.....WTF?!?!?!?

---

### Post by jpblock82 on 2007-11-29
Here's my latest dmesg:

[   72.172000] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[   72.284000] usb 3-1: new high speed USB device using ehci_hcd and address 3
[   73.156000] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[   73.268000] usb 3-1: new high speed USB device using ehci_hcd and address 4
[   73.676000] usb 3-1: device not accepting address 4, error -71
[   73.788000] usb 3-1: new high speed USB device using ehci_hcd and address 5
[   74.196000] usb 3-1: device not accepting address 5, error -71
[  150.080000] usb 3-7: new high speed USB device using ehci_hcd and address 6
[  150.952000] hub 3-0:1.0: Cannot enable port 7.  Maybe the USB cable is bad?
[  151.064000] usb 3-7: new high speed USB device using ehci_hcd and address 7
[  151.936000] hub 3-0:1.0: Cannot enable port 7.  Maybe the USB cable is bad?
[  152.048000] usb 3-7: new high speed USB device using ehci_hcd and address 8
[  152.456000] usb 3-7: device not accepting address 8, error -71
[  152.568000] usb 3-7: new high speed USB device using ehci_hcd and address 9
[  152.976000] usb 3-7: device not accepting address 9, error -71
[  283.400000] usb 3-7: new high speed USB device using ehci_hcd and address 10
[  284.272000] hub 3-0:1.0: Cannot enable port 7.  Maybe the USB cable is bad?
[  284.384000] usb 3-7: new high speed USB device using ehci_hcd and address 11
[  285.256000] hub 3-0:1.0: Cannot enable port 7.  Maybe the USB cable is bad?
[  285.368000] usb 3-7: new high speed USB device using ehci_hcd and address 12
[  285.776000] usb 3-7: device not accepting address 12, error -71
[  285.888000] usb 3-7: new high speed USB device using ehci_hcd and address 13
[  286.296000] usb 3-7: device not accepting address 13, error -71

---

### Post by nikoPSK on 2007-11-29
80 gig usb thumb drive? :confused: or external hd? Ive seen and own a 8 gig one but....

---

### Post by jpblock82 on 2007-11-30
...

it's a 80g external...

I downloaded the 7.10 install and put it on cd.  I then booted from the cd, and plugged in the th 80g external and still nothing.  Not even my 1gb thumb drives work.....whats the point of trying???  Guess it just wont work huh?????

---

### Post by TeaSwigger on 2007-11-30
> **jpblock82 said:**
> ...

it's a 80g external...

I downloaded the 7.10 install and put it on cd.  I then booted from the cd, and plugged in the th 80g external and still nothing.  Not even my 1gb thumb drives work.....whats the point of trying???  Guess it just wont work huh?????

Hello, I've no clue about usb stuff but I did some searching for you. There were a few replies which appeared to suggest this was "an acpi problem and not a usb problem." A suggestion was to try adding this line to the boot:

```
acpi=off
```

or 

```
pci=noacpi
```

and see if it works ok. It's greek to me, but I can tell you how to do it. At the GRUB boot screen, select the normal ubuntu version and press the e button (for Edit). Then pick the main line (with the kernel etc), it should have 'splash' in it. Press e to Edit that line. Simply type one of those codes above and press enter. Then press b (for Boot). See if it'll work. If not don't worry, it doesn't save that edit. If it does work add it to the appropriate line in /boot/grub/menu.lst to make it permanent.

I can also suggest that it'd be more ideal to install 7.10 fresh instead of upgrade from 7.04, but couldn't guess if that's related to this issue.

---

### Post by TeaSwigger on 2007-11-30
Hello again, another tidbit in case it helps. It may not be related but as you seem to have an odd issue, might as well try...

From here
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/88746](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/88746)

relevant part:
"5. Unload ehci_hcd with 'sudo modprobe -r ehci_hcd'
6. Insert your USB device again.
7. Check that everything works. (copy some files, etc.)"

That should be a quick way to tell if this is along the right track or not. If so it's a bug. Sometimes there are hassels stemming from the fact there's an awful lot of different hardware, and not that many releasing code so people can use it without also buying Microsoft products. Hope this is fixable now for you, if not may be a problem until a later kernel fixes it.

---

### Post by TeaSwigger on 2007-11-30
Just wanted to add that I understand and hope you'll stick with it. I have a usb scanner I just can't get to work yet, no clue why. I tell ya, next stuff I buy I'm going to make sure is supported outside Microsoft Windows(tm).

---

### Post by Andrew28 on 2007-11-30
I got the same problem with my USB Drive Enclosure (2.5" Fujitsu SATA).  However, I got a different result on *dmesg* when I did *acpi=off*

> [ 105.888000] Initializing USB Mass Storage driver...
[ 105.888000] scsi2 : SCSI emulation for USB Mass Storage devices
[ 105.888000] usb-storage: device found at 2
[ 105.888000] usb-storage: waiting for device to settle before scanning
[ 105.892000] usbcore: registered new interface driver usb-storage
[ 105.892000] USB Mass Storage support registered.
[ 110.888000] usb-storage: device scan complete
[ 110.892000] scsi 2:0:0:0: Direct-Access PQ: 0 ANSI: 2 CCS
[ 110.896000] sd 2:0:0:0: [sdb] Attached SCSI disk
[ 110.896000] sd 2:0:0:0: Attached scsi generic sg1 type 0

What should I do next?

---

### Post by jpblock82 on 2007-11-30
> **TeaSwigger said:**
> Hello again, another tidbit in case it helps. It may not be related but as you seem to have an odd issue, might as well try...

From here
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/88746](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/88746)

relevant part:
"5. Unload ehci_hcd with 'sudo modprobe -r ehci_hcd'
6. Insert your USB device again.
7. Check that everything works. (copy some files, etc.)"

That should be a quick way to tell if this is along the right track or not. If so it's a bug. Sometimes there are hassels stemming from the fact there's an awful lot of different hardware, and not that many releasing code so people can use it without also buying Microsoft products. Hope this is fixable now for you, if not may be a problem until a later kernel fixes it.

You are the MAN!!!  This was it!!!  Now how do I get this to work each time I power down/reboot without typing the cmd in each time?  I'm still very new at all this linux stuff...  Thanks homeslice!!!!

This problem is FIXED!!!!!!

---

### Post by nikoPSK on 2007-11-30
Ya!!! Good! I hope you don't have any more problems with ubuntu. What I don't like is people that switch and think all this stuff is the norm...

---

### Post by Gildp67 on 2007-11-30
Ok looks like the cmd line works for you, but looks like you need to do that every time you start you machine if Im reading your last post correctly. I was having the same problem what ended up fixing it for me was that I had to make sure in my bios setting that legacy usb support was enabled then poof everything was working great.

---

### Post by lespaul_rentals on 2007-11-30
[quote=jpblock82]Now how do I get this to work each time I power down/reboot without typing the cmd in each time?[/quote]

Add the following to /etc/rc.local:

```
modprobe -r ehci_hcd
```

---

### Post by ramonthomas on 2007-12-01
To begin with I am running Ubuntu 7.10 and this problem is the same in both Gnome and KDE. Anyway the problem started when I right clicked on the flash drive icon on the desktop and selected EJECT.

Since then the icon does not appear. I've tried to add mount points for sdb1 to /etc/fstab /etc/mtab to no avail. I've tried rebooting with flash drive in and without, no avail. I've tried following some other instructions on this forum to no avail.

This is the output from dmesg which seems to imply its being picked up fine on the hardware level:

[ 9482.684000] hub 4-0:1.0: hub_port_status failed (err = -32)
[ 9484.088000] usb 4-3: new high speed USB device using ehci_hcd and address 123
[ 9484.388000] usb 4-3: new high speed USB device using ehci_hcd and address 124

And this is the line in /etc/fstab
/dev/sdb1       /media/usb      auto    rw,user,noauto,exec 0   0

How else can I bring that icon back on the desktop?

---

### Post by nikoPSK on 2007-12-01
Have anybody told you to run this command yet?

```
lsusb
```

---

### Post by ramonthomas on 2007-12-01
No. Not sure what that command does but here's the output:

ramon@laotzu:/media$ lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

---

### Post by nikoPSK on 2007-12-01
lists all usb connections that it recognizes on your pc. Check if yours is there, I will look and try to decipher it.

---

### Post by nikoPSK on 2007-12-01
see heres mine:

niko@home:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 090c:1000 Feiya Technology Corp. Memory Bar
Bus 001 Device 002: ID 03f0:1204 Hewlett-Packard DeskJet 930c
Bus 001 Device 001: ID 0000:0000  
niko@home:~$ 

the first is my usb the second is my printer. I have four ports and only two are used.

---

### Post by nikoPSK on 2007-12-01
> **ramonthomas said:**
> No. Not sure what that command does but here's the output:

ramon@laotzu:/media$ lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

so it's not recognizing your usb. Was it plugged ?

---

### Post by ramonthomas on 2007-12-01
Yes, my usb flash drive is plugged in. Here's more output from running "mount" and also what's in my fstab. I'm running KDE desktop just in case that would make a difference but I've also tried all the same advice on Gnome with no effect in past.

ramon@laotzu:/media$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)

ramon@laotzu:/media$ mount | grep sdb
ramon@laotzu:/media$ more /etc/fstab | grep sdb
/dev/sdb1       /media/usb      auto    rw,user,noauto,exec 0   0
ramon@laotzu:/media$

How else can I get my flash drive to work without re-installing?

---

### Post by nikoPSK on 2007-12-01
has it been formatted properly? i know mine is FAT32......

---

### Post by trumants on 2007-12-01
:confused: I am having the same trouble with a SimpleDrive USB external drive.  I can see it, but I can't get it to mount.  Even went into the gconf-editor and removed and then replaced the "usefree" in the mounting oprtions list, but that didn't work for me either.

I am a reall noob myself at Linux.

---

### Post by ramonthomas on 2007-12-02
Yes, my usb flash drive is formatted. I use it on my WindowsXP machine and another Ubuntu 7.10 desktop machine. It's only the laptop also running Ubuntu 7.10, as I said, where I ejected the usb flash drive icon, and now it does not comes back when put the flash drive in again.

Can someone please post basic instructions on how to mount a usb flash drive from scratch and specifically so it automounts in KDE/Gnome desktops.

---

### Post by nikoPSK on 2007-12-02
you ejected it without clicking unmount? That could pose a threat but if it works on other machines.... :(

---

### Post by doubtful wisdom on 2007-12-02
Running Gutsy and had no problem with flash drives, until a few days ago.  None of my flash drives are recognized, on this box.  However, they work fine with Gutsy on my laptop.  Also work with Windows PC's, but not on my primary Gutsy PC.  Any help would be appreciated.  Read a lot of posts, and tried several suggestions with no success.

---

### Post by A-dogg on 2007-12-07
My SD card (a sandisk ultra II, which folds in half to plug directly into the USB port) is formatted for FAT32 and will not mount.

When I type  "sudo fdisk -l" it shows up as /dev/sdb
When I type "lsusb" it shows up as a "SanDisk" device plugged into the system.

But it won't mount.

Any advice? Should I reformat it to NTFS?

---

### Post by RustyWyatt on 2007-12-09
CRF,

This tip just saved me a lot more frustration! I have been trying to fix this problem for weeks... Just so I could backup on an additional device (usb drive) before I start from scratch and install MythTV on this pc.

Now I'm off and running!

Thanks again!!
Tom
====

When the computer starts, and the grub menu comes up, is there a choice to what kernel you can use?

If there is, try booting with an older kernel, and seeing if your usb drives are found.

I think you can also install other kernels using synaptic (with the name linux-image ... ) .[/QUOTE]
====

---

### Post by atentik on 2007-12-10
> **lespaul_rentals said:**
> Add the following to /etc/rc.local:

```
modprobe -r ehci_hcd
```

How do you add it to the rc.local?

---

### Post by jputman01 on 2007-12-11
> **atentik said:**
> How do you add it to the rc.local?


open a terminal and type

```
sudo gedit /etc/rc.local
```

when that opens just add it before the end 0, click save and you should be good.

glad i found this thread, ive been frustrated for a while with my 1gb thumb drive

---

