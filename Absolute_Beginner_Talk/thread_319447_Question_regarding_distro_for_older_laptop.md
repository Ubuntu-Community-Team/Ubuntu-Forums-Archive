---
title: "Question regarding distro for older laptop"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by Atreus12 on 2006-12-15
I have an older compaq laptop with the following specs:
Pendium III Processor (I don't know the speed, but slow)
64 MB RAM
5.5 GB Hard drive
Windows 98
DVD drive
10/100 ethernet card / no wireless

The computer runs ....so.... slow on windows 98, but compaq doesn't provide any software disks so reformating to windows 98 is not possible.

I would like to be able to do some web surfing, do word processing, have some mp3 playing ability, and be able to watch DVD's on trips. It currently does all of these on windows 98, just not very well.

I chose Ubuntu 6.06 for my desktop because Ubuntu is easy to set up out of the box. You just install it, and most everything works. I am not a computer science major, so I need something that is fairly easy to use.

So what distribution of linux would fit this application? Is there a 'small' version of Ubuntu that could run on this computer?

Thanks

-Andrew

Edit: As I mentioned, Compaq doesn't provide cd's of software, so I won't have any drivers.

---

### Post by Bachstelze on 2006-12-15
You could try Xubuntu (Ubuntu with the XFCE desktop environment instead of GNOME), which is much lighter.

---

### Post by taurus on 2006-12-15
You probably have two options: either install Xubuntu or install the server version and install fluxbox on it.  If not, you can always go for the fluxbuntu if you don't want to go with server + fluxbox.  Then, you can use automatix2 to install all the codecs for your media stuff.  And for word processing, stay away from OpenOffice.  Instead, use abiword which is not bad at all...  You can use swiftfox for surfing the net instead of firefox.

---

### Post by Atreus12 on 2006-12-15
Oh, by the way I forgot to say that I attempted to boot to the Ubuntu 6.06 live cd...and it didn't actually load. I got part way, and then the screen was just back with no progress being made. Think Xubuntu will work?

-Andrew

---

### Post by Bachstelze on 2006-12-15
Pretty normal, the harware is not sufficient to run a Live CD, get a Xubuntu Alternate CD.

---

### Post by hyper_ch on 2006-12-15
I would recommend trying to get another 64mb ram from ebay - that will boot your preformance massively and shouldn't be more than $ 20.-

---

### Post by derjames on 2006-12-16
or perhaps use PuppyLinux([http://www.puppylinux.com/](http://www.puppylinux.com/)) or 
DSL [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

### Post by AndrewB on 2006-12-16
I'll second Damn Small Linux for older hardware. I'd also recommend increasing your ram to at least 256MB if you want to play with Ubuntu.

---

### Post by scrooge_74 on 2006-12-16
I have a friend with a similar case, what he did was to use the Debian stable version CDs and then pick specific items he needed to get it working.

But DLS or Puppy should run on a system like that

---

### Post by Atreus12 on 2006-12-16
Ok, I tried Xubuntu 6.06 alternate cd (because I only have 64 mb ram) but it only boots to terminal mode. Does the xubuntu alternate only install a terminal mode? Or is something wrong?

I get an error on bootup that says something like error with accpi and bios. This is an unrecoverable error.

-Andrew

---

### Post by az on 2006-12-16
> **Atreus12 said:**
> Ok, I tried Xubuntu 6.06 alternate cd (because I only have 64 mb ram) but it only boots to terminal mode. Does the xubuntu alternate only install a terminal mode? Or is something wrong?

I get an error on bootup that says something like error with accpi and bios. This is an unrecoverable error.

-Andrew

But do you end up with a login prompt?  If so, try

sudo apt-get install xubuntu-desktop

to see if the whole things actually got installed.

Also, more ram is well worth the investment.  You have a decent machine and many people run Ubuntu (not Xubuntu) on a pentium II - it runs fine.  But you need more ram.

If I was looking for a laptop, I probably would buy a used one like your's and buy as much ram as I could get into it.  It should run fine in the long term, too.

---

### Post by Atreus12 on 2006-12-16
> **azz said:**
> But do you end up with a login prompt?  If so, try

sudo apt-get install xubuntu-desktop

to see if the whole things actually got installed.

Also, more ram is well worth the investment.  You have a decent machine and many people run Ubuntu (not Xubuntu) on a pentium II - it runs fine.  But you need more ram.

If I was looking for a laptop, I probably would buy a used one like your's and buy as much ram as I could get into it.  It should run fine in the long term, too.

The first time I booted up I was logged in as 'oem' and created another username. I can now boot up to the username I created.

I typed in
sudo apt-get install xubuntu-desktop
and got a prompt for a password. I typed the password and nothing happened. It went to the next line. I tried it twice just to make sure.

The only command I actually had sucess in using was 'vi'. I tried sudo apt-get update but again, nothing happened. I tried cd, ls etc. to try to list the directory but nothing happens.

Commands like 'lsusb' or 'lspci' work though. That is about the extent of my command line knowledge.

I verified the iso before burning.


-Andrew

---

### Post by Simanek on 2006-12-16
I had Ubuntu running on an old Gateway laptop with a Pentium II 198MHz and 196MB RAM. It ran poorly and I eventually moved to Xubuntu (which ran very well). I think your biggest problem is the RAM. A Pentium III should handle Ubuntu just fine if you could get your RAM up to 256 or even 512MB. That's not that old of a machine and my old Gateway was maxed-out at 196, so you should at the very least be able to go that high. Ubuntu isn't that much of a resource hog. Please don't get the idea that Ubuntu won't run on a Pentium III. Unfortunately there are too many people online that view Pentium IVs as antiques.

---

### Post by Nopposan on 2006-12-16
Hi.  I also have an old Compaq; an Armada 7750MT to be exact.  I did buy another 64 mb of RAM, but that meant buying two 32mb chips and they were more expensive than buying one 64mb would have been.  Anyway, I'm getting to some answers to your question but I must say that I doubt you'll be happy with Xfce on your machine if you've only got 64mb; 'could be that your speedy pentium III will give you a fair deal though so it's worth a try.  Xfce is heftier than fluxbox but in my experience switching to blackbox, which fluxbox is based on, didn't really speed up things to where I noticed.  Puppy Linux and DSL have the ability to load completely into RAM and thereby achieve amazing speed relative to reading off a hard drive as needed.  However, the Puppy website recommends at least 128mb RAM, I think.  Puppy uses something called jvwm I think, whereas DSL uses fluxbox.  You can install any of these window managers or desktops on your slow box using any Linux distribution that you can put on there.  (SuSE 10.0 works if you use the minimal gui option that installs a couple of different window managers including fvwm and blackbox, if I'm not mistaken.)  Graphical installers are oh so shiny and spiffy, but they often won't work on your old slow box 'cause they won't allow you to easily configure your screen or they just won't run on such a low memory.  I can run Xfld, which is the Xfce Live Demo, but I can't run the Xubuntu graphical installer 'cause it defaults a 24 bit color depth and I don't know how to change this to 16 before booting.

O.K., your question now . . . 'sorry, I was just so happy to find someone in this boat with me.

If you installed Xubuntu and you're getting an ACPI or BIOS error then you need to know exactly what that error is before you'll be able to figure out exactly what to do about it.  There are all kinds of ways to get to the files you've installed and figure out what went wrong, but I don't know them all; I only know what's easy and obvious for me.  Your mileage may vary, as they say.  What I'd do is run the following command after you log in on the command line.  (You are able to do that, right?  If it won't let you do that then stop reading my answer and move on to something smarter.)  Here's the command following the $:

yourhost@you~$ sudo dmesg > whatevercallitbootmesgmaybe

That'll save all of that jibberishy stuff that floats by while you're booting to a file that you can read with a text editor.

Now, you need a text editor.  There's probably a text editor that you can run from a command line like this:

yourhost@you~$ sudo cmdtextedit whatevercallitbootmesgmaybe

Then you could view your file and press q to quit the text editor.  However, I don't know what command line text editor might be packed with Ubuntu or even if there is one; 'probably is though.  Anyway, the dmesg output will have clues as to what's going wrong and you could post those suspicions here if you can get that output off your hard drive and into our web forum.  One way might be to use a text based web browser like lynx . . . ([http://en.wikipedia.org/wiki/Lynx_%28web_browser%29](http://en.wikipedia.org/wiki/Lynx_%28web_browser%29))
and then use lynx to attach the dmesg output file to your post on this forum.

What I'd do is butn a DSL cd and then use that cd to grab the file and look at it using a text editor called beaver.  I'd also use the DSL cd to do the following 'cause, like I said, I don't know how to edit text files via the command line terminal:

damnsmall@linux~$ cd /hda1/boot/grub
damnsmall@linux~$ sudo beaver menu.lst

You won't have to type a password 'cause that's a DSL default.  You'll get a popup window for beaver and you'll be able to edit your menu.lst file so that you can overwrite it.  What you want to change is the last part where it doesn't have the # signs and it lists the kernel to be booted.  It'll look something like this:

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

You want to make it look like this:

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash acpi=off
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

You could also try adding the commands noapic or nolapic to that line.  Then you'll save it under the exact same name (overwrite).  Don't worry, 'cause the previous version will automatically be saved as menu.lst~ and you can restore it with the cp command if necessary.

After you've tried out turning off acpi you can reboot your computer and see if you get the graphical login screen and Xfce.  If not, then you might want to try turning off your PnP BIOS with the command pnpbios=off.

You could probably also accomplish these things through the grub menu by pressing some key before grub begins; I'm not familiar with that process but it might be a whole lot easier than what I've done before.  All I know is that what I did worked for me most of the time.  I'm still having a problem with my cdrom not being recognized but maybe I should just see if running the update will fix that.

Oh yeah, you should be aware that Compaq/HP used to have something called a DIAGS partition at the beginning of the hard drive; if pressing F10 (or whatever key it's supposed to be) doesn't get you into the BIOS then the DIAGS partition has probably been wiped out.  Restoring that is beyond me right now.

Good luck.

---

### Post by Nopposan on 2006-12-16
Oh, 'didn't realize it wasn't allowing you to use the simple commands.

Did you preface them with the sudo command?  Well, that shouldn't matter really though, not for cd or ls anyway.

Hmph.

'Sorry.  'Don't know why it's doing that to you.  How cruel and unusual.

---

### Post by az on 2006-12-17
> **Atreus12 said:**
> The first time I booted up I was logged in as 'oem' and created another username. I can now boot up to the username I created.

I typed in
sudo apt-get install xubuntu-desktop
and got a prompt for a password. I typed the password and nothing happened. It went to the next line. I tried it twice just to make sure.

The only command I actually had sucess in using was 'vi'. I tried sudo apt-get update but again, nothing happened. I tried cd, ls etc. to try to list the directory but nothing happens.

Commands like 'lsusb' or 'lspci' work though. That is about the extent of my command line knowledge.

I verified the iso before burning.


-Andrew
It sounds like it did not install properly.  Why did you use the OEM mode?

The installer may not work properly with such a small amount of ram.  When the installer runs out of ram, it can be quite ungraceful or even fail silently.

---

### Post by Atreus12 on 2006-12-17
> **azz said:**
> It sounds like it did not install properly.  Why did you use the OEM mode?


Just followed the instructions. It said to log in as oem the first time, then create other users. I'll try to post the dmesg output.

-Andrew

---

### Post by az on 2006-12-17
> **Atreus12 said:**
> Just followed the instructions. It said to log in as oem the first time, then create other users. I'll try to post the dmesg output.

-Andrew

Yes, but you pick between a regular install and an OEM install when you start the installer.  You use an OEM install when you want to install Ubuntu on many identical machines.  That way, the end-user picks their username and password the first time they use they newly-bought machine.  This is different than the regular install which sets your username and password during the install.

---

### Post by Nopposan on 2006-12-17
Azz is right.  I installed using the Alternate CD and the standard install mode, although I added acpi=off to the boot options by first pressing F6.

Install worked well, but I just had to change the xorg.conf to 16 bit color depth.

---

### Post by Nopposan on 2006-12-17
I installed "Xubuntu" on just 64mb once and it went well even though I only have a 166MHz processor.  That was with Breezy though, I think; 'don't know if maybe the installer has changed to use more memory.

---

### Post by Nopposan on 2006-12-17
You may be better off forgetting about dmesg and just reinstalling.  It takes awhile but requires little interaction from you; you can go off and have a coffee and/or read the newspaper, then come back and try your first login again.  Probably you'll be pleased with the result.

---

### Post by Atreus12 on 2006-12-17
Well it sounds like I somehow installed the wrong type? I don't know how that happened, but I guess I will try again. I am currently posting from the laptop, running the live cd of DSL. Having never used it before I am impressed. I was expecting a terminal type install, not a full graphical os.

Ok. I will attempt reinstallation of Xubuntu from the alternate cd. Am I correct that I have to use the alternate cd to install with 64 mb ram? Or should I not be using the alternate cd?

I'll let you guys know in about an hour (hopefully)

-Andrew

---

### Post by Atreus12 on 2006-12-17
Well, I guess somehow on the first installation I screwed up. I am now on Xubuntu, but uhhh. It's pretty slow. I need to think about it a little bit. Either I need more ram, or I should just go back to DSL. Hmmm.

But at any rate, I am still getting an ACPI / BIOS error on bootup. Here is the memory info, followed by dmesg

$free
> 
             total       used       free     shared    buffers     cached
Mem:         61472      57832       3640          0        980      20884
-/+ buffers/cache:      35968      25504
Swap:       176672      64912     111760



$dmesg

> 
[17179569.184000] Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000eb400 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 0000000003ff0000 (usable)
[17179569.184000]  BIOS-e820: 0000000003ff0000 - 0000000003fffc00 (ACPI data)
[17179569.184000]  BIOS-e820: 0000000003fffc00 - 0000000004000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 63MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 16368
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 12272 pages, LIFO batch:1
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f7190
[17179569.184000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x03ffae1b
[17179569.184000] ACPI: FADT (v001 COMPAQ CPQB1B2  0x06040000 PTL  0x000f4240) @ 0x03ffae47
[17179569.184000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x03fffbd9
[17179569.184000] ACPI: DSDT (v001 PTLTD    DSDT   0x06040000 MSFT 0x0100000b) @ 0x00000000
[17179569.184000] ACPI: Vendor "PTLTD " System "  DSDT  " Revision 0x6040000 has a known ACPI BIOS problem.
[17179569.184000] ACPI: Reason: Multiple problems. This is a non-recoverable error
[17179569.184000] ACPI: Disabling ACPI support
[17179569.184000] Allocating PCI resources starting at 10000000 (gap: 04000000:fbf80000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (01081000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 256 (order: 8, 4096 bytes)
[    0.000000] Detected 593.249 MHz processor.
[   14.610219] Using tsc for high-res timesource
[   14.611642] Console: colour VGA+ 80x25
[   14.611996] Dentry cache hash table entries: 16384 (order: 4, 65536 bytes)
[   14.612271] Inode-cache hash table entries: 8192 (order: 3, 32768 bytes)
[   14.619817] Memory: 54544k/65472k available (1976k kernel code, 10520k reserved, 606k data, 288k init, 0k highmem)
[   14.619830] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   14.697805] Calibrating delay using timer specific routine.. 1188.07 BogoMIPS (lpj=2376149)
[   14.697894] Security Framework v1.0.0 initialized
[   14.697917] SELinux:  Disabled at boot.
[   14.697958] Mount-cache hash table entries: 512
[   14.698202] CPU: After generic identify, caps: 0387f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   14.698223] CPU: After vendor identify, caps: 0387f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   14.698248] CPU: L1 I cache: 16K, L1 D cache: 16K
[   14.698257] CPU: L2 cache: 256K
[   14.698264] CPU serial number disabled.
[   14.698272] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   14.698312] mtrr: v2.0 (20020519)
[   14.698326] CPU: Intel Pentium III (Coppermine) stepping 03
[   14.698338] Enabling fast FPU save and restore... done.
[   14.698346] Enabling unmasked SIMD FPU exception support... done.
[   14.698357] Checking 'hlt' instruction... OK.
[   14.714312] checking if image is initramfs... it is
[   17.228261] Freeing initrd memory: 6617k freed
[   17.266761] NET: Registered protocol family 16
[   17.266852] EISA bus registered
[   17.274605] PCI: PCI BIOS revision 2.10 entry at 0xfd9af, last bus=2
[   17.274625] PCI: Using configuration type 1
[   17.275116] ACPI: Subsystem revision 20051216
[   17.275124] ACPI: Interpreter disabled.
[   17.275133] Linux Plug and Play Support v0.97 (c) Adam Belay
[   17.275167] pnp: PnP ACPI: disabled
[   17.275178] PnPBIOS: Scanning system for PnP BIOS support...
[   17.275226] PnPBIOS: Found PnP BIOS installation structure at 0xc00f7110
[   17.275237] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x85c0, dseg 0x400
[   17.282588] PnPBIOS: 17 nodes reported by PnP BIOS; 17 recorded by driver
[   17.282628] PCI: Probing PCI hardware
[   17.282640] PCI: Probing PCI hardware (bus 00)
[   17.283053] PCI quirk: region 1000-103f claimed by PIIX4 ACPI
[   17.283064] PCI quirk: region 1040-104f claimed by PIIX4 SMB
[   17.283421] Boot video device is 0000:01:00.0
[   17.284624] PCI: Using IRQ router PIIX/ICH [8086/7110] at 0000:00:07.0
[   17.287369] pnp: 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[   17.287381] pnp: 00:0a: ioport range 0x1000-0x103f has been reserved
[   17.287403] pnp: 00:0a: ioport range 0x1040-0x104f has been reserved
[   17.287418] pnp: 00:0b: ioport range 0x3f0-0x3f0 has been reserved
[   17.287428] pnp: 00:0b: ioport range 0x3f1-0x3f1 has been reserved
[   17.288004] PCI: Bridge: 0000:00:01.0
[   17.288013]   IO window: 2000-2fff
[   17.288024]   MEM window: f4100000-f5ffffff
[   17.288034]   PREFETCH window: 14000000-140fffff
[   17.288045] PCI: Bus 2, cardbus bridge: 0000:00:08.0
[   17.288053]   IO window: 00001800-000018ff
[   17.288062]   IO window: 00001c00-00001cff
[   17.288072]   PREFETCH window: 10000000-11ffffff
[   17.288082]   MEM window: 12000000-13ffffff
[   17.288116] PCI: Found IRQ 9 for device 0000:00:08.0
[   17.288135] PCI: Sharing IRQ 9 with 0000:00:09.0
[   17.288149] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   17.288286] Simple Boot Flag at 0x38 set to 0x1
[   17.289391] audit: initializing netlink socket (disabled)
[   17.289424] audit(1166379045.992:1): initialized
[   17.289742] VFS: Disk quotas dquot_6.5.1
[   17.289806] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   17.289941] Initializing Cryptographic API
[   17.289954] io scheduler noop registered
[   17.289977] io scheduler anticipatory registered
[   17.289992] io scheduler deadline registered
[   17.290020] io scheduler cfq registered
[   17.290030] Limiting direct PCI/PCI transfers.
[   17.290459] isapnp: Scanning for PnP cards...
[   17.644946] isapnp: No Plug & Play device found
[   17.691270] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   17.692731] serio: i8042 AUX port at 0x60,0x64 irq 12
[   17.693009] serio: i8042 KBD port at 0x60,0x64 irq 1
[   17.693118] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[   17.693341] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   17.700342] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   17.701851] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   17.701986] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   17.701998] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   17.702377] mice: PS/2 mouse device common for all mice
[   17.702812] EISA: Probing bus 0 at eisa.0
[   17.702831] Cannot allocate resource for EISA slot 1
[   17.702841] Cannot allocate resource for EISA slot 2
[   17.702884] EISA: Detected 0 cards.
[   17.702997] NET: Registered protocol family 2
[   17.729581] input: AT Translated Set 2 keyboard as /class/input/input0
[   17.745705] IP route cache hash table entries: 1024 (order: 0, 4096 bytes)
[   17.746054] TCP established hash table entries: 4096 (order: 2, 16384 bytes)
[   17.746116] TCP bind hash table entries: 4096 (order: 2, 16384 bytes)
[   17.746176] TCP: Hash tables configured (established 4096 bind 4096)
[   17.746185] TCP reno registered
[   17.746398] TCP bic registered
[   17.746418] NET: Registered protocol family 1
[   17.746433] NET: Registered protocol family 8
[   17.746440] NET: Registered protocol family 20
[   17.746493] Using IPI Shortcut mode
[   17.746595] Freeing unused kernel memory: 288k freed
[   17.897432] Capability LSM initialized
[   19.287979] PIIX4: IDE controller at PCI slot 0000:00:07.1
[   19.288016] PIIX4: chipset revision 1
[   19.288024] PIIX4: not 100% native mode: will probe irqs later
[   19.288044]     ide0: BM-DMA at 0x1050-0x1057, BIOS settings: hda:DMA, hdb:pio
[   19.288080]     ide1: BM-DMA at 0x1058-0x105f, BIOS settings: hdc:DMA, hdd:pio
[   19.288105] Probing IDE interface ide0...
[   19.573566] hda: IBM-DARA-206000, ATA DISK drive
[   20.245841] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   20.246256] Probing IDE interface ide1...
[   20.981451] hdc: LG DVD-ROM DRN-8080B, ATAPI CD/DVD-ROM drive
[   21.656762] ide1 at 0x170-0x177,0x376 on irq 15
[   21.675898] hda: max request size: 128KiB
[   21.711242] hda: 11733120 sectors (6007 MB) w/418KiB Cache, CHS=12416/15/63, UDMA(33)
[   21.711264] hda: cache flushes not supported
[   21.711675]  hda: hda1 hda2 < hda5 >
[   21.767374] hdc: ATAPI 24X DVD-ROM drive, 512kB Cache, UDMA(33)
[   21.767399] Uniform CD-ROM driver Revision: 3.20
[   22.209631] usbcore: registered new driver usbfs
[   22.210495] usbcore: registered new driver hub
[   22.216331] USB Universal Host Controller Interface driver v2.3
[   22.217198] PCI: Found IRQ 5 for device 0000:00:07.2
[   22.217261] PCI: Sharing IRQ 5 with 0000:00:0a.0
[   22.217288] uhci_hcd 0000:00:07.2: UHCI Host Controller
[   22.218293] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[   22.218319] uhci_hcd 0000:00:07.2: irq 5, io base 0x00001060
[   22.219137] hub 1-0:1.0: USB hub found
[   22.219170] hub 1-0:1.0: 2 ports detected
[   22.514365] Attempting manual resume
[   22.606921] EXT3-fs: mounted filesystem with ordered data mode.
[   22.621254] kjournald starting.  Commit interval 5 seconds
[   43.693003] Linux agpgart interface v0.101 (c) Dave Jones
[   43.704058] agpgart: Detected an Intel 440BX Chipset.
[   43.708991] agpgart: AGP aperture is 64M @ 0xf8000000
[   45.366779] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[   45.441544] PCI: Found IRQ 5 for device 0000:00:0a.0
[   45.441566] PCI: Sharing IRQ 5 with 0000:00:07.2
[   45.476946] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   46.017117] Real Time Clock Driver v1.12
[   46.138824] Synaptics Touchpad, model: 1, fw: 5.5, id: 0x1d56b1, caps: 0x904713/0x4006
[   46.173639] input: SynPS/2 Synaptics TouchPad as /class/input/input1
[   46.299365] parport: PnPBIOS parport detected.
[   46.299460] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   46.341380] PCI: Found IRQ 9 for device 0000:00:08.0
[   46.341409] PCI: Sharing IRQ 9 with 0000:00:09.0
[   46.341433] Yenta: CardBus bridge found at 0000:00:08.0 [0e11:b103]
[   46.341456] Yenta: Enabling burst memory read transactions
[   46.341465] Yenta: Using CSCINT to route CSC interrupts to PCI
[   46.341472] Yenta: Routing CardBus interrupts to PCI
[   46.341483] Yenta TI: socket 0000:00:08.0, mfunc 0x01001002, devctl 0x64
[   46.424508] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   46.571910] Yenta: ISA IRQ mask 0x0818, PCI irq 9
[   46.571924] Socket status: 30000010
[   46.954073] input: PC Speaker as /class/input/input2
[   47.005093] Floppy drive(s): fd0 is 1.44M
[   47.023046] FDC 0 is a post-1991 82077
[   47.387242] pccard: PCMCIA card inserted into slot 0
[   47.650377] ts: Compaq touchscreen protocol output
[   47.911142] cs: IO port probe 0x100-0x3af: excluding 0x200-0x207
[   47.913292] cs: IO port probe 0x3e0-0x4ff: clean.
[   47.914175] cs: IO port probe 0x820-0x8ff: clean.
[   47.914934] cs: IO port probe 0xc00-0xcf7: clean.
[   47.915989] cs: IO port probe 0xa00-0xaff: clean.
[   47.916850] cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   47.921451] pcmcia: registering new device pcmcia0.0
[   48.415308]   ASIC rev 1,<6>eth0: Megahertz 574B at io 0x300, irq 3, hw_addr 00:50:DA:FE:D1:A3.
[   48.424106]  64K FIFO split 1:1 Rx:Tx, autoselect MII interface.
[   49.309294] lp0: using parport0 (interrupt-driven).
[   49.569593] Adding 176672k swap on /dev/hda5.  Priority:-1 extents:1 across:176672k
[   49.736217] EXT3 FS on hda1, internal journal
[   50.139805] NET: Registered protocol family 17
[   50.409676] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   50.409689] md: bitmap version 4.39
[   50.971306] eth0: found link beat
[   50.971322] eth0: autonegotiation complete: 100baseT-FD selected
[   51.776618] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[   53.091180] cdrom: open failed.
[   54.442710] NET: Registered protocol family 10
[   54.443049] lo: Disabled Privacy Extensions
[   54.443474] IPv6 over IPv4 tunneling driver
[   64.793862] eth0: no IPv6 routers present
[   75.081779] ppdev: user-space parallel port driver
[   77.468415] Compaq 12XL125 machine detected. Enabling interrupts during APM calls.
[   77.469119] apm: BIOS not found.


---

### Post by az on 2006-12-17
Yes, you need more ram.

As for the dmesg error, does it actually cause a problem?  Apm should work just as well - you should be able to hibernate using apm.  If the apm module is not working (hard to tell from the dmesg) be sure to see if you can set your bios to use apm instead of acpi.

---

### Post by Atreus12 on 2006-12-17
Seems to be working fine, just that is throws an error up on bootup. It actually says > ACPI BIOS ERROR. THIS ERROR IS UNRECOVERABLE but then proceeds to load up just fine.

I think it's ok. If it aint broke, don't fix it.

And I'm working on the ram issue.

I think this is probably the conclusion of this thread, but I just wanted to say thanks to everyone who took the time to help out a new user get linux running. 

-Andrew

---

### Post by az on 2006-12-17
> **Atreus12 said:**
> Seems to be working fine, just that is throws an error up on bootup. It actually says  but then proceeds to load up just fine.

I think it's ok. If it aint broke, don't fix it.

-Andrew

I think that message means that the ACPI functionality in the BIOS is broken (your motherboard has a bug) but it does not mean that your Ubuntu installation is broken.

---

### Post by Nopposan on 2006-12-18
'Could be.

Atreus, do you know how to get into your BIOS?  Will your computer allow you to access your BIOS?  You might decide it's prudent to reflash/update your BIOS.  I'm sure the HP website has a .exe file that will write a BIOS-flasher to a floppy for you if you run it on a Windows box.  It's a pain that they don't provide the BIOS flashing in a way that's convenient for those who are MS-free, however you're almost sure to be able to find a Windows environment that allows you to do this.  'Trouble is, floppies are very unreliable and any time you flash your BIOS you run a slight risk of totally trashing it and making your computer (permanently?) unbootable.

Cheers.

---

### Post by Nopposan on 2006-12-18
Yeah, more RAM would definitely be nicer.  It's probably not so expensive either.  However, you might want to try installing fluxbox on the Ubuntu system you've set up and see how that goes.

---

### Post by Atreus12 on 2006-12-26
Ok, back from the dead. I purchased a 256 MB stick of ram off a buddy so now I have enough ram. The question is, now that I got the ram situtation cleared up, is there a reason to stick with Xubuntu over Ubuntu?

-Andrew

---

### Post by az on 2006-12-26
> **Atreus12 said:**
> Ok, back from the dead. I purchased a 256 MB stick of ram off a buddy so now I have enough ram. The question is, now that I got the ram situtation cleared up, is there a reason to stick with Xubuntu over Ubuntu?

-Andrew

Using a Pentium III, I would just use Ubuntu, but if you find it slow, switch to Xubuntu.

---

### Post by Benchrest on 2006-12-26
I would not repeat what I have done, but only to give you an idea how things can go. I have a 1998 thinkpad celeron 433 mhz. The 4.8 gb harddrive went bad a couple of years ago so I upgraded to a 20 gb. Then a month later the Motherboard went bad. I replaced it myself.  It wasn't to expensive. I then upgraded the  the memory from 64 mg to 192 mg. I have windows 98SE and Edgy installed dual boot.  Runs great but slow. Should have saved my money and got a faster laptop. So I am against throwing money at an old laptop to get minimal improvement.

---

### Post by Nopposan on 2007-01-03
Xubuntu (Ubuntu with Xfce that's optimized for Ubuntu) is really cool!  However, it will probably require more customization and interaction from you before you'll be happy with the desktop.  If you go with Xubuntu you'll want to install Xfce-goodies and customize your Xfce menu.  After you've done this there's plenty more for you to play with.

If you're not so concerned about a modest improvement in speed and if you won't enjoy spending your time bringing more features to the desktop, then I advise you to go with Ubuntu or Kubuntu.  Xfce is a great lightweight desktop and it's a minimal desktop with optional extensions; it's very flexible, but to get all of the features that you're accustomed to in more mature full-fledged desktops will require a significant commitment of your time.  For now, I reserve Xfce for computers that truly need a faster desktop environment, and yours doesn't; yet I think that the next release of Xfce may be a real all-around alternative to Gnome/KDE.  If you're thinking of trying both Xfce and another desktop environment on the same computer then you'd do well to go with Xfce and Gnome (Ubuntu, not Kubuntu) as they share many libraries and Xubuntu's default desktop manager is GDM.

---

### Post by Nopposan on 2007-01-03
So, I guess you could just install Gnome on Xubuntu and see how it goes for you.  You don't have to reinstall.

P.S.  I was pleasantly surprised when hibernation worked on the old laptop that I installed Xubuntu on.  Check it out; you don't have to wait for bootup the next time you turn your computer on.  'Makes old machines ready for action just as fast as a newer machine rebooting.

Cheers.

---

### Post by mrcanard on 2007-01-16
Compaq, Presario, 12XL500, Celeron 766, 384m ram, about 5/6 years old.
Installed a spare 6g hdd and loaded Ubuntu 6.10 on it over this last weekend.
Took about 40 minutes to install and another 40 to update + install Automatix2.
Shut the machine down removed the cat 5 card. Inserted the Orinoco Gold card.
Less than 15 minutes after booting I had my wireless connection up.
It takes about 3 to 4 minutes to boot.
Runs comparable to w2k pro that's on the disk drive I replaced.
I'm happy about how it worked out.
BTW, I bought new restore disk a year or two ago, cost about $20.00 including shipping.
This machine sold with ME pre-installed so I don't think I'll ever use them.
Regards,

---

### Post by ABI90 on 2007-01-30
DSL or vector linux...

---

