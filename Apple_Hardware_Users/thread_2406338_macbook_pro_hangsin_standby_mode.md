---
title: "macbook pro hangsin standby mode"
date: 2018-11-19
forum: Apple Hardware Users
---

### Post by tolio.stefano on 2018-11-19
Hi.

 I’ve installed Ubuntu 18.04 on my Apple macbook pro 11,3 kernel 4.15.0-39.
My problem is connected with the standby mode

  1)when I try to put pc on standby mode (pressing alt and clicking on the pover icon on the top righr panel) screen become black but the display light stay on. Pc hangs and I have to reset pressing power button. I tried call standby mote via command shell and the pc crash too.  
  2) waiting  standby time screen became black but the screen back light remain on; in this case I can wake up the pc by the keyboard
 
 
 I tried:
-resetting smc
-changing linux kernel
-installing ubuntu 16.04
- using wayland

  no one of this works...

  Any suggestion?
thanks 

  Here my hardware list:
narkbkb@narkbkb-MacBookPro:~$ sudo lshw -short
 [sudo] password di narkbkb:  
 H/W path               Device     Class          Description
 ============================================================
                                   system         MacBookPro11,3 (System SKU#)
 /0                                bus            Mac-2BD1B31983FE1663
 /0/0                              processor      Intel(R) Core(TM) i7-4870HQ CPU
 /0/0/2                            memory         128KiB L1 cache
 /0/0/3                            memory         1MiB L2 cache
 /0/0/4                            memory         6MiB L3 cache
 /0/1                              memory         128KiB L1 cache
 /0/6                              memory         16GiB System Memory
 /0/6/0                            memory         8GiB SODIMM DDR3 Synchronous 16
 /0/6/1                            memory         8GiB SODIMM DDR3 Synchronous 16
 /0/c                              memory         1MiB BIOS
 /0/36dd                           memory         1019KiB BIOS
 /0/100                            bridge         Crystal Well DRAM Controller
 /0/100/1                          bridge         Crystal Well PCI Express x16 Co
 /0/100/1/0                        display        GK107M [GeForce GT 750M Mac Edi
 /0/100/1/0.1                      multimedia     GK107 HDMI Audio Controller
 /0/100/1.1                        bridge         Crystal Well PCI Express x8 Con
 /0/100/1.1/0                      bridge         DSL5520 Thunderbolt 2 Bridge [F
 /0/100/1.1/0/0                    bridge         DSL5520 Thunderbolt 2 Bridge [F
 /0/100/1.1/0/0/0                  generic        DSL5520 Thunderbolt 2 NHI [Falc
 /0/100/1.1/0/3                    bridge         DSL5520 Thunderbolt 2 Bridge [F
 /0/100/1.1/0/3/0                  bridge         DSL2210 Thunderbolt Controller  
 /0/100/1.1/0/3/0/0                bridge         DSL2210 Thunderbolt Controller  
 /0/100/1.1/0/3/0/0/0   ens9       network        NetXtreme BCM57762 Gigabit Ethe
 /0/100/1.1/0/4                    bridge         DSL5520 Thunderbolt 2 Bridge [F
 /0/100/1.1/0/5                    bridge         DSL5520 Thunderbolt 2 Bridge [F
 /0/100/1.1/0/6                    bridge         DSL5520 Thunderbolt 2 Bridge [F
 /0/100/14                         bus            8 Series/C220 Series Chipset Fa
 /0/100/14/0            usb1       bus            xHCI Host Controller
 /0/100/14/0/1                     bus            Hub in Apple Extended USB Keybo
 /0/100/14/0/1/1                   input          USB Optical Mouse
 /0/100/14/0/1/2                   printer        Officejet Pro K550
 /0/100/14/0/1/3                   input          Apple Extended USB Keyboard
 /0/100/14/0/8                     bus            BRCM20702 Hub
 /0/100/14/0/8/3                   communication  Bluetooth USB Host Controller
 /0/100/14/0/c                     input          Apple Internal Keyboard / Track
 /0/100/14/1            usb2       bus            xHCI Host Controller
 /0/100/14/1/4          scsi0      storage        Card Reader
 /0/100/14/1/4/0.0.0    /dev/sdb   disk           SD Card Reader
 /0/100/14/1/4/0.0.0/0  /dev/sdb   disk            
 /0/100/16                         communication  8 Series/C220 Series Chipset Fa
 /0/100/1b                         multimedia     8 Series/C220 Series Chipset Hi
 /0/100/1c                         bridge         8 Series/C220 Series Chipset Fa
 /0/100/1c.2                       bridge         8 Series/C220 Series Chipset Fa
 /0/100/1c.2/0          wlp3s0     network        BCM4360 802.11ac Wireless Netwo
 /0/100/1c.3                       bridge         8 Series/C220 Series Chipset Fa
 /0/100/1c.3/0                     multimedia     720p FaceTime HD Camera
 /0/100/1c.4                       bridge         8 Series/C220 Series Chipset Fa
 /0/100/1c.4/0                     storage        Apple PCIe SSD
 /0/100/1f                         bridge         HM87 Express LPC Controller
 /0/100/1f.3                       bus            8 Series/C220 Series Chipset Fa
 /0/2                   scsi1      storage         
 /0/2/0.0.0             /dev/sda   disk           500GB APPLE SSD SM0512
 /0/2/0.0.0/1                      volume         200MiB EFI GPT partition
 /0/2/0.0.0/2           /dev/sda2  volume         381GiB Non-FS data partition
 /0/2/0.0.0/3           /dev/sda3  volume         83GiB EXT4 volume
 /0/2/0.0.0/4           /dev/sda4  volume         20MiB Linux swap volume

---

