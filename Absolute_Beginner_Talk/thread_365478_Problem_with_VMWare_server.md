---
title: "Problem with VMWare server"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by pmillette on 2007-02-19
Hi,

This is my first post ever and not knowing exactly where to post with my problem, I decided to post here being a newbie myself.

Here is my hardware:

HP Media center PC with ADM 3800 dual core
2 gig ram
ATI Radeon XPRESS 200 graphics
250 gig HD

I installed Ubuntu 6.10 with all the updates no problem and everything works fine. I also installed VMWare server following the instructions from ubuntuguide.org and again everything works fine.

My problem is when I try to install the guest OS (Windows XP  SP2 french) at about 15% of the installation I get the following error message :

*** VMware Server internal monitor error ***
vcpu-0:FPU Safety: Error: FPU instruction executed in monitor context[#NM]: cs:eip 0x4020:0xae148 %cr0: 0x8001003b CR[0]: 0x8001003b
There is a problem in this version of VMware Server.
We rely on your feedback to improve the quality of our product. Please submit a support request that describes the problem at our Web page "http://www.vmware.com/info?id=8". Do not forget to attach the log file (/home/pmillette/Virtuel/Windows XP Professional/vmware.log) and the core file (/home/pmillette/Virtuel/Windows XP Professional/vmware-core.gz).
To collect files to submit to VMware support, run vm-support-lx.
We appreciate your feedback,
  -- the VMware Server team.

Before blaming the guest OS cd, let me elaborate on the whole process. I tried with three different Windows XP versions (Original, SP1 and SP2) either from CD or with an ISO file and I always get the same message. Now to make sure the problem is not from the guest OS, the CD or the ISO files, I did the same process on my laptop which runs the same version of Ubuntu 6.10 with all the updates and the guest OS installs and runs just fine. So the problem is somewhere with VMWare server and my machine.

Has anybody seen this problem before ? Any help will be appreciated. Also let me know if I should post elsewhere. 

I also included the log generated from the guest OS install crash :

Feb 19 16:10:16: vmx| Log for VMware Server pid=13003 version=1.0.1 build=build-29996 option=BETA
Feb 19 16:10:16: vmx| Command line: "/usr/lib/vmware/bin-debug/vmware-vmx" "-C" "-@" """" "/home/pmillette/Virtuel/Windows XP Professional/Windows XP Professional.vmx"
Feb 19 16:10:16: vmx| vmxvmdb: Index name being generated from config file
Feb 19 16:10:16: vmx| VMXVmdbConnectServerd - Trying to discover serverd
Feb 19 16:10:16: vmx| AllocTrack: Successfully initialized, pass-through mode, log level 0, log stack crawl FALSE.
Feb 19 16:10:16: vmx| AllocTrack: Options changed globally, now log level 1, log stack crawl FALSE.
Feb 19 16:10:16: vmx| MStat: Creating Stat system.cpuusage
Feb 19 16:10:16: vmx| MStat: Creating Stat system.ram
Feb 19 16:10:16: vmx| MStat: Creating Stat system.uptime
Feb 19 16:10:16: vmx| MStat: Creating Stat system.load
Feb 19 16:10:16: vmx| cpuids[0].id81.ecx = 0x3
Feb 19 16:10:16: vmx| cpuids[1].id81.ecx = 0x3
Feb 19 16:10:16: vmx| pcpu #0 CPUID numEntries=1 AuthcAMDenti
Feb 19 16:10:16: vmx| pcpu #0 CPUID version=0x20f32 id1.edx=0x178bfbff id1.ecx=0x1 id1.ebx=0x20800
Feb 19 16:10:16: vmx| pcpu #0 CPUID id80.eax=80000018 id81.edx=0xe3d3fbff id81.ecx=0x3
Feb 19 16:10:16: vmx| pcpu #1 CPUID numEntries=1 AuthcAMDenti
Feb 19 16:10:16: vmx| pcpu #1 CPUID version=0x20f32 id1.edx=0x178bfbff id1.ecx=0x1 id1.ebx=0x1020800
Feb 19 16:10:16: vmx| pcpu #1 CPUID id80.eax=80000018 id81.edx=0xe3d3fbff id81.ecx=0x3
Feb 19 16:10:16: vmx| CPUID id1.edx: 0x178bfbff id1.ecx: 0x1 id81.edx: 0xe3d3fbff id81.ecx: 0x3
Feb 19 16:10:16: vmx| CPUID id88.ecx: 0 id88.edx: 0
Feb 19 16:10:16: vmx| Setup symlink /var/run/vmware/%2Fhome%2Fpmillette%2FVirtuel%2FWindows%20XP%20Professional%2FWindows%20XP%20Professional%2Evmx -> /var/run/vmware/pmillette/13003
Feb 19 16:10:16: vmx| ACL_InitCapabilities: here 1 (bug 63252)
Feb 19 16:10:16: vmx| changing directory to /home/pmillette/Virtuel/Windows XP Professional/.
Feb 19 16:10:16: vmx| Config file: /home/pmillette/Virtuel/Windows XP Professional/Windows XP Professional.vmx
Feb 19 16:10:16: vmx| LOG failed to remove /home/pmillette/Virtuel/Windows XP Professional/vmware-2.log failed: No such file or directory
Feb 19 16:10:16: vmx| CnxAcceptConnection: Could not receive fd on 27: invalid control message
Feb 19 16:10:16: vmx| Failed to get IPC connection
Feb 19 16:10:16: vmx| Read from FIFO 32 -- connecting to serverd...
Feb 19 16:10:16: vmx| VMDB: Connected to serverd
Feb 19 16:10:16: vmx| VMXVmdbCbVmVmxExecState: Exec state change requested to state poweredOn without reset
Feb 19 16:10:16: vmx| PowerOn
Feb 19 16:10:16: vmx| Host ACPI: SRAT @ 0x7bef7140
Feb 19 16:10:16: vmx| Host ACPI: SRAT: LAPIC ID 0x00, proximity domain low 0x00
Feb 19 16:10:16: vmx| Host ACPI: SRAT: LAPIC ID 0x01, proximity domain low 0x00
Feb 19 16:10:16: vmx| Host: CPU #0 LAPIC ID 0x00, node 0x00
Feb 19 16:10:16: vmx| Host: CPU #1 LAPIC ID 0x01, node 0x00
Feb 19 16:10:16: vmx| Msg_Hint: msg.loader.debug.release (not shown)
Feb 19 16:10:16: vmx| HOST sysname Linux, nodename PC-PATRICK, release 2.6.17-11-generic, version #2 SMP Thu Feb 1 19:52:28 UTC 2007, machine i686, SMP, hz=250
Feb 19 16:10:16: vmx| DICT --- USER PREFERENCES
Feb 19 16:10:16: vmx| DICT       pref.grabOnKeyPress = FALSE
Feb 19 16:10:16: vmx| DICT    pref.autoFitFullScreen = fitHostToGuest
Feb 19 16:10:16: vmx| DICT     pref.view.navBar.type = favorites
Feb 19 16:10:16: vmx| DICT     pref.mruDest0.present = FALSE
Feb 19 16:10:16: vmx| DICT  pref.mruDest0.destString = 
Feb 19 16:10:16: vmx| DICT        pref.mruDest0.user = 
Feb 19 16:10:16: vmx| DICT     pref.mruDest1.present = FALSE
Feb 19 16:10:16: vmx| DICT  pref.mruDest1.destString = 
Feb 19 16:10:16: vmx| DICT        pref.mruDest1.user = 
Feb 19 16:10:16: vmx| DICT     pref.mruDest2.present = FALSE
Feb 19 16:10:16: vmx| DICT  pref.mruDest2.destString = 
Feb 19 16:10:16: vmx| DICT        pref.mruDest2.user = 
Feb 19 16:10:16: vmx| DICT     pref.mruDest3.present = FALSE
Feb 19 16:10:16: vmx| DICT  pref.mruDest3.destString = 
Feb 19 16:10:16: vmx| DICT        pref.mruDest3.user = 
Feb 19 16:10:16: vmx| DICT     pref.mruDest4.present = FALSE
Feb 19 16:10:16: vmx| DICT  pref.mruDest4.destString = 
Feb 19 16:10:16: vmx| DICT        pref.mruDest4.user = 
Feb 19 16:10:16: vmx| DICT     pref.mruDest5.present = FALSE
Feb 19 16:10:16: vmx| DICT  pref.mruDest5.destString = 
Feb 19 16:10:16: vmx| DICT        pref.mruDest5.user = 
Feb 19 16:10:16: vmx| DICT     pref.mruDest6.present = FALSE
Feb 19 16:10:16: vmx| DICT  pref.mruDest6.destString = 
Feb 19 16:10:16: vmx| DICT        pref.mruDest6.user = 
Feb 19 16:10:16: vmx| DICT     pref.mruDest7.present = FALSE
Feb 19 16:10:16: vmx| DICT  pref.mruDest7.destString = 
Feb 19 16:10:16: vmx| DICT        pref.mruDest7.user = 
Feb 19 16:10:16: vmx| DICT     webUpdate.checkPeriod = weekly
Feb 19 16:10:16: vmx| DICT       webUpdate.checkLast = 1171850800
Feb 19 16:10:16: vmx| DICT       pref.placement.left = 0
Feb 19 16:10:16: vmx| DICT        pref.placement.top = 51
Feb 19 16:10:16: vmx| DICT      pref.placement.right = 948
Feb 19 16:10:16: vmx| DICT     pref.placement.bottom = 597
Feb 19 16:10:16: vmx| DICT pref.console.openedObj0.present = TRUE
Feb 19 16:10:16: vmx| DICT pref.console.openedObj0.type = vm
Feb 19 16:10:16: vmx| DICT pref.console.openedObj0.path = /vm/#1976017e23179831/
Feb 19 16:10:16: vmx| DICT pref.console.openedObj0.file = /home/pmillette/Virtuel/Windows XP Professional/Windows XP Professional.vmx
Feb 19 16:10:16: vmx| DICT pref.console.openedObj0.dest = /host2/#b8ea0756f67fd895/
Feb 19 16:10:16: vmx| DICT pref.console.openedObj.maxNum = 1
Feb 19 16:10:16: vmx| DICT pref.console.currentObj.path = /vm/#036686203db3debb/
Feb 19 16:10:16: vmx| DICT pref.console.currentObj.type = home
Feb 19 16:10:16: vmx| DICT --- USER DEFAULTS
Feb 19 16:10:16: vmx| DICT --- HOST DEFAULTS
Feb 19 16:10:16: vmx| DICT    vmnet1.hostonlyaddress = 192.168.80.1
Feb 19 16:10:16: vmx| DICT     serverd.init.fullpath = /usr/lib/vmware/serverd/init.pl
Feb 19 16:10:16: vmx| DICT         authd.client.port = 902
Feb 19 16:10:16: vmx| DICT          control.fullpath = /usr/bin/vmware-cmd
Feb 19 16:10:16: vmx| DICT            authd.fullpath = /usr/sbin/vmware-authd
Feb 19 16:10:16: vmx| DICT             loop.fullpath = /usr/bin/vmware-loop
Feb 19 16:10:16: vmx| DICT                    libdir = /usr/lib/vmware
Feb 19 16:10:16: vmx| DICT           vmware.fullpath = /usr/bin/vmware
Feb 19 16:10:16: vmx| DICT    vmnet1.hostonlynetmask = 255.255.255.0
Feb 19 16:10:16: vmx| DICT                     vmdir = /home/pmillette/Virtuel
Feb 19 16:10:16: vmx| DICT            dhcpd.fullpath = /usr/bin/vmnet-dhcpd
Feb 19 16:10:16: vmx| DICT          serverd.fullpath = /usr/sbin/vmware-serverd
Feb 19 16:10:16: vmx| DICT            datastore.name = local
Feb 19 16:10:16: vmx| DICT       datastore.localpath = /home/pmillette/Virtuel/
Feb 19 16:10:16: vmx| DICT --- SITE DEFAULTS
Feb 19 16:10:16: vmx| DICT                  tag.help = introduction.htm
Feb 19 16:10:16: vmx| DICT   tag.configurationEditor = config_editor_newvm.htm
Feb 19 16:10:16: vmx| DICT             tag.ideConfig = devices_virtualdrive.htm
Feb 19 16:10:16: vmx| DICT          tag.floppyConfig = devices_floppy.htm
Feb 19 16:10:16: vmx| DICT           tag.mouseConfig = devices_mouse.htm
Feb 19 16:10:16: vmx| DICT             tag.netConfig = devices_netadapter.htm
Feb 19 16:10:16: vmx| DICT        tag.parallelConfig = devices_parallel.htm
Feb 19 16:10:16: vmx| DICT          tag.serialConfig = devices_serial.htm
Feb 19 16:10:16: vmx| DICT           tag.soundConfig = devices_sound.htm
Feb 19 16:10:16: vmx| DICT             tag.memConfig = configvm_memory.htm
Feb 19 16:10:16: vmx| DICT            tag.miscConfig = configvm.htm
Feb 19 16:10:16: vmx| DICT             tag.usbConfig = devices_usb.htm
Feb 19 16:10:16: vmx| DICT         tag.displayConfig = configvm_display-problems.htm
Feb 19 16:10:16: vmx| DICT                 tag.tools = vmtools.htm
Feb 19 16:10:16: vmx| DICT --- COMMAND LINE
Feb 19 16:10:16: vmx| DICT          gui.managementUI = TRUE
Feb 19 16:10:16: vmx| DICT --- CONFIGURATION
Feb 19 16:10:16: vmx| DICT            config.version = 8
Feb 19 16:10:16: vmx| DICT         virtualHW.version = 4
Feb 19 16:10:16: vmx| DICT             scsi0.present = TRUE
Feb 19 16:10:16: vmx| DICT                   memsize = 256
Feb 19 16:10:16: vmx| DICT            ide0:0.present = TRUE
Feb 19 16:10:16: vmx| DICT           ide0:0.fileName = Windows XP Professional.vmdk
Feb 19 16:10:16: vmx| DICT       ide0:0.writeThrough = TRUE
Feb 19 16:10:16: vmx| DICT            ide1:0.present = TRUE
Feb 19 16:10:16: vmx| DICT           ide1:0.fileName = /home/pmillette/Partage/Outils/Netload/Windows XP Pro SP2 french/WXPROSP2_FR.iso
Feb 19 16:10:16: vmx| DICT         ide1:0.deviceType = cdrom-image
Feb 19 16:10:16: vmx| DICT    floppy0.startConnected = FALSE
Feb 19 16:10:16: vmx| DICT          floppy0.fileName = /dev/fd0
Feb 19 16:10:16: vmx| DICT         Ethernet0.present = TRUE
Feb 19 16:10:16: vmx| DICT               displayName = Windows XP Professional
Feb 19 16:10:16: vmx| DICT                   guestOS = winxppro
Feb 19 16:10:16: vmx| DICT          priority.grabbed = normal
Feb 19 16:10:16: vmx| DICT        priority.ungrabbed = normal
Feb 19 16:10:16: vmx| DICT        powerType.powerOff = hard
Feb 19 16:10:16: vmx| DICT         powerType.powerOn = hard
Feb 19 16:10:16: vmx| DICT         powerType.suspend = hard
Feb 19 16:10:16: vmx| DICT           powerType.reset = hard
Feb 19 16:10:16: vmx| DICT                     debug = TRUE
Feb 19 16:10:16: vmx| DICT      disable_acceleration = TRUE
Feb 19 16:10:16: vmx| DICT monitor_control.log_vmsample = TRUE
Feb 19 16:10:16: vmx| DICT               MemTrimRate = 0
Feb 19 16:10:16: vmx| DICT --- USER DEFAULTS
Feb 19 16:10:16: vmx| DICT --- HOST DEFAULTS
Feb 19 16:10:16: vmx| DICT    vmnet1.hostonlyaddress = 192.168.80.1
Feb 19 16:10:16: vmx| DICT     serverd.init.fullpath = /usr/lib/vmware/serverd/init.pl
Feb 19 16:10:16: vmx| DICT         authd.client.port = 902
Feb 19 16:10:16: vmx| DICT          control.fullpath = /usr/bin/vmware-cmd
Feb 19 16:10:16: vmx| DICT            authd.fullpath = /usr/sbin/vmware-authd
Feb 19 16:10:16: vmx| DICT             loop.fullpath = /usr/bin/vmware-loop
Feb 19 16:10:16: vmx| DICT                    libdir = /usr/lib/vmware
Feb 19 16:10:16: vmx| DICT           vmware.fullpath = /usr/bin/vmware
Feb 19 16:10:16: vmx| DICT    vmnet1.hostonlynetmask = 255.255.255.0
Feb 19 16:10:16: vmx| DICT                     vmdir = /home/pmillette/Virtuel
Feb 19 16:10:16: vmx| DICT            dhcpd.fullpath = /usr/bin/vmnet-dhcpd
Feb 19 16:10:16: vmx| DICT          serverd.fullpath = /usr/sbin/vmware-serverd
Feb 19 16:10:16: vmx| DICT            datastore.name = local
Feb 19 16:10:16: vmx| DICT       datastore.localpath = /home/pmillette/Virtuel/
Feb 19 16:10:16: vmx| DICT --- SITE DEFAULTS
Feb 19 16:10:16: vmx| DICT                  tag.help = introduction.htm
Feb 19 16:10:16: vmx| DICT   tag.configurationEditor = config_editor_newvm.htm
Feb 19 16:10:16: vmx| DICT             tag.ideConfig = devices_virtualdrive.htm
Feb 19 16:10:16: vmx| DICT          tag.floppyConfig = devices_floppy.htm
Feb 19 16:10:16: vmx| DICT           tag.mouseConfig = devices_mouse.htm
Feb 19 16:10:16: vmx| DICT             tag.netConfig = devices_netadapter.htm
Feb 19 16:10:16: vmx| DICT        tag.parallelConfig = devices_parallel.htm
Feb 19 16:10:16: vmx| DICT          tag.serialConfig = devices_serial.htm
Feb 19 16:10:16: vmx| DICT           tag.soundConfig = devices_sound.htm
Feb 19 16:10:16: vmx| DICT             tag.memConfig = configvm_memory.htm
Feb 19 16:10:16: vmx| DICT            tag.miscConfig = configvm.htm
Feb 19 16:10:16: vmx| DICT             tag.usbConfig = devices_usb.htm
Feb 19 16:10:16: vmx| DICT         tag.displayConfig = configvm_display-problems.htm
Feb 19 16:10:16: vmx| DICT                 tag.tools = vmtools.htm
Feb 19 16:10:16: vmx| DICT --- GLOBAL SETTINGS
Feb 19 16:10:16: vmx| Msg_Hint: msg.guestos.xp (not shown)
Feb 19 16:10:16: vmx| WSSCAN: reserved mem (in MB) min=32 max=1888 recommended=1888
Feb 19 16:10:16: vmx|         hostMem=1984 maxAllowedAll=-1 maxAllowedVM=3600
Feb 19 16:10:16: vmx|         totOverhead=16
Feb 19 16:10:16: vmx| WSSCAN: used rec mem (in MB) 1888
Feb 19 16:10:16: vmx| WSSCAN: Overhead 71921 paged 5534 nonpaged 4096 maxFBSize
Feb 19 16:10:16: vmx| WSSCAN 1 1 483328 -1 483328 -1 50 0
Feb 19 16:10:16: vmx| MX: init lock: rank(monAct)=65535
Feb 19 16:10:16: vmx| MX: init lock: rank(monAct)=65535
Feb 19 16:10:16: vmx| MX: init lock: rank(monAct)=65535
Feb 19 16:10:16: vmx| MX: init lock: rank(monAct)=65535
Feb 19 16:10:16: vmx| MX: init lock: rank(monAct)=65535
Feb 19 16:10:16: vmx| MX: init lock: rank(monAct)=65535
Feb 19 16:10:16: vmx| MX: init lock: rank(monAct)=65535
Feb 19 16:10:16: vmx| MX: init lock: rank(monAct)=65535
Feb 19 16:10:16: vmx| MX: init lock: rank(stTable)=99
Feb 19 16:10:16: vmx| MX: init lock: rank(log)=0
Feb 19 16:10:16: vmx| LICENSE using: '/etc/vmware/license.vs.1.0-00' 
Feb 19 16:10:16: vmx| STATDECLGROUP stats Root "" null
Feb 19 16:10:16: vmx| MX: init lock: rank(iospaceLock)=120
Feb 19 16:10:16: vmx| Host CPUID features: version 0x20f32 id1.edx 0x178bfbff id1.ecx 0x1 id81.edx 0xe3d3fbff id81.ecx 0x3
Feb 19 16:10:16: vmx| CPU.cpuFeatures = 0xd83dffd0
Feb 19 16:10:16: vmx| CPUID after masking: version 0x20f32 id1.edx 0x78bfbff id1.ecx 0x1 id81.edx 0xe3d3fbff id81.ecx 0x1 id88.ecx 0x0
Feb 19 16:10:16: vmx| CPU.cpuFeatures = 0xd83dffd0
Feb 19 16:10:16: vmx| APIC: Local APIC at 0xfee00000
Feb 19 16:10:16: vmx| KHZEstimate 1000000
Feb 19 16:10:16: vmx| MHZEstimate 1000
Feb 19 16:10:16: vmx| NumVCPUs 1
Feb 19 16:10:16: vmx| MX: init lock: rank(monitorPoll)=65534
Feb 19 16:10:16: vmx| MX: init lock: rank(userlevelLock)=100
Feb 19 16:10:16: vmx| MX: init lock: rank(bigDeviceLock)=110
Feb 19 16:10:16: vmx| UUID: location-UUID is 56 4d 7d 62 34 75 6b 6b-69 ad 39 98 6f 87 00 54
Feb 19 16:10:16: vmx| UUID: canonical path is /home/pmillette/Virtuel/Windows XP Professional/Windows XP Professional.vmx
Feb 19 16:10:16: vmx| UUID: location-UUID is 56 4d 7d 62 34 75 6b 6b-69 ad 39 98 6f 87 00 54
Feb 19 16:10:16: vmx| UUID: Writing uuid.bios 56 4d 7d 62 34 75 6b 6b-69 ad 39 98 6f 87 00 54
Feb 19 16:10:16: vmx| UUID: Writing uuid.location 56 4d 7d 62 34 75 6b 6b-69 ad 39 98 6f 87 00 54
Feb 19 16:10:16: vmx| MM: Using partialmap, 65536 pages AC 1 CE 1 TM 1 DOHU 0
Feb 19 16:10:16: vmx| MX: init condvar: MMCpt
Feb 19 16:10:16: vmx| MX: init lock: rank(MMCpt)=65533
Feb 19 16:10:16: vmx| UUID: canonical path is /home/pmillette/Virtuel/Windows XP Professional/Windows XP Professional.vmx
Feb 19 16:10:16: vmx| UUID: location-UUID is 56 4d 7d 62 34 75 6b 6b-69 ad 39 98 6f 87 00 54
Feb 19 16:10:16: vmx| MM: using fileName /home/pmillette/Virtuel/Windows XP Professional/564d7d62-3475-6b6b-69ad-39986f870054.vmem for paging
Feb 19 16:10:16: vmx| Msg_Reset:
Feb 19 16:10:16: vmx| ----------------------------------------
Feb 19 16:10:16: vmx| Opened paging file /home/pmillette/Virtuel/Windows XP Professional/564d7d62-3475-6b6b-69ad-39986f870054.vmem
Feb 19 16:10:16: vmx| Mapped mainmem as pageable
Feb 19 16:10:16: vmx| MStat: Creating Stat vm.cpuusage
Feb 19 16:10:16: vmx| MStat: Creating Stat vm.ram
Feb 19 16:10:16: vmx| MStat: Creating Stat vm.uptime
Feb 19 16:10:16: vmx| MX: init lock: rank(intrLock)=65532
Feb 19 16:10:16: vmx| MX: init lock: rank(IOGGlobalLock)=65535
Feb 19 16:10:16: vmx| MX: init condvar: IOGPendingOps
Feb 19 16:10:16: vmx| AIOGNRC: Starting 4 I/O threads.
Feb 19 16:10:16: vmx| DISK: OPEN ide0:0 '/home/pmillette/Virtuel/Windows XP Professional/Windows XP Professional.vmdk' persistent R[(null)]
Feb 19 16:10:16: vmx| DISKLIB-DSCPTR: Opened [0]: "Windows XP Professional-f001.vmdk" 0 (0x2a)
Feb 19 16:10:16: vmx| DISKLIB-DSCPTR: Opened [1]: "Windows XP Professional-f002.vmdk" 0 (0x2a)
Feb 19 16:10:16: vmx| DISKLIB-DSCPTR: Opened [2]: "Windows XP Professional-f003.vmdk" 0 (0x2a)
Feb 19 16:10:16: vmx| DISKLIB-DSCPTR: Opened [3]: "Windows XP Professional-f004.vmdk" 0 (0x2a)
Feb 19 16:10:16: vmx| DISKLIB-DSCPTR: Opened [4]: "Windows XP Professional-f005.vmdk" 0 (0x2a)
Feb 19 16:10:16: vmx| DISKLIB-LINK  : Opened '/home/pmillette/Virtuel/Windows XP Professional/Windows XP Professional.vmdk' (0x2a): twoGbMaxExtentFlat, 16777216 sectors / 8192 Mb.
Feb 19 16:10:16: vmx| DISKLIB-LIB   : Opened "/home/pmillette/Virtuel/Windows XP Professional/Windows XP Professional.vmdk" (flags 0x2a).
Feb 19 16:10:16: vmx| DISK: OPEN '/home/pmillette/Virtuel/Windows XP Professional/Windows XP Professional.vmdk' Geo (16383/16/63) BIOS Geo (0/0/0) freeSpace=170585Mb
Feb 19 16:10:16: vmx| MX: init lock: rank(timeTracker)=65533
Feb 19 16:10:16: vmx| TimeTracker host to guest rate conversion 11100215025503 @ 1000000000Hz -> 11100215025503 @ 1000000000Hz
Feb 19 16:10:16: vmx| TimeTracker host to guest rate conversion ((x * 2147483648) >> 31) + 0
Feb 19 16:10:16: vmx| DISK: DELAY: vide.vtdelay=0 hard-disk.minVirtualTime=0 magicBoot1=0
Feb 19 16:10:16: vmx| MX: init lock: rank(VIDELock)=111
Feb 19 16:10:16: vmx| MStat: Creating Stat ide0:0.bytesread
Feb 19 16:10:16: vmx| MStat: Creating Stat ide0:0.byteswritten
Feb 19 16:10:16: vmx| MStat: Creating Stat ide1:0.bytesread
Feb 19 16:10:16: vmx| MStat: Creating Stat ide1:0.byteswritten
Feb 19 16:10:16: vmx| MX: init lock: rank(busLogicLock)=111
Feb 19 16:10:16: vmx| SCSI0: UNTAGGED commands will be converted to ORDER tags.
Feb 19 16:10:16: vmx| MX: init lock: rank(timer)=30
Feb 19 16:10:16: vmx| MStat: Creating Stat vm.heartbeat
Feb 19 16:10:16: vmx| DISKUTIL: ide0:0 : toolsVersion = 0
Feb 19 16:10:16: vmx| DISKUTIL: Offline toolsVersion = 0
Feb 19 16:10:16: vmx| TOOLS INSTALL initializing state to IDLE on power on.
Feb 19 16:10:16: vmx| No valid NVRAM file found, will create default NVRAM.
Feb 19 16:10:16: vmx| MX: init lock: rank(mksLock)=130
Feb 19 16:10:16: vmx| XINFO no-auth XOpenDisplay failed.  Trying auth info from UI (0).
Feb 19 16:10:16: vmx| MX: init lock: rank(vgaLock)=60
Feb 19 16:10:16: vmx| MX: init lock: rank(svgaLock)=30
Feb 19 16:10:16: vmx| MX: init condvar: svgaStopCondition
Feb 19 16:10:16: vmx| MX: init lock: rank(svgaPseudoCallLock)=101
Feb 19 16:10:16: vmx| MX: init condvar: svgaPseudoCallCondVar
Feb 19 16:10:16: vmx| VMMon_GetkHzEstimate: Calculated 1549471 kHz
Feb 19 16:10:16: vmx| VLANCE: send cluster threshold is 80, size = 2 recalcInterval is 2 ticks
Feb 19 16:10:16: vmx| MX: init lock: rank(vlanceLock)=30
Feb 19 16:10:16: vmx| MStat: Creating Stat ethernet0.bytesread
Feb 19 16:10:16: vmx| MStat: Creating Stat ethernet0.byteswritten
Feb 19 16:10:16: vmx| Ethernet0 MAC Address: 00:0c:29:87:00:54
Feb 19 16:10:16: vmx| VMXNET: send cluster threshold is 80, size = 2 recalcInterval is 2 ticks, dontClusterSize is 128
Feb 19 16:10:16: vmx| E1000: checksum cycles/kB: C=901 asm=293
Feb 19 16:10:16: vmx| MX: init lock: rank(TestAutomationGlobalLock)=65535
Feb 19 16:10:17: vmx| MX: init lock: rank(pollLock)=65534
Feb 19 16:10:17: vmx| VMX_PowerOn: ModuleTable_PowerOn = 1
Feb 19 16:10:17: vmx| VMX setting maximum IPC write buffers to 0 packets, 0 bytes
Feb 19 16:10:17: mks| Async MKS thread is alive
Feb 19 16:10:17: vmx| Accepted new connection at 158 for thread servercontrol (0x8546360)
Feb 19 16:10:17: vmx| VUINewControlConnection: before slow ACL gunk (bug 63252).
Feb 19 16:10:17: vmx| ACL_InitCapabilities: here 2 (bug 63252)
Feb 19 16:10:17: vmx| VUINewControlConnection: after slow ACL gunk (bug 63252).
Feb 19 16:10:17: vmx| VUI: A new VMControl client connected.
Feb 19 16:10:17: vcpu-0| MX: init lock: rank(offline)=99
Feb 19 16:10:17: vcpu-0| APIC: version = 0x10, max LVT = 4
Feb 19 16:10:17: vcpu-0| APIC: LDR = 0x2000000, DFR = 0xffffffff
Feb 19 16:10:17: vcpu-0| MX: init lock: rank(stopLock)=1
Feb 19 16:10:17: vcpu-0| MX: init lock: rank(respLock)=3
Feb 19 16:10:17: vcpu-0| MX: init lock: rank(busMemLock)=80
Feb 19 16:10:17: vcpu-0| MX: init lock: rank(busmemSample)=99
Feb 19 16:10:17: vcpu-0| MX: init lock: rank(vmkRelMemLock)=99
Feb 19 16:10:17: vcpu-0| PShare: enabled 1, scanRate 18, checkRate 16
Feb 19 16:10:17: vcpu-0| guestCpuFeatures = 0xd83dffd0
Feb 19 16:10:17: vcpu-0| Init modules.
Feb 19 16:10:17: vcpu-0| DISKUTIL: ide0:0 : capacity=16777216
Feb 19 16:10:17: vmx| IPC version negotiation version: VMX returning 2.1 to servercontrol
Feb 19 16:10:17: vmx| IPC vmcontrol-temp version: VMX returning 11.4 to servercontrol that tried 11.4
Feb 19 16:10:17: vcpu-0| CPU reset: hard
Feb 19 16:10:17: vmx| VNET: Notification enabled for Ethernet0
Feb 19 16:10:17: vcpu-0| sz=2731344
Feb 19 16:10:17: vcpu-0| MX: init lock: rank(barrierLck)=3
Feb 19 16:10:17: vcpu-0| MX: init condvar: barrierCV
Feb 19 16:10:17: vcpu-0| MX: init lock: rank(barrierLck)=3
Feb 19 16:10:17: vcpu-0| MX: init condvar: barrierCV
Feb 19 16:10:17: vcpu-0| vmm32 initialized: BETAbuild-29996. cflags: 0x00001002.03803000.00000054
Feb 19 16:10:17: mks| Connecting to window system.
Feb 19 16:10:17: mks| XINFO X fd is 43
Feb 19 16:10:17: mks| XINFO depth 24 bpp 32 class 4
Feb 19 16:10:17: mks| XINFO WARNING: XF86MISC version 0.9
Feb 19 16:10:17: mks| VT redirected kernel output to /dev/tty1
Feb 19 16:10:17: mks| rasterops MMXEXT accelerations enabled
Feb 19 16:10:17: mks| XINFO unsupported XF86VidMode version: 2.2
Feb 19 16:10:17: mks| XINFO XFree86 VidMode 0: 1280x1024 flags: 0x5
Feb 19 16:10:17: mks| XINFO XFree86 VidMode 1: 1024x768 flags: 0xa
Feb 19 16:10:17: mks| XINFO XFree86 VidMode 2: 800x600 flags: 0x5
Feb 19 16:10:17: mks| XINFO XFree86 VidMode 3: 640x480 flags: 0xa
Feb 19 16:10:17: mks| XINFO XFree86 VidMode 4: 1280x960 flags: 0x5
Feb 19 16:10:17: mks| XINFO XFree86 VidMode 5: 1280x800 flags: 0x0
Feb 19 16:10:17: mks| XINFO XFree86 VidMode 6: 1280x768 flags: 0x0
Feb 19 16:10:17: mks| XINFO XFree86 VidMode 7: 1152x768 flags: 0x5
Feb 19 16:10:17: mks| XINFO XFree86 VidMode 8: 800x600 flags: 0x5
Feb 19 16:10:17: mks| XINFO XFree86 VidMode 9: 400x300 flags: 0x25
Feb 19 16:10:17: mks| Ignoring update request in VGA_Expose (mode change pending).
Feb 19 16:10:17: mks| Adding local console 0x86bb4f0
Feb 19 16:10:17: mks| Ignoring update request in VGA_Expose (mode change pending).
Feb 19 16:10:18: vcpu-0| VMSAMPLE32: cs=0xe002, eip=0xd4e
Feb 19 16:10:18: vcpu-0| SVGA: Registering MemSpace at 0xf0000000(0x0) and 0xec000000(0x0)
Feb 19 16:10:18: vcpu-0| SVGA: Unregistering MemSpace at 0xf0000000(0xf0000000) and 0xec000000(0xec000000)
Feb 19 16:10:18: vcpu-0| maxStackDepth(1) = 3120
Feb 19 16:10:18: vcpu-0| SVGA: Registering MemSpace at 0xf0000000(0xf0000000) and 0xec000000(0xec000000)
Feb 19 16:10:18: vcpu-0| SVGA: Unregistering MemSpace at 0xf0000000(0xf0000000) and 0xec000000(0xec000000)
Feb 19 16:10:18: vcpu-0| SVGA: Registering IOSpace at 0x1400 (0x0)
Feb 19 16:10:18: vcpu-0| SVGA: Registering MemSpace at 0xf0000000(0xf0000000) and 0xec000000(0xec000000)
Feb 19 16:10:18: vcpu-0| VMSAMPLE32: cs=0xf000, eip=0x89b1
Feb 19 16:10:19: mks| Ignoring update request in VGA_Expose (mode change pending).
Feb 19 16:10:19: mks| Ignoring update request in VGA_Expose (mode change pending).
Feb 19 16:10:19: mks| Ignoring update request in VGA_Expose (mode change pending).
Feb 19 16:10:19: mks| Ignoring update request in VGA_Expose (mode change pending).
Feb 19 16:10:19: mks| Ignoring update request in VGA_Expose (mode change pending).
Feb 19 16:10:19: mks| Ignoring update request in VGA_Expose (mode change pending).
Feb 19 16:10:19: mks| Ignoring update request in VGA_Expose (mode change pending).
Feb 19 16:10:19: mks| Ignoring update request in VGA_Expose (mode change pending).
Feb 19 16:10:19: mks| Ignoring update request in VGA_Expose (mode change pending).
Feb 19 16:10:19: vcpu-0| VMSAMPLE32: cs=0xf000, eip=0x42e6
Feb 19 16:10:20: vcpu-0| VIDE: Curr CHS info cyls: 17475 heads: 15 sects: 63 lba_cap: 16777216
Feb 19 16:10:20: vcpu-0| VMSAMPLE32: cs=0xf000, eip=0x42e6
Feb 19 16:10:21: vcpu-0| BIOS-UUID is 56 4d 7d 62 34 75 6b 6b-69 ad 39 98 6f 87 00 54
Feb 19 16:10:21: vcpu-0| DISKUTIL: ide0:0 : toolsVersion = 0
Feb 19 16:10:21: vcpu-0| DISKUTIL: Offline toolsVersion = 0
Feb 19 16:10:21: mks| Ignoring update request in VGA_Expose (mode change pending).
Feb 19 16:10:21: vcpu-0| VMSAMPLE32: cs=0xf000, eip=0x42e6
Feb 19 16:10:22: vcpu-0| VMSAMPLE32: cs=0xf000, eip=0x42e6
Feb 19 16:10:23: vcpu-0| Unknown int 10h func 0x2000
Feb 19 16:10:23: mks| Ignoring update request in VGA_Expose (mode change pending).
Feb 19 16:10:23: mks| Ignoring update request in VGA_Expose (mode change pending).
Feb 19 16:10:23: mks| Ignoring update request in VGA_Expose (mode change pending).
Feb 19 16:10:23: mks| Ignoring update request in VGA_Expose (mode change pending).
Feb 19 16:10:23: mks| Ignoring update request in VGA_Expose (mode change pending).
Feb 19 16:10:23: mks| Ignoring update request in VGA_Expose (mode change pending).
Feb 19 16:10:23: mks| Ignoring update request in VGA_Expose (mode change pending).
Feb 19 16:10:23: mks| Ignoring update request in VGA_Expose (mode change pending).
Feb 19 16:10:23: vcpu-0| VMSAMPLE32: cs=0x1000, eip=0x27d7
Feb 19 16:10:24: vcpu-0| VMSAMPLE32: cs=0x1000, eip=0x27d7
Feb 19 16:10:25: vcpu-0| VMSAMPLE32: cs=0xf000, eip=0x431f
Feb 19 16:10:26: vcpu-0| VMSAMPLE32: cs=0x58, eip=0x3bc
Feb 19 16:10:27: vcpu-0| VMSAMPLE32: cs=0x2000, eip=0x255
Feb 19 16:10:28: vcpu-0| VMSAMPLE32: cs=0x58, eip=0x3bc
Feb 19 16:10:29: vcpu-0| VMSAMPLE32: cs=0x2000, eip=0x255
Feb 19 16:10:30: vcpu-0| VMSAMPLE32: cs=0x58, eip=0x26d
Feb 19 16:10:31: vcpu-0| maxStackDepth(0) = 3376
Feb 19 16:10:31: vcpu-0| VMSAMPLE32: cs=0xebe9, eip=0x4856
Feb 19 16:10:32: vcpu-0| VMSAMPLE32: cs=0xebe9, eip=0x4856
Feb 19 16:10:33: vcpu-0| VMSAMPLE32: cs=0xebe9, eip=0x4856
Feb 19 16:10:34: vcpu-0| VMSAMPLE32: cs=0xf000, eip=0x431f
Feb 19 16:10:35: vcpu-0| VMSAMPLE32: cs=0xebe9, eip=0x4856
Feb 19 16:10:36: vcpu-0| VMSAMPLE32: cs=0xebe9, eip=0x4856
Feb 19 16:10:37: vcpu-0| VMSAMPLE32: cs=0xf000, eip=0x431f
Feb 19 16:10:38: vcpu-0| VMSAMPLE32: cs=0xebe9, eip=0x4856
Feb 19 16:10:39: vcpu-0| VMSAMPLE32: cs=0xebe9, eip=0x4856
Feb 19 16:10:40: vcpu-0| VMSAMPLE32: cs=0xf000, eip=0x431f
Feb 19 16:10:40: mks| Ignoring update request in VGA_Expose (mode change pending).
Feb 19 16:10:41: vcpu-0| maxStackDepth(1) = 3448
Feb 19 16:10:41: vcpu-0| VMSAMPLE32: cs=0x8, eip=0x80196797
Feb 19 16:10:42: vcpu-0| VMSAMPLE32: cs=0x8, eip=0xf9958ef8
Feb 19 16:10:42: vcpu-0| maxStackDepth(1) = 3500
Feb 19 16:10:43: vcpu-0| SVGA: Unregistering IOSpace at 0x1400 (0x1400)
Feb 19 16:10:43: vcpu-0| SVGA: Unregistering MemSpace at 0xf0000000(0xf0000000) and 0xec000000(0xec000000)
Feb 19 16:10:43: vcpu-0| SVGA: Registering IOSpace at 0x1400 (0x0)
Feb 19 16:10:43: vcpu-0| SVGA: Registering MemSpace at 0xf0000000(0xf0000000) and 0xec000000(0xec000000)
Feb 19 16:10:43: vcpu-0| VMSAMPLE32: cs=0xa040, eip=0x160
Feb 19 16:10:44: vcpu-0| maxStackDepth(1) = 3832
Feb 19 16:10:44: vcpu-0| VMSAMPLE32: cs=0x8, eip=0x80811e37
Feb 19 16:10:45: vcpu-0| maxStackDepth(1) = 4252
Feb 19 16:10:45: vcpu-0| maxStackDepth(0) = 3752
Feb 19 16:10:45: vcpu-0| VMSAMPLE32: cs=0x8, eip=0x8080e135
Feb 19 16:10:46: vcpu-0| VMSAMPLE32: cs=0x8, eip=0x8080e135
Feb 19 16:10:47: vcpu-0| VIDE: Curr CHS info cyls: 17475 heads: 15 sects: 63 lba_cap: 16777216
Feb 19 16:10:47: vcpu-0| CDROM: Mode Sense for Unsupported Page 0x1B
Feb 19 16:10:47: vcpu-0| VMSAMPLE32: cs=0x8, eip=0x80196861
Feb 19 16:10:48: vcpu-0| CDROM: Emulate GET CONFIGURATION RT 0 start feature 0
Feb 19 16:10:48: vcpu-0| CDROM: Emulate GET CONFIGURATION RT 2 start feature 0
Feb 19 16:10:48: vcpu-0| CDROM: Emulate GET CONFIGURATION RT 0 start feature 0
Feb 19 16:10:48: vcpu-0| CDROM: Emulate GET CONFIGURATION RT 0 start feature 0
Feb 19 16:10:48: vcpu-0| VMSAMPLE32: cs=0x8, eip=0x8080e135
Feb 19 16:10:49: vcpu-0| VMSAMPLE32: cs=0x8, eip=0x8080eda8
Feb 19 16:10:50: mks| Ignoring update request in VGA_Expose (mode change pending).
Feb 19 16:10:50: vcpu-0| VMSAMPLE32: cs=0x8, eip=0x8080e135
Feb 19 16:10:51: vcpu-0| VMSAMPLE32: cs=0x8, eip=0xf99b56fc
Feb 19 16:10:52: vcpu-0| VMSAMPLE32: cs=0x8, eip=0xf99e18d5
Feb 19 16:10:53: vcpu-0| VMSAMPLE32: cs=0x8, eip=0xf99b56f5
Feb 19 16:10:54: mks| MKS lock acquiring
Feb 19 16:10:54: mks| MKS lock already locked
Feb 19 16:10:54: mks| MKS lock already locked
Feb 19 16:10:54: mks| MKS lock already locked
Feb 19 16:10:54: mks| MKS lock already locked
Feb 19 16:10:54: mks| MKS lock already locked
Feb 19 16:10:54: mks| MKS lock already locked
Feb 19 16:10:54: mks| MKS lock already locked
Feb 19 16:10:55: mks| MKS lock already locked
Feb 19 16:10:55: mks| MKS lock already locked
Feb 19 16:10:55: mks| MKS lock already locked
Feb 19 16:10:55: mks| MKS lock already locked
Feb 19 16:10:55: mks| MKS lock already locked
Feb 19 16:10:55: mks| MKS lock already locked
Feb 19 16:10:55: mks| MKS lock already locked
Feb 19 16:10:55: mks| MKS lock already locked
Feb 19 16:10:55: mks| MKS lock already locked
Feb 19 16:10:55: mks| MKS lock already locked
Feb 19 16:10:56: mks| MKS lock already locked
Feb 19 16:10:56: mks| MKS lock already locked
Feb 19 16:10:56: mks| MKS lock already locked
Feb 19 16:10:56: mks| Msg_Question:
Feb 19 16:10:56: mks| [msg.mks.lockFail] Failed to acquire lock to grab keyboard and mouse input. This may be because another virtual machine crashed or is hung.
Feb 19 16:10:56: mks| You can override the lock, but this may corrupt some of the X server state, such as keyboard autorepeat settings and the modifier mapping.
Feb 19 16:10:56: mks| Do you want to override the lock?
Feb 19 16:10:56: mks| ----------------------------------------
Feb 19 16:10:56: mks| Question without a remote UI:
Feb 19 16:10:56: mks| Failed to acquire lock to grab keyboard and mouse input. This may be because another virtual machine crashed or is hung.
Feb 19 16:10:56: mks| You can override the lock, but this may corrupt some of the X server state, such as keyboard autorepeat settings and the modifier mapping.
Feb 19 16:10:56: mks| Do you want to override the lock?
Feb 19 16:10:56: mks| 
Feb 19 16:10:56: mks| MKS release: start, nesting 0
Feb 19 16:10:56: mks| MKS starting full screen: off
Feb 19 16:10:56: mks| MKS already off
Feb 19 16:10:56: mks| MKS finished full screen: done
Feb 19 16:11:02: mks| Msg_Question: msg.mks.lockFail reply=0
Feb 19 16:11:02: mks| MKS lock releasing
Feb 19 16:11:02: vmx| MKS release: end, nesting 1
Feb 19 16:11:02: vcpu-0| VMSAMPLE32: cs=0x8, eip=0xf99e1892
Feb 19 16:11:03: vcpu-0| VMSAMPLE32: cs=0x8, eip=0xf99e1892
Feb 19 16:11:03: mks| MKS lock acquiring
Feb 19 16:11:03: mks| MKS lock not locked
Feb 19 16:11:03: mks| MKS lock acquiring
Feb 19 16:11:04: vcpu-0| VMSAMPLE32: cs=0x8, eip=0xf99e18d4
Feb 19 16:11:05: vcpu-0| VMSAMPLE32: cs=0x8, eip=0xf99e18d5
Feb 19 16:11:06: vcpu-0| VMSAMPLE32: cs=0x8, eip=0xf99e18d5
Feb 19 16:11:07: vcpu-0| VMSAMPLE32: cs=0x8, eip=0xf99e18d5
Feb 19 16:11:08: vcpu-0| VMSAMPLE32: cs=0x8, eip=0xf99e18d4
Feb 19 16:11:09: vcpu-0| VMSAMPLE32: cs=0x8, eip=0xf99b56fc
Feb 19 16:11:10: vcpu-0| VMSAMPLE32: cs=0x8, eip=0xf99b56fc
Feb 19 16:11:11: vcpu-0| VMSAMPLE32: cs=0x8, eip=0xf99e18d4
Feb 19 16:11:12: vcpu-0| VMSAMPLE32: cs=0x8, eip=0xf99b56fa
Feb 19 16:11:13: vcpu-0| VMSAMPLE32: cs=0x8, eip=0xf99e1892
Feb 19 16:11:14: vcpu-0| VMSAMPLE32: cs=0x8, eip=0xf99e1892
Feb 19 16:11:15: vcpu-0| VMSAMPLE32: cs=0x8, eip=0xf99e189c
Feb 19 16:11:16: vcpu-0| VMSAMPLE32: cs=0x8, eip=0xf99e18d4
Feb 19 16:11:17: vcpu-0| VMSAMPLE32: cs=0x8, eip=0xf99b56fa
Feb 19 16:11:18: vcpu-0| VMSAMPLE32: cs=0x8, eip=0x8081ad70
Feb 19 16:11:19: vcpu-0| VMSAMPLE32: cs=0x8, eip=0x8081ad70
Feb 19 16:11:20: vcpu-0| VMSAMPLE32: cs=0x8, eip=0x8081ad70
Feb 19 16:11:21: vcpu-0| VMSAMPLE32: cs=0x8, eip=0x8081ad70
Feb 19 16:11:22: vcpu-0| VMSAMPLE32: cs=0x8, eip=0x808bfcc3
Feb 19 16:11:23: vcpu-0| VMSAMPLE32: cs=0x8, eip=0x801962d0
Feb 19 16:11:24: vcpu-0| VMSAMPLE32: cs=0x8, eip=0x8080df55
Feb 19 16:11:25: vcpu-0| VMSAMPLE32: cs=0x8, eip=0x8019c8af
Feb 19 16:11:26: vcpu-0| VMSAMPLE32: cs=0x8, eip=0xf9b51321
Feb 19 16:11:27: vcpu-0| VMSAMPLE32: cs=0x8, eip=0x8080ee0f
Feb 19 16:11:28: vcpu-0| VMSAMPLE32: cs=0x8, eip=0x8019c8af
Feb 19 16:11:29: vcpu-0| VMSAMPLE32: cs=0x1b, eip=0x7c911a09
Feb 19 16:11:30: vcpu-0| VMSAMPLE32: cs=0x8, eip=0x8080ee0f
Feb 19 16:11:31: vcpu-0| VMSAMPLE32: cs=0x1b, eip=0x7c91eb94
Feb 19 16:11:32: vcpu-0| VMSAMPLE32: cs=0x8, eip=0x808a284c
Feb 19 16:11:33: vcpu-0| VMSAMPLE32: cs=0x1b, eip=0x100f9f6
Feb 19 16:11:34: vcpu-0| VMSAMPLE32: cs=0x8, eip=0x8019c919
Feb 19 16:11:35: vcpu-0| VMSAMPLE32: cs=0x8, eip=0x8080b100
Feb 19 16:11:35: vmx| NOT_TESTED /build/mts/release/bora-29996/pompeii2005/bora/lib/disklib/dataCache.c:2101
Feb 19 16:11:36: vcpu-0| VMSAMPLE32: cs=0x8, eip=0x8080e135
Feb 19 16:11:37: vcpu-0| VMSAMPLE32: cs=0x8, eip=0x8080e136
Feb 19 16:11:38: vcpu-0| VMSAMPLE32: cs=0x8, eip=0x8080e135
Feb 19 16:11:39: vcpu-0| VMSAMPLE32: cs=0x8, eip=0x8082c54f
Feb 19 16:11:40: vcpu-0| VMSAMPLE32: cs=0x8, eip=0x8080e135
Feb 19 16:11:41: vcpu-0| VMSAMPLE32: cs=0x8, eip=0x8080e135
Feb 19 16:11:42: vcpu-0| VMSAMPLE32: cs=0x8, eip=0x8019c919
Feb 19 16:11:43: vcpu-0| VMSAMPLE32: cs=0x8, eip=0x8080e135
Feb 19 16:11:44: vcpu-0| VMSAMPLE32: cs=0x8, eip=0x8080e135
Feb 19 16:11:45: vcpu-0| VMSAMPLE32: cs=0x8, eip=0x8080e135
Feb 19 16:11:46: vcpu-0| VMSAMPLE32: cs=0x8, eip=0x8080e135
Feb 19 16:11:47: vcpu-0| VMSAMPLE32: cs=0x8, eip=0x80194e20
Feb 19 16:11:48: vcpu-0| VMSAMPLE32: cs=0x8, eip=0xf99d052d
Feb 19 16:11:49: vcpu-0| VMSAMPLE32: cs=0x8, eip=0xf99d04d0
Feb 19 16:11:50: vcpu-0| VMSAMPLE32: cs=0x8, eip=0xf99d04d0
Feb 19 16:11:51: vcpu-0| VMSAMPLE32: cs=0x8, eip=0xf99d0459
Feb 19 16:11:52: vcpu-0| VMSAMPLE32: cs=0x8, eip=0x8080e137
Feb 19 16:11:53: vcpu-0| VMSAMPLE32: cs=0x8, eip=0x8080e135
Feb 19 16:11:54: vcpu-0| VMSAMPLE32: cs=0x8, eip=0x8080e135
Feb 19 16:11:55: vcpu-0| VMSAMPLE32: cs=0x8, eip=0x8080e135
Feb 19 16:11:56: vcpu-0| VMSAMPLE32: cs=0x8, eip=0x8080e135
Feb 19 16:11:57: vcpu-0| VMSAMPLE32: cs=0x8, eip=0x8080e135
Feb 19 16:11:58: vcpu-0| VMSAMPLE32: cs=0x8, eip=0xf9b7a94b
Feb 19 16:11:59: vcpu-0| MONITOR PANIC: vcpu-0:FPU Safety: Error: FPU instruction executed in monitor context[#NM]: cs:eip 0x4020:0xae148 %cr0: 0x8001003b CR[0]: 0x8001003b
Feb 19 16:11:59: vcpu-0| Core dump with build build-29996
Feb 19 16:11:59: vcpu-0| Writing monitor corefile "/home/pmillette/Virtuel/Windows XP Professional/vmware-core.gz"
Feb 19 16:11:59: vcpu-0| Beginning monitor coredump
Feb 19 16:11:59: vcpu-0| End monitor coredump
Feb 19 16:11:59: vcpu-0| Writing anonymous pages at pos: 401000
Feb 19 16:12:00: vcpu-0| Msg_Post: Error
Feb 19 16:12:00: vcpu-0| [msg.log.monpanic.beta] *** VMware Server internal monitor error ***
Feb 19 16:12:00: vcpu-0| vcpu-0:FPU Safety: Error: FPU instruction executed in monitor context[#NM]: cs:eip 0x4020:0xae148 %cr0: 0x8001003b CR[0]: 0x8001003b
Feb 19 16:12:00: vcpu-0| There is a problem in this version of VMware Server.
Feb 19 16:12:00: vcpu-0| We rely on your feedback to improve the quality of our product. Please submit a support request that describes the problem at our Web page "http://www.vmware.com/info?id=8". Do not forget to attach the log file (/home/pmillette/Virtuel/Windows XP Professional/vmware.log) and the core file (/home/pmillette/Virtuel/Windows XP Professional/vmware-core.gz).
Feb 19 16:12:00: vcpu-0| To collect files to submit to VMware support, run vm-support-lx.
Feb 19 16:12:00: vcpu-0| We appreciate your feedback,
Feb 19 16:12:00: vcpu-0|   -- the VMware Server team.
Feb 19 16:12:00: vcpu-0| ----------------------------------------
Feb 19 16:12:00: vcpu-0| POST(no connection): *** VMware Server internal monitor error ***
Feb 19 16:12:00: vcpu-0| vcpu-0:FPU Safety: Error: FPU instruction executed in monitor context[#NM]: cs:eip 0x4020:0xae148 %cr0: 0x8001003b CR[0]: 0x8001003b
Feb 19 16:12:00: vcpu-0| There is a problem in this version of VMware Server.
Feb 19 16:12:00: vcpu-0| We rely on your feedback to improve the quality of our product. Please submit a support request that describes the problem at our Web page "http://www.vmware.com/info?id=8". Do not forget to attach the log file (/home/pmillette/Virtuel/Windows XP Professional/vmware.log) and the core file (/home/pmillette/Virtuel/Windows XP Professional/vmware-core.gz).
Feb 19 16:12:00: vcpu-0| To collect files to submit to VMware support, run vm-support-lx.
Feb 19 16:12:00: vcpu-0| We appreciate your feedback,
Feb 19 16:12:00: vcpu-0|   -- the VMware Server team.
Feb 19 16:12:00: vcpu-0| 
Feb 19 16:12:00: vcpu-0| Exiting vcpu-0
Feb 19 16:12:00: vmx| MKS release: start, nesting 0
Feb 19 16:12:00: vmx| MKS starting full screen: off
Feb 19 16:12:00: vmx| MKS already off
Feb 19 16:12:00: vmx| MKS finished full screen: done
Feb 19 16:12:00: vmx| MKS lock releasing
Feb 19 16:12:01: vmx| VTHREAD watched thread 4 "vcpu-0" died
Feb 19 16:12:01: IO#0| VTHREAD watched thread 0 "vmx" died
Feb 19 16:12:01: IO#3| VTHREAD watched thread 0 "vmx" died
Feb 19 16:12:01: IO#2| VTHREAD watched thread 0 "vmx" died
Feb 19 16:12:01: IO#1| VTHREAD watched thread 0 "vmx" died
Feb 19 16:12:01: mks| VTHREAD watched thread 0 "vmx" died
Feb 19 16:12:01: mks| MKS release: start, nesting 1

---

### Post by n8bounds on 2007-02-19
looks like a classic case of MONITOR PANIC: vcpu-0:FPU Safety: Error: FPU instruction executed in monitor context[#NM]: cs:eip 0x4020:0xae148 %cr0: 0x8001003b CR[0]: 0x8001003b....whatever that is...have you checked the vmware forums?

---

### Post by electro93 on 2007-03-03
I am having the same issue as youself.  I tried looking on the VMWare forums with no luck.  Have you found a solution to the problem yet?

Thanks,

Jeff

---

