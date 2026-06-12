---
title: "[SOLVED] Installing drivers"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by SidewinderPro2 on 2007-12-28
How are downloaded drivers installed? The repositories do not have the codecs for my sound card and I would like to be able to hear things in my new operating system setup. I have the .tar.bz2 driver file downloaded. What do I do next?

Also, Ubuntu is running slower on my machine than Vista does. I'm running an AMD 6000+ and 3GB of RAM with an Nvidia 8800GTS SSC that owns VIsta. Ubuntu lags when switching windows, so is this just a generic repository driver problem?

---

### Post by taurus on 2007-12-28
Look at the section on how to install it by hand, [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/).

What driver do you use for your graphic card?  Have you activated the nvidia restricted driver for it?

---

### Post by SidewinderPro2 on 2007-12-28
I'm using the restricted driver that Ubuntu automatically found. I know quite well from Windows Update that automatically found drivers are not the best way to go.

Right now I'm trying to get a Realtek HD integrated card to work for sound and I'm going to attempt the driver straight from Nvidia. I'll read up on the link you provided.

---

### Post by overdrank on 2007-12-28
> **SidewinderPro2 said:**
> How are downloaded drivers installed? The repositories do not have the codecs for my sound card and I would like to be able to hear things in my new operating system setup. I have the .tar.bz2 driver file downloaded. What do I do next?

Also, Ubuntu is running slower on my machine than Vista does. I'm running an AMD 6000+ and 3GB of RAM with an Nvidia 8800GTS SSC that owns VIsta. Ubuntu lags when switching windows, so is this just a generic repository driver problem?

HI and for you graphics you may look at Envy
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by SidewinderPro2 on 2007-12-28
This is a little too complicated for driver installation. Too many installer options out there for Linux. Windows has a serious upperhand in the driver installation department...


I have these two files as of now:
NVIDIA-Linux-x86-169.07-pkg1.run

realtek-linux-audiopack-4.07a.tar.bz2


Is there any way to install these two drivers without a million steps and a million other programs?

---

### Post by overdrank on 2007-12-28
> **SidewinderPro2 said:**
> This is a little too complicated for driver installation. Too many installer options out there for Linux. Windows has a serious upperhand in the driver installation department...


I have these two files as of now:
NVIDIA-Linux-x86-169.07-pkg1.run

realtek-linux-audiopack-4.07a.tar.bz2


Is there any way to install these two drivers without a million steps and a million other programs?

HI and that is why I recommended Envy. If the restricted driver are not to your liking then you can use Envy script to install the latest nvidia drivers. Good luck!
Edit and also if you are using the restricted drivers, you maybe able to just configure your xorg to improve performance.

---

### Post by SidewinderPro2 on 2007-12-28
And how is Envy installed? This is turning into a 2007 version of DOS.

---

### Post by KentS on 2007-12-28
> **SidewinderPro2 said:**
> This is a little too complicated for driver installation. Too many installer options out there for Linux. Windows has a serious upperhand in the driver installation department...


I have these two files as of now:
NVIDIA-Linux-x86-169.07-pkg1.run


```
sudo sh NVIDIA-Linux-x86-169.07-pkg1.run
```

> 
realtek-linux-audiopack-4.07a.tar.bz2


```
tar -xjvf realtek-linux-audiopack-4.07a.tar.bz2
```
This will probably give you a readme file with installation instructions. If there is a .run file, it's probably the same as for the nvidia driver.
Otherwise (if its the source code) it's probably
```
./configure
make
sudo make install
```
But you should read the installation instructions for the program you're trying to install.

---

### Post by SidewinderPro2 on 2007-12-28
The Nvidia driver code that you posted couldn't be found. The Realtek was all errors.

---

### Post by Paqman on 2007-12-28
> **SidewinderPro2 said:**
> And how is Envy installed? This is turning into a 2007 version of DOS.

Download the .deb file and click on it :)

---

### Post by KentS on 2007-12-28
For nvidia:
Were you in the same directory as the nvidia file?
Did you type everything correctly (e.g. completing with tab key?
Installation instructions can be found on
[http://www.nvidia.com/object/linux_display_ia32_169.07.html](http://www.nvidia.com/object/linux_display_ia32_169.07.html)
(it's the same for all drivers)
So it should work.
If the above doesn't help, what is the exact error you get?

For realtek:
I need more info.
What did you type in?
Can you paste the errors in here?

---

### Post by jken146 on 2007-12-28
> **SidewinderPro2 said:**
> I know quite well from Windows Update that automatically found drivers are not the best way to go.

This may be true in Windows, but in Ubuntu you are better off (in general) with software in the repositories.

---

### Post by SidewinderPro2 on 2007-12-28
Excellent, something actually worked. They really need to make these installers a little more similar and usable outside of the terminal.

Now how do I get the Realtek codecs installed? I can't listen to anything until that card works. And why is Ubuntu so slow on a 6Ghz system?

---

### Post by SidewinderPro2 on 2007-12-28
This is what I did:

matt@matt-desktop:~$ tar -xjvf realtek-linux-audiopack-4.07a.tar.bz2

This is what I get:

tar: realtek-linux-audiopack-4.07a.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
matt@matt-desktop:~$

---

### Post by taurus on 2007-12-28
Are you in the right directory when you ran that command?  Did you download it to ~/Desktop?

```
cd ~/Desktop
tar xvjf realtek-linux-audiopack-4.07a.tar.bz2
```

---

### Post by KentS on 2007-12-28
Can you please check that there is a file named realtek-linux-audiopack-4.07a.tar.bz2 in the exact same directory you were in when typing the command?
Did you use the tab key to auto complete the name of the file?
To extract the file, you MUST be in the same directory. And you MUST use the exact filename. Be aware that 'A' is not the same as 'a'.
You might also check that the file isn't owned by root, and no other user has any rights, and your trying to extract it without the necessary rights. Don't think that's the problem, though.

---

### Post by xeth_delta on 2007-12-28
> **SidewinderPro2 said:**
> And how is Envy installed? This is turning into a 2007 version of DOS.

Welcome aboard! Please, don't misunderstand what I am about to say, since there is no bad will in it. I just wanted to make a short observation.
It might not be obvious for a beginner, especially one being a former Windows user, but the command line is an extremely powerful tool for working on your computer. Once you know how to use it and the commands you can call, it can be much faster to configure, set-up, or find your way around the system.

Of course, in the end it might be a matter of taste whether you prefer it to a GUI or not, but it is certainly a great way to learn new things about how linux work, not only one of its (many) graphical interfaces.

That said, I have used also DOS (from some ver old versions) and, in my opinion, there is no way to compare DOS to the Linux command line. I think the difference is just to great in favour of Linux.

Again, welcome to Ubuntu and the forum, just remember to keep an open mind because certain things will be done differently than in Windows, and as we should be aware of, different does not imply worse, it can actually be the other way around. You will just need a bit of patience to get used to it. :)

Good luck!
Xeth

---

### Post by SidewinderPro2 on 2007-12-28
I have been using Windows since the DOS days, and I am an expert with Windows by now. I can use the command prompt and DOS pretty well, and hunting down drivers isn't hard in WIndows. I can do some BASIC coding on top of that, not that it seems to help here.

I have the video card working now, and at least I know its being used right. As for the sound card, I pasted in the correct coding and got this:

matt@matt-desktop:~$ cd ~/Desktop
matt@matt-desktop:~/Desktop$ tar xvjf realtek-linux-audiopack-4.07a.tar.bz2 
./realtek-linux-audiopack-4.07a/
./realtek-linux-audiopack-4.07a/Readme.txt
./realtek-linux-audiopack-4.07a/version
./realtek-linux-audiopack-4.07a/alsa-driver-rt20071002.tar.bz2
./realtek-linux-audiopack-4.07a/alsa-lib-1.0.14.tar.bz2
./realtek-linux-audiopack-4.07a/install
./realtek-linux-audiopack-4.07a/alsa-utils-1.0.14.tar.bz2
./realtek-linux-audiopack-4.07a/test.wav.bz2
matt@matt-desktop:~/Desktop$ 


Now what?

---

### Post by xeth_delta on 2007-12-28
> **SidewinderPro2 said:**
> I have been using Windows since the DOS days, and I am an expert with Windows by now. I can use the command prompt and DOS pretty well, and hunting down drivers isn't hard in WIndows. I can do some BASIC coding on top of that, not that it seems to help here.

I have the video card working now, and at least I know its being used right. As for the sound card, I pasted in the correct coding and got this:

matt@matt-desktop:~$ cd ~/Desktop
matt@matt-desktop:~/Desktop$ tar xvjf realtek-linux-audiopack-4.07a.tar.bz2 
./realtek-linux-audiopack-4.07a/
./realtek-linux-audiopack-4.07a/Readme.txt
./realtek-linux-audiopack-4.07a/version
./realtek-linux-audiopack-4.07a/alsa-driver-rt20071002.tar.bz2
./realtek-linux-audiopack-4.07a/alsa-lib-1.0.14.tar.bz2
./realtek-linux-audiopack-4.07a/install
./realtek-linux-audiopack-4.07a/alsa-utils-1.0.14.tar.bz2
./realtek-linux-audiopack-4.07a/test.wav.bz2
matt@matt-desktop:~/Desktop$ 


Now what?

What does the following commands return?
```
glxinfo | grep -i direct
```
```
glxinfo | grep -i open
```
Just to make sure all is OK with the video card.

---

### Post by KentS on 2007-12-28
```
less ~/Desktop./realtek-linux-audiopack-4.07a/Readme.txt
```
Look for installation instructions. (You quit the program by pushing 'q'.
If install is a text file, also do
```
less ~/Desktop./realtek-linux-audiopack-4.07a/install
```

---

### Post by xeth_delta on 2007-12-28
About the audio part, install might be an installation script. Have a look at readme.txt, there might be some installation instructions specific to realtek. When you install the alsa drivers from source what you have to basically do is **configure**, compile with **make**, and install with **sudo make install**. Let us know if you need help with these.

---

### Post by KentS on 2007-12-28
Check out this thread:
[http://ubuntuforums.org/showthread.php?t=91501](http://ubuntuforums.org/showthread.php?t=91501)

The easiest is probably to do
```
cd ~/Desktop./realtek-linux-audiopack-4.07a/
./install
```

---

### Post by SidewinderPro2 on 2007-12-28
At this point I have no idea what the heck I am doing with these audio drivers. I can get to the point on the command prompt where it displays the contents of the original download. I went to the folder and read the readme and its way too complicated. Is there an easier way to get this rotten sound card working?

---

### Post by SidewinderPro2 on 2007-12-28
Installing right now, GUI style, going to reboot the system and see if it did anything. The command prompt install command above didn't work.

---

### Post by xeth_delta on 2007-12-28
> **SidewinderPro2 said:**
> At this point I have no idea what the heck I am doing with these audio drivers. I can get to the point on the command prompt where it displays the contents of the original download. I went to the folder and read the readme and its way too complicated. Is there an easier way to get this rotten sound card working?

Don't dispair, you'll se it is not that complicated. Do you have a link to the page you downloaded the drivers from, so that we can see their installation instructions? Don't worry, you'll get them working.

---

### Post by SidewinderPro2 on 2007-12-28
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#High Definition Audio Codecs]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#High Definition Audio Codecs")

Scroll down the the Linux option. This should be the proper driver. I'm using a Gateway GM5474 desktop with the HD Realtek built in sound, so its integrated into the motherboard. It installed and all but I can't seem to get any sound from the Eagles CD I'm testing with.

---

### Post by SidewinderPro2 on 2007-12-28
Just to note, the default driver that was provided by the repositories was not the correct one for the video card. The new one that I got with Envy is the correct one, it detected my Samsung monitor and brought it up to 60htz refreshrate from the default driver's 50htz. I can also see all of the card's specs in the Nvidia software.

I'm messing with the drivers and I can't figure out how to get any sound.

---

### Post by xeth_delta on 2007-12-28
i just had a look at the readme file. Did you remember to run the **install** script as root? Try
```
sudo ./install
```

---

### Post by SidewinderPro2 on 2007-12-28
It installed when I click on the icon. I've experimented with everything in the sound options and I still can't get any sound. Anyone have a clue as to how to get sound. (On a good note, I have Compiz running half decently.)

---

### Post by jabeez on 2007-12-28
if your audio is connected with optical/spdif, you should open a terminal and type alsamixer and go through and mess with the sliders/buttons. spacebar or "m" I think turns switches on/off. I know with my rig with optical audio there is a switch that needs to be turned on (can't remember what it's called, like IE958 or something).

---

### Post by xeth_delta on 2007-12-28
> **SidewinderPro2 said:**
> It installed when I click on the icon. I've experimented with everything in the sound options and I still can't get any sound. Anyone have a clue as to how to get sound. (On a good note, I have Compiz running half decently.)

Were you asked for a password when you executed the script from a file manager window?
Why don't you try what I asked you from a terminal. There is a difference between a regular user and the super user / root. Many system administration tasks require root privileges, which are given on a temporary basis for a certain command via sudo. The reason you don't run all the time as an administrator in linux or UNIX-like systems in general, is that it would be a huge security risk. This is different to how many Windows systems are set-up.

Xeth

---

### Post by SidewinderPro2 on 2007-12-28
> **xeth_delta said:**
> Were you asked for a password when you executed the script from a file manager window?
Why don't you try what I asked you from a terminal. There is a difference between a regular user and the super user / root. Many system administration tasks require root privileges, which are given on a temporary basis for a certain command via sudo. The reason you don't run all the time as an administrator in linux or UNIX-like systems in general, is that it would be a huge security risk. This is different to how many Windows systems are set-up.

Xeth

Did that, and I didn't work, command not found. Asked for my password and then it said "Command not found."

---

### Post by xeth_delta on 2007-12-28
> **SidewinderPro2 said:**
> Did that, and I didn't work, command not found. Asked for my password and then it said "Command not found."

You have to execute the command from inside the directory containing the install script, the one created after decompressing **realtek-linux-audiopack-4.07a.tar.bz2**. The directory in question is **realtek-linux-audiopack-4.07**

---

### Post by SidewinderPro2 on 2007-12-28
I'm telling you, it installed when I clicked on the install button. I watched it install through the command prompt, it took a few minutes going through the files and installing this and that. I can set things to Realtek inside the sound settings, but I can't get any sound from the music I am playing. I'm in Vista right now trying to find more driver info.

---

### Post by xeth_delta on 2007-12-28
> **SidewinderPro2 said:**
> I'm telling you, it installed when I clicked on the install button. I watched it install through the command prompt, it took a few minutes going through the files and installing this and that. I can set things to Realtek inside the sound settings, but I can't get any sound from the music I am playing. I'm in Vista right now trying to find more driver info.

Fine, in that case, you might need to add a line to the file **/etc/modprobe.d/alsa-base** about some sound card driver loading options, but you need to know the exact information on your realtek sound card:

Post the output of:
```
lspci
```
and the output lines from
```
dmesg
```
regarding your sound card.

Here you have some extra information on alsa drivers you are using: [http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

---

### Post by SidewinderPro2 on 2007-12-28
First Command gives me this:

> matt@matt-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
02:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTS] (rev a2)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
matt@matt-desktop:~$ 

Interesting (sort of...) that the sound device is an Nvidia but they go and use the Realtek stuff on Windows. Good old Gateway...hope my processor is being used right...


Second Command:
> 
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at c0000000 (gap: bff00000:30100000)
[    0.000000] Built 1 zonelists.  Total pages: 780003
[    0.000000] Kernel command line: root=UUID=86497e79-a917-4f41-bbbc-8093c2487290 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 3013.483 MHz processor.
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Memory: 3106944k/3144576k available (2015k kernel code, 36408k reserved, 916k data, 364k init, 2227072k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.000000]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[    0.000000]       .data : 0xc02f7de6 - 0xc03dce84   ( 916 kB)
[    0.000000]       .text : 0xc0100000 - 0xc02f7de6   (2015 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    0.000000] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[    0.000000] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[    0.000000] hpet0: 3 32-bit timers, 25000000 Hz
[    0.080000] Calibrating delay using timer specific routine.. 6032.55 BogoMIPS (lpj=12065113)
[    0.080000] Security Framework v1.0.0 initialized
[    0.080000] SELinux:  Disabled at boot.
[    0.080000] Mount-cache hash table entries: 512
[    0.080000] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f
[    0.080000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.080000] CPU: L2 Cache: 1024K (64 bytes/line)
[    0.080000] CPU 0(2) -> Core 0
[    0.080000] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f
[    0.080000] Compat vDSO mapped to ffffe000.
[    0.080000] Checking 'hlt' instruction... OK.
[    0.096000] SMP alternatives: switching to UP code
[    0.096000] Early unpacking initramfs... done
[    0.288000] ACPI: Core revision 20070126
[    0.288000] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    0.288000] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 6000+ stepping 03
[    0.288000] SMP alternatives: switching to SMP code
[    0.288000] Booting processor 1/1 eip 3000
[    0.300000] Initializing CPU#1
[    0.380000] Calibrating delay using timer specific routine.. 6026.98 BogoMIPS (lpj=12053976)
[    0.380000] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f
[    0.380000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.380000] CPU: L2 Cache: 1024K (64 bytes/line)
[    0.380000] CPU 1(2) -> Core 1
[    0.380000] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f
[    0.380000] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 6000+ stepping 03
[    0.380000] Total of 2 processors activated (12059.54 BogoMIPS).
[    0.380000] ENABLING IO-APIC IRQs
[    0.380000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.420000] Brought up 2 CPUs
[    0.536000] migration_cost=4000
[    0.536000] Booting paravirtualized kernel on bare hardware
[    0.536000] Time: 16:11:02  Date: 11/28/107
[    0.536000] NET: Registered protocol family 16
[    0.536000] EISA bus registered
[    0.536000] ACPI: bus type pci registered
[    0.540000] PCI: PCI BIOS revision 3.00 entry at 0xfa7a0, last bus=4
[    0.540000] PCI: Using configuration type 1
[    0.540000] Setting up standard PCI resources
[    0.544000] ACPI: EC: Look up EC in DSDT
[    0.548000] ACPI: Interpreter enabled
[    0.548000] ACPI: (supports S0 S3 S4 S5)
[    0.548000] ACPI: Using IOAPIC for interrupt routing
[    0.552000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.552000] PCI: Probing PCI hardware (bus 00)
[    0.552000] PCI: Transparent bridge - 0000:00:04.0
[    0.552000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.556000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.580000] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [LNK4] (IRQs *5 7 9 10 11 14 15)
[    0.580000] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [LNK6] (IRQs *5 7 9 10 11 14 15)
[    0.580000] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 *11 14 15)
[    0.580000] ACPI: PCI Interrupt Link [LIGP] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 *10 11 14 15)
[    0.580000] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 *10 11 14 15)
[    0.580000] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [LSMB] (IRQs *5 7 9 10 11 14 15)
[    0.580000] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)
[    0.580000] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 *10 11 14 15)
[    0.580000] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 *11 14 15)
[    0.584000] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.584000] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.584000] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.584000] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
[    0.584000] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[    0.584000] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0
[    0.584000] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[    0.584000] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0
[    0.584000] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22 23) *0, disabled.
[    0.584000] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[    0.584000] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
[    0.584000] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[    0.584000] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[    0.584000] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[    0.584000] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[    0.584000] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[    0.584000] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.584000] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[    0.584000] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[    0.584000] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.584000] pnp: PnP ACPI init
[    0.584000] ACPI: bus type pnp registered
[    0.588000] pnp: PnP ACPI: found 14 devices
[    0.588000] ACPI: ACPI bus type pnp unregistered
[    0.588000] PnPBIOS: Disabled by ACPI PNP
[    0.588000] PCI: Using ACPI for IRQ routing
[    0.588000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.640000] NET: Registered protocol family 8
[    0.640000] NET: Registered protocol family 20
[    0.640000] pnp: 00:01: ioport range 0x1000-0x107f has been reserved
[    0.640000] pnp: 00:01: ioport range 0x1080-0x10ff has been reserved
[    0.640000] pnp: 00:01: ioport range 0x1400-0x147f has been reserved
[    0.640000] pnp: 00:01: ioport range 0x1480-0x14ff has been reserved
[    0.640000] pnp: 00:01: ioport range 0x1800-0x187f has been reserved
[    0.640000] pnp: 00:01: ioport range 0x1880-0x18ff has been reserved
[    0.640000] pnp: 00:01: ioport range 0x2000-0x207f has been reserved
[    0.640000] pnp: 00:01: ioport range 0x2080-0x20ff has been reserved
[    0.640000] pnp: 00:01: iomem range 0x0-0x0 could not be reserved
[    0.640000] pnp: 00:01: iomem range 0xfefe0000-0xfefe01ff could not be reserved
[    0.640000] pnp: 00:01: iomem range 0xfefe1000-0xfefe10ff could not be reserved
[    0.640000] pnp: 00:01: iomem range 0x0-0x0 could not be reserved
[    0.640000] pnp: 00:0c: iomem range 0xf0000000-0xf3ffffff could not be reserved
[    0.640000] pnp: 00:0d: iomem range 0xf0000-0xfffff could not be reserved
[    0.640000] pnp: 00:0d: iomem range 0xfeff0000-0xfeff00ff could not be reserved
[    0.640000] pnp: 00:0d: iomem range 0xbfee0000-0xbfefffff could not be reserved
[    0.640000] pnp: 00:0d: iomem range 0xffff0000-0xffffffff could not be reserved
[    0.644000] Time: hpet clocksource has been installed.
[    0.644000] Switched to high resolution mode on CPU 0
[    0.644000] Switched to high resolution mode on CPU 1
[    0.668000] PCI: Bridge: 0000:00:04.0
[    0.668000]   IO window: b000-bfff
[    0.668000]   MEM window: fde00000-fdefffff
[    0.668000]   PREFETCH window: fdf00000-fdffffff
[    0.668000] PCI: Bridge: 0000:00:09.0
[    0.668000]   IO window: a000-afff
[    0.668000]   MEM window: f8000000-fbffffff
[    0.668000]   PREFETCH window: e0000000-efffffff
[    0.668000] PCI: Bridge: 0000:00:0b.0
[    0.668000]   IO window: 9000-9fff
[    0.668000]   MEM window: fdd00000-fddfffff
[    0.668000]   PREFETCH window: fdc00000-fdcfffff
[    0.668000] PCI: Bridge: 0000:00:0c.0
[    0.668000]   IO window: 8000-8fff
[    0.668000]   MEM window: fdb00000-fdbfffff
[    0.668000]   PREFETCH window: fda00000-fdafffff
[    0.668000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[    0.668000] PCI: Setting latency timer of device 0000:00:09.0 to 64
[    0.668000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[    0.668000] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[    0.668000] NET: Registered protocol family 2
[    0.712000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.712000] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[    0.712000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.712000] TCP: Hash tables configured (established 131072 bind 65536)
[    0.712000] TCP reno registered
[    0.728000] checking if image is initramfs... it is
[    1.104000] Freeing initrd memory: 7068k freed
[    1.104000] audit: initializing netlink socket (disabled)
[    1.104000] audit(1198858261.644:1): initialized
[    1.104000] highmem bounce pool size: 64 pages
[    1.108000] VFS: Disk quotas dquot_6.5.1
[    1.108000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.108000] io scheduler noop registered
[    1.108000] io scheduler anticipatory registered
[    1.108000] io scheduler deadline registered
[    1.108000] io scheduler cfq registered (default)
[    1.124000] Boot video device is 0000:02:00.0
[    1.124000] PCI: Setting latency timer of device 0000:00:09.0 to 64
[    1.124000] assign_interrupt_mode Found MSI capability
[    1.124000] Allocate Port Service[0000:00:09.0:pcie00]
[    1.124000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[    1.124000] assign_interrupt_mode Found MSI capability
[    1.124000] Allocate Port Service[0000:00:0b.0:pcie00]
[    1.124000] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[    1.124000] assign_interrupt_mode Found MSI capability
[    1.124000] Allocate Port Service[0000:00:0c.0:pcie00]
[    1.124000] isapnp: Scanning for PnP cards...
[    1.476000] isapnp: No Plug & Play device found
[    1.488000] Real Time Clock Driver v1.12ac
[    1.488000] hpet_resources: 0xfeff0000 is busy
[    1.488000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.488000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.488000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.488000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.488000] input: Macintosh mouse button emulation as /class/input/input0
[    1.488000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.488000] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.488000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.488000] mice: PS/2 mouse device common for all mice
[    1.488000] EISA: Probing bus 0 at eisa.0
[    1.488000] Cannot allocate resource for EISA slot 1
[    1.488000] Cannot allocate resource for EISA slot 2
[    1.488000] Cannot allocate resource for EISA slot 8
[    1.488000] EISA: Detected 0 cards.
[    1.488000] TCP cubic registered
[    1.488000] NET: Registered protocol family 1
[    1.492000] Using IPI No-Shortcut mode
[    1.492000]   Magic number: 3:455:187
[    1.492000] Freeing unused kernel memory: 364k freed
[    1.520000] input: AT Translated Set 2 keyboard as /class/input/input1
[    2.668000] AppArmor: AppArmor initialized<5>audit(1198858263.644:2):  type=1505 info="AppArmor initialized" pid=1257
[    2.680000] fuse init (API version 7.8)
[    2.684000] Failure registering capabilities with primary security module.
[    2.716000] ACPI: Fan [FAN] (on)
[    2.752000] ACPI: Thermal Zone [THRM] (40 C)
[    3.100000] usbcore: registered new interface driver usbfs
[    3.100000] usbcore: registered new interface driver hub
[    3.100000] usbcore: registered new device driver usb
[    3.100000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.100000] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[    3.100000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 16
[    3.100000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    3.100000] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    3.100000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[    3.100000] ohci_hcd 0000:00:02.0: irq 16, io mem 0xfe02f000
[    3.104000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    3.104000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    3.128000] SCSI subsystem initialized
[    3.128000] libata version 2.21 loaded.
[    3.176000] usb usb1: configuration #1 chosen from 1 choice
[    3.176000] hub 1-0:1.0: USB hub found
[    3.176000] hub 1-0:1.0: 10 ports detected
[    3.280000] NFORCE-MCP61: IDE controller at PCI slot 0000:00:06.0
[    3.280000] NFORCE-MCP61: chipset revision 162
[    3.280000] NFORCE-MCP61: not 100% native mode: will probe irqs later
[    3.280000] NFORCE-MCP61: BIOS didn't set cable bits correctly. Enabling workaround.
[    3.280000] NFORCE-MCP61: 0000:00:06.0 (rev a2) UDMA133 controller
[    3.280000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[    3.280000] Probing IDE interface ide0...
[    3.584000] usb 1-2: new full speed USB device using ohci_hcd and address 2
[    3.800000] usb 1-2: configuration #1 chosen from 1 choice
[    4.016000] hda: ATAPI DVD A DH16A1P, ATAPI CD/DVD-ROM drive
[    4.108000] usb 1-7: new full speed USB device using ohci_hcd and address 3
[    4.320000] usb 1-7: configuration #1 chosen from 1 choice
[    4.332000] usbcore: registered new interface driver libusual
[    4.332000] Initializing USB Mass Storage driver...
[    4.332000] scsi0 : SCSI emulation for USB Mass Storage devices
[    4.332000] usb-storage: device found at 3
[    4.332000] usb-storage: waiting for device to settle before scanning
[    4.332000] usbcore: registered new interface driver usb-storage
[    4.332000] USB Mass Storage support registered.
[    4.688000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    4.700000] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[    4.700000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 22 (level, low) -> IRQ 17
[    4.700000] PCI: Setting latency timer of device 0000:00:02.1 to 64
[    4.700000] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    4.700000] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[    4.700000] ehci_hcd 0000:00:02.1: debug port 1
[    4.700000] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[    4.700000] ehci_hcd 0000:00:02.1: irq 17, io mem 0xfe02e000
[    4.700000] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.700000] usb 1-2: USB disconnect, address 2
[    4.700000] usb usb2: configuration #1 chosen from 1 choice
[    4.700000] hub 2-0:1.0: USB hub found
[    4.700000] hub 2-0:1.0: 10 ports detected
[    4.804000] sata_nv 0000:00:08.0: version 3.4
[    4.804000] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 21
[    4.804000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSI] -> GSI 21 (level, low) -> IRQ 18
[    4.804000] PCI: Setting latency timer of device 0000:00:08.0 to 64
[    4.804000] scsi1 : sata_nv
[    4.804000] scsi2 : sata_nv
[    4.804000] ata1: SATA max UDMA/133 cmd 0x000109f0 ctl 0x00010bf2 bmdma 0x0001dc00 irq 18
[    4.804000] ata2: SATA max UDMA/133 cmd 0x00010970 ctl 0x00010b72 bmdma 0x0001dc08 irq 18
[    4.812000] hda: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(66)
[    4.812000] Uniform CD-ROM driver Revision: 3.20
[    4.828000] usb 1-7: USB disconnect, address 3
[    5.272000] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.292000] ata1.00: ATA-7: WDC WD5000AAKS-22TMA0, 12.01C01, max UDMA/133
[    5.292000] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    5.308000] ata1.00: configured for UDMA/133
[    5.436000] usb 2-7: new high speed USB device using ehci_hcd and address 3
[    5.568000] usb 2-7: configuration #1 chosen from 1 choice
[    5.568000] scsi3 : SCSI emulation for USB Mass Storage devices
[    5.568000] usb-storage: device found at 3
[    5.568000] usb-storage: waiting for device to settle before scanning
[    5.776000] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.800000] ata2.00: ATA-8: WDC WD2500AAKS-00VYA0, 12.01B02, max UDMA/133
[    5.800000] ata2.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    5.816000] ata2.00: configured for UDMA/133
[    5.816000] scsi 1:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-2 12.0 PQ: 0 ANSI: 5
[    5.816000] scsi 2:0:0:0: Direct-Access     ATA      WDC WD2500AAKS-0 12.0 PQ: 0 ANSI: 5
[    5.816000] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 20
[    5.816000] ACPI: PCI Interrupt 0000:00:08.1[B] -> Link [APSJ] -> GSI 20 (level, low) -> IRQ 19
[    5.816000] PCI: Setting latency timer of device 0000:00:08.1 to 64
[    5.816000] scsi4 : sata_nv
[    5.816000] scsi5 : sata_nv
[    5.816000] ata3: SATA max UDMA/133 cmd 0x000109e0 ctl 0x00010be2 bmdma 0x0001c800 irq 19
[    5.816000] ata4: SATA max UDMA/133 cmd 0x00010960 ctl 0x00010b62 bmdma 0x0001c808 irq 19
[    5.872000] usb 1-2: new full speed USB device using ohci_hcd and address 4
[    6.096000] usb 1-2: configuration #1 chosen from 1 choice
[    6.128000] ata3: SATA link down (SStatus 0 SControl 300)
[    6.448000] ata4: SATA link down (SStatus 0 SControl 300)
[    6.456000] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[    6.456000] ACPI: PCI Interrupt 0000:01:09.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 20
[    6.456000] PCI: Setting latency timer of device 0000:01:09.0 to 64
[    6.508000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[fdeff000-fdeff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    6.508000] sd 1:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[    6.508000] sd 1:0:0:0: [sda] Write Protect is off
[    6.508000] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.508000] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.508000] sd 1:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[    6.508000] sd 1:0:0:0: [sda] Write Protect is off
[    6.508000] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.508000] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.508000]  sda: sda1 sda2
[    6.516000] sd 1:0:0:0: [sda] Attached SCSI disk
[    6.516000] sd 2:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[    6.516000] sd 2:0:0:0: [sdb] Write Protect is off
[    6.516000] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    6.516000] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.516000] sd 2:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[    6.516000] sd 2:0:0:0: [sdb] Write Protect is off
[    6.516000] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    6.516000] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.516000]  sdb: sdb1 sdb2 < sdb5 >
[    6.548000] sd 2:0:0:0: [sdb] Attached SCSI disk
[    6.552000] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    6.552000] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    6.756000] Attempting manual resume
[    6.756000] swsusp: Resume From Partition 8:21
[    6.756000] PM: Checking swsusp image.
[    6.756000] PM: Resume from disk failed.
[    6.792000] kjournald starting.  Commit interval 5 seconds
[    6.792000] EXT3-fs: mounted filesystem with ordered data mode.
[    7.780000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00000ae6ffc22966]
[   10.572000] usb-storage: device scan complete
[   10.576000] scsi 3:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   10.580000] scsi 3:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   10.584000] scsi 3:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   10.584000] scsi 3:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   10.588000] sd 3:0:0:0: [sdc] Attached SCSI removable disk
[   10.588000] sd 3:0:0:0: Attached scsi generic sg2 type 0
[   10.588000] sd 3:0:0:1: [sdd] Attached SCSI removable disk
[   10.588000] sd 3:0:0:1: Attached scsi generic sg3 type 0
[   10.592000] sd 3:0:0:2: [sde] Attached SCSI removable disk
[   10.592000] sd 3:0:0:2: Attached scsi generic sg4 type 0
[   10.592000] sd 3:0:0:3: [sdf] Attached SCSI removable disk
[   10.592000] sd 3:0:0:3: Attached scsi generic sg5 type 0
[   10.884000] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   10.884000] i2c-adapter i2c-1: nForce2 SMBus adapter at 0xf400
[   10.968000] usbcore: registered new interface driver xpad
[   10.968000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   11.048000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   11.048000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.108000] input: PC Speaker as /class/input/input2
[   11.196000] ACPI: PCI Interrupt Link [APC6] enabled at IRQ 16
[   11.196000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [APC6] -> GSI 16 (level, low) -> IRQ 21
[   11.196000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   11.196000] sky2 0000:03:00.0: v1.18 addr 0xfddfc000 irq 21 Yukon-FE (0xb7) rev 3
[   11.196000] sky2 eth0: addr 00:1b:b9:72:0f:5a
[   11.228000] Linux agpgart interface v0.102 (c) Dave Jones
[   11.368000] nvidia: module license 'NVIDIA' taints kernel.
[   11.620000] ACPI: PCI Interrupt Link [APC8] enabled at IRQ 16
[   11.620000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [APC8] -> GSI 16 (level, low) -> IRQ 21
[   11.620000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   11.620000] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.07  Thu Dec 13 18:42:56 PST 2007
[   11.736000] input: PS/2 Logitech TrackMan as /class/input/input3
[   11.740000] parport_pc 00:09: reported by Plug and Play ACPI
[   11.740000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   11.768000] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
[   11.768000] ACPI: PCI Interrupt 0000:00:05.0[B] -> Link [AAZA] -> GSI 23 (level, low) -> IRQ 16
[   11.768000] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   11.976000] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   12.208000] lp0: using parport0 (interrupt-driven).
[   12.256000] Adding 9124880k swap on /dev/sdb5.  Priority:-1 extents:1 across:9124880k
[   12.660000] EXT3 FS on sdb1, internal journal
[   13.348000] input: Power Button (FF) as /class/input/input4
[   13.348000] ACPI: Power Button (FF) [PWRF]
[   13.348000] input: Power Button (CM) as /class/input/input5
[   13.348000] ACPI: Power Button (CM) [PWRB]
[   13.460000] No dock devices found.
[   13.648000] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual Core Processor 6000+ processors (version 2.00.00)
[   13.648000] powernow-k8:    0 : fid 0x16 (3000 MHz), vid 0x8
[   13.648000] powernow-k8:    1 : fid 0x14 (2800 MHz), vid 0xa
[   13.648000] powernow-k8:    2 : fid 0x12 (2600 MHz), vid 0xc
[   13.648000] powernow-k8:    3 : fid 0x10 (2400 MHz), vid 0xe
[   13.648000] powernow-k8:    4 : fid 0xe (2200 MHz), vid 0x10
[   13.648000] powernow-k8:    5 : fid 0xc (2000 MHz), vid 0x10
[   13.648000] powernow-k8:    6 : fid 0xa (1800 MHz), vid 0x10
[   13.648000] powernow-k8:    7 : fid 0x2 (1000 MHz), vid 0x12
[   14.324000] ppdev: user-space parallel port driver
[   14.420000] audit(1198876274.999:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5202 profile="/usr/sbin/cupsd"
[   14.456000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   14.456000] apm: disabled - APM is not SMP safe.
[   14.556000] sky2 eth0: enabling interface
[   15.240000] Failure registering capabilities with primary security module.
[   15.388000] Bluetooth: Core ver 2.11
[   15.388000] NET: Registered protocol family 31
[   15.388000] Bluetooth: HCI device and connection manager initialized
[   15.388000] Bluetooth: HCI socket layer initialized
[   15.400000] Bluetooth: L2CAP ver 2.8
[   15.400000] Bluetooth: L2CAP socket layer initialized
[   15.404000] Bluetooth: RFCOMM socket layer initialized
[   15.404000] Bluetooth: RFCOMM TTY layer initialized
[   15.404000] Bluetooth: RFCOMM ver 1.8
[   16.240000] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[   16.500000] Clocksource tsc unstable (delta = -333099996 ns)
[   16.908000] NET: Registered protocol family 10
[   16.908000] lo: Disabled Privacy Extensions
[   20.620000] NET: Registered protocol family 17
[   33.192000] eth0: no IPv6 routers present
matt@matt-desktop:~$ 


:lolflag: Enough info, or do you need my SS#? I'll look for stuff on Nvidia's site for that card. 

Edit: It appears that some smiles are automatically being put into the above code

---

### Post by xeth_delta on 2007-12-28
SidewinderPro2, you must understand that if I ask you for more information, is because I am trying to help you get that card working. So, I really don't think any sarcasm is necessary. I imagine you are impatient, but you have to help us help you. :)

If you have a look at the output you get from dmesg, you will notice the following line:

```
[ 11.976000] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
```

That means that there are some problems while trying to load the module for the codec in question, ALC883. This is most likely due to misconfiguration, as I have been able to see in other cases.

The fact that you need some realtek related drivers, even though you have an nVidia chipset is because the codec is provided by Realtek, if I am not mistaken.

Now, to the configuration issue. Make a back-up of the file **/etc/modprobe.d/alsa-base**. Open the original file with your favourite text editor, with administrative privileges. Look for a line like this:

```
options snd-hda-intel model=auto
```

If there isn't such a line, add it to the end. Try changing **model** to the options illustrated in **realtek-linux-audiopack-4.07a/alsa-driver-rt20071002/sound/Documentation/ALSA-Configuration.txt** for your codec (ALC883), since **auto** does not seem to work on your machine. Here is an excerpt from said file:

```
ALC883/888
          3stack-dig    3-jack with SPDIF I/O
          6stack-dig    6-jack digital with SPDIF I/O
          3stack-6ch    3-jack 6-channel
          3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
          6stack-dig-demo  6-jack digital for Intel demo board
          acer          Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
          acer-aspire   Acer Aspire 9810
          medion        Medion Laptops
          medion-md2    Medion MD2
          targa-dig     Targa/MSI
          targa-2ch-dig Targs/MSI with 2-channel
          laptop-eapd   3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
          lenovo-101e   Lenovo 101E
          lenovo-nb0763 Lenovo NB0763
          lenovo-ms7195-dig Lenovo MS7195
          haier-w66     Haier W66
          6stack-hp     HP machines with 6stack (Nettle boards)
          3stack-hp     HP machines with 3stack (Lucknow, Samba boards)
          auto          auto-config reading BIOS (default)

```

After a change restart and try (better try an audio file first, before your CD), as I have seen an alsa reinitialization might not be enough. I recommend you to start with the option model=acer.

You might be questioning now why you are trying to configure for hda_intel. I might be in fact wrong, but the way I see it is that several chipsets mught be using the same codec provided by a certain company, for instance Realtek, Sigmatel, etc, and it is coded one time in the drivers, with the possibility of sharing the same module with different chipsets. I kindly ask anybody to correct me if I am wrong.

To make sure that snd_hda_intel is being loaded, please run the following and post the output:
```
lsmod | grep -i snd
```
Good luck, let us know how it's going.

P.S.: the smileys appear in your post because the text was placed as quote and not as code.

---

### Post by SidewinderPro2 on 2007-12-29
The snd_hda_intel check brings me this, which I think means its working:

```
matt@matt-desktop:~$ lsmod | grep -i snd
snd_hda_intel         263712  1 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
matt@matt-desktop:~$ 
```

I found the alsa-base file, but it was read only under root permissions, so it wouldn't let me save it. Also, the line of code was absent from the file. How can I edit the file and is there anywhere in particular that I should place the line of code?


Thanks

Side

---

### Post by xeth_delta on 2007-12-29
> **SidewinderPro2 said:**
> The snd_hda_intel check brings me this, which I think means its working:

```
matt@matt-desktop:~$ lsmod | grep -i snd
snd_hda_intel         263712  1 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
matt@matt-desktop:~$ 
```

I found the alsa-base file, but it was read only under root permissions, so it wouldn't let me save it. Also, the line of code was absent from the file. How can I edit the file and is there anywhere in particular that I should place the line of code?


Thanks

Side

Modules are being loaded, that's good. You have to run your text editor as root. To do so, from a terminal:
```
gksudo gedit /etc/modprobe.d/alsa-base
```

You will be asked for your password. You are most welcome! Give it a try and let us know how it goes.

Xeth

---

### Post by SidewinderPro2 on 2007-12-29
I will give it a whirl once I get back into Ubuntu. I have to get a certain dosage of Crysis and Quake Wars each day to keep my shooter addiction in check. 

I'm starting to find Linux pretty interesting now. I was able to download a free version of Quake III, which no longer works with Vista.

---

### Post by SidewinderPro2 on 2007-12-30
No luck, I've tried a few of the options that would have any relation to my sound card and I still can't get anything. Any other ideas?

---

### Post by xeth_delta on 2007-12-30
Did you restart after the changes? A few days ago anoher forum member had a similar problem with a custom build laptop. Using "acer" did the trick for him. I'd say try the other options shown in a previous post for the ALC883 codec.

I am not sure if this will help, but try adding the following to the end of your /etc/modprobe.d/alsa-base file:

```
install snd-hda-intel position_fix=1 /sbin/modprobe --ignore-install snd-hda-intel $CMDLINE_OPTS
```

Xeth

---

### Post by SidewinderPro2 on 2007-12-31
That didn't work either. I have been restarting the computer every time I apply new changes, bu to no avail. The guys at the Nvidia forums were no help at all. I looked through the ALSA wiki for driver support for the Nvidia, but I really didn't understand the coding and commands so I didn't mess around with it. I'm not even sure that is what is the cause of the no sound.

Is there any other way to approach this sound problem? I'm beginning to consider going in my storage room and hunting down a SoundBlaster 5.1 Live. I don't want to install a soundcard unless I really have to because it will interfere with the air intake of my monster video card (got it up to 71 degrees Celsius the other day :lolflag: )

---

### Post by g2g591 on 2007-12-31
if only your realtek card would work like mine did,  **_Don't give up_**, you'll find installing most things is very very easy. Just check a box in Synaptic package manager or sudo apt-get install someprogram .

---

### Post by SidewinderPro2 on 2007-12-31
> **g2g591 said:**
> if only your realtek card would work like mine did,  **_Don't give up_**, you'll find installing most things is very very easy. Just check a box in Synaptic package manager or sudo apt-get install someprogram .

Its the only thing that won't work for me right now hardware wise. I have Compiz Fusion running really sweet. The internet connection was done automatically and works perfectly, which is something that takes a little while on Windows for my network. I was able to get the Nvidia drivers going well with Envy too. Its just the sound thats not working.

---

### Post by SidewinderPro2 on 2008-01-04
Got it all working myself. The Nvidia drivers are working well and so does the sound. The alsamixer was muting everything.



BTW, gtg, Windows isn't malware. XP and 98SE own and pwn...

However, if you're just taking Vista into account, then you have my backing :lolflag:
Now that is a fine example of malware.

---

