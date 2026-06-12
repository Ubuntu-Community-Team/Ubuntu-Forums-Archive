---
title: "Cant Get the SiS191 Ethernet to Connect to Internet on Acer M1610"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by RoronoaZoro747 on 2008-03-11
ok to start,i have

Processors - Intel Core 2 Duo CPU E4500 @ 2.20GHz
Memory - 1 GB Ram
HDD - 250GB [[c drive - 130 GB,d drive 100GB]]
OS - Windows Vista Ultimate 32-bit [[Installed in C drive]]
PC Model/Mobo - Acer Aspire M1610
Computer - ACPI x86 Based PC
Disk drives - Hitachi HDT725025VLA380
Display Adapters - ATI Radeon HD2400 PRO
DVD/CD-ROM drives - HL-DT-ST DVDRAM_GSA-H40N ATA Device
Keyboards - HID Keyboard Device
Mice - HID-Compliant mouse
Monitors - Acer LCD Monitor X173
Network Adapters - SiS191 Ethernet Controller
Sound,Video and game controllers - Realtek High Definition Audio
Storage Contollers - Microsoft iSCSI Initiator

Thats all i think necessary to let you guys know,i f you need to anything else just name it..

Ok now on to my problem,i wanted to dual boot my vista with linux ubuntu,but there is one problem.btw i have ubuntu 7.10,linux mint,knoppix and mandriva liveCD's....

after tried booting all of them i've choose to use ubuntu.they are working well except i cant connect to internet.same to knoppix,i got input not supported on linux mint and yet to try mandriva as i just finish downloading the iso.but it doesnt matter because i want ubuntu.

i know how to make partition using the vista disk manager so in think no need to tell me that(i still didnt do it so i might ask about it if i have problems.)

i dont really know if all of my hardware was detected but the most obvious thing is my internet couldnt be connected,i also try the terminal thing,but it always said no ethernet card was found.

so can someone tell me any step or guide o how to get it to work??i dont want to change any hardware so please tell bout changing that at the very last step...

Thnxs in advance....

---

### Post by RoronoaZoro747 on 2008-03-11
ok let me tell one by one what i dont understand.to refresh i have a Sis191 Ethernet Controller,and i'm looking at this guide right now - [http://www.howtoforge.com/creating-the-sis191-gigabit-ethernet-driver-on-linux-2.6](http://www.howtoforge.com/creating-the-sis191-gigabit-ethernet-driver-on-linux-2.6)

i'll take all the contents there and put them here.
ok here we go.....**[[The one in red is my response,ans please i need real help,dont give me a link or somewhat this time,i'm really a noob one so go easy with me....]]**

------------------------------------------------------------------------------------------------------------------
**The Problem**

When executing

```
modprobe sis190
```

, under a vanilla 2.6.x kernel (mine is 2.6.22 from ubuntu 7.10), you will see this error:

'Can not find ISA bridge'

And no networking interface will be found. If you're unlucky, as I was until I bought a PCI network card, you'll have no network so this how-to will be impossible for you to reach.

The reason is that vanilla driver searches for ISA bridge ID 965, but mine is 968, as I saught executing 

**[COLOR="Red"]Well i tried the code on the terminal but nothing comes out.....[/COLOR]**

```
lspci -nn
```

[I]00:02.0 ISA bridge [0601]: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] [1039:0968] (rev 01)

[...]

00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter [1039:0191] (rev 02)
[/I]

[B][COLOR="Red"]I tried this i got this,
ubuntu@ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: Silicon Integrated Systems [SiS] 671MX [1039:0671]
00:01.0 PCI bridge [0604]: Silicon Integrated Systems [SiS] PCI-to-PCI bridge [1039:0004]
00:02.0 ISA bridge [0601]: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] [1039:0968] (rev 01)
00:02.5 IDE interface [0101]: Silicon Integrated Systems [SiS] 5513 [IDE] [1039:5513] (rev 01)
00:03.0 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.0 Controller [1039:7001] (rev 0f)
00:03.1 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.0 Controller [1039:7001] (rev 0f)
00:03.3 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 2.0 Controller [1039:7002]
00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter [1039:0191] (rev 02)
00:05.0 IDE interface [0101]: Silicon Integrated Systems [SiS] SATA Controller / IDE mode [1039:1183] (rev 03)
00:06.0 PCI bridge [0604]: Silicon Integrated Systems [SiS] PCI-to-PCI bridge [1039:000a]
00:0c.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) [104c:8024]
00:0f.0 Audio device [0403]: Silicon Integrated Systems [SiS] Azalia Audio Controller [1039:7502]
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Unknown device [1002:94c3]
01:00.1 Audio device [0403]: ATI Technologies Inc Unknown device [1002:aa10][/COLOR][/B]

As you can see, I actually have an Ethernet controller model 191 from SIS ;) 

**The Solution**

We must change the ISA bridge ID from the vanilla driver, from 0x965 to 0x968, or whatever ID you have (see output from lspci)

Ignore the sis191 official driver download. It is completely out-of date (see [www.sis.com/download](www.sis.com/download), then Download Center > Network Driver : SiS191 Gigabit & SiS190 LAN : Linux)

Instead, go to [www.kernel.org](www.kernel.org) and grab the .tar.gz file for your current kernel version (see 

```
uname -r
```

). Once uncompressed with

```
tar -xvzf [file.tar.gz]
```

 edit the driver' source file in *'[kernel_src_folder]/drivers/net/sis190.c'.* At line 1576 you'll find this section:

 [I]*      sis190_get_mac_addr_from_apc - Get MAC address for SiS965 model
 *      @pci_dev: the sis190 pci device
 *      @net_dev: the net device to get address for
 *
 *      SiS965 model, use APC CMOS RAM to store MAC address.
 *      APC CMOS RAM is accessed through ISA bridge.
 *      MAC address is read into @net_dev->dev_addr.
 */
static int __devinit sis190_get_mac_addr_from_apc(struct pci_dev * pci_dev, struct net_device *net_dev)
{
        struct pci_dev *isa_bridge = NULL;
        struct sis190_private * sis_priv = net_dev->priv;
        u8 reg, temp;
        int i;

        printk(KERN_INFO "%s: Read MAC address from APC\n", net_dev->name);
        
        isa_bridge = pci_find_device(0x1039, 0x0965, isa_bridge);
        if (!isa_bridge) {
                printk("%s: Can not find ISA bridge\n", net_dev->name);
                return 0;
        }[/I]

**[COLOR="Red"]Ok i got linux 2.6.24.tar.gz from here - [http://www.kernel.org/pub/linux/kernel/v2.6/](http://www.kernel.org/pub/linux/kernel/v2.6/) with the size 56MB and was released on 24/01/08,how to know my kernel anyway??is this the right one for me??[/COLOR]**

Now change the line

*isa_bridge = pci_find_device(0x1039, 0x0965, isa_bridge);*

to

*isa_bridge = pci_find_device(0x1039, 0x0968, isa_bridge);*

Or whatever ID you actually have (mine is 0x0968, remember).

**[COLOR="Red"]I got this one:):):):)[/COLOR]**

**Compile And Use The New Module**

[COLOR="Red"]**I'll Ask Bout this once i got the above one clear....**[/COLOR]

Thnxs....

---

