---
title: "Following directions for newer mac mini ubuantu download"
date: 2015-04-13
forum: Apple Hardware Users
---

### Post by Trish9 on 2015-04-13
[Using the chart on Ubuntu's support pages]("https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages") in order to download the right pick for ubuntu, I do  not find the option for Mac  Mini Late 2012.  The directions read:

"If you have a hardware revision of a Mac, that is new or unlisted, post your Mac version and the output of 'lspci' to the [Apple Users Ubuntu Forums]("http://ubuntuforums.org/forumdisplay.php?f=328").  In this way the support team can see what hardware you have. Try to use  the wiki page for the latest version of your Mac. Note anything that  works on your new hardware."   Oh, dear, forgot to mention.  I am Mountain Lion.

The last listed Mac Mini is 
[TABLE]
[TR]
[TD]5,1[/TD]
[TD]mid 2011[/TD]
[TD][Macmini5-1/Precise]("https://help.ubuntu.com/community/Macmini5-1/Precise")[/TD]
[/TR]
[/TABLE]

I will hold off installing until I hear back.  BTW,  I am really liking the Linux forum; it feels familiar.

Trish9

---

### Post by Trish9 on 2015-04-13
Doesn't anyone know which Ubuntu operating system works best on the MacMini 2012 (late) Mt. Lion?  
Would the ubuntu-14.04.2-desktop-amd64 .iso work?  Would I have to change the .iso?

---

### Post by buzzingrobot on 2015-04-13
> **Trish9 said:**
> Doesn't anyone know which Ubuntu operating system works best on the MacMini 2012 (late) Mt. Lion?  
Would the ubuntu-14.04.2-desktop-amd64 .iso work?  Would I have to change the .iso?

I've never put Ubuntu on a Mini, but I did put it on a 2011 Macbook Pro. The problems I had all involved the Macbook's hybrid video:  Onboard Intel and a discrete AMD card. OS X defaults to the Intel and switches to the AMD card when demand requires it.  Apple uses hardware to make that switch, so it happens transparently.  Ubuntu couldn't do that, so I had to resort to find a way to shut off the Radeon card so Ubuntu would think it was running on a machine with only Intel video.  And, if I shut down the Intel instead, Ubuntu used the AMD card, and lacked the necessary fan control (they ran maxed out all the time).

The Mini has just onboard Intel, right?  So you should not run into the issues I had. The Linux Intel video driver is written and maintained by Intel and is used by default on any Ubuntu install that detects an active Intel video unit. You don't have to chase down or even install a driver.

I'd imagine the 14.04.02 is a good bet to work.  Best approach is to just boot the iso in the Mini and play with it in Live Mode (the installer offers you a choice between 'Try" or "Install".  It's useful to check out hardware compatibility via "Try").

If you search for help, use the specific model number of your Mini.  I found that subtle changes between models made a big difference; advice that worked for the model just before or just after mine often would not work on my hardware.

---

### Post by cariboo on 2015-04-13
Moved to Apple Hardware Users sub-forum.

---

### Post by Trish9 on 2015-04-14
Thanks 
     [**[COLOR=#000000]buzzingrobot[/COLOR]**]("http://ubuntuforums.org/member.php?u=1488460")      

I appreciate your help!

  I have been struggling with this for 4 days, and I mean long days.  But as usual, it's always the tiny details that can mess me up.  I now have 7 DVDs for installing Ubuntu.  Yep, long story short, I though the software [rEFlt-0.14]("http://refit.sourceforge.net/doc/c1s5_burning.html") was going to wake up and install Ubuntu onto the DVD; each time I took a stab at burning a Bootable DVD for Ubuntu following different instructions, and each time I forgot to hold down the "C" key.  I nearly fell off my chair when I finally saw the screen turn black and Ubuntu came to life.

Now, I have to figure out which technique I want to use, Parallels, Oracle VM VirtualBox Manager, or rEFlit.

Looks like my question got moved.  Hope you found my thank you.

Trish
**Can't find the option to add (Solved)**

---

### Post by bapoumba on 2015-04-15
You can mark your thread as Solved in the Thread Tools menu.

Mainly because my MBP is from work and I do not want to mess with it, and because my personal old Ubuntu laptop is mostly dead, I run Ubuntu in VBox on the Yosemite host. It's painless, you can install from the downloaded .iso (running the guest additions for video), if something breaks, you can revert to the last working snapshot (provided you do snapshot), and try different flavors :)

---

### Post by puntigilio on 2015-05-05
Here Macmini 6,1 with Ubuntu 15.04 Vivid, Mac OS X Yosemite, Refind 0.8.6

$>sudo dmidecode -s system-product-name
Macmini6,1
$>lspci
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM57766 Gigabit Ethernet PCIe (rev 01)
01:00.1 SD Host controller: Broadcom Corporation BCM57765/57785 SDXC/MMC Card Reader (rev 01)
02:00.0 Network controller: Broadcom Corporation BCM4331 802.11a/b/g/n (rev 02)
03:00.0 FireWire (IEEE 1394): LSI Corporation FW643 [TrueFire] PCIe 1394b Controller (rev 08)
04:00.0 PCI bridge: Intel Corporation DSL3510 Thunderbolt Port [Cactus Ridge] (rev 03)
05:00.0 PCI bridge: Intel Corporation DSL3510 Thunderbolt Port [Cactus Ridge] (rev 03)
05:03.0 PCI bridge: Intel Corporation DSL3510 Thunderbolt Port [Cactus Ridge] (rev 03)
05:04.0 PCI bridge: Intel Corporation DSL3510 Thunderbolt Port [Cactus Ridge] (rev 03)
05:05.0 PCI bridge: Intel Corporation DSL3510 Thunderbolt Port [Cactus Ridge] (rev 03)
05:06.0 PCI bridge: Intel Corporation DSL3510 Thunderbolt Port [Cactus Ridge] (rev 03)
06:00.0 System peripheral: Intel Corporation DSL3510 Thunderbolt Port [Cactus Ridge] (rev 03)

Everything works perfectly !

---

