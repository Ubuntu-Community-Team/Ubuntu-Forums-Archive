---
title: "Screen keeps freezing after a few minutes after fresh install of 20.04 on iMac"
date: 2020-05-29
forum: Apple Hardware Users
---

### Post by titania177 on 2020-05-29
Hello,
I have been running Ubuntu on a iMac for several years with no problems. I just did a clean install of 20.04 and now the screen very often freezes after several minutes of use. Sometimes it freezes mid boot-up, and sometimes I can't boot up at all. I am wondering if it's a graphics card issue? Here's my lspci readout. Thanks in advance for your help. I'm not very techy but can manage to use the command line if given specific instructions! 

```
0:00.0 Host bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C216 Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C216 Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C216 Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C216 Chipset Family PCI Express Root Port 4 (rev c4)
00:1c.4 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 5 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a4)
00:1f.0 ISA bridge: Intel Corporation Z77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series/C210 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C216 Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GK107M [GeForce GT 640M Mac Edition] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GK107 HDMI Audio Controller (rev a1)
03:00.0 Ethernet controller: Broadcom Inc. and subsidiaries NetXtreme BCM57766 Gigabit Ethernet PCIe (rev 01)
03:00.1 SD Host controller: Broadcom Inc. and subsidiaries BCM57765/57785 SDXC/MMC Card Reader (rev 01)
04:00.0 Network controller: Broadcom Inc. and subsidiaries BCM4331 802.11a/b/g/n (rev 02)
06:00.0 PCI bridge: Intel Corporation DSL3510 Thunderbolt Controller [Cactus Ridge 4C 2012] (rev 03)
07:00.0 PCI bridge: Intel Corporation DSL3510 Thunderbolt Controller [Cactus Ridge 4C 2012] (rev 03)
07:03.0 PCI bridge: Intel Corporation DSL3510 Thunderbolt Controller [Cactus Ridge 4C 2012] (rev 03)
07:04.0 PCI bridge: Intel Corporation DSL3510 Thunderbolt Controller [Cactus Ridge 4C 2012] (rev 03)
07:05.0 PCI bridge: Intel Corporation DSL3510 Thunderbolt Controller [Cactus Ridge 4C 2012] (rev 03)
07:06.0 PCI bridge: Intel Corporation DSL3510 Thunderbolt Controller [Cactus Ridge 4C 2012] (rev 03)
08:00.0 System peripheral: Intel Corporation DSL3510 Thunderbolt Controller [Cactus Ridge 4C 2012] (rev 03)
```

---

### Post by CelticWarrior on 2020-05-29
```
01:00.0 VGA compatible controller: NVIDIA Corporation GK107M [GeForce GT 640M Mac Edition] (rev a1)
```

You need the Nvidia proprietary drivers.

---

### Post by xxteraxx on 2020-05-29
Okay Heres what you have to do.  NVIDIA does not have drivers prebuilt into ubuntu, since they are proprietary. So what you do is you download the .run file from this link [https://www.nvidia.com/en-us/drivers/results/153717/](https://www.nvidia.com/en-us/drivers/results/153717/).  After downloading open a fresh terminal and type in 

```
cd ~/Downloads/
``` 

Then type in 

```
chmod +x NVIDIA-Linux*
```

Then 

```
sudo ./NVIDIA*
```

Reboot and see if the crashing still happens

---

### Post by titania177 on 2020-06-01
Thanks so much to both of you, will try that!

---

### Post by CelticWarrior on 2020-06-01
No, do NOT try that. NEVER install Nvidia drivers using their script.

Just open Additional Drivers and select and apply the recommended version there.

---

### Post by howefield on 2020-06-01
Moved to the "*Apple Hardware Users*" forum.

---

### Post by titania177 on 2020-06-02
Thank you so much, that seems to have worked! I needed to disable the Nouveau driver, and then I installed the NVIDIA driver. [https://linuxconfig.org/how-to-disable-blacklist-nouveau-nvidia-driver-on-ubuntu-20-04-focal-fossa-linux](https://linuxconfig.org/how-to-disable-blacklist-nouveau-nvidia-driver-on-ubuntu-20-04-focal-fossa-linux)

---

