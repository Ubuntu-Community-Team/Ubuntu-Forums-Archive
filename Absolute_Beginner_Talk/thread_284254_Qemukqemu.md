---
title: "Qemu/kqemu"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by delphiguy on 2006-10-25
Cheers,

I just installed QEMU in my Ubuntu 6.06 by following the instructions at this link [http://maconstuff.blogspot.com/2006/06/how-to-run-windows-xp-under-ubuntu.html](http://maconstuff.blogspot.com/2006/06/how-to-run-windows-xp-under-ubuntu.html)

But while installing WindowsXP on QEMU I noticed that it is just too slow, and I read from that same link that by installing KQEMU will greatly increase the performance.

So I attempted to install it on my system by following the instructions given at this link [http://www.ubuntuforums.org/showthread.php?t=187413](http://www.ubuntuforums.org/showthread.php?t=187413) which basically says that I need to download the installation script.
So that is what I did.  But when I tried to run the script from terminal I got this error:

delphiguy@zion:/mystuffs/WindowsXP$ sudo ./install_qemu.sh
Your Ubuntu release is: Dapper Drake 6.06
Is this correct? y
Would you like to download QEMU from the CVS (Unstable)? y
Installing Dependencies...
Reading package lists... Done
Building dependency tree... Done
libsdl1.2debian is already the newest version.
build-essential is already the newest version.
zlib1g-dev is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libsdl1.2-dev: Depends: libglu1-mesa-dev but it is not going to be installed or
                          libglu-dev
E: Broken packages
ERROR: Unable to Install Dependencies.

Did I do something wrong here??? What do I have to do to make this work?

Thanks in advanced.

---

### Post by Bachstelze on 2006-10-25
I suggest trying VMWare instead, I found it to be much faster than QEMU.

---

### Post by TitusDalwards on 2006-10-25
you didn't do anything wrong, it just needs some depencies.you have to install these first.

and i am agree with HymnToLife about VmWare

---

### Post by delphiguy on 2006-10-25
I did tried VMWare-Player but I cant seem to make it work on my system, here is the text of vmware.log.

Oct 25 23:09:39: vmx| Log for VMware Player pid=11624 version=1.0.2 build=build-29634 option=Release
Oct 25 23:09:39: vmx| Command line: "/usr/lib/vmware/bin/vmware-vmx" "-@" "pipe=/tmp/vmware-delphiguy/vmx12a70b1f3192426d;vm=12a70b1f3192426d" "/media/dropzone/WindowsXP/WindowsXP.vmx"
Oct 25 23:09:39: vmx| UI Connecting to pipe '/tmp/vmware-delphiguy/vmx12a70b1f3192426d' with user '(null)'
Oct 25 23:09:39: vmx| Using system libcrypto, version 90703F
Oct 25 23:09:39: vmx| pcpu #0 CPUID numEntries=1 AuthcAMDenti
Oct 25 23:09:39: vmx| pcpu #0 CPUID version=0x20ff0 id1.edx=0x78bfbff id1.ecx=0x1 id1.ebx=0x800
Oct 25 23:09:39: vmx| pcpu #0 CPUID id80.eax=80000018 id81.edx=0xe3d3fbff id81.ecx=0x0
Oct 25 23:09:39: vmx| CPUID id1.edx: 0x78bfbff id1.ecx: 0x1 id81.edx: 0xe3d3fbff id81.ecx: 0
Oct 25 23:09:39: vmx| CPUID id88.ecx: 0 id88.edx: 0
Oct 25 23:09:39: vmx| Setup symlink /var/run/vmware/%2fmedia%2fdropzone%2fWindowsXP%2fWindowsXP%2evmx -> /var/run/vmware/delphiguy/11624
Oct 25 23:09:39: vmx| ACL_InitCapabilities: here 1 (bug 63252)
Oct 25 23:09:39: vmx| changing directory to /media/dropzone/WindowsXP/.
Oct 25 23:09:39: vmx| Config file: /media/dropzone/WindowsXP/WindowsXP.vmx
Oct 25 23:09:39: vmx| FILEIO: Unknown filesystem 0x65735546 for directory /media/dropzone/WindowsXP. Using non-linking locking.
Oct 25 23:09:40: vmx| FILEIO: Unknown filesystem 0x65735546 for directory /media/dropzone/WindowsXP. Using non-linking locking.
Oct 25 23:09:40: vmx| FILEIO: Unknown filesystem 0x65735546 for directory /media/dropzone/WindowsXP. Using non-linking locking.
Oct 25 23:09:40: vmx| LOG failed to remove /media/dropzone/WindowsXP/vmware-2.log failed: No such file or directory
Oct 25 23:09:40: vmx| changing directory to /media/dropzone/WindowsXP/.
Oct 25 23:09:40: vmx| VMXVmdbCbVmVmxExecState: Exec state change requested to state poweredOn without reset
Oct 25 23:09:40: vmx| TOOLS delaying state change request to state 4
Oct 25 23:09:40: vmx| PowerOn
Oct 25 23:09:40: vmx| Host ACPI: can't find SRAT
Oct 25 23:09:40: vmx| DISKUTIL: Offline toolsVersion = 0
Oct 25 23:09:40: vmx| UPGRADE: VM is non-painful guest winXPHome: It is alright to upgrade HW with out-of-date tools
Oct 25 23:09:40: vmx| Msg_Hint: msg.upgrade.legacyVM (shown)
Oct 25 23:09:40: vmx| FILEIO: Unknown filesystem 0x65735546 for directory /media/dropzone/WindowsXP. Using non-linking locking.
Oct 25 23:09:40: vmx| FILEIO: Unknown filesystem 0x65735546 for directory /media/dropzone/WindowsXP. Using non-linking locking.
Oct 25 23:09:40: vmx| FILEIO: Unknown filesystem 0x65735546 for directory /media/dropzone/WindowsXP. Using non-linking locking.
Oct 25 23:09:40: vmx| Resuming virtual machine from /media/dropzone/WindowsXP/WindowsXP.vmss
Oct 25 23:09:40: vmx| DUMPER: restoring checkpoint version 7
Oct 25 23:09:40: vmx| HOST sysname Linux, nodename zion, release 2.6.15-27-386, version #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006, machine i686, hz=250
Oct 25 23:09:40: vmx| DICT --- USER PREFERENCES
Oct 25 23:09:40: vmx| DICT       pref.grabOnKeyPress = FALSE
Oct 25 23:09:40: vmx| DICT       pref.eula.0.appName = VMware Player
Oct 25 23:09:40: vmx| DICT   pref.eula.0.buildNumber = 29634
Oct 25 23:09:40: vmx| DICT            pref.eula.size = 1
Oct 25 23:09:40: vmx| DICT    pref.autoFitFullScreen = fitHostToGuest
Oct 25 23:09:40: vmx| DICT     pref.view.navBar.type = favorites
Oct 25 23:09:40: vmx| DICT     pref.mruDest0.present = FALSE
Oct 25 23:09:40: vmx| DICT  pref.mruDest0.destString = 
Oct 25 23:09:40: vmx| DICT        pref.mruDest0.user = 
Oct 25 23:09:40: vmx| DICT     pref.mruDest1.present = FALSE
Oct 25 23:09:40: vmx| DICT  pref.mruDest1.destString = 
Oct 25 23:09:40: vmx| DICT        pref.mruDest1.user = 
Oct 25 23:09:40: vmx| DICT     pref.mruDest2.present = FALSE
Oct 25 23:09:40: vmx| DICT  pref.mruDest2.destString = 
Oct 25 23:09:40: vmx| DICT        pref.mruDest2.user = 
Oct 25 23:09:40: vmx| DICT     pref.mruDest3.present = FALSE
Oct 25 23:09:40: vmx| DICT  pref.mruDest3.destString = 
Oct 25 23:09:40: vmx| DICT        pref.mruDest3.user = 
Oct 25 23:09:40: vmx| DICT     pref.mruDest4.present = FALSE
Oct 25 23:09:40: vmx| DICT  pref.mruDest4.destString = 
Oct 25 23:09:40: vmx| DICT        pref.mruDest4.user = 
Oct 25 23:09:40: vmx| DICT     pref.mruDest5.present = FALSE
Oct 25 23:09:40: vmx| DICT  pref.mruDest5.destString = 
Oct 25 23:09:40: vmx| DICT        pref.mruDest5.user = 
Oct 25 23:09:40: vmx| DICT     pref.mruDest6.present = FALSE
Oct 25 23:09:40: vmx| DICT  pref.mruDest6.destString = 
Oct 25 23:09:40: vmx| DICT        pref.mruDest6.user = 
Oct 25 23:09:40: vmx| DICT     pref.mruDest7.present = FALSE
Oct 25 23:09:40: vmx| DICT  pref.mruDest7.destString = 
Oct 25 23:09:40: vmx| DICT        pref.mruDest7.user = 
Oct 25 23:09:40: vmx| DICT       webUpdate.checkLast = 1161705988
Oct 25 23:09:40: vmx| DICT pref.vmplayer.vmPos0.index = 0
Oct 25 23:09:40: vmx| DICT pref.vmplayer.vmPos0.vmPath = /vm/#e5e98301ae5dfa07/
Oct 25 23:09:40: vmx| DICT pref.vmplayer.vmPos0.geometry = 728x458+599+131
Oct 25 23:09:40: vmx| DICT --- USER DEFAULTS
Oct 25 23:09:40: vmx| DICT --- HOST DEFAULTS
Oct 25 23:09:40: vmx| DICT        vmplayer.searchbar = TRUE
Oct 25 23:09:40: vmx| DICT    vmnet1.hostonlyaddress = 192.168.1.1
Oct 25 23:09:40: vmx| DICT    vmnet1.hostonlynetmask = 255.255.255.0
Oct 25 23:09:40: vmx| DICT          control.fullpath = /usr/bin/vmware-cmd
Oct 25 23:09:40: vmx| DICT             loop.fullpath = /usr/bin/vmware-loop
Oct 25 23:09:40: vmx| DICT            dhcpd.fullpath = /usr/bin/vmnet-dhcpd
Oct 25 23:09:40: vmx| DICT                    libdir = /usr/lib/vmware
Oct 25 23:09:40: vmx| DICT           vmware.fullpath = /usr/bin/vmware
Oct 25 23:09:40: vmx| DICT --- SITE DEFAULTS
Oct 25 23:09:40: vmx| DICT                  tag.help = introduction.htm
Oct 25 23:09:40: vmx| DICT   tag.configurationEditor = config_editor_newvm.htm
Oct 25 23:09:40: vmx| DICT             tag.ideConfig = devices_virtualdrive.htm
Oct 25 23:09:40: vmx| DICT          tag.floppyConfig = devices_floppy.htm
Oct 25 23:09:40: vmx| DICT           tag.mouseConfig = devices_mouse.htm
Oct 25 23:09:40: vmx| DICT             tag.netConfig = devices_netadapter.htm
Oct 25 23:09:40: vmx| DICT        tag.parallelConfig = devices_parallel.htm
Oct 25 23:09:40: vmx| DICT          tag.serialConfig = devices_serial.htm
Oct 25 23:09:40: vmx| DICT           tag.soundConfig = devices_sound.htm
Oct 25 23:09:40: vmx| DICT             tag.memConfig = configvm_memory.htm
Oct 25 23:09:40: vmx| DICT            tag.miscConfig = configvm.htm
Oct 25 23:09:40: vmx| DICT             tag.usbConfig = devices_usb.htm
Oct 25 23:09:40: vmx| DICT         tag.displayConfig = configvm_display-problems.htm
Oct 25 23:09:40: vmx| DICT                 tag.tools = vmtools.htm
Oct 25 23:09:40: vmx| DICT --- COMMAND LINE
Oct 25 23:09:40: vmx| DICT             gui.available = TRUE
Oct 25 23:09:40: vmx| DICT --- CONFIGURATION
Oct 25 23:09:40: vmx| DICT               displayName = Windows XP
Oct 25 23:09:40: vmx| DICT                   guestOS = winxphome
Oct 25 23:09:40: vmx| DICT                   memsize = 64
Oct 25 23:09:40: vmx| DICT           ide0:0.fileName = WindowsXP.vmdk
Oct 25 23:09:40: vmx| DICT           ide1:0.fileName = WindowsXP.iso
Oct 25 23:09:40: vmx| DICT            config.version = 8
Oct 25 23:09:40: vmx| DICT         virtualHW.version = 3
Oct 25 23:09:40: vmx| DICT     MemAllowAutoScaleDown = FALSE
Oct 25 23:09:40: vmx| DICT               MemTrimRate = -1
Oct 25 23:09:40: vmx| DICT             uuid.location = 56 4d f1 42 b0 5f b7 dc-89 83 41 fc 61 bc 03 04
Oct 25 23:09:40: vmx| DICT                 uuid.bios = 56 4d f1 42 b0 5f b7 dc-89 83 41 fc 61 bc 03 04
Oct 25 23:09:40: vmx| DICT               uuid.action = create
Oct 25 23:09:40: vmx| DICT        checkpoint.vmState = WindowsXP.vmss
Oct 25 23:09:40: vmx| DICT         ethernet0.present = TRUE
Oct 25 23:09:40: vmx| DICT  ethernet0.connectionType = nat
Oct 25 23:09:40: vmx| DICT     ethernet0.addressType = generated
Oct 25 23:09:40: vmx| DICT ethernet0.generatedAddress = 00:0c:29:bc:03:04
Oct 25 23:09:40: vmx| DICT ethernet0.generatedAddressOffset = 0
Oct 25 23:09:40: vmx| DICT               usb.present = TRUE
Oct 25 23:09:40: vmx| DICT             sound.present = TRUE
Oct 25 23:09:40: vmx| DICT             scsi0.present = FALSE
Oct 25 23:09:40: vmx| DICT          scsi0.virtualdev = lsilogic
Oct 25 23:09:40: vmx| DICT           scsi0:0.present = FALSE
Oct 25 23:09:40: vmx| DICT        scsi0:0.deviceType = disk
Oct 25 23:09:40: vmx| DICT              scsi0:0.mode = persistent
Oct 25 23:09:40: vmx| DICT              scsi0:0.redo = 
Oct 25 23:09:40: vmx| DICT      scsi0:0.writeThrough = FALSE
Oct 25 23:09:40: vmx| DICT    scsi0:0.startConnected = FALSE
Oct 25 23:09:40: vmx| DICT           scsi0:1.present = FALSE
Oct 25 23:09:40: vmx| DICT           floppy0.present = FALSE
Oct 25 23:09:40: vmx| DICT            ide0:0.present = TRUE
Oct 25 23:09:40: vmx| DICT            ide0:1.present = FALSE
Oct 25 23:09:40: vmx| DICT            ide1:1.present = FALSE
Oct 25 23:09:40: vmx| DICT            ide1:0.present = TRUE
Oct 25 23:09:40: vmx| DICT         ide1:0.deviceType = cdrom-image
Oct 25 23:09:40: vmx| DICT         ide1:0.autodetect = TRUE
Oct 25 23:09:40: vmx| DICT     ide1:0.startConnected = TRUE
Oct 25 23:09:40: vmx| DICT               ide0:0.redo = 
Oct 25 23:09:40: vmx| DICT          sound.virtualDev = es1371
Oct 25 23:09:40: vmx| DICT --- USER DEFAULTS
Oct 25 23:09:40: vmx| DICT --- HOST DEFAULTS
Oct 25 23:09:40: vmx| DICT        vmplayer.searchbar = TRUE
Oct 25 23:09:40: vmx| DICT    vmnet1.hostonlyaddress = 192.168.1.1
Oct 25 23:09:40: vmx| DICT    vmnet1.hostonlynetmask = 255.255.255.0
Oct 25 23:09:40: vmx| DICT          control.fullpath = /usr/bin/vmware-cmd
Oct 25 23:09:40: vmx| DICT             loop.fullpath = /usr/bin/vmware-loop
Oct 25 23:09:40: vmx| DICT            dhcpd.fullpath = /usr/bin/vmnet-dhcpd
Oct 25 23:09:40: vmx| DICT                    libdir = /usr/lib/vmware
Oct 25 23:09:40: vmx| DICT           vmware.fullpath = /usr/bin/vmware
Oct 25 23:09:40: vmx| DICT --- SITE DEFAULTS
Oct 25 23:09:40: vmx| DICT                  tag.help = introduction.htm
Oct 25 23:09:40: vmx| DICT   tag.configurationEditor = config_editor_newvm.htm
Oct 25 23:09:40: vmx| DICT             tag.ideConfig = devices_virtualdrive.htm
Oct 25 23:09:40: vmx| DICT          tag.floppyConfig = devices_floppy.htm
Oct 25 23:09:40: vmx| DICT           tag.mouseConfig = devices_mouse.htm
Oct 25 23:09:40: vmx| DICT             tag.netConfig = devices_netadapter.htm
Oct 25 23:09:40: vmx| DICT        tag.parallelConfig = devices_parallel.htm
Oct 25 23:09:40: vmx| DICT          tag.serialConfig = devices_serial.htm
Oct 25 23:09:40: vmx| DICT           tag.soundConfig = devices_sound.htm
Oct 25 23:09:40: vmx| DICT             tag.memConfig = configvm_memory.htm
Oct 25 23:09:40: vmx| DICT            tag.miscConfig = configvm.htm
Oct 25 23:09:40: vmx| DICT             tag.usbConfig = devices_usb.htm
Oct 25 23:09:40: vmx| DICT         tag.displayConfig = configvm_display-problems.htm
Oct 25 23:09:40: vmx| DICT                 tag.tools = vmtools.htm
Oct 25 23:09:40: vmx| DICT --- GLOBAL SETTINGS
Oct 25 23:09:40: vmx| Msg_Hint: msg.guestos.xp (shown)
Oct 25 23:09:40: vmx| WSSCAN: reserved mem (in MB) min=32 max=928 recommended=928
Oct 25 23:09:40: vmx|         hostMem=1024 maxAllowedAll=4096 maxAllowedVM=3600
Oct 25 23:09:40: vmx|         totOverhead=16
Oct 25 23:09:40: vmx| WSSCAN: used rec mem (in MB) 928
Oct 25 23:09:40: vmx| WSSCAN: Overhead 22769 paged 5150 nonpaged 4096 maxFBSize
Oct 25 23:09:40: vmx| WSSCAN 1 1 237568 -1 237568 -1 50 0
Oct 25 23:09:40: vmx| LICENSE: Running in restricted mode
Oct 25 23:09:40: vmx| STATDECLGROUP stats Root "" null
Oct 25 23:09:40: vmx| Host CPUID features: version 0x20ff0 id1.edx 0x78bfbff id1.ecx 0x1 id81.edx 0xe3d3fbff id81.ecx 0x0
Oct 25 23:09:40: vmx| CPU.cpuFeatures = 0xd83dffd0
Oct 25 23:09:40: vmx| CPUID after masking: version 0x20ff0 id1.edx 0x78bfbff id1.ecx 0x1 id81.edx 0xe3d3fbff id81.ecx 0x0 id88.ecx 0x0
Oct 25 23:09:40: vmx| CPU.cpuFeatures = 0xd83dffd0
Oct 25 23:09:40: vmx| APIC: Local APIC at 0xfee00000
Oct 25 23:09:40: vmx| KHZEstimate 1808360
Oct 25 23:09:40: vmx| MHZEstimate 1808
Oct 25 23:09:40: vmx| NumVCPUs 1
Oct 25 23:09:40: vmx| UUID: location-UUID is 56 4d 44 22 f2 e8 3e 0b-d7 65 70 56 15 42 d3 53
Oct 25 23:09:40: vmx| UUID: canonical path is /media/dropzone/WindowsXP/WindowsXP.vmx
Oct 25 23:09:40: vmx| UUID: location-UUID is 56 4d 44 22 f2 e8 3e 0b-d7 65 70 56 15 42 d3 53
Oct 25 23:09:40: vmx| UUID: Writing uuid.bios 56 4d 44 22 f2 e8 3e 0b-d7 65 70 56 15 42 d3 53
Oct 25 23:09:40: vmx| UUID: Writing uuid.location 56 4d 44 22 f2 e8 3e 0b-d7 65 70 56 15 42 d3 53
Oct 25 23:09:40: vmx| MM: Using partialmap, 16384 pages AC 0 CE 1 TM 0 DOHU 0
Oct 25 23:09:40: vmx| MStat: Creating Stat vm.uptime
Oct 25 23:09:40: vmx| AIOGNRC: Starting 4 I/O threads.
Oct 25 23:09:40: vmx| DISK: OPEN ide0:0 '/media/dropzone/WindowsXP/WindowsXP.vmdk' persistent R[(null)]
Oct 25 23:09:40: vmx| FILEIO: Unknown filesystem 0x65735546 for directory /media/dropzone/WindowsXP. Using non-linking locking.
Oct 25 23:09:40: vmx| FILEIO: Unknown filesystem 0x65735546 for directory /media/dropzone/WindowsXP. Using non-linking locking.
Oct 25 23:09:40: vmx| FILEIO: Unknown filesystem 0x65735546 for directory /media/dropzone/WindowsXP. Using non-linking locking.
Oct 25 23:09:41: vmx| FILEIO: Unknown filesystem 0x65735546 for directory /media/dropzone/WindowsXP. Using non-linking locking.
Oct 25 23:09:41: vmx| DISKLIB-DSCPTR: Opened [0]: "WindowsXP.vmdk" (0xa)
Oct 25 23:09:41: vmx| DISKLIB-LINK  : Opened '/media/dropzone/WindowsXP/WindowsXP.vmdk' (0xa): monolithicSparse, 41943040 sectors / 20480 Mb.
Oct 25 23:09:41: vmx| DISKLIB-LIB   : Opened "/media/dropzone/WindowsXP/WindowsXP.vmdk" (flags 0xa).
Oct 25 23:09:41: vmx| DISK: OPEN '/media/dropzone/WindowsXP/WindowsXP.vmdk' Geo (41610/16/63) BIOS Geo (2610/255/63) freeSpace=51635Mb
Oct 25 23:09:41: vmx| TimeTracker host to guest rate conversion 18240820985833 @ 1808360000Hz -> 18240820985833 @ 1808360000Hz
Oct 25 23:09:41: vmx| TimeTracker host to guest rate conversion ((x * 2147483648) >> 31) + 0
Oct 25 23:09:41: vmx| MStat: Creating Stat vm.heartbeat
Oct 25 23:09:41: vmx| DISKUTIL: ide0:0 : toolsVersion = 0
Oct 25 23:09:41: vmx| DISKUTIL: Offline toolsVersion = 0
Oct 25 23:09:41: vmx| TOOLS INSTALL initializing state to IDLE on power on.
Oct 25 23:09:41: vmx| XINFO X fd is 46
Oct 25 23:09:41: vmx| XINFO depth 24 bpp 32 class 4
Oct 25 23:09:41: vmx| VT redirected kernel output to /dev/tty1
Oct 25 23:09:41: vmx| USB: Initializing UHCI host controller
Oct 25 23:09:41: vmx| USB: Initializing USB Generic backend
Oct 25 23:09:41: vmx| VMMon_GetkHzEstimate: Calculated 1808242 kHz
Oct 25 23:09:41: vmx| VLANCE: send cluster threshold is 80, size = 2 recalcInterval is 2 ticks
Oct 25 23:09:41: vmx| Ethernet0 MAC Address: 00:0c:29:42:d3:53
Oct 25 23:09:41: vmx| VMXNET: send cluster threshold is 80, size = 2 recalcInterval is 2 ticks, dontClusterSize is 128
Oct 25 23:09:41: vmx| E1000: checksum cycles/kB: C=919 asm=293
Oct 25 23:09:41: vmx| CPT: Restoring checkpoint /media/dropzone/WindowsXP/WindowsXP.vmss
Oct 25 23:09:41: vmx| DUMPER: restoring checkpoint version 7
Oct 25 23:09:41: vmx| checkpointCPUID: cpt vendor AuthcAMDenti host vendor AuthcAMDenti
Oct 25 23:09:41: vmx| checkpointCPUID: cpt family 0f model 2f0 host family 0f model 2f0
Oct 25 23:09:41: vmx| checkpointCPUID: cpt  id1.ecx 1 id1.edx 78bfbff id81.ecx 0 id81.edx e3d3fbff
Oct 25 23:09:41: vmx| checkpointCPUID: host id1.ecx 1 id1.edx 78bfbff id81.ecx 0 id81.edx e3d3fbff
Oct 25 23:09:41: vmx| DUMPER: item eip [0,-1] in group cpu not used
Oct 25 23:09:41: vmx|   restoring Snapshot
Oct 25 23:09:41: vmx| DUMPER: item cfgFile [-1,-1] in group Snapshot not used
Oct 25 23:09:41: vmx| DUMPER: item nvramFile [-1,-1] in group Snapshot not used
Oct 25 23:09:41: vmx|   restoring memory
Oct 25 23:09:41: vmx| Mapped mainmem as pageable
Oct 25 23:09:41: vmx| Msg_Reset:
Oct 25 23:09:41: vmx| ----------------------------------------
Oct 25 23:09:41: vmx| Opened paging file /media/dropzone/WindowsXP/WindowsXP.vmem
Oct 25 23:09:41: vmx| Lazy Restore with prefetch of 64 MB
Oct 25 23:09:41: vmx| Msg_Hint: msg.mainmem.lazyResumeHint (shown)
Oct 25 23:09:41: vmx| Could not mmap paging file : No such device
Oct 25 23:09:41: vmx| Could not mmap paging file : No such device
Oct 25 23:09:41: vmx| Caught signal 11 -- tid 11624
Oct 25 23:09:41: vmx| SIGNAL: eip 0x823d6a0 esp 0xbfca8a10 ebp 0xbfca8aa8
Oct 25 23:09:41: vmx| SIGNAL: eax 0x20000 ebx 0x0 ecx 0x20000 edx 0x0 esi 0x0 edi 0xffbff000
Oct 25 23:09:41: vmx| SIGNAL: stack 0xbfca8a10 : 0x00000001 0xbfca8a70 0xffbff000 0x0806aa8e
Oct 25 23:09:41: vmx| SIGNAL: stack 0xbfca8a20 : 0x00000000 0x00cfe390 0x085ee380 0x0858e210
Oct 25 23:09:41: vmx| SIGNAL: stack 0xbfca8a30 : 0x00000000 0xb7dba0d4 0xbfca8a78 0x080b7b9c
Oct 25 23:09:41: vmx| SIGNAL: stack 0xbfca8a40 : 0x0858e210 0xffffffff 0x00000000 0x0858e210
Oct 25 23:09:41: vmx| SIGNAL: stack 0xbfca8a50 : 0x00000000 0x00000000 0x00000020 0x00008a78
Oct 25 23:09:41: vmx| SIGNAL: stack 0xbfca8a60 : 0xb7cfc34a 0xb7dc5320 0x0858e210 0x0858e210
Oct 25 23:09:41: vmx| SIGNAL: stack 0xbfca8a70 : 0x00000000 0x00000000 0x00000020 0x00000000
Oct 25 23:09:41: vmx| SIGNAL: stack 0xbfca8a80 : 0x00000001 0xffffffff 0x00000000 0x00000001
Oct 25 23:09:41: vmx| Backtrace:
Oct 25 23:09:41: vmx| Backtrace[0] 0xbfca85e8 eip 0x805a640 
Oct 25 23:09:41: vmx| Backtrace[1] 0xbfca86b8 eip 0x80ea0ea 
Oct 25 23:09:41: vmx| Backtrace[2] 0xbfca8728 eip 0x80e9e7a 
Oct 25 23:09:41: vmx| Backtrace[3] 0xbfca8aa8 eip 0xffffe420 
Oct 25 23:09:41: vmx| Backtrace[4] 0xbfca8ad8 eip 0x823d289 
Oct 25 23:09:41: vmx| Backtrace[5] 0xbfca8b08 eip 0x823e08a 
Oct 25 23:09:41: vmx| Backtrace[6] 0xbfca8b38 eip 0x819a160 
Oct 25 23:09:41: vmx| Backtrace[7] 0xbfca8e98 eip 0x80a616c 
Oct 25 23:09:41: vmx| Backtrace[8] 0xbfca8eb8 eip 0x80a4f4b 
Oct 25 23:09:41: vmx| Backtrace[9] 0xbfca8ed8 eip 0x80c43f2 
Oct 25 23:09:41: vmx| Backtrace[10] 0xbfca8ef8 eip 0x80bc118 
Oct 25 23:09:41: vmx| Backtrace[11] 0xbfca8f28 eip 0x80bbfec 
Oct 25 23:09:41: vmx| Backtrace[12] 0xbfca8f78 eip 0x804fb52 
Oct 25 23:09:41: vmx| Backtrace[13] 0xbfca8f98 eip 0x804eb64 
Oct 25 23:09:41: vmx| Backtrace[14] 0xbfca8ff8 eip 0xb7cadea2 
Oct 25 23:09:41: vmx| Backtrace[15] 00000000 eip 0x804dd61 
Oct 25 23:09:41: vmx| Unexpected signal: 11.
Oct 25 23:09:41: vmx| Backtrace:
Oct 25 23:09:41: vmx| Backtrace[0] 0xbfca81c8 eip 0x805a640 
Oct 25 23:09:41: vmx| Backtrace[1] 0xbfca85e8 eip 0x80bc86b 
Oct 25 23:09:41: vmx| Backtrace[2] 0xbfca86b8 eip 0x80ea14d 
Oct 25 23:09:41: vmx| Backtrace[3] 0xbfca8728 eip 0x80e9e7a 
Oct 25 23:09:41: vmx| Backtrace[4] 0xbfca8aa8 eip 0xffffe420 
Oct 25 23:09:41: vmx| Backtrace[5] 0xbfca8ad8 eip 0x823d289 
Oct 25 23:09:41: vmx| Backtrace[6] 0xbfca8b08 eip 0x823e08a 
Oct 25 23:09:41: vmx| Backtrace[7] 0xbfca8b38 eip 0x819a160 
Oct 25 23:09:41: vmx| Backtrace[8] 0xbfca8e98 eip 0x80a616c 
Oct 25 23:09:41: vmx| Backtrace[9] 0xbfca8eb8 eip 0x80a4f4b 
Oct 25 23:09:41: vmx| Backtrace[10] 0xbfca8ed8 eip 0x80c43f2 
Oct 25 23:09:41: vmx| Backtrace[11] 0xbfca8ef8 eip 0x80bc118 
Oct 25 23:09:41: vmx| Backtrace[12] 0xbfca8f28 eip 0x80bbfec 
Oct 25 23:09:41: vmx| Backtrace[13] 0xbfca8f78 eip 0x804fb52 
Oct 25 23:09:41: vmx| Backtrace[14] 0xbfca8f98 eip 0x804eb64 
Oct 25 23:09:41: vmx| Backtrace[15] 0xbfca8ff8 eip 0xb7cadea2 
Oct 25 23:09:41: vmx| Backtrace[16] 00000000 eip 0x804dd61 
Oct 25 23:09:41: vmx| Core dump limit is 0 kb.
Oct 25 23:09:41: vmx| Attempting to dump core...
Oct 25 23:09:41: MMPageWalker| Entering MM LazySave Loop
Oct 25 23:09:42: vmx| Child process 11639 failed to dump core (status 0x6).
Oct 25 23:09:42: vmx| Msg_Post: Error
Oct 25 23:09:42: vmx| [msg.log.error.unrecoverable] VMware Player unrecoverable error: (vmx)
Oct 25 23:09:42: vmx| Unexpected signal: 11.
Oct 25 23:09:42: vmx| [msg.panic.haveLog] A log file is available in "/media/dropzone/WindowsXP/vmware.log".  [msg.panic.requestSupport.withLog] Please request support and include the contents of the log file.  [msg.panic.requestSupport.linux] 
Oct 25 23:09:42: vmx| To collect files to submit to VMware support, run vm-support.
Oct 25 23:09:42: vmx| [msg.panic.response] We will respond on the basis of your support entitlement.
Oct 25 23:09:42: vmx| ----------------------------------------
Oct 25 23:09:54: IO#2| VTHREAD watched thread 0 "vmx" died
Oct 25 23:09:54: IO#3| VTHREAD watched thread 0 "vmx" died
Oct 25 23:09:54: IO#0| VTHREAD watched thread 0 "vmx" died
Oct 25 23:09:54: IO#1| VTHREAD watched thread 0 "vmx" died
Oct 25 23:09:54: MMPageWalker| VTHREAD watched thread 0 "vmx" died


I know im doing something wrong here but I dont know what.

---

### Post by Bachstelze on 2006-10-25
Unless I'm very mistaken, VMWare Player won't let you create virtual machines. you should go with VMWare Server, which works like a charm if you follow the Wiki page about it.

---

### Post by Ben Sprinkle on 2006-10-25
Here be a little surprise. :)

[http://www.slax.org/modules.php?category=system&id=1657&name=VMWare+Workstation](http://www.slax.org/modules.php?category=system&id=1657&name=VMWare+Workstation)
[http://www.slax.org/modules.php?category=system&id=641&name=VMwareWorkstn+5.5.1+for+slax+5.0.6](http://www.slax.org/modules.php?category=system&id=641&name=VMwareWorkstn+5.5.1+for+slax+5.0.6)

Get the required things to extract modules.

---

### Post by nickburns on 2006-10-25
I have tried qemu and failed too.  But I found this great vmware server software and love it.  You can get it working in a few minutes really easy.

Follow these simple instructions to get it up and running....

[http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware]("http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware")

---

### Post by delphiguy on 2006-10-25
Wow amazing at last I was able to install VMWare on my system thanks alot for the help guys, Im installing XP on my VM now.

Again thanks a lot for the help.

---

