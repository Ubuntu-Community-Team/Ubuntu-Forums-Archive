---
title: "Problem playing DVD"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by shouvik_jnu on 2008-02-29
I am having a peculiar problem in my DVD drive. I am able to play and write a CD in my DVD+-RW (SONY). Howevr the problem is arising when I am trying to play a DVD. I am unable to play or write anything on the DVD disk. Please help me.
Thanks in advance.:)

---

### Post by piperdown10 on 2008-02-29
I can tell you what your problem is, I'm unsure of how to fix it. You'll need to download a codec to play dvds. I know that Totem has one but if you're using a different player you'll have to search for one.

---

### Post by jan quark on 2008-02-29
for dvd playing see here

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs?highlight=%28dvd%29%7C%28restricted%29](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs?highlight=%28dvd%29%7C%28restricted%29)

---

### Post by shouvik_jnu on 2008-02-29
I have done as was suggested in the website.

I ran tis commands on the terminal:

sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
sudo /usr/share/doc/libdvdread3/install-css.sh

But after running these commands also I am unable to play or write in my DVD Writer.

After running the Commands these things appeared on the terminal:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdread3 is already the newest version.
libdvdread3 set to manual installed.
libxine1-ffmpeg is already the newest version.
libxine1-ffmpeg set to manual installed.
The following packages were automatically installed and are no longer required:
  libboost-thread1.34.1 libboost-date-time1.34.1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dpkg-dev g++ g++-4.1 gettext html2text intltool-debian libc6-dev
  libstdc++6-4.1-dev linux-libc-dev patch po-debconf
Suggested packages:
  dh-make debian-keyring g++-multilib g++-4.1-multilib gcc-4.1-doc cvs
  gettext-doc glibc-doc manpages-dev libstdc++6-4.1-doc diff-doc
Recommended packages:
  libmail-sendmail-perl libcompress-zlib-perl
The following packages will be REMOVED:
  totem-gstreamer
The following NEW packages will be installed:
  build-essential debhelper dpkg-dev fakeroot g++ g++-4.1 gettext html2text
  intltool-debian libc6-dev libstdc++6-4.1-dev linux-libc-dev patch po-debconf
  totem-xine
0 upgraded, 15 newly installed, 1 to remove and 0 not upgraded.
Need to get 7998kB/12.1MB of archives.
After unpacking 40.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main linux-libc-dev 2.6.22-14.52 [653kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main libc6-dev 2.6.1-1ubuntu10 [3287kB]
Media change: please insert the disc labeled                      
 'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)'
in the drive '/cdrom/' and press enter

Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main html2text 1.3.2a-3build1 [90.6kB]   
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main gettext 0.16.1-2ubuntu3 [1552kB]    
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main intltool-debian 0.35.0+20060710.1 [31.6kB]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main po-debconf 1.0.9 [117kB]            
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main debhelper 5.0.51ubuntu3 [526kB]     
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main totem-xine 2.20.0-0ubuntu3 [1740kB] 
Fetched 7998kB in 4m58s (26.8kB/s)                                             
dpkg: totem-gstreamer: dependency problems, but removing anyway as you request:
 totem-mozilla depends on totem-xine (>= 2.20.0-0ubuntu3) | totem-gstreamer (>= 2.20.0-0ubuntu3); however:
  Package totem-xine is not installed.
  Package totem-gstreamer is to be removed.
 totem depends on totem-gstreamer (>= 2.20.0-0ubuntu3) | totem-xine (>= 2.20.0-0ubuntu3); however:
  Package totem-gstreamer is to be removed.
  Package totem-xine is not installed.
(Reading database ... 98317 files and directories currently installed.)
Removing totem-gstreamer ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Selecting previously deselected package linux-libc-dev.
(Reading database ... 98075 files and directories currently installed.)
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.22-14.52_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.6.1-1ubuntu10_i386.deb) ...
Selecting previously deselected package libstdc++6-4.1-dev.
Unpacking libstdc++6-4.1-dev (from .../libstdc++6-4.1-dev_4.1.2-16ubuntu2_i386.deb) ...
Selecting previously deselected package g++-4.1.
Unpacking g++-4.1 (from .../g++-4.1_4.1.2-16ubuntu2_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4.1.2-9ubuntu2_i386.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../p/patch/patch_2.5.9-4_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.14.5ubuntu16_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3ubuntu1_i386.deb) ...
Selecting previously deselected package html2text.
Unpacking html2text (from .../html2text_1.3.2a-3build1_i386.deb) ...
Selecting previously deselected package gettext.
Unpacking gettext (from .../gettext_0.16.1-2ubuntu3_i386.deb) ...
Selecting previously deselected package intltool-debian.
Unpacking intltool-debian (from .../intltool-debian_0.35.0+20060710.1_all.deb) ...
Selecting previously deselected package po-debconf.
Unpacking po-debconf (from .../po-debconf_1.0.9_all.deb) ...
Selecting previously deselected package debhelper.
Unpacking debhelper (from .../debhelper_5.0.51ubuntu3_all.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.7.1ubuntu1_i386.deb) ...
Selecting previously deselected package totem-xine.
Unpacking totem-xine (from .../totem-xine_2.20.0-0ubuntu3_i386.deb) ...
Setting up linux-libc-dev (2.6.22-14.52) ...
Setting up libc6-dev (2.6.1-1ubuntu10) ...
Setting up patch (2.5.9-4) ...
Setting up dpkg-dev (1.14.5ubuntu16) ...
Setting up html2text (1.3.2a-3build1) ...

Setting up gettext (0.16.1-2ubuntu3) ...

Setting up intltool-debian (0.35.0+20060710.1) ...
Setting up po-debconf (1.0.9) ...
Setting up debhelper (5.0.51ubuntu3) ...
Setting up fakeroot (1.7.1ubuntu1) ...

Setting up totem-xine (2.20.0-0ubuntu3) ...

Setting up libstdc++6-4.1-dev (4.1.2-16ubuntu2) ...
Setting up g++-4.1 (4.1.2-16ubuntu2) ...
Setting up g++ (4:4.1.2-9ubuntu2) ...

Setting up build-essential (11.3ubuntu1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
shouvik@shouvik-desktop:~$ ps x
  PID TTY      STAT   TIME COMMAND
 5154 ?        SL     0:00 /usr/bin/gnome-keyring-daemon -d
 5157 ?        Ssl    0:00 x-session-manager
 5196 ?        Ss     0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-s
 5199 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session x-session-ma
 5200 ?        Ss     0:00 /usr/bin/dbus-daemon --fork --print-pid 4 --print-add
 5202 ?        S      0:00 /usr/lib/libgconf2-4/gconfd-2 6
 5206 ?        Sl     0:00 /usr/lib/gnome-control-center/gnome-settings-daemon
 5233 ?        S      0:00 /usr/bin/metacity --sm-client-id=default0
 5235 ?        S      0:01 gnome-panel --sm-client-id default1
 5237 ?        S      0:01 nautilus --no-default-window --sm-client-id default2
 5245 ?        Ssl    0:00 /usr/lib/bonobo-activation/bonobo-activation-server -
 5246 ?        Ss     0:00 gnome-volume-manager --sm-client-id default4
 5258 ?        S      0:00 vino-session --sm-client-id default5
 5259 ?        S      0:00 bluetooth-applet
 5262 ?        S      0:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
 5290 ?        S      0:00 update-notifier
 5297 ?        Sl     0:00 /usr/lib/evolution/2.12/evolution-alarm-notify
 5302 ?        SNl    0:00 trackerd
 5305 ?        S      0:00 python /usr/share/system-config-printer/applet.py
 5308 ?        S      0:00 nm-applet --sm-disable
 5311 ?        Ss     0:00 gnome-power-manager
 5322 ?        Ss     0:00 gnome-screensaver
 5337 ?        Sl     0:00 /usr/lib/evolution/2.12/evolution-exchange-storage --
 5347 ?        S      0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid
 5350 ?        Sl     0:00 /usr/lib/evolution/evolution-data-server-1.12 --oaf-a
 5362 ?        S      0:00 /usr/lib/nautilus-cd-burner/mapping-daemon
 5383 ?        Sl     0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-i
 5398 ?        S      0:02 /usr/lib/fast-user-switch-applet/fast-user-switch-app
 5400 ?        Sl     0:00 /usr/bin/python /usr/lib/deskbar-applet/deskbar-apple
 5412 ?        S      0:00 /bin/sh /usr/bin/firefox
 5424 ?        S      0:00 /bin/sh /usr/lib/firefox/run-mozilla.sh /usr/lib/fire
 5428 ?        Sl     0:19 /usr/lib/firefox/firefox-bin
 5448 ?        Sl     0:00 gnome-terminal
 5450 ?        S      0:00 gnome-pty-helper
 5451 pts/0    Ss     0:00 bash
 5725 pts/0    R+     0:00 ps x
shouvik@shouvik-desktop:~$ sudo /usr/share/doc/libdvdread3/install-css.sh
--23:11:56--  [http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb](http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb)
           => `/tmp/dvdcss-Fp5728/libdvdcss.deb'
Resolving [www.dtek.chalmers.se](www.dtek.chalmers.se)... 129.16.30.198
Connecting to www.dtek.chalmers.se|129.16.30.198|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 25,178 (25K) [text/plain]

100%[====================================>] 25,178        18.40K/s             

23:11:58 (18.38 KB/s) - `/tmp/dvdcss-Fp5728/libdvdcss.deb' saved [25178/25178]

dpkg - warning: downgrading libdvdcss2 from 1.2.9-2medibuntu4 to 1.2.5-1.
(Reading database ... 100645 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.9-2medibuntu4 (using .../dvdcss-Fp5728/libdvdcss.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.5-1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place


This things did not make much sense to me....but in case anybody can comprehend. I then tried Apllications->Sound and Video->Xine Movie Player

Then also it failed to play.

Please help! I am really confused.

---

### Post by SunnyRabbiera on 2008-02-29
you probably need libdvdcss or something

---

### Post by shouvik_jnu on 2008-02-29
One of my friends asked me to type the command **_dmesg_** on the terminal. I have run the command. I have received this messages in the terminal.

[   16.828654]   MEM window: fea00000-feafffff
[   16.828657]   PREFETCH window: ee900000-fe8fffff
[   16.828661] PCI: Bridge: 0000:00:06.0
[   16.828663]   IO window: disabled.
[   16.828666]   MEM window: disabled.
[   16.828668]   PREFETCH window: disabled.
[   16.828672] PCI: Bridge: 0000:00:07.0
[   16.828673]   IO window: disabled.
[   16.828676]   MEM window: disabled.
[   16.828678]   PREFETCH window: disabled.
[   16.828694] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   16.828703] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   16.828715] NET: Registered protocol family 2
[   16.867057] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   16.867105] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   16.867329] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   16.867463] TCP: Hash tables configured (established 16384 bind 16384)
[   16.867466] TCP reno registered
[   16.879105] checking if image is initramfs... it is
[   17.330554] Switched to high resolution mode on CPU 0
[   17.503285] Freeing initrd memory: 7068k freed
[   17.503623] audit: initializing netlink socket (disabled)
[   17.503635] audit(1204326001.984:1): initialized
[   17.505165] VFS: Disk quotas dquot_6.5.1
[   17.505209] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   17.505289] io scheduler noop registered
[   17.505291] io scheduler anticipatory registered
[   17.505293] io scheduler deadline registered
[   17.505306] io scheduler cfq registered (default)
[   17.505345] Boot video device is 0000:01:00.0
[   17.505473] isapnp: Scanning for PnP cards...
[   17.858468] isapnp: No Plug & Play device found
[   17.878641] Real Time Clock Driver v1.12ac
[   17.878726] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   17.878811] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   17.879317] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   17.879929] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   17.880095] input: Macintosh mouse button emulation as /class/input/input0
[   17.880157] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   17.880410] serio: i8042 KBD port at 0x60,0x64 irq 1
[   17.880414] serio: i8042 AUX port at 0x60,0x64 irq 12
[   17.880547] mice: PS/2 mouse device common for all mice
[   17.880641] EISA: Probing bus 0 at eisa.0
[   17.880677] EISA: Detected 0 cards.
[   17.880834] TCP cubic registered
[   17.880852] NET: Registered protocol family 1
[   17.880872] Using IPI No-Shortcut mode
[   17.881016]   Magic number: 12:556:50
[   17.881486] Freeing unused kernel memory: 364k freed
[   17.921907] input: AT Translated Set 2 keyboard as /class/input/input1
[   19.061639] AppArmor: AppArmor initialized<5>audit(1204326003.484:2):  type=1505 info="AppArmor initialized" pid=1191
[   19.067108] fuse init (API version 7.8)
[   19.071089] Failure registering capabilities with primary security module.
[   19.534887] SCSI subsystem initialized
[   19.539149] libata version 2.21 loaded.
[   19.540305] pata_sis 0000:00:02.5: version 0.5.1
[   19.540433] scsi0 : pata_sis
[   19.540473] scsi1 : pata_sis
[   19.540565] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[   19.540568] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[   19.564444] usbcore: registered new interface driver usbfs
[   19.564466] usbcore: registered new interface driver hub
[   19.564486] usbcore: registered new device driver usb
[   19.588055] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   19.781583] Floppy drive(s): fd0 is 1.44M
[   19.833042] FDC 0 is a post-1991 82077
[   20.223496] ata1.00: ATAPI: Optiarc DVD RW AD-7190A, 1.03, max UDMA/66
[   20.223502] ata1.01: ATAPI: SONY    CD-RW  CRX230EE, 2YS1, max UDMA/33
[   20.411285] ata1.00: configured for UDMA/66
[   20.599078] ata1.01: configured for UDMA/33
[   20.755877] scsi 0:0:0:0: CD-ROM            Optiarc  DVD RW AD-7190A  1.03 PQ: 0 ANSI: 5
[   20.757022] scsi 0:0:1:0: CD-ROM            SONY     CD-RW  CRX230EE  2YS1 PQ: 0 ANSI: 5
[   20.759434] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 16
[   20.759447] ohci_hcd 0000:00:03.0: OHCI Host Controller
[   20.759744] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[   20.759762] ohci_hcd 0000:00:03.0: irq 16, io mem 0xfebf4000
[   20.779442] sr0: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
[   20.779448] Uniform CD-ROM driver Revision: 3.20
[   20.779664] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   20.785033] sr1: scsi3-mmc drive: 124x/52x writer cd/rw xa/form2 cdda tray
[   20.785160] sr 0:0:1:0: Attached scsi CD-ROM sr1
[   20.788968] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   20.788987] sr 0:0:1:0: Attached scsi generic sg1 type 5
[   20.816756] usb usb1: configuration #1 chosen from 1 choice
[   20.816784] hub 1-0:1.0: USB hub found
[   20.816795] hub 1-0:1.0: 3 ports detected
[   20.918644] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 17
[   20.918658] ohci_hcd 0000:00:03.1: OHCI Host Controller
[   20.918680] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[   20.918696] ohci_hcd 0000:00:03.1: irq 17, io mem 0xfebf5000
[   20.976528] usb usb2: configuration #1 chosen from 1 choice
[   20.976553] hub 2-0:1.0: USB hub found
[   20.976561] hub 2-0:1.0: 3 ports detected
[   21.078428] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 22 (level, low) -> IRQ 18
[   21.078439] ohci_hcd 0000:00:03.2: OHCI Host Controller
[   21.078459] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[   21.078473] ohci_hcd 0000:00:03.2: irq 18, io mem 0xfebf6000
[   21.136341] usb usb3: configuration #1 chosen from 1 choice
[   21.136365] hub 3-0:1.0: USB hub found
[   21.136372] hub 3-0:1.0: 2 ports detected
[   21.238583] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 19
[   21.238594] ehci_hcd 0000:00:03.3: EHCI Host Controller
[   21.238617] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 4
[   21.238646] PCI: cache line size of 64 is not supported by device 0000:00:03.3
[   21.238654] ehci_hcd 0000:00:03.3: irq 19, io mem 0xfebf7000
[   21.238662] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   21.238726] usb usb4: configuration #1 chosen from 1 choice
[   21.238752] hub 4-0:1.0: USB hub found
[   21.238760] hub 4-0:1.0: 8 ports detected
[   21.342239] sata_sis 0000:00:05.0: version 0.8
[   21.342260] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 17 (level, low) -> IRQ 20
[   21.342266] sata_sis 0000:00:05.0: Detected SiS 182/965L chipset
[   21.342342] scsi2 : sata_sis
[   21.342379] scsi3 : sata_sis
[   21.342403] ata3: SATA max UDMA/133 cmd 0x0001ec00 ctl 0x0001e802 bmdma 0x0001dc00 irq 20
[   21.342407] ata4: SATA max UDMA/133 cmd 0x0001e400 ctl 0x0001e002 bmdma 0x0001dc08 irq 20
[   23.547617] ata3: SATA link down (SStatus 1 SControl 300)
[   24.023098] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   24.031377] ata4.00: ATA-6: ST380817AS, 3.42, max UDMA/133
[   24.031380] ata4.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   24.047362] ata4.00: configured for UDMA/133
[   24.047462] scsi 3:0:0:0: Direct-Access     ATA      ST380817AS       3.42 PQ: 0 ANSI: 5
[   24.047861] scsi 3:0:0:0: Attached scsi generic sg2 type 0
[   24.054427] sd 3:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   24.054441] sd 3:0:0:0: [sda] Write Protect is off
[   24.054444] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.054458] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.054504] sd 3:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   24.054512] sd 3:0:0:0: [sda] Write Protect is off
[   24.054515] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.054527] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.054532]  sda: sda1 sda2 < sda5 > sda3 sda4
[   24.098125] sd 3:0:0:0: [sda] Attached SCSI disk
[   24.355258] Attempting manual resume
[   24.355262] swsusp: Resume From Partition 8:4
[   24.355264] PM: Checking swsusp image.
[   24.355471] PM: Resume from disk failed.
[   24.368943] EXT3-fs: INFO: recovery required on readonly filesystem.
[   24.368947] EXT3-fs: write access will be enabled during recovery.
[   27.203880] kjournald starting.  Commit interval 5 seconds
[   27.203895] EXT3-fs: recovery complete.
[   27.221254] EXT3-fs: mounted filesystem with ordered data mode.
[   33.175449] Linux agpgart interface v0.102 (c) Dave Jones
[   33.287178] agpgart: Detected SiS chipset - id:1888
[   33.287604] agpgart: AGP aperture is 4M @ 0xe0000000
[   33.309758] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   33.312350] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   33.613895] sis190 Gigabit Ethernet driver 1.2 loaded.
[   33.613919] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 21
[   33.613929] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   33.628473] 0000:00:04.0: Read MAC address from APC.
[   33.684418] 0000:00:04.0: Realtek PHY RTL8201 transceiver at address 1.
[   34.211812] 0000:00:04.0: Using transceiver at address 1 as default.
[   34.243896] 0000:00:04.0: SiS 190 PCI Fast Ethernet adapter at de956c00 (IRQ: 21), 12:34:56:78:90:12
[   34.243900] eth0: GMII mode.
[   34.243905] eth0: Enabling Auto-negotiation.
[   34.614614] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 22
[   35.034900] intel8x0_measure_ac97_clock: measured 52410 usecs
[   35.034904] intel8x0: clocking to 48000
[   35.108125] input: ImPS/2 Logitech Wheel Mouse as /class/input/input2
[   35.111036] parport_pc 00:09: reported by Plug and Play ACPI
[   35.111076] parport0: PC-style at 0x378, irq 7 [PCSPP]
[   35.112522] input: PC Speaker as /class/input/input3
[   35.711449] lp0: using parport0 (interrupt-driven).
[   35.749198] Adding 1405676k swap on /dev/sda4.  Priority:-1 extents:1 across:1405676k
[   36.188923] EXT3 FS on sda3, internal journal
[   41.908020] No dock devices found.
[   42.020816] input: Power Button (FF) as /class/input/input4
[   42.024693] ACPI: Power Button (FF) [PWRF]
[   42.058079] input: Power Button (CM) as /class/input/input5
[   42.061980] ACPI: Power Button (CM) [PWRB]
[   42.301278] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 2800+ processors (version 2.00.00)
[   42.301318] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x2
[   42.301321] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x12
[   43.100506] Failure registering capabilities with primary security module.
[   43.355152] ppdev: user-space parallel port driver
[   43.577585] audit(1204306228.648:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4720 profile="/usr/sbin/cupsd"
[   43.641950] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   43.641956] apm: overridden by ACPI.
[   43.943808] Bluetooth: Core ver 2.11
[   43.943926] NET: Registered protocol family 31
[   43.943929] Bluetooth: HCI device and connection manager initialized
[   43.943932] Bluetooth: HCI socket layer initialized
[   43.962595] Bluetooth: L2CAP ver 2.8
[   43.962599] Bluetooth: L2CAP socket layer initialized
[   44.025033] Bluetooth: RFCOMM socket layer initialized
[   44.025131] Bluetooth: RFCOMM TTY layer initialized
[   44.025134] Bluetooth: RFCOMM ver 1.8
[   31.012000] Marking TSC unstable due to: cpufreq changes.
[   31.064000] Time: acpi_pm clocksource has been installed.
[   31.512000] Clocksource tsc unstable (delta = -241713037 ns)
[   36.956000] eth0: mii ext = 0000.
[   36.972000] eth0: mii lpa = 45e1 adv = 01e1.
[   36.972000] eth0: link on 100 Mbps Full Duplex mode.
[   39.140000] NET: Registered protocol family 17
[   45.672000] NET: Registered protocol family 10
[   45.688000] lo: Disabled Privacy Extensions
[   56.560000] eth0: no IPv6 routers present
[  418.928000] cdrom: sr1: mrw address space DMA selected
[  418.948000] cdrom: sr1: mrw address space DMA selected
[  419.668000] UDF-fs: No VRS found
[  419.688000] ISO 9660 Extensions: Microsoft Joliet Level 3
[  419.708000] ISO 9660 Extensions: RRIP_1991A
[  424.204000] cdrom: sr1: mrw address space DMA selected
[  424.896000] cdrom: sr1: mrw address space DMA selected
[  814.264000] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  814.264000] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  814.264000] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  814.264000] end_request: I/O error, dev sr0, sector 64
[  814.264000] Buffer I/O error on device sr0, logical block 8
[  821.988000] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  821.988000] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  821.988000] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  821.988000] end_request: I/O error, dev sr0, sector 64
[  821.988000] Buffer I/O error on device sr0, logical block 8
[  829.532000] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  829.532000] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  829.532000] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  829.532000] end_request: I/O error, dev sr0, sector 0
[  829.532000] Buffer I/O error on device sr0, logical block 0
[  829.532000] Buffer I/O error on device sr0, logical block 1
[  829.532000] Buffer I/O error on device sr0, logical block 2
[  829.532000] Buffer I/O error on device sr0, logical block 3
[  836.988000] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  836.988000] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  836.988000] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  836.988000] end_request: I/O error, dev sr0, sector 0
[  836.988000] Buffer I/O error on device sr0, logical block 0
[  844.572000] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  844.572000] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  844.572000] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  844.572000] end_request: I/O error, dev sr0, sector 128
[  844.572000] Buffer I/O error on device sr0, logical block 16
[  852.200000] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  852.200000] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  852.200000] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  852.200000] end_request: I/O error, dev sr0, sector 128
[  852.200000] Buffer I/O error on device sr0, logical block 16
[  859.272000] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  859.272000] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  859.272000] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  859.272000] end_request: I/O error, dev sr0, sector 1024
[  859.272000] Buffer I/O error on device sr0, logical block 128
[  866.700000] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  866.700000] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  866.700000] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  866.700000] end_request: I/O error, dev sr0, sector 1024
[  866.700000] Buffer I/O error on device sr0, logical block 128
[  874.728000] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  874.728000] sr 0:0:0:0: [sr0] Sense Key : Medium Error [deferred] 
[  874.728000] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  874.728000] end_request: I/O error, dev sr0, sector 1024
[  874.728000] Buffer I/O error on device sr0, logical block 128
[  882.252000] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  882.252000] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  882.252000] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  882.252000] end_request: I/O error, dev sr0, sector 0
[  882.252000] Buffer I/O error on device sr0, logical block 0
[  889.348000] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  889.348000] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  889.348000] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  889.348000] end_request: I/O error, dev sr0, sector 128
[  889.348000] Buffer I/O error on device sr0, logical block 16
[  896.308000] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  896.308000] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  896.308000] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  896.308000] end_request: I/O error, dev sr0, sector 1024
[  896.308000] Buffer I/O error on device sr0, logical block 128
[  903.524000] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  903.524000] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  903.524000] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  903.524000] end_request: I/O error, dev sr0, sector 1024
[  903.524000] Buffer I/O error on device sr0, logical block 128
[  911.860000] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  911.860000] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  911.860000] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  911.860000] end_request: I/O error, dev sr0, sector 0
[  911.860000] Buffer I/O error on device sr0, logical block 0
[  918.928000] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  918.928000] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  918.928000] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  918.928000] end_request: I/O error, dev sr0, sector 8
[  918.928000] Buffer I/O error on device sr0, logical block 1
[  918.928000] Buffer I/O error on device sr0, logical block 2
[  918.928000] Buffer I/O error on device sr0, logical block 3
[  926.688000] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  926.688000] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  926.688000] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  926.688000] end_request: I/O error, dev sr0, sector 0
[  926.688000] Buffer I/O error on device sr0, logical block 0
[  934.316000] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  934.316000] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  934.316000] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  934.316000] end_request: I/O error, dev sr0, sector 128
[  934.316000] Buffer I/O error on device sr0, logical block 16
[  941.928000] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  941.928000] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  941.928000] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  941.928000] end_request: I/O error, dev sr0, sector 128
[  941.928000] Buffer I/O error on device sr0, logical block 16
[  948.916000] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  948.916000] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  948.916000] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  948.916000] end_request: I/O error, dev sr0, sector 1024
[  948.916000] Buffer I/O error on device sr0, logical block 128
[  955.876000] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  955.876000] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  955.876000] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  955.876000] end_request: I/O error, dev sr0, sector 1024
[  955.876000] Buffer I/O error on device sr0, logical block 128
[  962.876000] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  962.876000] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  962.876000] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  962.876000] end_request: I/O error, dev sr0, sector 1024
[  962.876000] Buffer I/O error on device sr0, logical block 128
[  969.860000] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  969.860000] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  969.860000] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  969.860000] end_request: I/O error, dev sr0, sector 0
[  969.860000] Buffer I/O error on device sr0, logical block 0
[  977.668000] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  977.668000] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  977.668000] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  977.668000] end_request: I/O error, dev sr0, sector 8
[  977.668000] Buffer I/O error on device sr0, logical block 1
[  977.668000] Buffer I/O error on device sr0, logical block 2
[  977.668000] Buffer I/O error on device sr0, logical block 3
[  984.776000] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  984.776000] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  984.776000] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  984.776000] end_request: I/O error, dev sr0, sector 0
[  984.776000] Buffer I/O error on device sr0, logical block 0
[  991.836000] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  991.836000] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  991.836000] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  991.836000] end_request: I/O error, dev sr0, sector 128
[  991.836000] Buffer I/O error on device sr0, logical block 16
[  998.864000] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  998.864000] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  998.864000] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  998.864000] end_request: I/O error, dev sr0, sector 128
[  998.864000] Buffer I/O error on device sr0, logical block 16
[ 1005.860000] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1005.860000] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 1005.860000] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[ 1005.860000] end_request: I/O error, dev sr0, sector 1024
[ 1005.860000] Buffer I/O error on device sr0, logical block 128
[ 1012.436000] sr 0:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[ 1012.436000] : Add. Sense: Medium not present
[ 1012.436000] end_request: I/O error, dev sr0, sector 1024
[ 1012.436000] Buffer I/O error on device sr0, logical block 128
[ 1012.444000] sr 0:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[ 1012.444000] : Add. Sense: Medium not present
[ 1012.444000] end_request: I/O error, dev sr0, sector 1024
[ 1012.444000] Buffer I/O error on device sr0, logical block 128
[ 1097.112000] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1097.112000] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 1097.112000] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[ 1097.112000] end_request: I/O error, dev sr0, sector 64
[ 1097.112000] Buffer I/O error on device sr0, logical block 8
[ 1104.332000] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1104.332000] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 1104.332000] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[ 1104.332000] end_request: I/O error, dev sr0, sector 64
[ 1104.332000] Buffer I/O error on device sr0, logical block 8
[ 1215.644000] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1215.644000] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 1215.644000] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[ 1215.644000] end_request: I/O error, dev sr0, sector 0
[ 1215.644000] Buffer I/O error on device sr0, logical block 0
[ 1215.644000] Buffer I/O error on device sr0, logical block 1
[ 1215.644000] Buffer I/O error on device sr0, logical block 2
[ 1215.644000] Buffer I/O error on device sr0, logical block 3
[ 1222.592000] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1222.592000] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 1222.592000] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[ 1222.592000] end_request: I/O error, dev sr0, sector 0
[ 1222.592000] Buffer I/O error on device sr0, logical block 0
[ 1229.576000] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1229.576000] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 1229.576000] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[ 1229.576000] end_request: I/O error, dev sr0, sector 128
[ 1229.576000] Buffer I/O error on device sr0, logical block 16
[ 1236.568000] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1236.568000] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 1236.568000] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[ 1236.568000] end_request: I/O error, dev sr0, sector 128
[ 1236.568000] Buffer I/O error on device sr0, logical block 16
[ 1244.052000] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1244.052000] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 1244.052000] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[ 1244.052000] end_request: I/O error, dev sr0, sector 1024
[ 1244.052000] Buffer I/O error on device sr0, logical block 128
[ 1251.016000] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1251.016000] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 1251.016000] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[ 1251.016000] end_request: I/O error, dev sr0, sector 1024
[ 1251.016000] Buffer I/O error on device sr0, logical block 128
[ 1258.640000] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1258.640000] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 1258.640000] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[ 1258.640000] end_request: I/O error, dev sr0, sector 1024
[ 1258.640000] Buffer I/O error on device sr0, logical block 128
[ 1265.744000] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1265.744000] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 1265.744000] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[ 1265.744000] end_request: I/O error, dev sr0, sector 0
[ 1265.744000] Buffer I/O error on device sr0, logical block 0
[ 1273.388000] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1273.388000] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 1273.388000] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[ 1273.388000] end_request: I/O error, dev sr0, sector 128
[ 1273.388000] Buffer I/O error on device sr0, logical block 16
[ 1280.336000] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1280.336000] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 1280.336000] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[ 1280.336000] end_request: I/O error, dev sr0, sector 1024
[ 1280.336000] Buffer I/O error on device sr0, logical block 128
[ 1287.360000] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1287.360000] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 1287.360000] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[ 1287.360000] end_request: I/O error, dev sr0, sector 1024
[ 1287.360000] Buffer I/O error on device sr0, logical block 128


I am not a technical person. So, this messages really does not make much sense to me. I am  using UBUNTU 7.10. Please somebody help me.

Thanks in advance:(

---

### Post by forrestcupp on 2008-02-29
> **SunnyRabbiera said:**
> you probably need libdvdcss or something

+1

Install this and it should work in any media player.
```
sudo apt-get install libdvdcss
```

---

### Post by shouvik_jnu on 2008-02-29
I have already installed libdvdcss

But it is still not working

---

### Post by shouvik_jnu on 2008-02-29
Somebody please help!!

---

### Post by NotPhil on 2008-02-29
> **shouvik_jnu said:**
> I have already installed libdvdcss

But it is still not workingYou might need to install regionset and use it to change the region on your DVD drive to whatever region your DVDs use.

---

### Post by sanddgroper on 2008-02-29
Hi
Sounds like you may need a new DVD RW.What brand are you using now?.
What writing software are you using.
you might like to look through this thread.
[http://ubuntuforums.org/showthread.php?t=645470&highlight=dvd+mounting](http://ubuntuforums.org/showthread.php?t=645470&highlight=dvd+mounting)

Cheers
Sandy

---

### Post by shouvik_jnu on 2008-02-29
I have typed the following commands:

sudo lshw -C disk

cat /etc/fstab

I am posting the output as suggested by the link given above:

The terminal showed:
*-cdrom:0               
       description: DVD-RAM writer
       product: DVD RW AD-7190A
       vendor: Optiarc
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.03
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=open
  *-cdrom:1
       description: CD-R/CD-RW writer
       product: CD-RW  CRX230EE
       vendor: SONY
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/cdrom1
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: 2YS1
       capabilities: removable audio cd-r cd-rw
       configuration: ansiversion=5 status=open
  *-disk
       description: SCSI Disk
       product: ST380817AS
       vendor: ATA
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/sda
       version: 3.42
       serial: 4MR10Y62
       size: 74GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
shouvik@shouvik-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=da39b122-0fd0-42ac-b596-17e3162ab579 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=00885FBA885FAD42 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=C855-EDC8  /media/sda5     vfat    defaults,umask=007,gid=46 0       1
# /dev/sda4
UUID=7ba8b2a5-2daf-45d1-baa7-f5cc1aa12de9 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

I am unable to do the next step.

Please help!

---

### Post by shouvik_jnu on 2008-02-29
My DVD Writer is that of Sony

---

### Post by shouvik_jnu on 2008-02-29
I typed the command:

 ls -l /dev | grep dvd*


The prompt from my Terminal was

lrwxrwxrwx 1 root   root           4 2008-03-01 09:07 dvd -> scd0

Thanks in advance for the help

---

### Post by shouvik_jnu on 2008-02-29
I have run the command

gksudo gedit /etc/fstab

and this were the results





# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=da39b122-0fd0-42ac-b596-17e3162ab579 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=00885FBA885FAD42 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=C855-EDC8  /media/sda5     vfat    defaults,umask=007,gid=46 0       1
# /dev/sda4
UUID=7ba8b2a5-2daf-45d1-baa7-f5cc1aa12de9 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by sanddgroper on 2008-03-01
Hi

Well unless I am reading something wrong your DVD writer is an optiarc and your
sony is only a cd writer.If this is so then it will only read and write CD's
does the Optiarc work ok?
See this
description: CD-R/CD-RW writer
product: CD-RW CRX230EE
vendor: SONY
Only reads and writes CD's

This
description: DVD-RAM writer
product: DVD RW AD-7190A
vendor: Optiarc
Reads and writes DVD's

Cheers
Sandy

---

### Post by shouvik_jnu on 2008-03-01
thanks for your help!!

I had to go and replace my new DVD-RW and it is working fine now.

Thanks again for the help.
:):guitar:

---

