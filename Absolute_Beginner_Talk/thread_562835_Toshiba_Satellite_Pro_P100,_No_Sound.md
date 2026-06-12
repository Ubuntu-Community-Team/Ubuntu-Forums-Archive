---
title: "Toshiba Satellite Pro P100, No Sound"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by mandeepsmagh on 2007-09-29
Hi, everyone. I have got Toshiba Satellite Pro P100. I installed Ubuntu 7.04 Feisty for the first time. Everything is working fine,except sound. It shows sound icon,which means it recognises sound card. By clicking on preference it shows HDA Intel (Alsa Mixer) and Connexant Wikii. I tried to install Alsa Drivers But couldn't do it. Pls Help !

---

### Post by ThrobbingBrain66 on 2007-09-29
Give my solution here a shot:
[http://ubuntuforums.org/showthread.php?t=560670](http://ubuntuforums.org/showthread.php?t=560670)

---

### Post by mandeepsmagh on 2007-09-29
Thanks I tried but it didn't help. I am total new to Ubuntu. Pls tell me how to install Alsa drivers first and how to compile them. thanks

---

### Post by dwhitney67 on 2007-09-29
Do you know what kind of audio chip-set you have?

On my P200 I have this one:

[FONT="Courier New"]00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)[/FONT]

You can find yours by running:

[FONT="Courier New"]$ lspci | grep -i audio[/FONT]

---

### Post by mandeepsmagh on 2007-09-30
Ya its same here .Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

---

### Post by dwhitney67 on 2007-09-30
To get that chip-set to work on my system that runs Fedora 7, I had to include an additional entry (marked below in blue) into the /etc/modprobe.conf file.
[FONT="Courier New"]
alias snd-card-0 snd-hda-intel
options snd-card-0 index=0
options snd-hda-intel index=0
[COLOR="Blue"]options snd-hda-intel model=3stack[/COLOR][/FONT]

Under Ubuntu, you should have a file called /etc/modprobe.d/alsa-base.  I do not know if adding any of what I provided above would help your cause, so below is a copy of my alsa-base that I have on my Ubuntu system.  Please note that my Ubuntu system has _rev 01_ of the Intel 82801G audio chip-set, so I do not know if that makes a difference.

[PHP]# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388[/PHP]

P.S.  If you make any changes, you may be required to reboot your system to "hear" any effect.

---

### Post by mandeepsmagh on 2007-09-30
I may sound stupid. But can u tell me which code i should type to go through all these steps. Thanks for help.

---

### Post by dwhitney67 on 2007-09-30
This isn't code.  The information I provided is (or should be) within the file /etc/modprobe.d/alsa-base.

The first thing I would do is to compare your /etc/modprobe.d/alsa-base file with what I have provided.  You can examine your file by running this command:

$ more /etc/modprobe.d/alsa-base

and using the "enter" key or the "space bar" to peruse through the file.

Frankly, I am surprised that you are having trouble with the Intel audio chip-set.  Do a search on Ubuntu in the "Absolute Beginner Talk" forum for "sound" and "alsa".  Somebody just fixed their system the other day (Thursday?) with a similar problem to what you are having.  Go [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=560252&page=2") to see how they did it.

---

### Post by mandeepsmagh on 2007-09-30
I tried suggested thread but nothing happened. I have also included result of the code which returns same as yours. Pls  help me to find the line needs to be edited.

---

### Post by mandeepsmagh on 2007-09-30
[PHP]manpreet@manpreet-laptop:~$ more /etc/modprobe.d/alsa-base
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprob
e -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin
/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /
sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin
/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS &&
 { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS &&
 { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin
/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprob
e -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
manpreet@manpreet-laptop:~$ 

[/PHP]

---

### Post by mandeepsmagh on 2007-09-30
This is result of the code lspci
[PHP]manpreet@manpreet-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7900 GTX (rev a1)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
0a:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0a:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0a:04.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
[/PHP]

---

### Post by mandeepsmagh on 2007-09-30
This is the result it shows with code lspci -v
[PHP]manpreet@manpreet-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: d0000000-d1ffffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at d2400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Memory behind bridge: 8c000000-8c0fffff
        Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1800 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1820 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1840 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 1860 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, medium devsel, latency 0, IRQ 19
        Memory at d2404000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0a, subordinate=0e, sec-latency=32
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: d2000000-d20fffff
        Prefetchable memory behind bridge: 0000000088000000-000000008bffffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02) (prog-if 80 [Master])
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 18b0 [size=16]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: medium devsel, IRQ 11
        I/O ports at 18c0 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7900 GTX (rev a1) (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at d1000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at d0000000 (64-bit, non-prefetchable) [size=16M]
        I/O ports at 2000 [size=128]
        Capabilities: <access denied>

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Intel Corporation Unknown device 1040
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at 8c000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

0a:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, medium devsel, latency 168, IRQ 17
        Memory at d2004000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=0a, secondary=0b, subordinate=0e, sec-latency=176
        Memory window 0: 88000000-8bfff000 (prefetchable)
        Memory window 1: 90000000-93fff000
        I/O window 0: 00003000-000030ff
        I/O window 1: 00003400-000034ff
        16-bit legacy interface ports at 0001

0a:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, medium devsel, latency 64, IRQ 17
        Memory at d2006000 (32-bit, non-prefetchable) [size=2K]
        Memory at d2000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

0a:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, medium devsel, latency 64, IRQ 17
        Memory at d2005000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

0a:04.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller (prog-if 01)
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, medium devsel, latency 64, IRQ 17
        Memory at d2006800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
[/PHP]

---

### Post by dwhitney67 on 2007-09-30
I am going to assume that you need to uninstall and then re-install the appropriate Alsa drivers for your audio chip-set.  Please search this forum.  Other people are reporting the same problem that you are having and many have resolved their audio problems.  I believe a lot of this occurred recently when lots of folks updated their kernel.

I cannot help you any further because I do not have the experience necessary to instruct you where to get the Alsa drivers.  That link I provided earlier may give you some hints.

---

### Post by lawrencewmooreJ on 2007-09-30
Hi there,

I just wanted to let you know that I'm dealing with the same problem.  I have a Toshiba Sattelite P series.  A lot of the other posts about problems are older, so I'm glad that I found one that's recent.  I haven't solved it yet, but let's stay in touch in case one of us does.  I'm running Ubuntu Studio.  

I have the same sound information as you, but I was wondering if our sound card is being detected properly?  I've tried to look up specs on the computer to see what the sound system is listed as, but I haven't found specific chipset information.  Maybe the sound is being recognized incorrectly.

---

### Post by dwhitney67 on 2007-09-30
The audio chip-set is definitely is probably being recognized, but is not fully enabled.  My Ubuntu system is working fine, thus I refuse to update the kernel because I know that I will fall into the same "boat" as you and the others.

However, for those who made the mistake of updating their kernels (when nothing warranted such) or if they are doing a new install, then they will fall into the same predicament that you find yourself in now.  I can assure you that Linux does support your audio chip-set.  You may have to re-install the "Alsa" driver(s) for your chip-set.

I'm sure Canonical is aware of the situation and will remedy it "soon" with their next release.  However, for now, you will have to take matters into your own hands.  Dig deeper into the forums or search other Linux forums (e.g. LinuxQuestions.org).  This is not an issue relegated only to Ubuntu; it is occuring (or has occurred) in other distros.

---

### Post by mandeepsmagh on 2007-09-30
This is what i was trying to do.
[PHP]

sudo apt-get install build-essential ncurses-dev 

sudo apt-get install linux-headers-`uname -r` 

cd ~ 

mkdir alsa-src 

cd alsa-src 

wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc3.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc3.tar.bz2) 

wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.14rc3.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.14rc3.tar.bz2) 

wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.14rc2.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.14rc2.tar.bz2) 



sudo /etc/init.d/alsasound stop 



tar xvf alsa-driver-1.0.14rc3.tar.bz2 

tar xvf alsa-lib-1.0.14rc3.tar.bz2 

tar xvf alsa-utils-1.0.14rc2.tar.bz2 



cd ~/alsa-src 
 
tar xvf realtek6.tar.gz 

cp patch_realtek.c ~/alsa-driver-1.0.14rc3/alsa-kernel/pci/hda/ 



cd alsa-driver-1.0.14rc3 

./configure --with-cards=hda-intel 

make 

sudo make install 



cd ../alsa-lib-1.0.14rc3 

./configure 

make 

sudo make install 



cd ../alsa-utils-1.0.14rc2 

./configure 

make 

sudo make install 



sudo modprobe snd-hda-intel [/PHP]
  
But i have got problem with patch since it is for realtek  and mine is** conexant cx20551(wikiki)**** (oss mixer)**. I think i need to patch accordingly my sound card. But i have no idea how to do it.

---

### Post by mandeepsmagh on 2007-09-30
Hi, Lawrence 

Thanks for joining in. I am quite eager to listen sound on Ubuntu. I have tried everything i could to get sound. But nothing worked. Now both of us  can help each other.  I think we need to patch Alsa drivers, atleast that is what i have found in the most threads and i have done quite a lot of googling. It would be nice to get view from ur side. Thanks again.

---

### Post by dwhitney67 on 2007-09-30
If you do not have a realtek audio card (or chip-set), then there should be no need to compile that particular driver (and hence not worry about the patch file).

I think the main thing is to recompile Alsa to use the new kernel headers (which you obtained when you obtained the kernel source).

Now because your system has a Conexant, this might encumber your efforts to get your audio device working.  I did a little research using Google and did not find much, but I did find this [link]("http://www.linuxquestions.org/questions/showthread.php?t=531575") that perhaps might help.

For those of you who have the Intel 82801G (IH7 Family), I would follow the steps listed by mandeepsmagh (with the exception of the realtek stuff).

---

### Post by mandeepsmagh on 2007-10-01
Thanks, Dwhitney

for helping me. I tried to recompile alsa drivers by skipping realtek codes. I think alsa drivers are installed correctly this time. But there is no sound yet. Probably there is something that is still missing. Do you have any other idea to recompile alsa drivers.  It seems like missing just one or two steps. When i run this code - 
sudo apt-get install linux-headers-`uname -r` . It returns like this

[PHP]manpreet@manpreet-laptop:~$ sudo apt-get install linux-header-'uname -r'
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-header-uname -r
manpreet@manpreet-laptop:~$ 

[/PHP]
According to me this is the cause of the problem. Maybe you would be able to interpret it better.

---

### Post by dwhitney67 on 2007-10-01
Try your apt-get command again, this time ensuring that you specify linux-header**s**-`uname -r`.  Note the 's' at the end of headers.

---

### Post by mandeepsmagh on 2007-10-01
Still same result
[PHP]manpreet@manpreet-laptop:~$ sudo apt-get install linux-headers-'uname -r'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-uname -r
manpreet@manpreet-laptop:~$ sudo apt-get install linux-headers-'uname-r'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-uname-r
manpreet@manpreet-laptop:~$ 

[/PHP]

---

### Post by dwhitney67 on 2007-10-01
A common mistake... you used the wrong single-quote characters to surround uname -r.  Use the other single quote that is shared with the ~ character on your keyboard.

---

### Post by mandeepsmagh on 2007-10-01
This is what i got this time
[PHP]manpreet@manpreet-laptop:~$ sudo apt-get install linux-headers-`uname-r`
bash: uname-r: command not found
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
manpreet@manpreet-laptop:~$ sudo apt-get install linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.20-16-generic is already the newest version.
linux-headers-2.6.20-16-generic set to manual installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
manpreet@manpreet-laptop:~$ 


[/PHP]

---

### Post by mandeepsmagh on 2007-10-01
I assume by this that there is no problem with it. It might be something else.

---

### Post by dwhitney67 on 2007-10-01
It's probably not a problem, however if you wish to verify again, ensure that you place white-space between uname and the -r.

You can test uname on the command line:

$ uname -r
$ uname -a
$ man uname
etc.

---

### Post by mandeepsmagh on 2007-10-01
I checked it and there is no problem with linux headers.  It is something else, don't know what?

---

### Post by dwhitney67 on 2007-10-01
Try to see if the (second) script in this [post]("http://ubuntuforums.org/showthread.php?t=485486&page=2") will help.

---

### Post by mandeepsmagh on 2007-10-02
I am going to give up Ubuntu for now. Probably in future i will try again.
Thanks guys for helping me. Thanks alot. Bye !

---

### Post by Hairy Hobbit on 2007-10-31
Afternoon all,

I just wondered if anyone got anywhere after the original person decided to give up on Ubuntu.  I have a Satellite Pro P100 PSPA4E.  I have a completely fresh and clean install of Ubuntu.  All I have done is the install and the automatic security updates.  I decided to go back and do a fresh install as I've tried about 5 different solutions to no avail and didnt want to have those failures affect anything I try now - I like things clean and simple when I'm trying to resolve a problem.

Anyone help?

Thanks,
HH

---

### Post by rax_m on 2007-10-31
Hi 

I have a Toshiba P100-429 and found that the only way to get sound (in both edgy and feisty) was to update the ACPI / DSDT. The default one is buggy as hell. 
I have a conextant card i think with  hda-intel (rev 02)

I followed this link : [http://ubuntuforums.org/showthread.php?t=349491&highlight=p100+sound](http://ubuntuforums.org/showthread.php?t=349491&highlight=p100+sound)

Basically it involves : 
1. Updating your bios
2. recompiling your DSDT to a working version. 
3. Installing the latest version of Alsa

I found that I also HAD to make changes to the DSDT in order to ensure that the graphics card fan works properly. 

I posted my DSDT at [http://acpi.sourceforge.net](http://acpi.sourceforge.net) 

Hope that helps. 

Cheers
Rax

---

### Post by dwhitney67 on 2007-10-31
I think I mentioned earlier that I have a P200.  The audio chip-set works fine.  Of course I have Fedora 7 installed.

My /etc/modprobe.conf looks like the following:

[FONT="Courier New"]alias eth0 r8169
alias scsi_hostadapter ata_piix
alias wlan0 iwl3945
[B]alias snd-card-0 snd-hda-intel
options snd-card-0 index=0
options snd-hda-intel index=0[/B][/FONT]

Unlike with Fedora, Ubuntu chooses to use a directory called /etc/modprobe.d where various files similar to my modprobe.conf exist.  If you have a file called alsa-base, I would check to see if the entries (that are in bold text above) are present.

Btw, please verify that you are using the same sound card as I have by running this command:

```
$ lspci | grep -i audio
```

I have the following:
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
```

P.S.  If you make changes to any file in the modprobe.d directory, you will need to reboot for any changes to be detected.

---

### Post by mandeepsmagh on 2007-11-02
Hi, Guys

          Can u tell me does Gutsy makes any difference with sound. I want to try Ubuntu again. Although I tried testing version, it was not better than Feisty (in respect of Sound).

---

### Post by gene6482 on 2007-11-02
you can make it work with feisty, sadly gutsy actually breaks the sound.

---

### Post by mandeepsmagh on 2007-11-02
Can u help me with feisty.  I have tried all most everything, except playing with  Bios and I don't want to do it because I am totally noob in this area. Thanks.

---

### Post by gene6482 on 2007-11-03
even with feisty you'll have to edit the dsdt (for the bios) to get it to work, if you check the bug page you can download the mandriva kernel and as long as you boot with acpi_osi=!Linux you'll be fine.(You'll have to make sure that you have bios v 3.8 to get it to work.

---

### Post by bernecky on 2008-02-11
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/newreply.php?do=newreply&amp;noquote=1&amp;p=3678026](http://ubuntuforums.org/newreply.php?do=newreply&amp;noquote=1&amp;p=3678026) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have spent several days (OK, more than that) dorking around with DSDT tables, acpi settings,
etc., trying to get sound to work on my Toshiba Satellite Pro P100 Model  PSPAEE.

Just on a whim, I downloaded Hardy Heron Alpha 4 and ran the Live CD:
Sound works out of the box, a bit loud (to the point of distortion), but I think
I can find the volume control eventually.

So, I'm happy, but still am unlikely to buy another Toshiba product unless they
clean up their act on the Linux front.

rbe

---

### Post by mandeepsmagh on 2008-03-01
Thanks bernecky for informing us. That is a great news for Toshiba users. I hope it will be completely fixed when Hardy will officially be  released. Thanks !

---

### Post by Smittysmit on 2008-03-02
I too have had no success with sound on a Toshiba Satellite laptop A205.  I want to confirm that when i tried the Hardy alpha CD, sound did indeed work right out of the box.

This is GREAT news for everyone with a Toshiba satellite.  Now we just wait till next month for the final release.  This should be the trick for me to totally jump to Ubuntu on my laptop.

Ubuntu is AWESOME and it just got better.

---

### Post by mandeepsmagh on 2008-04-26
Well, The sound problem has been solved in Hardy. I hope this happened to everyone outthere. Feeling so great. Good on you , Ubuntu development team for solving this problem. I can just sit and enjoy the world of ubuntu. Did I mention I am happy ? :guitar:

---

### Post by the-nuke on 2008-04-26
Had the same problem, tried everything. Updated to hardy yesterday. everything working perfect.Hope this helps

---

