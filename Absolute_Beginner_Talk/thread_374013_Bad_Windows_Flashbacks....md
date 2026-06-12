---
title: "Bad Windows Flashbacks..."
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by mconway0003 on 2007-03-01
Hello, 

Unfortunately I have been experiencing some all too familiar symptoms from a life before ubuntu. 
        I don't know if it was because I was not removing two different ipods 'un-safely', if it was from not updating frequently enough, or some other reason; but almost everything I tried doing on the desktop was going exremely slow. For instance, when I tried starting gaim it gave me the 'loading mouse cursor' and did not even show up in the upper right hand tool bar. Secondly-and suprisingly-when I tried loading the terminal the same thing happened. Regardless if it was local or network issues, everything was running way to slow. 

         Is there some command I can use in the terminal that would output system specs or something that I could post here, so the problem can be diagnosed easier?

Thanks in advance

---

### Post by mr.v. on 2007-03-01
Yes there are several things you can post here that would help.

 If things are going too painfully slow in the graphical section you can go to a console by pressing ctrl + alt + F1 (or F2-F6).

Go to a terminal and type the following:
```

dmesg > boot.txt

```
then either attach boot.txt or paste the contents between CODE tags (the # button on the forum editor).

Also do the following to give us the xorg log.
```

cat /var/log/Xorg.0.log > xorglog.txt

```

do the same as above...attach the file or place between CODE tags

another helpful thing would be your xorg.conf
so paste the contents of /etc/X11/xorg.conf

Those would be a start. We can go from there.

---

### Post by mconway0003 on 2007-03-02
> **mr.v. said:**
> Yes there are several things you can post here that would help.

 If things are going too painfully slow in the graphical section you can go to a console by pressing ctrl + alt + F1 (or F2-F6).

Go to a terminal and type the following:
```

dmesg > boot.txt

```
then either attach boot.txt or paste the contents between CODE tags (the # button on the forum editor).

Also do the following to give us the xorg log.
```

cat /var/log/Xorg.0.log > xorglog.txt

```

do the same as above...attach the file or place between CODE tags

another helpful thing would be your xorg.conf
so paste the contents of /etc/X11/xorg.conf

Those would be a start. We can go from there.

Ok,

Heres what happens when I try 'dmesg > boot.txt (and I dont think it worked correctly)

```
marcus@Marcus:~$ dmesg > boot.txt
marcus@Marcus:~$ 
```



and here are the unsuccessful 'cat' commands. as you will see, I tried doing the command with sudo once as well since it said persion denied.

```
marcus@Marcus:~$ cat /var/log/Xorg.0.log.txt
cat: /var/log/Xorg.0.log.txt: No such file or directory
marcus@Marcus:~$ cd /var/log
marcus@Marcus:/var/log$ cd ./Xorg.0.log.txt
bash: cd: ./Xorg.0.log.txt: No such file or directory
marcus@Marcus:/var/log$ ls
acpid            daemon.log.1.gz  kern.log            scrollkeeper.log.2
acpid.1.gz       daemon.log.2.gz  kern.log.0          secure
acpid.2.gz       daemon.log.3.gz  kern.log.1.gz       syslog
acpid.3.gz       debug            kern.log.2.gz       syslog.0
acpid.4.gz       debug.0          kern.log.3.gz       syslog.1.gz
apport.log       debug.1.gz       kern.log.4.gz       syslog.2.gz
apport.log.1     debug.2.gz       lastlog             syslog.3.gz
apport.log.2.gz  debug.3.gz       lpr.log             syslog.4.gz
apport.log.3.gz  dist-upgrade     mail.err            syslog.5.gz
apport.log.4.gz  dmesg            mail.info           syslog.6.gz
apport.log.5.gz  dmesg.0          mail.log            udev
aptitude         dmesg.1.gz       mail.warn           unattended-upgrades
auth.log         dmesg.2.gz       messages            user.log
auth.log.0       dmesg.3.gz       messages.0          user.log.0
auth.log.1.gz    dmesg.4.gz       messages.1.gz       user.log.1.gz
auth.log.2.gz    dpkg.log         messages.2.gz       user.log.2.gz
auth.log.3.gz    dpkg.log.1       messages.3.gz       user.log.3.gz
boot             dpkg.log.2.gz    messages.4.gz       uucp.log
bootstrap.log    dpkg.log.3.gz    news                wtmp
btmp             faillog          ntpstats            wtmp.1
btmp.1           fontconfig.log   proftpd             wvdialconf.log
cups             fsck             pycentral.log       Xorg.0.log
daemon.log       gdm              scrollkeeper.log    Xorg.0.log.old
daemon.log.0     installer        scrollkeeper.log.1
marcus@Marcus:/var/log$ /Xorg.0.log
bash: /Xorg.0.log: No such file or directory
marcus@Marcus:/var/log$ cd ./Xorg.0.log
bash: cd: ./Xorg.0.log: Not a directory
marcus@Marcus:/var/log$ cd ./xorg.0.log
bash: cd: ./xorg.0.log: No such file or directory
marcus@Marcus:/var/log$ locate boot.txt
marcus@Marcus:/var/log$ Xorg.0.log
bash: Xorg.0.log: command not found
marcus@Marcus:/var/log$ cd Xorg.0.log
bash: cd: Xorg.0.log: Not a directory
marcus@Marcus:/var/log$ cat /var/log/Xorg.0.log > xorglog.txt
bash: xorglog.txt: Permission denied
marcus@Marcus:/var/log$ sudo cat /var/log/Xorg.0.log > xorglog.txt
bash: xorglog.txt: Permission denied
marcus@Marcus:/var/log$ 

```

and here is whats in xorg.conf

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Rage Mobility M3 AGP 2x"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Rage Mobility M3 AGP 2x"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by mr.v. on 2007-03-02
sorry I should have offered more explanation...

```
dmesg > boot.txt
```

dmesg is a command. That command prints messages from the kernel. the **>** symbol takes the output that normally would have been sent to the screen and placed it into a file called boot.txt in your current directory which is likely to be your /home/USERNAME directory.

for instance if my username was **mrv** i could do the following.
```
dmesg > /home/mrv/dmesg-text.txt
```
and that would put the output of the command dmesg into a file called "dmesg-text.txt" in the /home/mrv directory.

to see it on your desktop for instance you can use the **~** as an alias for your /home/username directory
so the following
```
dmesg > ~/Desktop/dmesg.txt
```
will put the output of dmesg on a text file on your desktop. Anyway, you somehow have to attach the file boot.txt or dmesg.txt (or whatever you want to call it) here. So find a folder you like (Say **~** a.k.a. /home/username [where username is your specific username]) and create a file using the command dmesg and output to the file of your choice as above. Then either attach the file or paste the contents here.

As far as the other cat command...you have to be very very careful.
here's what you did wrong first...I said ```
cat /var/log/Xorg.0.log > xorglog.txt
```
you first did ```
cat /var/log/Xorg.0.log.txt
```

see the difference? you added .txt to the first.
You also then tried to change the directory into Xorg.0.log using cd...but Xorg.0.log isn't a directory! it's a log =). Anyway, you got the right idea later but you ended up with permission denied. That's because when you changed directories you weren't in the default directory when you go into a terminal...namely you username's home directory (~ or /home/username like above) directory. In linux, for security reasons, if you're a plain-jane user, you pretty much cannot write in any other directory accept your home directory unless you become the root user or you use **sudo**.

Anyway, when you finally did ```
cat /var/log/Xorg.0.log > xorglog.txt
``` you were in a directory where neither you nor even sudo could make changes...the /var/log directory. What happened is you were trying to make a file xorglog.txt in your CURRENT directory. So you can do the following from your home directory
```
cat /var/log/Xorg.0.log > xorglog.txt
```
and it will make the file in your home directory...OR...if you're in a directory where you don't have write access...you can type ```
cat /var/log/Xorg.0.log > ~/xorglog.txt
``` which will explicitly make the file in your home directory...

Or (because I'm an idiot) i should have just said...just open the file /var/log/Xorg.0.log and paste the contents here. Sorry I was going to have you use the grep command to check for errors but then I figured I wouldn't but didn't edit my post...sorry =)

so now you know, please post your /var/log/Xorg.0.log file here as well as the file you created when you ran dmesg and sent the output using > to a file in  your home directory

---

### Post by mconway0003 on 2007-03-02
> **mr.v. said:**
> sorry I should have offered more explanation...

```
dmesg > boot.txt
```

dmesg is a command. That command prints messages from the kernel. the **>** symbol takes the output that normally would have been sent to the screen and placed it into a file called boot.txt in your current directory which is likely to be your /home/USERNAME directory.

for instance if my username was **mrv** i could do the following.
```
dmesg > /home/mrv/dmesg-text.txt
```
and that would put the output of the command dmesg into a file called "dmesg-text.txt" in the /home/mrv directory.

to see it on your desktop for instance you can use the **~** as an alias for your /home/username directory
so the following
```
dmesg > ~/Desktop/dmesg.txt
```
will put the output of dmesg on a text file on your desktop. Anyway, you somehow have to attach the file boot.txt or dmesg.txt (or whatever you want to call it) here. So find a folder you like (Say **~** a.k.a. /home/username [where username is your specific username]) and create a file using the command dmesg and output to the file of your choice as above. Then either attach the file or paste the contents here.

As far as the other cat command...you have to be very very careful.
here's what you did wrong first...I said ```
cat /var/log/Xorg.0.log > xorglog.txt
```
you first did ```
cat /var/log/Xorg.0.log.txt
```

see the difference? you added .txt to the first.
You also then tried to change the directory into Xorg.0.log using cd...but Xorg.0.log isn't a directory! it's a log =). Anyway, you got the right idea later but you ended up with permission denied. That's because when you changed directories you weren't in the default directory when you go into a terminal...namely you username's home directory (~ or /home/username like above) directory. In linux, for security reasons, if you're a plain-jane user, you pretty much cannot write in any other directory accept your home directory unless you become the root user or you use **sudo**.

Anyway, when you finally did ```
cat /var/log/Xorg.0.log > xorglog.txt
``` you were in a directory where neither you nor even sudo could make changes...the /var/log directory. What happened is you were trying to make a file xorglog.txt in your CURRENT directory. So you can do the following from your home directory
```
cat /var/log/Xorg.0.log > xorglog.txt
```
and it will make the file in your home directory...OR...if you're in a directory where you don't have write access...you can type ```
cat /var/log/Xorg.0.log > ~/xorglog.txt
``` which will explicitly make the file in your home directory...

Or (because I'm an idiot) i should have just said...just open the file /var/log/Xorg.0.log and paste the contents here. Sorry I was going to have you use the grep command to check for errors but then I figured I wouldn't but didn't edit my post...sorry =)

so now you know, please post your /var/log/Xorg.0.log file here as well as the file you created when you ran dmesg and sent the output using > to a file in  your home directory

Oh ok, I understand now that was very helpful. Ok heres the boot.txt and the xorg.0.log

```
[17179569.184000] Linux version 2.6.17-11-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Thu Feb 1 19:52:28 UTC 2007 (Ubuntu 2.6.17-11.35-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000000ffdb000 (usable)
[17179569.184000]  BIOS-e820: 000000000ffdb000 - 0000000010000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000100a0000 - 0000000010100000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 255MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 65499
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 61403 pages, LIFO batch:15
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 DELL                                  ) @ 0x000f4c80
[17179569.184000] ACPI: RSDT (v001 DELL    CPi R   0x27d20b07 ASL  0x00000061) @ 0x0fff0000
[17179569.184000] ACPI: FADT (v001 DELL    CPi R   0x27d20b07 ASL  0x00000061) @ 0x0fff0400
[17179569.184000] ACPI: DSDT (v001 INT430 SYSFexxx 0x00001001 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 10100000:efd00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (0120a000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[17179569.184000] Detected 902.166 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.572000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179569.572000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[17179569.600000] Memory: 250080k/261996k available (1911k kernel code, 11368k reserved, 1073k data, 308k init, 0k highmem)
[17179569.600000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.680000] Calibrating delay using timer specific routine.. 1805.77 BogoMIPS (lpj=3611551)
[17179569.680000] Security Framework v1.0.0 initialized
[17179569.680000] SELinux:  Disabled at boot.
[17179569.680000] Mount-cache hash table entries: 512
[17179569.680000] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179569.680000] CPU: After vendor identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179569.680000] CPU: L1 I cache: 16K, L1 D cache: 16K
[17179569.680000] CPU: L2 cache: 256K
[17179569.680000] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[17179569.680000] Checking 'hlt' instruction... OK.
[17179569.696000] SMP alternatives: switching to UP code
[17179569.696000] Freeing SMP alternatives: 16k freed
[17179569.696000] checking if image is initramfs... it is
[17179570.788000] Freeing initrd memory: 5326k freed
[17179570.788000] ACPI: Core revision 20060707
[17179570.792000] ACPI: Looking for DSDT ... not found!
[17179570.792000] ACPI: setting ELCR to 0200 (from 0820)
[17179570.796000] CPU0: Intel Pentium III (Coppermine) stepping 0a
[17179570.796000] SMP motherboard not detected.
[17179570.796000] Local APIC not detected. Using dummy APIC emulation.
[17179570.796000] Brought up 1 CPUs
[17179570.796000] migration_cost=0
[17179570.796000] NET: Registered protocol family 16
[17179570.796000] EISA bus registered
[17179570.796000] ACPI: bus type pci registered
[17179570.800000] PCI: PCI BIOS revision 2.10 entry at 0xfc13e, last bus=8
[17179570.800000] PCI: Using configuration type 1
[17179570.800000] Setting up standard PCI resources
[17179570.808000] ACPI: Interpreter enabled
[17179570.808000] ACPI: Using PIC for interrupt routing
[17179570.812000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.812000] PCI: Probing PCI hardware (bus 00)
[17179570.812000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179570.836000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:07.1
[17179570.836000] PCI quirk: region 0800-083f claimed by PIIX4 ACPI
[17179570.836000] PCI quirk: region 0840-084f claimed by PIIX4 SMB
[17179570.836000] PIIX4 devres B PIO at 00e0-00e7
[17179570.836000] PIIX4 devres C PIO at 0850-085f
[17179570.836000] Boot video device is 0000:01:00.0
[17179570.836000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.908000] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[17179570.908000] ACPI: PCI Interrupt Link [LNKB] (IRQs *5 7)
[17179570.908000] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *0, disabled.
[17179570.912000] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
[17179570.912000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[17179570.912000] ACPI: Power Resource [PADA] (on)
[17179570.916000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.916000] pnp: PnP ACPI init
[17179570.992000] pnp: PnP ACPI: found 15 devices
[17179570.992000] PnPBIOS: Disabled by ACPI PNP
[17179570.992000] PCI: Using ACPI for IRQ routing
[17179570.992000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179571.012000] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
[17179571.012000] pnp: 00:02: ioport range 0x800-0x805 could not be reserved
[17179571.012000] pnp: 00:02: ioport range 0x808-0x80f could not be reserved
[17179571.012000] pnp: 00:03: ioport range 0x806-0x807 has been reserved
[17179571.012000] pnp: 00:03: ioport range 0x850-0x853 has been reserved
[17179571.012000] pnp: 00:03: ioport range 0x856-0x85f has been reserved
[17179571.012000] pnp: 00:03: ioport range 0x810-0x83f has been reserved
[17179571.012000] pnp: 00:03: ioport range 0x840-0x84f has been reserved
[17179571.012000] pnp: 00:03: ioport range 0x600-0x67f has been reserved
[17179571.012000] pnp: 00:03: ioport range 0x680-0x6ff has been reserved
[17179571.012000] pnp: 00:04: ioport range 0xf000-0xf0fe has been reserved
[17179571.012000] pnp: 00:04: ioport range 0xf100-0xf1fe has been reserved
[17179571.012000] pnp: 00:04: ioport range 0xf200-0xf2fe has been reserved
[17179571.012000] pnp: 00:04: ioport range 0xf400-0xf4fe has been reserved
[17179571.012000] pnp: 00:04: ioport range 0xf500-0xf5fe has been reserved
[17179571.012000] pnp: 00:04: ioport range 0xf600-0xf6fe has been reserved
[17179571.012000] pnp: 00:04: ioport range 0xf800-0xf8fe has been reserved
[17179571.012000] pnp: 00:04: ioport range 0xf900-0xf9fe has been reserved
[17179571.012000] pnp: 00:09: ioport range 0x3f0-0x3f1 has been reserved
[17179571.012000] PCI: Bridge: 0000:00:01.0
[17179571.012000]   IO window: e000-efff
[17179571.012000]   MEM window: fd000000-feffffff
[17179571.012000]   PREFETCH window: f4000000-f7ffffff
[17179571.012000] PCI: Bus 9, cardbus bridge: 0000:00:03.0
[17179571.012000]   IO window: 00001000-000010ff
[17179571.012000]   IO window: 00001400-000014ff
[17179571.012000]   PREFETCH window: 20000000-21ffffff
[17179571.012000]   MEM window: 22000000-23ffffff
[17179571.012000] PCI: Bus 13, cardbus bridge: 0000:00:03.1
[17179571.012000]   IO window: 00001800-000018ff
[17179571.012000]   IO window: 00001c00-00001cff
[17179571.012000]   PREFETCH window: 24000000-25ffffff
[17179571.012000]   MEM window: 26000000-27ffffff
[17179571.012000] PCI: Bridge: 0000:00:10.0
[17179571.012000]   IO window: d000-dfff
[17179571.012000]   MEM window: fb000000-fcffffff
[17179571.012000]   PREFETCH window: disabled.
[17179571.012000] PCI: Enabling device 0000:00:03.0 (0000 -> 0003)
[17179571.012000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[17179571.012000] PCI: setting IRQ 11 as level-triggered
[17179571.012000] ACPI: PCI Interrupt 0000:00:03.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179571.012000] PCI: Enabling device 0000:00:03.1 (0000 -> 0003)
[17179571.012000] ACPI: PCI Interrupt 0000:00:03.1[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179571.012000] NET: Registered protocol family 2
[17179571.052000] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[17179571.052000] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[17179571.052000] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[17179571.052000] TCP: Hash tables configured (established 8192 bind 4096)
[17179571.052000] TCP reno registered
[17179571.052000] audit: initializing netlink socket (disabled)
[17179571.052000] audit(1172863061.052:1): initialized
[17179571.052000] VFS: Disk quotas dquot_6.5.1
[17179571.052000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179571.052000] Initializing Cryptographic API
[17179571.052000] io scheduler noop registered
[17179571.052000] io scheduler anticipatory registered
[17179571.052000] io scheduler deadline registered
[17179571.052000] io scheduler cfq registered (default)
[17179571.052000] Limiting direct PCI/PCI transfers.
[17179571.052000] isapnp: Scanning for PnP cards...
[17179571.408000] isapnp: No Plug & Play device found
[17179571.464000] Real Time Clock Driver v1.12ac
[17179571.464000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179571.464000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.464000] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.468000] mice: PS/2 mouse device common for all mice
[17179571.468000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179571.468000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.468000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179571.468000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179571.476000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179571.476000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.476000] EISA: Probing bus 0 at eisa.0
[17179571.476000] Cannot allocate resource for EISA slot 1
[17179571.476000] EISA: Detected 0 cards.
[17179571.476000] TCP bic registered
[17179571.476000] NET: Registered protocol family 1
[17179571.476000] NET: Registered protocol family 8
[17179571.476000] NET: Registered protocol family 20
[17179571.476000] Using IPI No-Shortcut mode
[17179571.476000] ACPI: (supports S0 S1 S3 S4 S5)
[17179571.480000] Freeing unused kernel memory: 308k freed
[17179571.516000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.716000] Capability LSM initialized
[17179572.804000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179572.828000] ACPI: Thermal Zone [THM] (26 C)
[17179573.828000] PIIX4: IDE controller at PCI slot 0000:00:07.1
[17179573.828000] PIIX4: chipset revision 1
[17179573.828000] PIIX4: not 100% native mode: will probe irqs later
[17179573.828000]     ide0: BM-DMA at 0x0860-0x0867, BIOS settings: hda:DMA, hdb:pio
[17179573.828000]     ide1: BM-DMA at 0x0868-0x086f, BIOS settings: hdc:pio, hdd:pio
[17179573.828000] Probing IDE interface ide0...
[17179574.116000] hda: IC25N030ATDA04-0, ATA DISK drive
[17179574.788000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179574.804000] Probing IDE interface ide1...
[17179575.384000] hda: max request size: 128KiB
[17179575.384000] hda: 58605120 sectors (30005 MB) w/1806KiB Cache, CHS=58140/16/63, UDMA(33)
[17179575.388000] hda: cache flushes not supported
[17179575.388000]  hda: hda1 hda2 < hda5 >
[17179575.696000] Probing IDE interface ide1...
[17179575.836000] usbcore: registered new driver usbfs
[17179575.840000] usbcore: registered new driver hub
[17179575.840000] USB Universal Host Controller Interface driver v3.0
[17179575.840000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179575.840000] uhci_hcd 0000:00:07.2: UHCI Host Controller
[17179575.840000] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[17179575.840000] uhci_hcd 0000:00:07.2: irq 11, io base 0x0000cce0
[17179575.840000] usb usb1: configuration #1 chosen from 1 choice
[17179575.840000] hub 1-0:1.0: USB hub found
[17179575.840000] hub 1-0:1.0: 2 ports detected
[17179576.184000] usb 1-1: new low speed USB device using uhci_hcd and address 2
[17179576.320000] Attempting manual resume
[17179576.368000] usb 1-1: configuration #1 chosen from 1 choice
[17179576.388000] usbcore: registered new driver hiddev
[17179576.392000] kjournald starting.  Commit interval 5 seconds
[17179576.392000] EXT3-fs: mounted filesystem with ordered data mode.
[17179576.408000] input: Logitech USB-PS/2 Trackball as /class/input/input1
[17179576.408000] input: USB HID v1.00 Mouse [Logitech USB-PS/2 Trackball] on usb-0000:00:07.2-1
[17179576.408000] usbcore: registered new driver usbhid
[17179576.408000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179597.968000] Linux agpgart interface v0.101 (c) Dave Jones
[17179598.036000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179598.040000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179598.184000] ACPI: PCI Interrupt 0000:00:03.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179598.184000] Yenta: CardBus bridge found at 0000:00:03.0 [1028:00b0]
[17179598.184000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179598.184000] Yenta: Routing CardBus interrupts to PCI
[17179598.184000] Yenta TI: socket 0000:00:03.0, mfunc 0x01261222, devctl 0x64
[17179598.416000] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[17179598.416000] Socket status: 30000006
[17179598.456000] ACPI: PCI Interrupt 0000:00:03.1[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179598.456000] Yenta: CardBus bridge found at 0000:00:03.1 [1028:00b0]
[17179598.456000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179598.456000] Yenta: Routing CardBus interrupts to PCI
[17179598.456000] Yenta TI: socket 0000:00:03.1, mfunc 0x01261222, devctl 0x64
[17179598.692000] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[17179598.692000] Socket status: 30000020
[17179598.808000] agpgart: Detected an Intel 440BX Chipset.
[17179598.816000] agpgart: AGP aperture is 64M @ 0xf0000000
[17179599.312000] e100: Intel(R) PRO/100 Network Driver, 3.5.10-k2-NAPI
[17179599.312000] e100: Copyright(c) 1999-2005 Intel Corporation
[17179599.312000] ACPI: PCI Interrupt 0000:08:04.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179599.336000] e100: eth0: e100_probe: addr 0xfbfff000, irq 11, MAC addr 00:20:E0:69:AA:37
[17179599.364000] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[17179599.380000] Floppy drive(s): fd0 is 1.44M
[17179599.468000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[17179599.468000] PCI: setting IRQ 5 as level-triggered
[17179599.468000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[17179599.468000] maestro3: enabled hack for 'Dell Inspiron 4000'
[17179599.484000] pccard: CardBus card inserted into slot 1
[17179599.484000] PCI: Enabling device 0000:0d:00.0 (0000 -> 0003)
[17179599.484000] ACPI: PCI Interrupt 0000:0d:00.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179599.484000] uhci_hcd 0000:0d:00.0: UHCI Host Controller
[17179599.484000] uhci_hcd 0000:0d:00.0: new USB bus registered, assigned bus number 2
[17179599.484000] uhci_hcd 0000:0d:00.0: irq 11, io base 0x00001880
[17179599.484000] usb usb2: configuration #1 chosen from 1 choice
[17179599.484000] hub 2-0:1.0: USB hub found
[17179599.484000] hub 2-0:1.0: 2 ports detected
[17179599.588000] PCI: Enabling device 0000:0d:00.1 (0000 -> 0003)
[17179599.588000] ACPI: PCI Interrupt 0000:0d:00.1[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179599.588000] uhci_hcd 0000:0d:00.1: UHCI Host Controller
[17179599.588000] uhci_hcd 0000:0d:00.1: new USB bus registered, assigned bus number 3
[17179599.588000] uhci_hcd 0000:0d:00.1: irq 11, io base 0x000018a0
[17179599.588000] usb usb3: configuration #1 chosen from 1 choice
[17179599.588000] hub 3-0:1.0: USB hub found
[17179599.588000] hub 3-0:1.0: 2 ports detected
[17179599.640000] FDC 0 is a post-1991 82077
[17179599.812000] input: PC Speaker as /class/input/input2
[17179599.880000] parport: PnPBIOS parport detected.
[17179599.880000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179600.384000] Synaptics Touchpad, model: 1, fw: 5.5, id: 0x9b58b1, caps: 0x804793/0x0
[17179600.384000] serio: Synaptics pass-through port at isa0060/serio1/input0
[17179600.436000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[17179600.792000] cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x200-0x207 0x370-0x37f
[17179600.796000] cs: IO port probe 0x3e0-0x4ff: clean.
[17179600.796000] cs: IO port probe 0x820-0x8ff: clean.
[17179600.796000] cs: IO port probe 0xc00-0xcf7: clean.
[17179600.796000] cs: IO port probe 0xa00-0xaff: clean.
[17179600.796000] cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x200-0x207 0x370-0x37f
[17179600.796000] cs: IO port probe 0x3e0-0x4ff: clean.
[17179600.796000] cs: IO port probe 0x820-0x8ff: clean.
[17179600.796000] cs: IO port probe 0xc00-0xcf7: clean.
[17179600.800000] cs: IO port probe 0xa00-0xaff: clean.
[17179601.044000] PCI: Enabling device 0000:0d:00.2 (0000 -> 0002)
[17179601.044000] ACPI: PCI Interrupt 0000:0d:00.2[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179601.044000] ehci_hcd 0000:0d:00.2: EHCI Host Controller
[17179601.044000] ehci_hcd 0000:0d:00.2: new USB bus registered, assigned bus number 4
[17179601.044000] ehci_hcd 0000:0d:00.2: irq 11, io mem 0x26000a00
[17179601.044000] ehci_hcd 0000:0d:00.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179601.044000] usb usb4: configuration #1 chosen from 1 choice
[17179601.044000] hub 4-0:1.0: USB hub found
[17179601.044000] hub 4-0:1.0: 4 ports detected
[17179601.148000] ts: Compaq touchscreen protocol output
[17179601.416000] ieee1394: Initialized config rom entry `ip1394'
[17179601.488000] PCI: Enabling device 0000:0d:00.3 (0080 -> 0083)
[17179601.488000] ACPI: PCI Interrupt 0000:0d:00.3[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179601.488000] PCI: Setting latency timer of device 0000:0d:00.3 to 64
[17179601.540000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[26000000-260007ff]  Max Packet=[1024]  IR/IT contexts=[4/8]
[17179602.400000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[17179602.820000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011060000003536]
[17179603.484000] NET: Registered protocol family 17
[17179605.232000] lp0: using parport0 (interrupt-driven).
[17179605.320000] SCSI subsystem initialized
[17179605.400000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179605.400000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179605.492000] Adding 746980k swap on /dev/disk/by-uuid/35ebcc71-c093-41be-8a32-6a46146c6943.  Priority:-1 extents:1 across:746980k
[17179605.588000] EXT3 FS on hda1, internal journal
[17179605.776000] NET: Registered protocol family 10
[17179605.776000] lo: Disabled Privacy Extensions
[17179605.776000] IPv6 over IPv4 tunneling driver
[17179606.472000] IBM TrackPoint firmware: 0x0b, buttons: 2/3
[17179606.776000] input: TPPS/2 IBM TrackPoint as /class/input/input4
[17179613.568000] ACPI: AC Adapter [AC] (on-line)
[17179614.004000] ACPI: Battery Slot [BAT0] (battery present)
[17179614.004000] ACPI: Battery Slot [BAT1] (battery absent)
[17179614.044000] ACPI: Lid Switch [LID]
[17179614.044000] ACPI: Power Button (CM) [PBTN]
[17179614.044000] ACPI: Sleep Button (CM) [SBTN]
[17179614.132000] ACPI: ACPI Dock Station Driver 
[17179614.276000] ibm_acpi: ec object not found
[17179614.332000] pcc_acpi: loading...
[17179614.572000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[17179616.324000] eth0: no IPv6 routers present
[17179620.188000] Dell Inspiron machine detected. Enabling interrupts during APM calls.
[17179620.188000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179620.188000] apm: overridden by ACPI.
[17179630.552000] Bluetooth: Core ver 2.8
[17179630.552000] NET: Registered protocol family 31
[17179630.552000] Bluetooth: HCI device and connection manager initialized
[17179630.552000] Bluetooth: HCI socket layer initialized
[17179630.616000] Bluetooth: L2CAP ver 2.8
[17179630.616000] Bluetooth: L2CAP socket layer initialized
[17179630.628000] Bluetooth: RFCOMM socket layer initialized
[17179630.628000] Bluetooth: RFCOMM TTY layer initialized
[17179630.628000] Bluetooth: RFCOMM ver 1.7

```

and I attached my xorglog.txt b/c it was too long and I had to change it to a .tar file because it was too big as well, hope it helps

Thanks

---

### Post by mr.v. on 2007-03-03
First I do hope others look these logs over too, but I just didn't see any errors or reasons for why it would be slow and unresponsive. You've got DRI and DRM working fine.

So now we've got to delve a bit deeper.

I've thought of a few possibilities that need exploring.
1) You've got a process running that's eating resources. To check in the GUI you can go to System --> Administration --> System Monitor --> Processes tab and sort by CPU% to see if there's anything chewing up resources. If the GUI won't respond (your problem =) then go to a console and type **top**. The command **top** displays the top processes consuming system resources. See if there's something chewing up the processor or RAM.

2) your GNOME install is broken. GNOME is a window (desktop) manager for X windows. It's possible that your X windows is just fine, but the window manager is a problem. You may be able to determine that by installing a simple window manager for X like FluxBox for example and then loading that. See if programs managed by fluxbox run much much faster than in GNOME. Because if that's true...GNOME is the problem.

3) if fluxbox is still responding sluggishly, then it could be your X-server. It may be as simple as reconfiguring or it may require removing and reinstalling the X-server packages.

4) A new driver update for, say, your opensource ATI driver is the issue. Perhaps it doesn't support your card well anymore. That may be as simple as rolling back the drivers to an earlier version and seeing if things start drawing quickly again.

---

### Post by omrsafetyo on 2007-03-03
this sounds like the problem I was trying to describe having here: [http://www.ubuntuforums.org/showthread.php?t=374679](http://www.ubuntuforums.org/showthread.php?t=374679)

---

### Post by mconway0003 on 2007-03-05
> **mr.v. said:**
> First I do hope others look these logs over too, but I just didn't see any errors or reasons for why it would be slow and unresponsive. You've got DRI and DRM working fine.

So now we've got to delve a bit deeper.

I've thought of a few possibilities that need exploring.
1) You've got a process running that's eating resources. To check in the GUI you can go to System --> Administration --> System Monitor --> Processes tab and sort by CPU% to see if there's anything chewing up resources. If the GUI won't respond (your problem =) then go to a console and type **top**. The command **top** displays the top processes consuming system resources. See if there's something chewing up the processor or RAM.

2) your GNOME install is broken. GNOME is a window (desktop) manager for X windows. It's possible that your X windows is just fine, but the window manager is a problem. You may be able to determine that by installing a simple window manager for X like FluxBox for example and then loading that. See if programs managed by fluxbox run much much faster than in GNOME. Because if that's true...GNOME is the problem.

3) if fluxbox is still responding sluggishly, then it could be your X-server. It may be as simple as reconfiguring or it may require removing and reinstalling the X-server packages.

4) A new driver update for, say, your opensource ATI driver is the issue. Perhaps it doesn't support your card well anymore. That may be as simple as rolling back the drivers to an earlier version and seeing if things start drawing quickly again.


Thanks a lot, I will check on these and get back to you.

---

