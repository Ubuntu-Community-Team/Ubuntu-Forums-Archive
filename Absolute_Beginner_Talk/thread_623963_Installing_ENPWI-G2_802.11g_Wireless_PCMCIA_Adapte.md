---
title: "Installing ENPWI-G2 802.11g Wireless PCMCIA Adapter on Ubuntu."
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by ubuntokun on 2007-11-26
I would like ti know how to install my ENPWI-G2 802.11g Wireless PCMCIA Adapter on Ubuntu i already got the driver for it on Ubuntu . What do i do now?

---

### Post by mndzmyst on 2008-02-01
Just so happened that I figured it out on my own laptop. You need to use the windows driver from their website [http://www.encore-usa.com/product_item.php?region=us&bid=2&pgid=4&pid=289](http://www.encore-usa.com/product_item.php?region=us&bid=2&pgid=4&pid=289). The linux driver would not compile properly on my pc. Next you install with ndiswrapper.

sudo ndiswrapper -i (path to inf file)
sudo modprobe ndiswrapper
sudo ndiswrapper -m
sudo ndiswrapper -l to see if the card and hardware is recognized.

Also, i had to blacklist the r8180 driver since it kept loading against the ndis one. 
sudo gedit /etc/modprobe.d/blacklist and add these lines to the bottom:  
# blocks original driver from stopping net8185 ndiswrapper driver
blacklist r8180

Not sure, but I also needed to add ndiswrapper to my list of modules loaded at startup
(sudo gedit /etc/modules)

Hope that helps!!! :guitar:

---

### Post by ArgyBargy on 2008-05-22
I would also like to install this card on Ubuntu. I'm new to Ubuntu but did use FreeBSD a few years back so I'm not too scared of the terminal window and all that.

I've been reading several forums but I've had no joy in getting this card to work. Here's my story:

I bought the card, plugged it in and the lights come on (activity light flashing) but there seems to be no one at home becuase it doesn't see any wifi networks.

I've had a look at lspci and the card apears as an 8185 unknown device. The chipset of my wifi card is 8185 so it looks like it's found but lspci doesn't know what it is.

I installed the windows XP and 98 drivers for RTL8185 via ndiswrapper. This makes no change and lspci shows the same.

When I blacklist the original linux r8185 driver the laptop hangs on bootup or when I plug in the PCMCIA card and do a cardctl insert.

I also tried to install the 8185 linux drivers from encore web site but I think it's for a different type or version of linux becuase there are some lib modules or something missing when I try to make.

So the question is which road should I go down? Stick with the original ubuntu driver? Keep trying with nsdiswrapper and windows drivers? Or try to get these linux drivers working?

Any help or experience would help me.

many thanks

Steve

---

### Post by mndzmyst on 2008-05-23
Not 100% sure since I've bought a new laptop since then, with built-in wifi. Yet, from what I remember my chipset also was 8185, but I had to blacklist r8180. It might be that blacklisting r8185 would cause it to conflict with ndiswrapper.

---

### Post by ArgyBargy on 2008-05-23
Thanks for your reply.

That looks familiar becuase when I try the standard drivers I get this with dmesg:

[17179595.828000] Linux kernel driver for RTL8180 / RTL8185 based WLAN cards
[17179595.828000] Copyright (c) 2004-2005, Andrea Merello
[17179595.828000] rtl8180: Initializing module
[17179595.828000] rtl8180: Wireless extensions version 19
[17179595.828000] rtl8180: Initializing proc filesystem
[17179596.024000] MC'97 0 converters and GPIO not ready (0x1)
[17179596.052000] rtl8180: Configuring chip resources
[17179596.052000] PCI: Enabling device 0000:06:00.0 (0000 -> 0003)
[17179596.052000] ACPI: PCI Interrupt 0000:06:00.0[A] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[17179596.052000] PCI: Setting latency timer of device 0000:06:00.0 to 64
[17179596.052000] rtl8180: Memory mapped space @ 0x16000000
[17179596.052000] rtl8180: MAC controller is a RTL8185 b/g (V. D)
[17179596.052000] rtl8180: This is a CARDBUS NIC
[17179596.052000] rtl8180: Reported EEPROM chip is a 93c56 (2Kbit)
[17179596.056000] rtl8180: Card MAC address is 00:18:e7:1e:72:2a
[17179596.072000] rtl8180: EEPROM version 105
[17179596.076000] rtl8180: Card reports RF frontend Realtek 8225
[17179596.076000] rtl8180: WW:This driver has EXPERIMENTAL support for this chipset.
[17179596.076000] rtl8180: WW:use it with care and at your own risk and
[17179596.076000] rtl8180: WW:**PLEASE** REPORT SUCCESS/INSUCCESS TO [email]andreamrl@tiscali.it[/email]
[17179596.076000] rtl8180: Energy threshold: b
[17179596.076000] rtl8180: PAPE from CONFIG2: 6
[17179596.076000] rtl8180: IRQ 9
[17179596.076000] rtl8180: Driver probe completed
[17179596.076000]
[17179596.928000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17179596.988000] rtl8180: Bringing up iface

It looks like it should work but it doesn't see any networks when I scan.

When I blacklist the following:

blacklist r818x
blacklist rtl818x
blacklist ieee80211_rtl

and then install drivers with ndiswrapper the laptop hangs on bootup, or if i plug in the pccard when running it sometimes crashes system but if not i get a dmesg like this:

[17179717.420000] pccard: CardBus card inserted into slot 1
[17179717.504000] ndiswrapper: driver net8185 (Realtek,01/29/2007,5.1096.0129.2007) loaded
[17179717.508000] PCI: Enabling device 0000:06:00.0 (0000 -> 0003)
[17179717.508000] ACPI: PCI Interrupt 0000:06:00.0[A] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
**[17179717.508000] Unable to handle kernel NULL pointer dereference at virtual address 00000000**
[17179717.508000]  printing eip:
[17179717.508000] cfd9f413
[17179717.508000] *pde = 00000000
[17179717.508000] Oops: 0002 [#1]
[17179717.508000] PREEMPT
[17179717.508000] Modules linked in: ipv6 rfcomm l2cap bluetooth ppdev cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sony_acpi pcc_acpi hotkey dev_acpi container button acpi_sbs battery ac i2c_acpi_ec dm_mod md_mod ndiswrapper sr_mod sbp2 scsi_mod lp af_packet snd_seq_dummy snd_seq_oss snd_seq_midi snd_seq_midi_event snd_seq snd_via82xx gameport snd_mpu401_uart joydev tsdev snd_rawmidi floppy snd_seq_device pcmcia psmouse serio_raw rtc pcspkr snd_via82xx_modem snd_ac97_codec snd_ac97_bus snd_pcm_oss snd_mixer_oss i2c_viapro snd_pcm i2c_core via_ircc snd_timer irda crc_ccitt parport_pc snd soundcore snd_page_alloc parport via_agp agpgart yenta_socket shpchp pci_hotplug rsrc_nonstatic pcmcia_core 8139cp 8139too mii evdev ext3 jbd ide_generic uhci_hcd usbcore ohci1394 ieee1394 ide_cd cdrom ide_disk via82cxxx generic thermal processor fan capability commoncap vga16fb vgastate fbcon tileblit font bitblit softcursor
[17179717.508000] CPU:    0
[17179717.508000] EIP:    0060:[<cfd9f413>]    Tainted: P      VLI
[17179717.508000] EFLAGS: 00010202   (2.6.15-51-386)
[17179717.508000] EIP is at 0xcfd9f413
[17179717.508000] eax: 00000000   ebx: 00000000   ecx: 0000003d   edx: cfdca752
[17179717.508000] esi: cfe70b82   edi: cfde003d   ebp: c9a2fc60   esp: c9a2fc54
[17179717.508000] ds: 007b   es: 007b   ss: 0068
[17179717.508000] Process pccardd (pid: 2914, threadinfo=c9a2e000 task=c995f070)
[17179717.508000] Stack: cfe70b82 cfde5000 cfdd0b99 c9a2fcc8 cfd9f7e9 cfe70b82 cfdcf288 0000003d
[17179717.508000]        00000000 00000000 c3ce9668 ffffffff cfe70d90 cfde5000 c87cdc20 c3ce9668
[17179717.508000]        00000000 000000c8 c87c0000 c0000001 cfc4061e cfc3e09b cfde5aac c9a2fce4
[17179717.508000] Call Trace:
[17179717.508000]  [<cfc4061e>] NdisInitializeEvent+0xe/0x20 [ndiswrapper]
[17179717.508000]  [<cfc3e09b>] NdisAllocateSpinLock+0xb/0x20 [ndiswrapper]
[17179717.508000]  [<cfc4c92e>] miniport_init+0x6e/0xf0 [ndiswrapper]
[17179717.508000]  [<cfc4e317>] ndis_start_device+0x17/0x4c0 [ndiswrapper]
[17179717.508000]  [<c01dd626>] vsnprintf+0x356/0x590
[17179717.508000]  [<c011c5e0>] call_console_drivers+0x150/0x170
[17179717.508000]  [<c011c8d3>] vprintk+0x1d3/0x340
[17179717.508000]  [<c01491d1>] kzalloc+0x11/0x40
[17179717.508000]  [<cfc46b05>] IofCompleteRequest+0xd5/0x1c0 [ndiswrapper]
[17179717.508000]  [<cfc4b554>] pdoDispatchPnp+0x34/0x170 [ndiswrapper]
[17179717.508000]  [<cfc4e260>] NdisDispatchPnp+0xb0/0x150 [ndiswrapper]
[17179717.508000]  [<cfc46a14>] IofCallDriver+0x54/0x70 [ndiswrapper]
[17179717.508000]  [<cfc4bc30>] pnp_start_device+0x60/0xf0 [ndiswrapper]
[17179717.508000]  [<cfc4bfee>] wrap_pnp_start_device+0xfe/0x150 [ndiswrapper]
[17179717.508000]  [<c01e736c>] __pci_device_probe+0x3c/0x60
[17179717.508000]  [<c01e73af>] pci_device_probe+0x1f/0x40
[17179717.508000]  [<c024490b>] driver_probe_device+0x3b/0xc0
[17179717.508000]  [<c0244990>] __device_attach+0x0/0x10
[17179717.508000]  [<c0244108>] bus_for_each_drv+0x48/0x80
[17179717.508000]  [<c02449f4>] device_attach+0x54/0x60
[17179717.508000]  [<c0244990>] __device_attach+0x0/0x10
[17179717.508000]  [<c0244241>] bus_add_device+0x21/0xa0
[17179717.508000]  [<c024323d>] device_add+0xdd/0x140
[17179717.508000]  [<c01e355e>] pci_bus_add_device+0xe/0x60
[17179717.508000]  [<c01e3650>] pci_bus_add_devices+0xa0/0xf0
[17179717.508000]  [<cf9e4c08>] cb_alloc+0xb8/0xd0 [pcmcia_core]
[17179717.508000]  [<cf9e0b86>] socket_insert+0x126/0x180 [pcmcia_core]
[17179717.508000]  [<cf9e0e12>] socket_detect_change+0x32/0x90 [pcmcia_core]
[17179717.508000]  [<cf9e0ffc>] pccardd+0x18c/0x1e0 [pcmcia_core]
[17179717.508000]  [<c0118940>] default_wake_function+0x0/0x20
[17179717.508000]  [<cf9e0e70>] pccardd+0x0/0x1e0 [pcmcia_core]
[17179717.508000]  [<c0101385>] kernel_thread_helper+0x5/0x10
[17179717.508000] Code: 04 00 cc cc cc cc cc cc 8b ff 55 8b ec 56 8b 75 08 57 66 8b 7d 10 0f b7 cf 33 c0 85 c9 7e 15 53 8b 55 0c 8b 52 04 8a 14 42 8b 1e <88> 14 18 40 3b c1 7c ed 5b 66 89 7e 04 5f 33 c0 5e 5d c2 0c 00
[17179717.508000]

That "Unable to handle kernel NULL pointer" looks dodgy to me. Any ideas what this means?

Steve

---

### Post by mndzmyst on 2008-05-23
My knowledge of linux is limited, so I can only tell you some things I tried to get it to work. I know that I have had problems with installing ndiswrapper drivers after using other drivers. I eventually had to reinstall (I know, it's drastic, but I have my home on separate partition). Then I immediately blacklisted r8180, rebooted, and installed ndiswrapper drivers for card....Sorry I can't be more help tho. :confused:

---

