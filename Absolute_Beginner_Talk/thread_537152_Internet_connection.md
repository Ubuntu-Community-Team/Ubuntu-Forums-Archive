---
title: "Internet connection"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by Ozcu on 2007-08-28
Cant connect to internet... Via wireless or eithe via wired



osmo@osmo:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)
06:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
06:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:06.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
osmo@osmo:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:00:4C:D1:5D  
          inet addr:*  Bcast:*  Mask:*
          inet6 addr: fe80::215:ff:fe4c:d15d/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Base address:0x6000 Memory:c8206000-c8206fff 

eth1      Link encap:Ethernet  HWaddr 00:0A:E4:DE:A7:EA  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Base address:0xa400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:692 (692.0 b)  TX bytes:692 (692.0 b)

---

### Post by uclalinux on 2007-08-29
Read this for LAN connection, 


Its all on this page [http://ubuntuforums.org/showthread.php?t=467757&highlight=realtek+rtl8111%2F8186b](http://ubuntuforums.org/showthread.php?t=467757&highlight=realtek+rtl8111%2F8186b)

```

Hey Bill,

The command lsmod lists all kernel modules (drivers) that are loaded. You will notice that there's a module r8169. dmesg shows the kernel messages, and there is a line that indicates that r8169 is being used for the ethernet card (eth0). I believe that that's not the right driver for your card. So what you would have to do is remove that driver and install the right one.
The output of lspci (which lists the pci devices in your system) shows your network card is RTL8111/8168B PCI Express. I went to the Realtek web page, and they have a linux driver for that card:

http://www.realtek.com.tw/downloads/...&GetDown=false

You want to download the "Linux driver for kernel 2.6.x (Support x86 and x64)". This is where the problem might begin, because you don't have any working network card in your computer. Any chance you might get another network card? Ok, I'll assume for now that's solved.

Once you have that driver, you'll have to compile it. What you downloaded is the source code and you need to convert it to machine code to run it. For that you need to install some tools necessary for compiling. With a running network connection, run the following commands:
Code:

sudo aptitude install build-essential
sudo aptitude install linux-headers-`uname -r`

All right, now you have to unpack the driver source: run
Code:

 tar xjf 8168-8.001.00.tar.bz2

in the folder where you downloaded the driver.
That will create a folder, r8168-8.001.00, so change there and compile the source:
Code:

cd r8168-8.001.00
make clean modules
sudo make install
sudo depmod -a

(if something goes wrong here, please post the output of those commands)

That should compile it and copy it to the system folder where it has to be. Well, if everything went fine, it's time to load it in the kernel. First unload the incorrect driver:
Code:

sudo modprobe -r r8169

and then load the newly compiled one:
Code:

sudo modprobe r8168

You can check that it's loaded by running lsmod, and checking the driver it's there. If you run ifconfig -a, you should see the network interface (eth?). Try to configure the network and see if it works. If it doesn't please post the output of dmesg after loading the new driver.

If it works, I'll send you instructions to make these changes permanent. Good luck!
```

---

