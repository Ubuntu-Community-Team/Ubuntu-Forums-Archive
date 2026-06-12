---
title: "Ubuntu Locking Up"
date: 2006-03-13
forum: Absolute Beginner Talk
---

### Post by WoodyMahan on 2006-03-13
My Ubuntu OS seems to hang after being used for a short time.  It locks up completely and won't respond to keyboard or mouse interactions in any way.

I hard boot and everything comes back up OK.  But if I use the machine for about an hour or so it will hang up again.   The machine is away from my desk so I use VNC to terminal into it.  I don't do anything more than jusr surf the web a little bit.  Then disconnect.  When I reconnect, it will hang up.  

Is this a bug in the VNC connection?

Thanks

Wood

---

### Post by WoodyMahan on 2006-03-13
Nothing?  No one has ever had problems with their Breezy OS locking up?

---

### Post by AtinLango on 2006-03-13
What RAM size does the computer have? Perhaps it runs out of memory. Try to check free memory using (not sure if sudo is mandatory in these cases):

```
sudo free
```

and also see what processes are running:

```
sudo ps
```

and let us see.

---

### Post by Brunellus on 2006-03-13
[QUOTE=WoodyMahan]Nothing?  No one has ever had problems with their Breezy OS locking up?[/QUOTE]
possible culprits:  

1) bad RAM

2) bad kernel module 

3) wrong kernel (highly unlikely--this would make for an unbootable system)

Post your detailed system specifications and let's see if we can't help you solve the mystery.

---

### Post by WoodyMahan on 2006-03-13
Pent III 1 GB Mhz processor
1 GB RAM
I'll post the ps readouts in a sec.

---

### Post by WoodyMahan on 2006-03-13
woody@ubuntu:~$ sudo free
Password:
             total       used       free     shared    buffers     cached
Mem:       1036700     303644     733056          0      21268     168660
-/+ buffers/cache:     113716     922984
Swap:       755012          0     755012
woody@ubuntu:~$



woody@ubuntu:~$ sudo ps
  PID TTY          TIME CMD
 8443 pts/0    00:00:00 ps
woody@ubuntu:~$


Of course I would like to have some sort of readout to provide during the lockup but I can't get it to do anything then.


ALSO:  If there is a command that will print out the entir system specs for me to post the might be helpful.

Thanks all.

---

### Post by WoodyMahan on 2006-03-13
How would I test for a bad kernel module?

---

### Post by Brunellus on 2006-03-13
you would probably get a better idea of what's going on of you printed the output of pstree -a

also, have you looked through the logfiles in /var/log for warnings or errors?

---

### Post by WoodyMahan on 2006-03-13
I did check the logs, but honestly I can't make heads or tails of the output there yet.  Are there any keyword in the output that might point to a problem?

Here is the out put from pstree -a

woody@ubuntu:~$ pstree -a
init
  &#9500;&#9472;acpid -c /etc/acpi/events -s /var/run/acpid.socket
  &#9500;&#9472;atd
  &#9500;&#9472;bonobo-activati --ac-activate--ior-output-f
  &#9500;&#9472;clock-applet--oaf-activate-iid=OAFIID:GNOME_ClockApplet_Fa
  &#9500;&#9472;cron
  &#9500;&#9472;cupsd -F
  &#9500;&#9472;dbus-daemon --system
  &#9500;&#9472;dbus-daemon --fork --print-pid 8 --print-address 6 --session
  &#9500;&#9472;dbus-launch --exit-with-session x-session-manager
  &#9500;&#9472;dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
  &#9500;&#9472;dhclient3 -pf /var/run/dhclient.eth0.pid -lf ...
  &#9500;&#9472;(events/0)
  &#9500;&#9472;firefox /usr/bin/firefox
  &#9474;   &#9492;&#9472;run-mozilla.sh /opt/firefox/run-mozilla.sh /opt/firefox/firefox-bin
  &#9474;       &#9492;&#9472;firefox-bin
  &#9500;&#9472;gam_server
  &#9500;&#9472;gconfd-2 5
  &#9500;&#9472;gdm
  &#9474;   &#9492;&#9472;gdm
  &#9474;       &#9500;&#9472;Xorg :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp ...
  &#9474;       &#9492;&#9472;x-session-manag
  &#9474;           &#9492;&#9472;ssh-agent /usr/bin/dbus-launch --exit-with-session ...
  &#9500;&#9472;getty 38400 tty1
  &#9500;&#9472;getty 38400 tty2
  &#9500;&#9472;getty 38400 tty3
  &#9500;&#9472;getty 38400 tty4
  &#9500;&#9472;getty 38400 tty5
  &#9500;&#9472;getty 38400 tty6
  &#9500;&#9472;gmail-notify /usr/bin/gmail-notify
  &#9474;   &#9492;&#9472;python ./notifier.py
  &#9500;&#9472;gnome-cups-icon --sm-config-prefix /gnome-cups-icon-FRWTS4/ ...
  &#9500;&#9472;gnome-keyring-d
  &#9500;&#9472;gnome-panel --sm-config-prefix /gnome-panel-a828fa/ --sm-client-id...
  &#9500;&#9472;gnome-settings---oaf-activate-iid=OAFIID:GNOME_Se
  &#9500;&#9472;gnome-terminal --working-directory=
  &#9474;   &#9500;&#9472;bash
  &#9474;   &#9474;   &#9492;&#9472;pstree -a
  &#9474;   &#9492;&#9472;gnome-pty-helpe
  &#9500;&#9472;gnome-vfs-daemo--oaf-activate-iid=OAFIID:GNOME_VFS_Daemon_
  &#9500;&#9472;gnome-volume-ma --sm-config-prefix /gnome-volume-manager-KTRnG4/--sm-clien
  &#9500;&#9472;hald
  &#9474;   &#9500;&#9472;hald-addon-acpi
  &#9474;   &#9492;&#9472;hald-addon-stor
  &#9500;&#9472;hcid
  &#9500;&#9472;hpiod
  &#9500;&#9472;(khelper)
  &#9500;&#9472;(khubd)
  &#9500;&#9472;(kjournald)
  &#9500;&#9472;(kjournald)
  &#9500;&#9472;klogd -P /var/run/klogd/kmsg
  &#9500;&#9472;(krfcommd)
  &#9500;&#9472;(kseriod)
  &#9500;&#9472;(ksoftirqd/0)
  &#9500;&#9472;(kswapd0)
  &#9500;&#9472;(kthread)
  &#9474;   &#9500;&#9472;(aio/0)
  &#9474;   &#9500;&#9472;(kacpid)
  &#9474;   &#9500;&#9472;(kblockd/0)
  &#9474;   &#9500;&#9472;(pdflush)
  &#9474;   &#9492;&#9472;(pdflush)
  &#9500;&#9472;mapping-daemon
  &#9500;&#9472;metacity --sm-save-file 1141849473-7153-3437182930.ms
  &#9500;&#9472;mixer_applet2--oaf-activate-iid=OAFIID:GNOME_MixerApplet
  &#9500;&#9472;nautilus --sm-config-prefix /nautilus-y8Xi84/ --sm-client-id...
  &#9500;&#9472;notification-ar--oaf-activate-iid=OAFIID:GNOME_No
  &#9500;&#9472;notification-da
  &#9500;&#9472;python /usr/sbin/hpssd
  &#9500;&#9472;(scsi_eh_0)
  &#9500;&#9472;(scsi_eh_1)
  &#9500;&#9472;sdpd
  &#9500;&#9472;syslogd -u syslog
  &#9500;&#9472;trashapplet--oaf-activate-iid=OAFIID:GNOME_Panel_TrashAp
  &#9500;&#9472;udevd --daemon
  &#9500;&#9472;update-notifier --sm-config-prefix /update-notifier-XS1Kc5/ ...
  &#9500;&#9472;vino-server --oaf-activate-iid=OAFIID:GNOME_RemoteDesktopServer--
  &#9500;&#9472;wnck-applet--oaf-activate-iid=OAFIID:GNOME_Wncklet_Factory
  &#9492;&#9472;xscreensaver -nosplash

---

### Post by WoodyMahan on 2006-03-13
Here'e a copy of today's syslog as well.  The system locked up on me around 9 or 9:30.

localhost syslogd 1.4.1#17ubuntu3 restart.
localhost anacron[24144] Job `cron.daily' terminated
localhost anacron[24144] Normal exit (1 job run)
localhost  -- MARK --
localhost syslogd 1.4.1#17ubuntu3 restart.
localhost kernel Inspecting /boot/System.map-2.6.12-10-386
localhost kernel Loaded 29010 symbols from /boot/System.map-2.6.12-10-386.
localhost kernel Symbols match kernel version 2.6.12.
localhost kernel No module symbols loaded - kernel modules not enabled. 
localhost kernel kernel code, 16884k reserved, 762k data, 224k init, 131064k highmem)
localhost kernel [4294668.875000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
localhost kernel [4294668.875000] Calibrating delay loop... 1974.27 BogoMIPS (lpj=987136)
localhost kernel [4294668.896000] Security Framework v1.0.0 initialized
localhost kernel [4294668.896000] SELinux:  Disabled at boot.
localhost kernel [4294668.896000] Mount-cache hash table entries: 512
localhost kernel [4294668.896000] CPU: After generic identify, caps: 0383fbff 00000000 00000000 00000000 00000000 00000000 00000000
localhost kernel [4294668.896000] CPU: After vendor identify, caps: 0383fbff 00000000 00000000 00000000 00000000 00000000 00000000
localhost kernel [4294668.896000] CPU: L1 I cache: 16K, L1 D cache: 16K
localhost kernel [4294668.896000] CPU: L2 cache: 256K
localhost kernel [4294668.896000] CPU: After all inits, caps: 0383fbff 00000000 00000000 00000040 00000000 00000000 00000000
localhost kernel [4294668.896000] CPU: Intel Pentium III (Coppermine) stepping 0a
localhost kernel [4294668.896000] Enabling fast FPU save and restore... done.
localhost kernel [4294668.896000] Enabling unmasked SIMD FPU exception support... done.
localhost kernel [4294668.896000] Checking 'hlt' instruction... OK.
localhost kernel [4294668.900000] Checking for popad bug... OK.
localhost kernel [4294668.900000] checking if image is initramfs... it is
localhost kernel [4294669.711000] Freeing initrd memory: 5172k freed
localhost kernel [4294669.717000] ACPI: Looking for DSDT in initrd... not found!
localhost kernel [4294669.843000]  not found!
localhost kernel [4294669.871000] ENABLING IO-APIC IRQs
localhost kernel [4294669.871000] ..TIMER: vector=0x31 pin1=0 pin2=-1
localhost kernel [4294669.982000] NET: Registered protocol family 16
localhost kernel [4294669.982000] EISA bus registered
localhost kernel [4294669.982000] ACPI: bus type pci registered
localhost kernel [4294669.996000] PCI: PCI BIOS revision 2.10 entry at 0xfc7de, last bus=1
localhost kernel [4294669.996000] PCI: Using configuration type 1
localhost kernel [4294669.996000] mtrr: v2.0 (20020519)
localhost kernel [4294669.997000] ACPI: Subsystem revision 20050729
localhost kernel [4294670.012000] ACPI: Interpreter enabled
localhost kernel [4294670.012000] ACPI: Using IOAPIC for interrupt routing
localhost kernel [4294670.013000] ACPI: PCI Root Bridge [PCI0] (0000:00)
localhost kernel [4294670.013000] PCI: Probing PCI hardware (bus 00)
localhost kernel [4294670.013000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
localhost kernel [4294670.021000] ACPI: Assume root bridge [\_SB_.PCI1] segment is 0
localhost kernel [4294670.024000] Boot video device is 0000:00:0e.0
localhost kernel [4294670.026000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
localhost kernel [4294670.031000] ACPI: PCI Root Bridge [PCI1] (0000:01)
localhost kernel [4294670.031000] PCI: Probing PCI hardware (bus 01)
localhost kernel [4294670.031000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
localhost kernel [4294670.040000] ACPI: Assume root bridge [\_SB_.PCI1] segment is 0
localhost kernel [4294670.044000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI1._PRT]
localhost kernel [4294670.046000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14)
localhost kernel [4294670.047000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
localhost kernel [4294670.048000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
localhost kernel [4294670.049000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
localhost kernel [4294670.050000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
localhost kernel [4294670.051000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
localhost kernel [4294670.052000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
localhost kernel [4294670.053000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
localhost kernel [4294670.054000] ACPI: PCI Interrupt Link [LNKI] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
localhost kernel [4294670.055000] ACPI: PCI Interrupt Link [LNKJ] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
localhost kernel [4294670.056000] ACPI: PCI Interrupt Link [LNKK] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
localhost kernel [4294670.057000] ACPI: PCI Interrupt Link [LNKL] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
localhost kernel [4294670.058000] ACPI: PCI Interrupt Link [LNKM] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
localhost kernel [4294670.059000] ACPI: PCI Interrupt Link [LNKN] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
localhost kernel [4294670.060000] ACPI: PCI Interrupt Link [LNKO] (IRQs 3 4 *5 6 7 9 10 11 12 14)
localhost kernel [4294670.061000] ACPI: PCI Interrupt Link [LNKP] (IRQs 3 4 5 6 7 9 10 *11 12 14)
localhost kernel [4294670.062000] ACPI: PCI Interrupt Link [LUSB] (IRQs 3 4 5 6 7 *10 11 12 14)
localhost kernel [4294670.062000] Linux Plug and Play Support v0.97 (c) Adam Belay
localhost kernel [4294670.062000] pnp: PnP ACPI init
localhost kernel [4294670.080000] pnp: PnP ACPI: found 12 devices
localhost kernel [4294670.080000] PnPBIOS: Disabled by ACPI PNP
localhost kernel [4294670.080000] PCI: Using ACPI for IRQ routing
localhost kernel [4294670.080000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
localhost kernel [4294670.088000] pnp: 00:0a: ioport range 0x814-0x85b could not be reserved
localhost kernel [4294670.088000] pnp: 00:0a: ioport range 0x580-0x58f has been reserved
localhost kernel [4294670.088000] pnp: 00:0a: ioport range 0xc00-0xcd7 has been reserved
localhost kernel [4294670.088000] pnp: 00:0a: ioport range 0xf50-0xf58 has been reserved
localhost kernel [4294670.089000] audit: initializing netlink socket (disabled)
localhost kernel [4294670.089000] audit: initialized
localhost kernel [4294670.089000] highmem bounce pool size: 64 pages
localhost kernel [4294670.089000] VFS: Disk quotas dquot_6.5.1
localhost kernel [4294670.089000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
localhost kernel [4294670.089000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
localhost kernel [4294670.089000] devfs: boot_options: 0x0
localhost kernel [4294670.089000] Initializing Cryptographic API
localhost kernel [4294670.089000] isapnp: Scanning for PnP cards...
localhost kernel [4294670.443000] isapnp: No Plug & Play device found
localhost kernel [4294670.474000] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
localhost kernel [4294670.475000] serio: i8042 AUX port at 0x60,0x64 irq 12
localhost kernel [4294670.475000] serio: i8042 KBD port at 0x60,0x64 irq 1
localhost kernel [4294670.475000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
localhost kernel [4294670.476000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
localhost kernel [4294670.476000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
localhost kernel [4294670.479000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
localhost kernel [4294670.480000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
localhost kernel [4294670.480000] io scheduler noop registered
localhost kernel [4294670.480000] io scheduler anticipatory registered
localhost kernel [4294670.480000] io scheduler deadline registered
localhost kernel [4294670.480000] io scheduler cfq registered
localhost kernel [4294670.481000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
localhost kernel [4294670.481000] EISA: Probing bus 0 at eisa.0
localhost kernel [4294670.481000] EISA: Cannot allocate resource for mainboard
localhost kernel [4294670.481000] EISA: Detected 0 cards.
localhost kernel [4294670.481000] NET: Registered protocol family 2
localhost kernel [4294670.491000] IP: routing cache hash table of 8192 buckets, 64Kbytes
localhost kernel [4294670.491000] TCP established hash table entries: 262144 (order: 9, 2097152 bytes)
localhost kernel [4294670.500000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
localhost kernel [4294670.502000] TCP: Hash tables configured (established 262144 bind 65536)
localhost kernel [4294670.502000] NET: Registered protocol family 8
localhost kernel [4294670.502000] NET: Registered protocol family 20
localhost kernel [4294670.502000] ACPI wakeup devices: 
localhost kernel [4294670.502000] PCI0 DRAC PCI1 
localhost kernel [4294670.502000] ACPI: (supports S0 S4 S5)
localhost kernel [4294670.503000] Freeing unused kernel memory: 224k freed
localhost kernel [4294670.515000] input: AT Translated Set 2 keyboard on isa0060/serio0
localhost kernel [4294670.535000] vga16fb: initializing
localhost kernel [4294670.535000] vga16fb: mapped to 0xc00a0000
localhost kernel [4294670.665000] Console: switching to colour frame buffer device 80x30
localhost kernel [4294670.665000] fb0: VGA16 VGA frame buffer device
localhost kernel [4294671.813000] Capability LSM initialized
localhost kernel [4294671.837000] NET: Registered protocol family 1
localhost kernel [4294671.863000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
localhost kernel [4294671.863000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
localhost kernel [4294671.863000] ACPI: bus type ide registered
localhost kernel [4294671.889000] SCSI subsystem initialized
localhost kernel [4294671.897000] ACPI: PCI Interrupt 0000:01:02.0[A] -> GSI 30 (level, low) -> IRQ 30
localhost kernel [4294672.106000] ACPI: PCI Interrupt 0000:01:02.1[B] -> GSI 31 (level, low) -> IRQ 31
localhost kernel [4294672.317000] scsi0 : Adaptec AIC7XXX EISA/VLB/PCI SCSI HBA DRIVER, Rev 6.2.36
localhost kernel [4294672.317000]         <Adaptec aic7899 Ultra160 SCSI adapter>
localhost kernel [4294672.317000]         aic7899: Ultra160 Wide Channel A, SCSI Id=7, 32/253 SCBs
localhost kernel [4294672.317000] 
localhost kernel [4294687.316000]   Vendor: QUANTUM   Model: ATLAS10K2-TY184L  Rev: DA40
localhost kernel [4294687.316000]   Type:   Direct-Access                      ANSI SCSI revision: 03
localhost kernel [4294687.316000] scsi0:A:0:0: Tagged Queuing enabled.  Depth 8
localhost kernel [4294687.316000]  target0:0:0: Beginning Domain Validation
localhost kernel [4294687.317000] WIDTH IS 1
localhost kernel [4294687.318000] (scsi0:A:0): 6.600MB/s transfers (16bit)
localhost kernel [4294687.320000] (scsi0:A:0): 160.000MB/s transfers (80.000MHz DT, offset 127, 16bit)
localhost kernel [4294687.322000]  target0:0:0: Ending Domain Validation
localhost kernel [4294687.323000]   Vendor: QUANTUM   Model: ATLAS10K2-TY184L  Rev: DA40
localhost kernel [4294687.323000]   Type:   Direct-Access                      ANSI SCSI revision: 03
localhost kernel [4294687.323000] scsi0:A:1:0: Tagged Queuing enabled.  Depth 8
localhost kernel [4294687.323000]  target0:0:1: Beginning Domain Validation
localhost kernel [4294687.324000] WIDTH IS 1
localhost kernel [4294687.324000] (scsi0:A:1): 6.600MB/s transfers (16bit)
localhost kernel [4294687.327000] (scsi0:A:1): 160.000MB/s transfers (80.000MHz DT, offset 127, 16bit)
localhost kernel [4294687.329000]  target0:0:1: Ending Domain Validation
localhost kernel [4294687.330000]   Vendor: SEAGATE   Model: ST373307LW        Rev: DS09
localhost kernel [4294687.330000]   Type:   Direct-Access                      ANSI SCSI revision: 03
localhost kernel [4294687.330000] scsi0:A:2:0: Tagged Queuing enabled.  Depth 8
localhost kernel [4294687.330000]  target0:0:2: Beginning Domain Validation
localhost kernel [4294687.332000] WIDTH IS 1
localhost kernel [4294687.333000] (scsi0:A:2): 6.600MB/s transfers (16bit)
localhost kernel [4294687.337000] (scsi0:A:2): 160.000MB/s transfers (80.000MHz DT, offset 63, 16bit)
localhost kernel [4294687.339000]  target0:0:2: Ending Domain Validation
localhost kernel [4294690.416000] scsi1 : Adaptec AIC7XXX EISA/VLB/PCI SCSI HBA DRIVER, Rev 6.2.36
localhost kernel [4294690.416000]         <Adaptec aic7899 Ultra160 SCSI adapter>
localhost kernel [4294690.416000]         aic7899: Ultra160 Wide Channel B, SCSI Id=7, 32/253 SCBs
localhost kernel [4294690.416000] 
localhost kernel [4294709.281000] SvrWks OSB4: IDE controller at PCI slot 0000:00:0f.1
localhost kernel [4294709.282000] SvrWks OSB4: chipset revision 0
localhost kernel [4294709.282000] SvrWks OSB4: not 100%% native mode: will probe irqs later
localhost kernel [4294709.282000]     ide0: BM-DMA at 0x08b0-0x08b7, BIOS settings: hda:DMA, hdb:pio
localhost kernel [4294709.282000]     ide1: BM-DMA at 0x08b8-0x08bf, BIOS settings: hdc:pio, hdd:pio
localhost kernel [4294709.282000] Probing IDE interface ide0...
localhost kernel [4294709.954000] hda: CRD-8482B, ATAPI CD/DVD-ROM drive
localhost kernel [4294710.566000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
localhost kernel [4294710.566000] Probing IDE interface ide1...
localhost kernel [4294711.079000] Probing IDE interface ide1...
localhost kernel [4294711.592000] Probing IDE interface ide2...
localhost kernel [4294712.104000] Probing IDE interface ide3...
localhost kernel [4294712.616000] Probing IDE interface ide4...
localhost kernel [4294713.128000] Probing IDE interface ide5...
localhost kernel [4294713.650000] hda: ATAPI 48X CD-ROM drive, 128kB Cache
localhost kernel [4294713.650000] Uniform CD-ROM driver Revision: 3.20
localhost kernel [4294713.660000] SCSI device sda: 35566478 512-byte hdwr sectors (18210 MB)
localhost kernel [4294713.662000] SCSI device sda: drive cache: write through
localhost kernel [4294713.662000] SCSI device sda: 35566478 512-byte hdwr sectors (18210 MB)
localhost kernel [4294713.663000] SCSI device sda: drive cache: write through
localhost kernel [4294713.663000]  /dev/scsi/host0/bus0/target0/lun0: p1
localhost kernel [4294713.664000] Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
localhost kernel [4294713.664000] SCSI device sdb: 35566478 512-byte hdwr sectors (18210 MB)
localhost kernel [4294713.665000] SCSI device sdb: drive cache: write through
localhost kernel [4294713.665000] SCSI device sdb: 35566478 512-byte hdwr sectors (18210 MB)
localhost kernel [4294713.667000] SCSI device sdb: drive cache: write through
localhost kernel [4294713.667000]  /dev/scsi/host0/bus0/target1/lun0: p1 p2 < p5 >
localhost kernel [4294713.678000] Attached scsi disk sdb at scsi0, channel 0, id 1, lun 0
localhost kernel [4294713.678000] SCSI device sdc: 143374650 512-byte hdwr sectors (73408 MB)
localhost kernel [4294713.680000] SCSI device sdc: drive cache: write through
localhost kernel [4294713.680000] SCSI device sdc: 143374650 512-byte hdwr sectors (73408 MB)
localhost kernel [4294713.682000] SCSI device sdc: drive cache: write through
localhost kernel [4294713.682000]  /dev/scsi/host0/bus0/target2/lun0: p1 p2
localhost kernel [4294713.692000] Attached scsi disk sdc at scsi0, channel 0, id 2, lun 0
localhost kernel [4294714.253000] Attempting manual resume
localhost kernel [4294714.254000] swsusp: Suspend partition has wrong signature?
localhost kernel [4294714.301000] e100: Intel(R) PRO/100 Network Driver, 3.4.8-k2-NAPI
localhost kernel [4294714.301000] e100: Copyright(c) 1999-2005 Intel Corporation
localhost kernel [4294714.301000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
localhost kernel [4294714.323000] e100: eth0: e100_probe: addr 0xfe102000, irq 16, MAC addr 00:B0:D0:F9:65:C2
localhost kernel [4294714.387000] usbcore: registered new driver usbfs
localhost kernel [4294714.387000] usbcore: registered new driver hub
localhost kernel [4294714.390000] ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
localhost kernel [4294714.391000] ACPI: PCI Interrupt Link [LUSB] enabled at IRQ 10
localhost kernel [4294714.391000] ACPI: PCI Interrupt 0000:00:0f.2[A] -> Link [LUSB] -> GSI 10 (level, low) -> IRQ 10
localhost kernel [4294714.391000] ohci_hcd 0000:00:0f.2: ServerWorks OSB4/CSB5 OHCI USB Controller
localhost kernel [4294714.391000] ohci_hcd 0000:00:0f.2: new USB bus registered, assigned bus number 1
localhost kernel [4294714.391000] ohci_hcd 0000:00:0f.2: irq 10, io mem 0xfe100000
localhost kernel [4294714.444000] hub 1-0:1.0: USB hub found
localhost kernel [4294714.444000] hub 1-0:1.0: 2 ports detected
localhost kernel [4294717.122000] ACPI: CPU0 (power states: C1[C1])
localhost kernel [4294717.232000] Attempting manual resume
localhost kernel [4294717.232000] swsusp: Suspend partition has wrong signature?
localhost kernel [4294717.249000] EXT3-fs: INFO: recovery required on readonly filesystem.
localhost kernel [4294717.249000] EXT3-fs: write access will be enabled during recovery.
localhost kernel [4294717.683000] kjournald starting.  Commit interval 5 seconds
localhost kernel [4294717.683000] EXT3-fs: recovery complete.
localhost kernel [4294717.695000] EXT3-fs: mounted filesystem with ordered data mode.
localhost kernel [4294718.760000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
localhost kernel [4294722.548000] hda: Disabling (U)DMA for CRD-8482B (blacklisted)
localhost kernel [4294722.548000] hda: Disabling (U)DMA for CRD-8482B (blacklisted)
localhost kernel [4294722.615000] Adding 755012k swap on /dev/sdb5.  Priority:-1 extents:1
localhost kernel [4294722.784000] EXT3 FS on sdb1, internal journal
localhost kernel [4294727.754000] parport: PnPBIOS parport detected.
localhost kernel [4294727.754000] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
localhost kernel [4294727.847000] lp0: using parport0 (interrupt-driven).
localhost kernel [4294727.900000] mice: PS/2 mouse device common for all mice
localhost kernel [4294728.150000] logips2pp: Detected unknown logitech mouse model 1
localhost kernel [4294728.231000] input: PS/2 Logitech Mouse on isa0060/serio1
localhost kernel [4294728.732000] ts: Compaq touchscreen protocol output
localhost kernel [4294731.964000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
localhost kernel [4294732.539000] cdrom: open failed.
localhost kernel [4294732.954000] kjournald starting.  Commit interval 5 seconds
localhost kernel [4294732.960000] EXT3 FS on sdc2, internal journal
localhost kernel [4294732.960000] EXT3-fs: recovery complete.
localhost kernel [4294732.966000] EXT3-fs: mounted filesystem with ordered data mode.
localhost kernel [4294733.948000] Linux agpgart interface v0.101 (c) Dave Jones
localhost kernel [4294733.966000] agpgart: unable to determine aperture size.
localhost kernel [4294733.966000] agpgart: agp_backend_initialize() failed.
localhost kernel [4294733.966000] agpgart-serverworks: probe of 0000:00:00.0 failed with error -22
localhost kernel [4294733.966000] agpgart: unable to determine aperture size.
localhost kernel [4294733.966000] agpgart: agp_backend_initialize() failed.
localhost kernel [4294733.966000] agpgart-serverworks: probe of 0000:00:00.1 failed with error -22
localhost kernel [4294734.427000] piix4_smbus 0000:00:0f.0: Found 0000:00:0f.0 device
localhost kernel [4294736.327000] input: PC Speaker
localhost kernel [4294736.531000] Floppy drive(s): fd0 is 1.44M
localhost kernel [4294736.543000] FDC 0 is a National Semiconductor PC87306
localhost kernel [4294737.564000] Real Time Clock Driver v1.12
localhost kernel [4294738.660000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
localhost kernel [4294738.682000] NET: Registered protocol family 17
localhost kernel [4294744.076000] NET: Registered protocol family 10
localhost kernel [4294744.077000] Disabled Privacy Extensions on device c02eb280(lo)
localhost kernel [4294744.077000] IPv6 over IPv4 tunneling driver
localhost kernel [4294745.477000] ACPI: Power Button (FF) [PWRF]
localhost kernel [4294745.694000] ibm_acpi: ec object not found
localhost hpiod 0.9.5 accepting connections at 32769... 
localhost hp unable to open /var/run/hplip/hpssd.port: No such file or directory: prnt/hpijs/hplip_api.c 84 
localhost hpiod invalid message: 
localhost hp unable to connect hpssd socket 50002: Connection refused: prnt/hpijs/hplip_api.c 710 
localhost hpiod unable to ParDevice::Open hp:/par/ANY?device=/dev/parport0: No such file or directory: io/hpiod/ppdevice.cpp 827 
localhost hpiod unable to ParDevice::Open hp:/par/ANY?device=/dev/parport1: No such file or directory: io/hpiod/ppdevice.cpp 827 
localhost hpiod unable to ParDevice::Open hp:/par/ANY?device=/dev/parport2: No such file or directory: io/hpiod/ppdevice.cpp 827 
localhost hpiod unable to ParDevice::Open hp:/par/ANY?device=/dev/parport3: No such file or directory: io/hpiod/ppdevice.cpp 827 
localhost kernel [4294752.310000] apm: BIOS not found.
localhost kernel [4294754.396000] eth0: no IPv6 routers present
localhost hcid[6870] Bluetooth HCI daemon
localhost kernel [4294754.808000] Bluetooth: Core ver 2.7
localhost kernel [4294754.808000] NET: Registered protocol family 31
localhost kernel [4294754.808000] Bluetooth: HCI device and connection manager initialized
localhost kernel [4294754.808000] Bluetooth: HCI socket layer initialized
localhost kernel [4294755.049000] Bluetooth: L2CAP ver 2.7
localhost kernel [4294755.049000] Bluetooth: L2CAP socket layer initialized
localhost sdpd[6878] Bluetooth SDP daemon 
localhost kernel [4294755.094000] Bluetooth: RFCOMM ver 1.5
localhost kernel [4294755.094000] Bluetooth: RFCOMM socket layer initialized
localhost kernel [4294755.094000] Bluetooth: RFCOMM TTY layer initialized
localhost anacron[6907] Anacron 2.3 started on 2006-03-13
localhost anacron[6907] Normal exit (0 jobs run)
localhost /usr/sbin/cron[6932] (CRON) INFO (pidfile fd = 3)
localhost /usr/sbin/cron[6933] (CRON) STARTUP (fork ok)
localhost /usr/sbin/cron[6933] (CRON) INFO (Running @reboot jobs)
localhost gconfd (woody-7035) starting (version 2.12.0), pid 7035 user 'woody'
localhost gconfd (woody-7035) Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
localhost gconfd (woody-7035) Resolved address "xml:readonly:/usr/share/gconf/local.mandatory" to a read-only configuration source at position 1
localhost gconfd (woody-7035) Resolved address "xml:readwrite:/home/woody/.gconf" to a writable configuration source at position 2
localhost gconfd (woody-7035) Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 3
localhost gconfd (woody-7035) Resolved address "xml:readonly:/usr/share/gconf/local.defaults" to a read-only configuration source at position 4
localhost gconfd (woody-7035) Resolved address "xml:readonly:/usr/share/gconf/cdd.defaults" to a read-only configuration source at position 5
localhost gconfd (woody-7035) Resolved address "xml:readonly:/usr/share/gconf/debian.defaults" to a read-only configuration source at position 6
localhost gconfd (woody-7035) Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7
localhost gconfd (woody-7035) Resolved address "xml:readwrite:/home/woody/.gconf" to a writable configuration source at position 0
localhost  -- MARK --
localhost  -- MARK --
localhost /USR/SBIN/CRON[7706] (root) CMD (   run-parts --report /etc/cron.hourly)
localhost  -- MARK --
localhost  -- MARK --
localhost  -- MARK --
localhost gconfd (woody-7035) Resolved address "xml::/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 0
localhost gconfd (woody-7035) None of the resolved addresses are writable; saving configuration settings will not be possible
localhost gconfd (woody-7035) Resolved address "xml::/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
localhost gconfd (woody-7035) None of the resolved addresses are writable; saving configuration settings will not be possible
localhost /USR/SBIN/CRON[8482] (root) CMD (   run-parts --report /etc/cron.hourly)
localhost  -- MARK --

---

### Post by WoodyMahan on 2006-03-13
Hoping for some help on this one.  The system has locked up 5 times today.  Can't move forward like this.  Maybe the hard drive partitions can be edited?  Doesn't Linux partition a protion of the hard drive for Memory Allocations?

---

### Post by blackrim on 2006-03-14
so i think i have a similar problem where my system is freezing up. in my case, it seems to only happen on the gui. i can leave the system on, without logging out and ssh in and i am fine. maybe it is because i am only doing simple tasks in the ssh but i don't know. 
it is pretty frustrating and i am not sure whether a fresh install would help, or whether it is a hardware issue. i also have dual monitors and am not sure whether that has something to do with it. i have some external firewire drives and maybe it is that. 
i really have not idea.
hopefully someone can help

---

### Post by Moodel on 2006-03-14
Hm.... well it would appear I have a similair issue on my system. I thought it was to do with swap space and have increased my swap file accordingly but I'm not so sure as I still get freezes in the GUI......I'm not sure if this is relevent but it mostly occurs in Thunderbird and Firefox.

I tend to have them running all the time as well as a couple of konsoles, Kopete and VMPlayer running a W2k3 image. Under XP I have no issues and run the same apps...

If anyone can suggest anything that would be most helpful. There are no errors in any of my logs and the only issue I have at boot time is to do with not mounting a vfat partition....but thats not important.

---

### Post by Jason_25 on 2006-03-14
If you have an amd cpu, remove powernowd.  If not, maybe try running memtest86 for a few cycles.

---

### Post by WoodyMahan on 2006-03-14
In my case I am just about convinced the my system is locking up when I log into it using VNC.  I downloaded the TightVNC viewer to run from my windows machine and it seemed to be locking up everytime I tried to use Firefox or the GUI system browser for any amount of time.  I went over to the Linux box yesterday and sat down in front of it and clicked around on the internet, tested downloading some word docs and spreadsheets, etc. and it never locked up when I was working directly on the machine.

---

### Post by flarkit on 2006-03-14
Hi

I'd like to add myself to the list of people who experience "lock-ups" in Ubuntu. It happens at random times, when I'm not doing anything strenuous.
:confused: 

I've recently increased my RAM from 1x1Gb to 2x1Gb (of the same model), although I doubt this is the cause. It's a new installation, so I may reinstall again.

Thanks

---

### Post by Brunellus on 2006-03-14
to those of you experiencing lock-ups, have you considered that you might be running the wrong drivers for  your graphics cards?

---

### Post by WoodyMahan on 2006-03-15
OK.  My lockup issue is absolutley related somehow to using VNC.  It locks up evey time I log in remotely.  Is there a more reliable program?  Can I setup my Ubuntu machine as a "Terminal Server" where I can simply log in and open a session on the machine instead of simply taking over the desktop?


Thanks All

Wood

---

### Post by Bagnaj97 on 2006-03-15
The only thing that has caused lockups for me is the spca5xx webcam driver. The version that ships with Breezy is broken and the latest from the website wasn't much better. Do you have a webcam installed?

---

### Post by henriquemaia on 2006-03-16
I'm having lockups, random ones too. I run a double AMD1800. If I turn the powernowd off, the problem seems to get a bit better, even though it still hangs from time to time. I have the computer on all the time, running folding@home. 

With powernowd on, the system hangs whenever folding@home starts and the 2 CPUs are running at full load, some five minutes after a reboot.

I also added to the kernel the options **noapic nolapic**, as suggested by someone on this forum. The problem persists, but more randomly.

ps: one more thing, I did memtest and my memory is ok.

---

### Post by youBun2 on 2006-03-16
Alright, I am in the same boat as you all but far worse.

I currently run Windows XP Home Edition on my desktop that was bought last February. The file system on my main and only hard drive of 200 GB is NTFS.

Yesterday a friend gave me a copy of Ubuntu (official copy from the website) and I decided to load up the Live CD. Without a result I found that perhaps it is just the Live CD and so I went ahead and started with an installation.

Using a partioning program I managed to create a 10 GB partition for Linux etc. I carried on with the install and towards the end it asked me if I wanted to have the GNU GRUB installed on my C: (with Windows XP) as to have a choice in OS when at boot-up.

Innocent me went ahead with that choice and enjoyed the first few steps at seeing Ubuntu. I managed to create myself a user account and I logged in... it froze. I then decided to restart and load up Windows XP instead. It won't load. When I select Windows XP Home Edition it has:

root (hd0,1)
savedefault
makeactive
chainloader +1

and stops. When I checked out the same boot-up process for Ubuntu, I saw that it reads:

root hd(0,2)
kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/sda3 ro quiet splash
intrid /boot/initrd.img-2.6.12-9-386
savedefault
boot

and obviously loads Ubuntu and allows me to log in but freezes on the centered image.

From what I can see, it appears Windows XP doesn't load up its kernal or something like that. Are there any ways I can simply log on to my Windows system?

---

### Post by WoodyMahan on 2006-03-16
I would suggest adding this on the forum as a new post marked as an installation problem.  You have a major issue here and don't want it bried at the back on an ongoing post.  Sorry I don't have an anwer for ya.  Good luck.

---

### Post by henriquemaia on 2006-03-17
Just to update the situation.

I turned off the nvidia driver from my xorg.conf and started with nv (xorg driver) because every other workaround was not working. The system got stable. As I really want to have 3D acceleration, I downgraded the Nvidia driver to the 7676 version (as opposed to the 8178 I was using). The system looks ok now.

I'll going to push up thing here for the next days to see if this is really the solution. 

The problem with lockups is to try to find what causes them. As guide for anyone with this [huge] problem on Breezy, try to isolate the cause by following the steps:

1. add **noapic nolapic** the your grub options during boot time (on the grub menu you'll have the option to edit your boot options).

2. If that does not work, turn off the following services (using BUM or other init editor):
[B]
acpid
acpi-support
apmd[/B]

3. If that does not work, and if you're using an AMD processor, turn off **powernowd** service (using BUM or other init editor)

4. If that does not work, check if you're using some proprietary driver for some of your hardware (graphical card, for instance) and disable it. Try using an alternative driver or a newer (or older) and stabler version of it.

5. If that does not work, use all the above at the same time (severall faults).

6. If that does not work, check your hardware for faults (use memtest86 during boot time or other tests you find appropriate).


This is just a suggestion of steps. If someone thinks that something is missing here or that the order is not correct, please add to the thread. Please note that what is causing you trouble can be something very particular to your computer only.

Hope this helps someone.

---

### Post by WoodyMahan on 2006-03-17
Great Suggestions Henri.  Thanks.

---

### Post by blackrim on 2006-03-17
Actually I don't want to speak too soon either but it appears that my system is stable after I also uninstalled the xorg driver and installed the official nvidia driver. This was a couple of days ago so I am not positive, but no freezes yet.

---

### Post by blackrim on 2006-03-21
ok, i spoke too soon. i installed xubuntu and the official nvidia drivers and it is still crashing. i ran memtest and everything was fine. what could it be. what is the deal?

---

### Post by WoodyMahan on 2006-03-21
FYI:  I have moved away from VNC and started using FreeNX and I haven't hung up in a couple of days.  Just for anyone who might be interested.  Not a Vid Card error in my case.

---

### Post by blackrim on 2006-04-10
just an update. it seems like my problem was multiple monitors (or xine movie player), either way, stopped both and no more problems.

---

### Post by blackrim on 2006-04-12
mine was fixed when i stopped using xine (and started using totem-xine) and stopped using dual monitors. don't know which did it, but one of them fixed it.

---

### Post by qw3rty on 2006-04-20
Ubuntu just locked up for me.  It may be the computer because it was locking up all the time with Windows 98.  It's a 400 mhz computer with 160 MB of RAM.  Ubuntu ran for 5 days without locking up.  It's not completely frozen because I can still connect with VNC.  None of the icons show up on the desktop, the top menu bar is blank, except for the time that stopped 10 minutes ago.  I can move the mouse around, but clicking doesn't do anything.

On Mac OS X there is a crash log that you can look at to see what was going on when your system crashed.  Does Ubuntu have something similar?

---

### Post by blackrim on 2006-04-20
There are some logs for linux after crashing but I don't remember them, you should be able to find the answer to that and possibly your crashing problem at another thread (that is where I eventually found my answer) : [http://ubuntuforums.org/showthread.php?t=76288](http://ubuntuforums.org/showthread.php?t=76288)

---

### Post by TheOtherShoe on 2006-05-19
To those who are still experiencing lockups: is it possible that your filesystem is mounted read-only?

I have also been getting lockups. When this happens I can still work in the terminal by hitting Alt+F2; if I try to run a command like the following,
```
cat test > test_file
```
Then I get an error saying that the filesystem is read-only.

I can also see that the mount options for my root partition in /etc/fstab include,
```
errors=remount-ro
```
So my theory is that there is something wrong with my filesystem, which is causing errors, which is causing the filesystem to be mounted read-only. While the filesystem is read-only, Gnome will not open new programs.

---

