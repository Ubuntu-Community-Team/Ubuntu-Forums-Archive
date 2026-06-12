---
title: "Suspend=Fail &amp; Coldboot problem LM16 Intel 82845G"
date: 2014-01-20
forum: Any Other OS
---

### Post by WinXpRefugee on 2014-01-20
Hello 
This is my second problem after installing LM16 MATE.
Here was my first JIC they are related which I suspect they are being a xp refugee!
[http://ubuntuforums.org/showthread.php?t=2200144](http://ubuntuforums.org/showthread.php?t=2200144)

Here is my hardware

```

computer                  
    description: Desktop Computer
    product: Dimension 2350
    vendor: Dell Computer Corporation
    version: A02
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 07W080
       vendor: Dell Computer Corporation
       physical id: 0
       version: A00
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Mitac International
          physical id: 1
          version: A02
          date: 03/24/2003
          size: 128KiB
          capacity: 192KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.20GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: 15.2.7
          slot: Socket 478
          size: 2200MHz
          capacity: 2800MHz
          width: 32 bits
          clock: 400MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: Internal Cache
             size: 8KiB
             capacity: 8KiB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: a
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous external write-back unified
     *-memory
          description: System Memory
          physical id: 20
          slot: System board or motherboard
          size: 1GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM SDRAM Synchronous 266 MHz (3.8 ns)
             product: None
             vendor: None
             physical id: 0
             serial: [REMOVED]
             slot: A0
             size: 512MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 266 MHz (3.8 ns)
             product: None
             vendor: None
             physical id: 1
             serial: [REMOVED]
             slot: A1
             size: 512MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:e8000000-ebffffff
        *-display
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:e0000000-e7ffffff memory:ee000000-ee07ffff
        *-usb:0
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:d800(size=32)
        *-usb:1
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:d000(size=32)
        *-usb:2
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:d400(size=32)
        *-usb:3
             description: USB controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:ee080000-ee0803ff
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:c000(size=4096) memory:ec000000-edffffff memory:40000000-400fffff
           *-communication
                description: Modem
                product: BCM4212 v.90 56k modem
                vendor: Broadcom Corporation
                physical id: 4
                bus info: pci@0000:01:04.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm generic bus_master cap_list
                configuration: driver=serial latency=32
                resources: irq:16 memory:ed002000-ed002fff ioport:c000(size=16)
           *-network
                description: Ethernet interface
                product: BCM4401 100Base-T
                vendor: Broadcom Corporation
                physical id: 9
                bus info: pci@0000:01:09.0
                logical name: eth0
                version: 01
                serial: [REMOVED]
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list rom ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=[REMOVED] latency=32 link=yes multicast=yes port=twisted pair speed=100Mbit/s
                resources: irq:17 memory:ed000000-ed001fff memory:40000000-40003fff
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: 82801DB (ICH4) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16) memory:40100000-401003ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:500(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=0
             resources: irq:17 ioport:e000(size=256) ioport:e400(size=64) memory:ee081000-ee0811ff memory:ee082000-ee0820ff
     *-scsi:0
          physical id: 0
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD800JB-00JJ
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 05.0
             serial: [REMOVED]
             size: 74GiB (80GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000b0f0b
           *-volume:0
                description: Linux filesystem partition
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot
                version: 1.0
                serial: [REMOVED]
                size: 243MiB
                capacity: 243MiB
                capabilities: primary bootable extended_attributes ext2 initialized
                configuration: filesystem=ext2 modified=2014-01-17 17:17:11 mount.fstype=ext2 mount.options=rw,relatime,errors=continue,user_xattr,acl state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 74GiB
                capacity: 74GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux LVM Physical Volume partition
                   physical id: 5
                   logical name: /dev/sda5
                   serial: [REMOVED]
                   size: 74GiB
                   capacity: 74GiB
                   capabilities: multi lvm2
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom:0
             description: DVD-RAM writer
             product: iHAP222   W
             vendor: ATAPI
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 7L05
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
        *-cdrom:1
             description: CD-R/CD-RW writer
             product: CD-RW  CRX216E
             vendor: SONY
             physical id: 0.1.0
             bus info: scsi@1:0.1.0
             logical name: /dev/sr1
             version: PD01
             capabilities: removable audio cd-r cd-rw
             configuration: ansiversion=5 status=nodisc

```
Overnight the computer of couse went to sleep and wouldnt wake up by pressing any keys on the keybord or moving clicking the mouse. so i used the power buton and it made all the noises that a working computer makes but no video at all waited for about a minute still no video.
Did a power off
Powered on after LM logo had black screen and mouse pointer no visible login screen. Waited moving the mouse around an I noticed that in certain places it would change to a hand so I clicked and moved it around some more was able to get the login to appear with a green tint then after some further clicking and moving around it appeared to be normal was able to log in. Apperently it is there it is just not rendered.

So now I have tried suspend and cold boot several times.
Suspend=No video Consistantly! I mean nothing the monitor shows "no signal"
Cold boot=my "mouse trick" works some of the time.

here is my xorg.conf
```

Section "Device"
    Identifier "Intel Graphics"
    Driver "intel"
    Option "AccelMethod" "uxa"
EndSection

```

---

### Post by squakie on 2014-01-20
I don't know about Mint - i know it isn't using the "new" gnome with Unity, but I know that the 845 won't run Unity.  There have also been problems reported in the past with the 845, with graphics support being minimal becuase of that GPU.  I don't know if any of this has changed or not, nor do I know how it might affect Mint.  Best bet at this point is to probably google saerch tihe following in the search string:  

linux mint 16 intal 845 graphics

and see what comes up.

EDIT:  If mint 16 is using compizx by default, I don't think the 845 will work with that either.  Someone will correct me if I'm wrong.

---

### Post by Elfy on 2014-01-20
*Thread moved to **Other OS/Distro Support**.*

---

### Post by WinXpRefugee on 2014-01-20
Crap, I guess I posted in the wrong place!!!
 Thanks Elfy
I hate to vent, but will The mint forum not as helpful as ubuntu forum for my problems.
So far mintforum 0-1 Ubuntu forum 1-0.
I may have to get better hardware that will run unity!!!!!

---

### Post by Elfy on 2014-01-20
>  I hate to vent, but will The mint forum not as helpful as ubuntu forum for my problems.Apparently so ;)

> I may have to get better hardware that will run unity!!!!! Or use something else :)

---

### Post by WinXpRefugee on 2014-01-20
[B]Elfy,
Thanks for your Response,

[/B][SIZE=2]I am getting ready for the XPocalypse this April 2014.
As my sig say's been using linux since 1/14/2014.
I do computer work/service as a hobby and need a distro that I can swich my xp people to.
It is getting harder and harder to fix xp.
Most of them run similar hardware to this machine -->something you can buy at walmart in 2007 (LOL)
I  found that most of the people that I help with their computer only use  it for web and web based email, storing digital photos and as one of the  people I help put it I cant loose my "M PEE Number 3's".
Maybe some low end games like card games Spider solitare ect.
They really don't need the power they have but hey think they need MORE?
Most  of them are like me, working people and don't have the $$$ to just go  buy an new computer or upgrade to the latest windows ver.
So I had a good freind who can use a computer he brought me his nuked (typical malware virus stuff) 
Dell 2350 P4 1GB 80GBHD running XPP32SP3
Thought he would be a good test case see if real "non geek" user could live with Linux. 

Installed [COLOR=#000080]Zorin[/COLOR] liked the look and feel but, Not enough  hardware power [SIZE=2]to display [/SIZE]"windows decorations"? 

Installed [COLOR=#FF8000]Ubuntu[/COLOR] 13.10 again [/SIZE][SIZE=2][SIZE=2]Not enough  hardware power [SIZE=2]to display GUI properly things missing not rendered.
[/SIZE][/SIZE]
Loved it on my multicore machine running from the Live DVD!
Since then someone suggested [COLOR=#a52a2a]Lubuntu [/COLOR]on the same Dell and that it works

Tried [COLOR=#4040FF]Xubuntu[/COLOR] from the live dvd it looked fine and seemed to work well.

I read a post (Some forum) about a guy kind of does tech support like I do.He set up his Sextigenarian grandma on [COLOR=#00BF00]Mint-MATE[/COLOR], and some other adventurous XP users with glowing results.

That is why I picked Mint I have had problems and have not got alot out of the support forums
I need to get adept enough to support the people I help.
If this works out well I can really help alot of people.
I took the Dell 2350 running[COLOR=#008000] Linux MINT Petra - MATE [/COLOR]to him January 18, 2014 and he is using it But I am told I should have used LTS distro by another forum.

[COLOR=#ff8c00]I am unsure what to do the forum support here has been a better experience for me.
 Most of the machines that I "fix" will probably not have the processing power to run Ubuntu GUI
Would love suggestions 
[/COLOR]
[/SIZE]

---

### Post by squakie on 2014-01-20
I would SERIOUSLY consider downloading and trying either lubuntu or even better yet xubuntu.  Xubuntu I beleive is the "thinest".  Either way, you won't have to worry about Unity - lubuntu and xubuntu use different desktop managers.  Since you like the support here (nothing against Mint - I also have a Mint 16 installation on a different box), perhaps you'd like to find an ubuntu flavor knowing you'll get support here.  The links for downloading lubuntu and xubuntu are at the top of this page under the "Ubuntu Community" option (on the bottom part of the orange colored header).  Just a thought.......  ;) ;)

EDIT:  I should add, in answer to your question at the end of your last post, the xubuntu will run great on older/smaller hardware (one of my systems is an old Dell Inspiron 8500 laptop nad it won't run "normal" Ubuntu but runs xubuntu like a champ.  There are also smaller, more lightweight linux distributions out there for small, old hardware.   I personally have never tried them, so I can't comment on them  A couple of the names I remember seeing mentioned in posts here on the ubuntu forums include DSL (Damn Small Linux) and puupylinux.  Again, I have firsthand knowledge of either of those or any of the other very lightwieght distribtuions.  Someone else will, I'm sure, post more on some of those options for you here.

---

### Post by WinXpRefugee on 2014-01-20
Squakie,
Thanks a bunch for the advice,
I am learning alot the advice I am getting seems to direct me tword xubuntu
Typical machine I seem to be working with was built 2006-2010 seems that that is the right distro for that era machine.
Do you think that is a good distro to start on, will the things I learn there apply to other distributions.
Since my end goal is to be able to be as geeky with linux as I am now with windows. (eg I can see the screen in my mind and tell you what to click)

---

### Post by WinXpRefugee on 2014-01-20
Squakie,
Thanks a bunch for the advice,
I am learning alot the advice I am getting seems to direct me tword xubuntu
Typical machine I seem to be working with was built 2006-2010 seems that that is the right distro for that era machine.
Do you think that is a good distro to start on, will the things I learn there apply to other distributions.
Since my end goal is to be able to be as geeky with linux as I am now with windows. (eg I can see the screen in my mind and tell you what to click) 
Whoha! I am getting way off Topic. (sorry)
I am going to stick it out with mint for a week or so if I cant get the suspend  and cold boot problem fixed then I will switch to Xubuntu.
Any Ideas on my issue with the susspend Cold boot problem!

---

### Post by squakie on 2014-01-20
on a laptop, suspend and resume are a hit and miss.  one thing  i would check is the size of the swap partition.  to suspend I *think* is like hibernating in that in those cases swap must normally be twie the size of physical memory with a little more added for overhead.  in a normal environment swap can be kept small, but in the case of suspend/hibernate on a laptop, it at least used to be that physical memory was just copied to/from swap with no regard to what was actually being used (I'm going back a LONG way here, so someone else can tell you if it has changed in that situation). I know there are also ways at least in some cases to restart the xserver, etc., on wake up.  I really don't remember much about that.

The choice of which version of ubuntu ("normal/lubuntu or xubunt) is really dependant on any given hardware configuation.  It's possible a ten year old platform could run todays ubuntu depending on memory, graphics, etc..  There is probably a minimum cpui requirement (I've never looked), and while an older cpu might fall in those requirements, the actual performance of the OS and espcially the graphical presentation may be, shall we say, less than desireable.  But there are also extremely inexpensive brand new EDIT: LAPTOPS that I wouldn't even attempt to install "normal" ubuntu on - I would still go with one of the lighter flavors.  The only true way to to tell is check the version of ubuntu you want to install to see what its minimum requirements are, then just try from there.  As I mentioned above, there are systems that might meet the requirements, but the cpu speed, the bus spedd, the memory speed, etc., might result in a most unsatisfactory experience!

---

### Post by squakie on 2014-01-21
> **Bill_Graves said:**
> ....I am learning alot the advice I am getting seems to direct me tword xubuntu
Typical machine I seem to be working with was built 2006-2010 seems that that is the right distro for that era machine.
Do you think that is a good distro to start on, will the things I learn there apply to other distributions....
Any Ideas on my issue with the susspend Cold boot problem!

Yes, I think xubuntu would be a good distro to start on - you should be safe with it on the hardware you mention.  There is one other thing to keep in mind regarding applying to other distributions:  each distro will have the same basic kernel, and a lot of the tools will be the same or similar.  Things like the desktop manager, the package manager, the editor, etc., may well be different since these are in no way part of the kernel.  However, the look and feel is always comfortable no matter what the desktop looks like, since it is point and click like Windows.  Menus may be different, so you may have to "hunt" to find something.  If you are comfortable with XP then actually using most modern linux distributions won't be a problem.

Just a little something (hint, hint, hint ;) ;) ) you might also want to keep in mind:  Mint is based off ubuntu, with their own specializations such as the desktop not being the current gnome (e.g., no unity).  But since it's based off ubuntu - why not go with the "base" and use one of the ubuntu flavors ;) ;)

Again - nothing against Mint.  In your situation it might be best to pick either lubuntu or xubuntu (xubuntu might be best if you want something common across everything from weak hardware to modern hardware so you don't have to support more than 1 flavor).

---

### Post by WinXpRefugee on 2014-01-27
[ 						 							]("http://ubuntuforums.org/member.php?u=1741485")[COLOR=#000000]squakie,

[/COLOR]Sorry took so long to respond have been having some account issues wanted to use a psuedomym

All the Distros I tried had same problem Video which I could fix with the creation of the .conf file
then they would not resume Tried S3 and S1 settings in BIOS.

Linux Lite OS 1.0.6 worked great out of the box. video, resume, 
 I am not sure why since it uses ubuntu as well.
had to manually install lite user manager and lite Software manager some how they did not get packaged.

I modded it with 
wiskers 
and installed 
Libre office, Banshee, shotwell, weather app 
VLC does not autoplay DVD's have to swich to the Device tab and select the Drive but then it plays 
tried tux cart for kicks (NOPE!) Unistalled it 				
Marking this as solved I am sure I will eventually figure why 1.0.6 worked and 1.0.8 did not. because I am confident that is the problem that I am having will all the latest ubuntu flavors.

---

