---
title: "enabling wifi on leopard macbook?"
date: 2009-07-13
forum: Apple Hardware Users
---

### Post by pcrussell50 on 2009-07-13
i have a perfectly functioning dual boot of leopard and ubu9.04 using refit.  love it.  

but...

i know this has got to be buried somewhere in this mac users forum, [and i am inferring without knowing for sure that] i will need to do some sort of ndiswrapper solution, but i have no idea now to do it.  is there a step-by-step walkthrough someone could link me to?

core2 duo 2.2Ghz, 1Gb ram, fully up-to-date leopard, 10.5.7, plain white macbook

thanks and regards,
peter

---

### Post by hvthao on 2009-07-14
Check this link: [https://help.ubuntu.com/community/MacBook4-1/Jaunty](https://help.ubuntu.com/community/MacBook4-1/Jaunty) (Wireless section). It seems that you don't need ndiswrapper anymore, unless you're using Intrepid or before.

PS: and also this link: [https://help.ubuntu.com/community/MacBook3-1/Jaunty](https://help.ubuntu.com/community/MacBook3-1/Jaunty) (I'm thinking your mac is 3.1)

---

### Post by pcrussell50 on 2009-07-15
> **hvthao said:**
> Check this link: [https://help.ubuntu.com/community/MacBook4-1/Jaunty](https://help.ubuntu.com/community/MacBook4-1/Jaunty) (Wireless section). It seems that you don't need ndiswrapper anymore, unless you're using Intrepid or before.

PS: and also this link: [https://help.ubuntu.com/community/MacBook3-1/Jaunty](https://help.ubuntu.com/community/MacBook3-1/Jaunty) (I'm thinking your mac is 3.1)

ok, thanks.  THAT was the information i was looking for.  completely model-specific.  thanks so much.

my macbook is a 3,1 by the way.

-peter

---

### Post by pcrussell50 on 2009-07-19
for review, i have a fully current, leopard macbook, 3,1 and i cant get wireless to run on jaunty, 9.04. 

> **hvthao said:**
> 
PS: and also this link: [https://help.ubuntu.com/community/MacBook3-1/Jaunty](https://help.ubuntu.com/community/MacBook3-1/Jaunty) (I'm thinking your mac is 3.1)

Ok, i'm back home with access to an ethernet connection, which works fine.  I tried the techniques listed in the above link, excerpted here:

> Wireless (AirPort)

In Ubuntu 9.04, support for the AirPort (a Broadcom BCM4328 chip) is included in the linux-restricted-modules package. Just go to Systems -> Hardware Drivers and activate "Broadcom STA wireless driver". If your network manager frontend doesn't immediately show the new network interface, you might need to reboot your MacBook. Afterwards you're immediately good to go!

Some people complained about the driver being shown as activated, but unused. If this happens to you, try to deactivate and re-activate the driver in the Systems -> Hardware Drivers frontend and reboot.

If this doesn't work either, you might want to try the Broadcom driver from [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

the second paragraph applied to me, so i followed the instructions and now it says that the driver is "activated and in use", only when i unplug my ethernet cable to test the wireless, i get nothing.  any ideas as to where to go from here?  maybe i just need to configure something under the "system" menu?  but what? how?

i REALLY don't want to try the tar.gz file in the last step, since i don't know how to use them, and my specific bcm card is not listed as one of the ones that the driver is for, and i don't know if my 3,1 macbook is 32 or 64 bit.

-peter

---

### Post by pcrussell50 on 2009-07-19
fwiw, from another thread, they wanted the result of when i type:

> /var/log/messages

into the terminal, i get "permission denied"

when i try, > sudo /var/log/messages , i get, "command not found"

is my syntax wrong in using > /var/log/messages in the terminal?

-peter

---

### Post by hvthao on 2009-07-19
/var/log/messages is a file. To read it, using the command "cat":

cat /var/log/messages

---

### Post by pcrussell50 on 2009-07-19
> **hvthao said:**
> /var/log/messages is a file. To read it, using the command "cat":

cat /var/log/messages

here goes, but it's huge and looks uninteresting, and i don't know why:

> 





















































































































































































































































































































Jul 19 10:33:23 peter-laptop kernel: [    0.521686] TCP: Hash tables configured (established 131072 bind 65536)n
Logged in as pcrussell50
Title:
	   	u me

Jul 19 10:33:23 peter-laptop kernel: [    0.521688] TCP reno registered
Jul 19 10:33:23 peter-laptop kernel: [    0.525055] NET: Registered protocol family 1
Jul 19 10:33:23 peter-laptop kernel: [    0.525154] checking if image is initramfs... it is
Jul 19 10:33:23 peter-laptop kernel: [    1.070978] Freeing initrd memory: 7377k freed
Jul 19 10:33:23 peter-laptop kernel: [    1.071169] cpufreq: No nForce2 chipset.
Jul 19 10:33:23 peter-laptop kernel: [    1.071288] audit: initializing netlink socket (disabled)
Jul 19 10:33:23 peter-laptop kernel: [    1.071304] type=2000 audit(1248024791.069:1): initialized
Jul 19 10:33:23 peter-laptop kernel: [    1.077773] highmem bounce pool size: 64 pages
Jul 19 10:33:23 peter-laptop kernel: [    1.077777] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Jul 19 10:33:23 peter-laptop kernel: [    1.078905] VFS: Disk quotas dquot_6.5.1
Jul 19 10:33:23 peter-laptop kernel: [    1.078957] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jul 19 10:33:23 peter-laptop kernel: [    1.079467] fuse init (API version 7.10)
Jul 19 10:33:23 peter-laptop kernel: [    1.079538] msgmni has been set to 1725
Jul 19 10:33:23 peter-laptop kernel: [    1.079691] alg: No test for stdrng (krng)
Jul 19 10:33:23 peter-laptop kernel: [    1.079700] io scheduler noop registered
Jul 19 10:33:23 peter-laptop kernel: [    1.079703] io scheduler anticipatory registered
Jul 19 10:33:23 peter-laptop kernel: [    1.079705] io scheduler deadline registered
Jul 19 10:33:23 peter-laptop kernel: [    1.079716] io scheduler cfq registered (default)
Jul 19 10:33:23 peter-laptop kernel: [    1.090929] pcieport-driver 0000:00:1c.0: found MSI capability
Jul 19 10:33:23 peter-laptop kernel: [    1.091129] pcieport-driver 0000:00:1c.4: found MSI capability
Jul 19 10:33:23 peter-laptop kernel: [    1.091321] pcieport-driver 0000:00:1c.5: found MSI capability
Jul 19 10:33:23 peter-laptop kernel: [    1.091475] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 19 10:33:23 peter-laptop kernel: [    1.092016] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jul 19 10:33:23 peter-laptop kernel: [    1.092112] ACPI: AC Adapter [ADP1] (on-line)
Jul 19 10:33:23 peter-laptop kernel: [    1.223984] ACPI: Battery Slot [BAT0] (battery present)
Jul 19 10:33:23 peter-laptop kernel: [    1.224049] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Jul 19 10:33:23 peter-laptop kernel: [    1.224051] ACPI: Power Button (FF) [PWRF]
Jul 19 10:33:23 peter-laptop kernel: [    1.224089] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
Jul 19 10:33:23 peter-laptop kernel: [    1.224204] ACPI: Lid Switch [LID0]
Jul 19 10:33:23 peter-laptop kernel: [    1.224241] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
Jul 19 10:33:23 peter-laptop kernel: [    1.224243] ACPI: Power Button (CM) [PWRB]
Jul 19 10:33:23 peter-laptop kernel: [    1.224282] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
Jul 19 10:33:23 peter-laptop kernel: [    1.224284] ACPI: Sleep Button (CM) [SLPB]
Jul 19 10:33:23 peter-laptop kernel: [    1.224756] ACPI: SSDT 3EEC9A98, 02FE (r1  APPLE  Cpu0Ist     3000 INTL 20061109)
Jul 19 10:33:23 peter-laptop kernel: [    1.225043] ACPI: SSDT 3EEC7C98, 0222 (r1  APPLE  Cpu0Cst     3001 INTL 20061109)
Jul 19 10:33:23 peter-laptop kernel: [    1.226859] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Jul 19 10:33:23 peter-laptop kernel: [    1.226880] processor ACPI_CPU:00: registered as cooling_device0
Jul 19 10:33:23 peter-laptop kernel: [    1.226883] ACPI: Processor [CPU0] (supports 8 throttling states)
Jul 19 10:33:23 peter-laptop kernel: [    1.227179] ACPI: SSDT 3EEC8F18, 00C8 (r1  APPLE  Cpu1Ist     3000 INTL 20061109)
Jul 19 10:33:23 peter-laptop kernel: [    1.227450] ACPI: SSDT 3EEC7F18, 0085 (r1  APPLE  Cpu1Cst     3000 INTL 20061109)
Jul 19 10:33:23 peter-laptop kernel: [    1.228043] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
Jul 19 10:33:23 peter-laptop kernel: [    1.228059] processor ACPI_CPU:01: registered as cooling_device1
Jul 19 10:33:23 peter-laptop kernel: [    1.228062] ACPI: Processor [CPU1] (supports 8 throttling states)
Jul 19 10:33:23 peter-laptop kernel: [    1.243438] isapnp: Scanning for PnP cards...
Jul 19 10:33:23 peter-laptop kernel: [    1.597324] isapnp: No Plug & Play device found
Jul 19 10:33:23 peter-laptop kernel: [    1.601930] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Jul 19 10:33:23 peter-laptop kernel: [    1.602791] brd: module loaded
Jul 19 10:33:23 peter-laptop kernel: [    1.603046] loop: module loaded
Jul 19 10:33:23 peter-laptop kernel: [    1.603101] Fixed MDIO Bus: probed
Jul 19 10:33:23 peter-laptop kernel: [    1.603106] PPP generic driver version 2.4.2
Jul 19 10:33:23 peter-laptop kernel: [    1.603153] input: Macintosh mouse button emulation as /devices/virtual/input/input4
Jul 19 10:33:23 peter-laptop kernel: [    1.603177] Driver 'sd' needs updating - please use bus_type methods
Jul 19 10:33:23 peter-laptop kernel: [    1.603185] Driver 'sr' needs updating - please use bus_type methods
Jul 19 10:33:23 peter-laptop kernel: [    1.603287] ata_piix 0000:00:1f.1: power state changed by ACPI to D0
Jul 19 10:33:23 peter-laptop kernel: [    1.603297] ata_piix 0000:00:1f.1: PCI INT A -> GSI 21 (level, low) -> IRQ 21


remember, we are now at the stage where "system > administration > hardware drivers" says that the broadcom driver is "activated and in use".  it's just that i don't know how to get it to see and join any wireless networks.

-peter

---

### Post by pcrussell50 on 2009-07-23
i followed these instructions here:
 [https://help.ubuntu.com/community/MacBook3-1/Jaunty](https://help.ubuntu.com/community/MacBook3-1/Jaunty) 

and by golly, i'm getting wireless, working great.  don't know why it all of a sudden decided to start working, but i'm tickled with it.

thanks for all the help up to this point, gang.

-peter

---

