---
title: "Good bye my fellows..."
date: 2008-07-15
forum: Apple Hardware Users
---

### Post by Oscar Pradilla on 2008-07-15
i have to switch back, my MBP is too hot, i´ve able to run cooler but not as it needs, i´m not gonna risk it..

Also my video output crash, stop working, i´m tired of trying to make it run as i want so i will switch back to mac os...

i´m gonna miss this enviroment, i will try again with 8.1, let´s see what happen...

Has anyone tried mandriva gnome 2008?

Tks, and see you later..

---

### Post by cyberdork33 on 2008-07-15
Heat has been an issue how people on these machines. I do have to say that your Mac will turn itself off if it gets too hot.

Thanks for trying out Ubuntu though. You are likely to have the very same cooling / power performance in Mandriva (or any other distro) because they all use pretty much the same software to handle these things.

---

### Post by spencercarran on 2008-07-15
Is there any way of dealing with the heating issues? Mine usually isn't terrible, but it definitely runs appreciably hotter than it did under OSX.

---

### Post by stream303 on 2008-07-15
I'm just thinking out loud here... :)

Does top reveal any cpu-hogging processes?

Although it has top in it's name, the following utility is NOT really dedicated to being a top replacement, but a power-saving utility from Intel: PowerTop.  (it is in the normal download repos)  Has anyone run that to help identify power-hogging issues and seeing if the recommendations make any improvements?

Any kernel gurus out there?  Has anyone played with the ioscheduler to change the default from CFQ to something like NOOP, DEADLINE, etc and compared results?  End-users can change this on the fly or in grub's menu.lst

.. I guess I have my propeller-hat on today.  :)

---

### Post by cyberdork33 on 2008-07-15
you can cool the machine down a bit by doing some power saving / performance changes as people have stated in other threads.

[http://ubuntuforums.org/showthread.php?t=858814](http://ubuntuforums.org/showthread.php?t=858814)
[http://ubuntuforums.org/showthread.php?t=590867](http://ubuntuforums.org/showthread.php?t=590867)

---

### Post by stream303 on 2008-07-15
True enough - however I've found that Intel's powertop, which is in the download repos, can expose things that aren't normally seen, and offer suggestions to cut power use down further, such as VM Dirty Writeback times, etc.

It is definitely worth running to see what it finds.  It will cycle through a few suggestions if you leave it running for about a minute.  I think it would expecially useful to those who want to compile their own kernels, but you can change a few things from an end-user standpoint.

Note that you have to run powertop as root, ie sudo powertop.  Fortunately, this isn't something you normally leave running except to just gather the initial information it provides.

---

### Post by Oscar Pradilla on 2008-07-15
well this is what i've donde and make it run between 30 - 40 C better than the last time

1. Install Powersaved 
2. sudo gedit /etc/init.d/rc
3. Change then Concurrency=none   for Concurrency=shell

It runs much better, but the video output....grrr..can't get it right, after installing with envyg i've got the white screen.... and can't make it work....


I'm gonna try other distro and i will tell you...if not...mac os again..

---

### Post by spencercarran on 2008-07-15
> **Oscar Pradilla said:**
> well this is what i've donde and make it run between 30 - 40 C better than the last time

1. Install Powersaved 
2. sudo gedit /etc/init.d/rc
3. Change then Concurrency=none   for Concurrency=shell

It runs much better, but the video output....grrr..can't get it right, after installing with envyg i've got the white screen.... and can't make it work....


I'm gonna try other distro and i will tell you...if not...mac os again..
Well, OSX is a great operating system too, and I think if you really want to you can play around in the command line (it is derived from BSD, after all). You might want to experiment around with Solaris or FreeBSD if the heating is too big an issue; I don't have much experience here but I've heard that the heating tends to be a Linux thing.

---

### Post by Oscar Pradilla on 2008-07-15
Well i'm back on mac os, runs really good, but it' s not what i want...miss you ubuntu...lets hope that next one will be better

I will run ubuntu under virtual machine which one do you recomend?

1. VMfusion
2. Virtualbox
3. Parallels

TKS

---

### Post by hansdown on 2008-07-15
> **Oscar Pradilla said:**
> Well i'm back on mac os, runs really good, but it' s not what i want...miss you ubuntu...lets hope that next one will be better

I will run ubuntu under virtual machine which one do you recomend?

1. VMfusion
2. Virtualbox
3. Parallels

TKS

Hope You're able to come back Oscar Pradilla.

---

### Post by hajk on 2008-07-16
I'm sorry to hear about the temperature problems the OP is having with his MBP -- the more so, since I know from experience that it can be very different. 

For the record: I have a 15" 2.4GHz MBP 4,1 (Penryn) with 4GB RAM, on which I dual-boot Mac OS X and GNU/Linux (using the rEFIt boot manager). I've been experimenting a bit with versions of GNU/Linux, having used both Ubuntu Hardy 8.04 and Debian testing (with a smidgen of unstable) -- I've found very little difference between the two, especially since some of the Ubuntu installation tools have migrated upstream to the Debian installer. My current installation is Debian, using the 2.6.25-amd 64-bit kernel.

My MBP has been switched on for several hours as I write this, it sitting on a flat wooden tabletop (which is not the greatest surface for cooling): it is slightly warm to the touch on the LHS of the palm rest (above the HD); the bottom is likewise warm (not hot) near the power connector. The CPU frequency monitor shows both CPUs running at 800MHz (33%) most of the time; the hddtemp monitor shows the HD temperature as 40 deg C (just a bit above body temperature) and the CPUs at 32 deg C (room temperature is 23 deg C). The Airport (Broadcom 4328 rev 05) wireless is not used (although the modules are loaded and the wlan0 interface is available), connecting instead through the Ethernet port to a wireless bridge (due to WAP/WAP2 problems). 

For reference, I'll show the output of lsmod```

henk@mbp:~$ lsmod
Module                  Size  Used by
coretemp               13056  0 
ssb                    39684  0 
nvidia               8114064  26 
ndiswrapper           226944  0 
rfcomm                 46112  0 
l2cap                  29696  5 rfcomm
ppdev                  13832  0 
parport_pc             34344  0 
lp                     17540  0 
parport                44848  3 ppdev,parport_pc,lp
acpi_cpufreq           14096  2 
cpufreq_userspace       9092  0 
cpufreq_stats          10528  0 
cpufreq_powersave       6272  0 
cpufreq_ondemand       13712  1 
freq_table              9728  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative    13320  0 
ipv6                  294120  22 
loop                   23044  0 
firewire_sbp2          22808  0 
snd_hda_intel         414296  2 
snd_pcm_oss            46752  0 
snd_pcm                88072  2 snd_hda_intel,snd_pcm_oss
snd_mixer_oss          21376  1 snd_pcm_oss
snd_seq_dummy           8580  0 
snd_seq_oss            36736  0 
snd_seq_midi           13376  0 
snd_rawmidi            31008  1 snd_seq_midi
uvcvideo               59656  0 
snd_seq_midi_event     12544  2 snd_seq_oss,snd_seq_midi
compat_ioctl32         13184  1 uvcvideo
snd_seq                58912  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29328  2 snd_pcm,snd_seq
snd_seq_device         12948  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
videodev               38528  2 uvcvideo,compat_ioctl32
usbhid                 49632  0 
hci_usb                21148  2 
i2c_i801               15260  0 
snd                    66888  13 snd_hda_intel,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
v4l1_compat            16516  2 uvcvideo,videodev
hid                    44736  1 usbhid
i2c_core               30752  2 nvidia,i2c_i801
pcspkr                  7808  0 
iTCO_wdt               17360  0 
bluetooth              65444  7 rfcomm,l2cap,hci_usb
video                  27412  8 
output                  8704  1 video
ff_memless             10248  1 usbhid
soundcore              13088  1 snd
snd_page_alloc         15120  2 snd_hda_intel,snd_pcm
battery                14208  0 
ac                      9344  0 
button                 13856  0 
intel_agp              34160  0 
evdev                  17408  21 
jfs                   169296  1 
nls_base               13444  1 jfs
ide_cd_mod             41504  0 
cdrom                  39464  1 ide_cd_mod
sd_mod                 33728  3 
piix                   12808  0 [permanent]
ide_pci_generic         9476  0 [permanent]
ata_piix               28932  3 
ide_core              138160  3 ide_cd_mod,piix,ide_pci_generic
ata_generic            13572  0 
firewire_ohci          27908  0 
firewire_core          45920  2 firewire_sbp2,firewire_ohci
sky2                   53636  0 
crc_itu_t               6656  1 firewire_core
libata                166064  2 ata_piix,ata_generic
scsi_mod              170488  3 firewire_sbp2,sd_mod,libata
dock                   16288  1 libata
pcmcia                 45080  1 ssb
pcmcia_core            46500  1 pcmcia
firmware_class         14976  1 pcmcia
ehci_hcd               40076  0 
uhci_hcd               29472  0 
thermal                26656  0 
processor              49388  4 acpi_cpufreq,thermal
fan                    10760  0
```
Note the cpufreq-related modules that seem to be doing a super job of keeping my MBP cool. I haven't bothered to monitor fan speed, since I can barely hear them spin even with my ears close to the keyboard. This is confirmed by```
  
henk@mbp:~$ acpi -V
     Battery 0: Full, 98%
  AC Adapter 0: on-line
     Cooling 0: Processor 0 of 10
     Cooling 1: Processor 0 of 10
```
which shows the fans at their lowest settings (about 2000RPM, confirmed with the istat widget in Mac OS X).

Needless to say, I'm very pleased with this, the more so since all of the cpufreq stuff works out-of-the-box. I would encourage the OP to check his system to see whether acpi, cpufreq-utils and the like are properly installed (if necessary verify with an installation of Debian testing).

---

### Post by Oscar Pradilla on 2008-07-16
Well i can tell you that i can't wait this weekend... i'm gonna format my laptop again, to run ubuntu, but from the last post i want to know 

1. what is this **installation of Debian testing**
2. what is you power configuration, i mean,., you use powernow or powersaved or cpufreq or cpudyn....please help me...

3. How do you get video output from your mac, i have this video card 
 Chipset Model:	ATY,RadeonX1600
  Type:	Display
  Bus:	PCIe
  PCIe Lane Width:	x16
  VRAM (Total):	256 MB
  Vendor:	ATI (0x1002)
  Device ID:	0x71c5
  Revision ID:	0x0000
  ROM Revision:	113-xxxxxx-086
  EFI Driver Version:	01.00.086

Tks a lot

---

### Post by cyberdork33 on 2008-07-16
> **Oscar Pradilla said:**
> Well i'm back on mac os, runs really good, but it' s not what i want...miss you ubuntu...lets hope that next one will be better

I will run ubuntu under virtual machine which one do you recomend?

1. VMfusion
2. Virtualbox
3. Parallels

TKS
My ranking:
1. VirtualBox
2. VMWare Fusion
3. Parallels

stream, 
I would never recommend against PowerTop. It is of course how most of the power saving techniques I linked to were found.

Hajk,
You are a small minority from my experience here. It doesn't seem that you have really done anything special either is what's weird about it.

---

### Post by hajk on 2008-07-16
> **Oscar Pradilla said:**
> 
1. what is this **installation of Debian testing**
Well, "seek and ye shall find" the internet way (i.e. use Google). I'm not pushing the use of another OS in this Ubuntu forum, but you could try and do a trial install of Debian testing just to see that your MBP can run cool. Once that's confirmed (a big if), then you can try and duplicate settings on your Ubuntu installation.> 
2. what is you power configuration, i mean,., you use powernow or powersaved or cpufreq or cpudyn....please help me...For starters, you can compare the output of the "lsmod" command on your own system with that in my post -- do you see any mention of cpufreq there? If not, then you might look for a suitable package to install (use the search function in Synaptics). It is also possible that you have messed your system up by installing all sorts of packages, you could consider doing a clean reinstall.> 
3. How do you get video output from your mac, i have this video card 
 Chipset Model:	ATY,RadeonX1600
  Type:	Display
  Bus:	PCIe
  PCIe Lane Width:	x16
  VRAM (Total):	256 MB
  Vendor:	ATI (0x1002)
  Device ID:	0x71c5
  Revision ID:	0x0000
  ROM Revision:	113-xxxxxx-086
  EFI Driver Version:	01.00.086
You should consult the various MacBook Pro wikis, your machine is an older model that should be supported; there is also a new driver "radeonhd" for ATI cards that may be applicable to your machine (you may need to upgrade the kernel to 2.6.25, check backports).

I give all this advice in the hope that you will consider getting your MBP to run with Ubuntu an interesting challenge, for which you cannot wholly rely on other people giving you solution recipes. If you're not really interested in meeting such a challenge (and doing whatever it takes to surmount the problems), then you could still run Ubuntu in a VM... I like to use VMware Fusion for that running under Mac OS X: everything in Ubuntu works out-of-the-box, except a few key codes that are easily fixed.

---

### Post by hajk on 2008-07-16
> **cyberdork33 said:**
> 
Hajk,
You are a small minority from my experience here. It doesn't seem that you have really done anything special either is what's weird about it.
Yeah, guilty as charged... could somebody running Ubuntu Hardy on a 4,1 MBP compare the output of "lsmod" with that in my earlier post? Does Ubuntu use the cpufreq modules? If not, there might be the key to the heat solution...

---

### Post by fxjr on 2008-07-18
Hi, all!

I have a macbook (not a pro) with ubuntu 8.04.1. And I can notice that it runs so cool or maybe even cooler than when running with osx.
I can only say this by puting my hands in the keyboard and seeing that it is not hot, only on the left size near charger but on osx it is also hot in this area.

Unfortunately, I can't get cpu temps because coretemp module on ubuntu doesn't recognize the model 17 45nm cpu. I'd like to know how do you get a module which works with macbook 4,1. This is the ubuntu bug handling this issue:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/235119](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/235119)


As was pointed out, I can barely hear the fans, which is nice. But does linux speed up my fans automatically or do I need to modprobe applesmc? I heard about crashs because of this module and so I didn't want to load it.

I'm liking very much Ubuntu on my macbook. Today the only problem I see is that sound is too low on ubuntu compared to osx. But of course this is another issue. Just talked here wondering if you have any idea if this could be fixed/improved or if I have to live with that.

Thanks in advance.

---

### Post by Oscar Pradilla on 2008-07-18
i can tell you..don't mess with that.... it work fine just that, i've done the test, it will keep it HD temp max 41, Core 35, something i don't know...62-95 

I also have GREAT GREAT NEWS !!!

once again i'm on ubuntu (just ubuntu, not dual boot) i've tried this morning, and video output works just great...

is nice to be back....

---

