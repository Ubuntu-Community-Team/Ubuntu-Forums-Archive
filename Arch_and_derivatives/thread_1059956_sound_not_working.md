---
title: "sound not working"
date: 2009-02-04
forum: Arch and derivatives
---

### Post by stonecoldjha on 2009-02-04
i logged in as non-root user and then went to the terminal,and typed in 
"alsamixer" to configure sound settings.but,the following was the output:

[sonujha@arch ~]$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory
[sonujha@arch ~]$ 


i have configured my sound card as per the instructions on the arch's beginner's guide i found at [http://archlinux.org](http://archlinux.org).

What's wrong,and how do i fix this?

---

### Post by smartboyathome on 2009-02-04
You sure you have the correct driver installed for your sound card? What card is it, by the way?

---

### Post by sisco311 on 2009-02-04
Did you add your user to the 'audio' group?

---

### Post by stonecoldjha on 2009-02-04
i believe i have installed the proper driver.i did add my user to audio group.

---

### Post by sisco311 on 2009-02-04
You have to log out and log back in after you added the user to the audio group. Did you try to run alsamixer as root?

What's the output of:
```
aplay -l
lspci -v
lsmod | grep snd
```

---

### Post by stonecoldjha on 2009-02-04
the output of the first and last commands were as follows:

[sonujha@arch ~]$ aplay -l
aplay: device_list:217: no soundcards found...
[sonujha@arch ~]$ lsmod | grep snd
snd_page_alloc         10120  0 
[sonujha@arch ~]$ 


the output of the second command was:

[sonujha@arch ~]$ lspci -v
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
	Subsystem: ASRock Incorporation Device 2770
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: fc000000-febfffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: ASRock Incorporation Device 0888
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at fbefc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Prefetchable memory behind bridge: 00000000cff00000-00000000cfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fbf00000-fbffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
	Subsystem: ASRock Incorporation Device 27c8
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at d480 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
	Subsystem: ASRock Incorporation Device 27c9
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at d800 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
	Subsystem: ASRock Incorporation Device 27ca
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at d880 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
	Subsystem: ASRock Incorporation Device 27cb
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at dc00 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
	Subsystem: ASRock Incorporation Device 27cc
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at fbefbc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
	Subsystem: ASRock Incorporation Device 27b8
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-rng, iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
	Subsystem: ASRock Incorporation Device 27df
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ffa0 [size=16]
	Kernel driver in use: ata_piix
	Kernel modules: piix, ata_piix

00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: ASRock Incorporation Device 27c0
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at d400 [size=8]
	I/O ports at d080 [size=4]
	I/O ports at d000 [size=8]
	I/O ports at cc00 [size=4]
	I/O ports at c880 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
	Subsystem: ASRock Incorporation Device 27da
	Flags: medium devsel, IRQ 19
	I/O ports at 0400 [size=32]
	Kernel driver in use: i801_smbus
	Kernel modules: i2c-i801

01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
	Subsystem: ASRock Incorporation Device 8136
	Flags: bus master, fast devsel, latency 0, IRQ 764
	I/O ports at e800 [size=256]
	Memory at fbfff000 (64-bit, non-prefetchable) [size=4K]
	Expansion ROM at fbfc0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

03:00.0 VGA compatible controller: nVidia Corporation NV44 [GeForce 6200 TurboCache(TM)] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: XFX Pine Group Inc. Device 2147
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fc000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at febe0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

[sonujha@arch ~]$ clear

[sonujha@arch ~]$ aplay -l
aplay: device_list:217: no soundcards found...
[sonujha@arch ~]$ lsmod | grep snd
snd_page_alloc         10120  0 
[sonujha@arch ~]$ clear



















[sonujha@arch ~]$ lspci -v
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
	Subsystem: ASRock Incorporation Device 2770
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: fc000000-febfffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: ASRock Incorporation Device 0888
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at fbefc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Prefetchable memory behind bridge: 00000000cff00000-00000000cfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fbf00000-fbffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
	Subsystem: ASRock Incorporation Device 27c8
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at d480 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
	Subsystem: ASRock Incorporation Device 27c9
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at d800 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
	Subsystem: ASRock Incorporation Device 27ca
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at d880 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
	Subsystem: ASRock Incorporation Device 27cb
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at dc00 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
	Subsystem: ASRock Incorporation Device 27cc
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at fbefbc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
	Subsystem: ASRock Incorporation Device 27b8
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-rng, iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
	Subsystem: ASRock Incorporation Device 27df
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ffa0 [size=16]
	Kernel driver in use: ata_piix
	Kernel modules: piix, ata_piix

00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: ASRock Incorporation Device 27c0
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at d400 [size=8]
	I/O ports at d080 [size=4]
	I/O ports at d000 [size=8]
	I/O ports at cc00 [size=4]
	I/O ports at c880 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
	Subsystem: ASRock Incorporation Device 27da
	Flags: medium devsel, IRQ 19
	I/O ports at 0400 [size=32]
	Kernel driver in use: i801_smbus
	Kernel modules: i2c-i801

01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
	Subsystem: ASRock Incorporation Device 8136
	Flags: bus master, fast devsel, latency 0, IRQ 764
	I/O ports at e800 [size=256]
	Memory at fbfff000 (64-bit, non-prefetchable) [size=4K]
	Expansion ROM at fbfc0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

03:00.0 VGA compatible controller: nVidia Corporation NV44 [GeForce 6200 TurboCache(TM)] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: XFX Pine Group Inc. Device 2147
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fc000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at febe0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

[sonujha@arch ~]$

---

### Post by sisco311 on 2009-02-04
load the module.
as root:
```
modprobe snd-hda-intel
```

---

### Post by stonecoldjha on 2009-02-04
i did the following:
#modprobe snd-hda-intel
and got the following output:

FATAL:Error inserting snd-hda-intel(/lib/modules/2.6.28-ARCH/kernel/sound/pci/hda/snd-hda-intel.ko):Unknown symbol in modules or unknown parameter(see dmesg)

---

### Post by smartboyathome on 2009-02-04
I am using the same driver, and got no such problems. Seems like a corrupt module.

---

### Post by Sunflower1970 on 2009-02-04
I'm in the middle of installing Arch myself and ran into this problem last night. Did you run alsaconf as root already? That was my problem. Once I ran it, my sound worked as it should.

---

### Post by stonecoldjha on 2009-02-04
so,what should i do now?

---

### Post by Sunflower1970 on 2009-02-04
After I ran alsaconf and it set up my soundcard, I then reopened alsamixer just to make sure all my levels were set, then I ran the soundfile: 
$ aplay /usr/share/sounds/alsa/Front_Center.wav
and everything seemed to work fine. Then I added alsa to the DAEMONS section in /etc/rc.conf.

Hopee that works for you... :)

---

### Post by wolfvorkian1 on 2009-02-04
> **Sunflower1970 said:**
> After I ran alsaconf and it set up my soundcard, I then reopened alsamixer just to make sure all my levels were set, then I ran the soundfile: 
$ aplay /usr/share/sounds/alsa/Front_Center.wav
and everything seemed to work fine. Then I added alsa to the DAEMONS section in /etc/rc.conf.

Hopee that works for you... :)

Do you have sound after a reboot? I do on a desktop but not on an old laptop that I'm playing with. The command  # alsactl store  doesn't help the problem. Alsaconf finds the card and works for me until I reboot. Then nothing. I have to run alsaconf again to have sound.

---

### Post by Sunflower1970 on 2009-02-04
Yes, I do have sound afterwards. I'm using Arch on an old PII desktop. Not sure what the soundcard is at the moment (I'm at work). Never tried putting Arch on my laptop...

Did you try the part in the Archlinux beginner's guide about having snd_pcsp load after alsamixer? (here: [http://wiki.archlinux.org/index.php/Beginners_Guide#Configure_sound_with_alsamixer](http://wiki.archlinux.org/index.php/Beginners_Guide#Configure_sound_with_alsamixer)) Or have you tried blacklisting it? (also in the above link?) 

Found this on troubleshooting too: [http://wiki.archlinux.org/index.php/ALSA#Troubleshooting](http://wiki.archlinux.org/index.php/ALSA#Troubleshooting)

---

### Post by wolfvorkian1 on 2009-02-04
> **Sunflower1970 said:**
> Yes, I do have sound afterwards. I'm using Arch on an old PII desktop. Not sure what the soundcard is at the moment (I'm at work). Never tried putting Arch on my laptop...

Did you try the part in the Archlinux beginner's guide about having snd_pcsp load after alsamixer? (here: [http://wiki.archlinux.org/index.php/Beginners_Guide#Configure_sound_with_alsamixer](http://wiki.archlinux.org/index.php/Beginners_Guide#Configure_sound_with_alsamixer)) Or have you tried blacklisting it? (also in the above link?) 

Found this on troubleshooting too: [http://wiki.archlinux.org/index.php/ALSA#Troubleshooting](http://wiki.archlinux.org/index.php/ALSA#Troubleshooting)

Yes, I've tried all of those and they didn't solve the problem. I've spent quit a bit of time googling and just got through trying a technique a debian user used to fix his but still no go here. 

What was odd was the first time I tried Front_Center.wav while installing it worked. I went ahead and put X on and loaded some programs and then hit the hay. Next morning, no sound. I first figured maybe the kernel upgrade had hosed it but after examining the packman log, it was apparent that wasn't what did it. Never dawned on me that shutting the machine off was the culprit until I stumbled across it while googling. Only way I've been able to get sound back is by using the alsaconf script but it won't stick and  googling again has told me this is a common problem with this script. I don't know where to go next except back to google or to just forget about it. Sound and everything works fine in XP, maybe this laptop is doomed to always be a windows machine. Wireless card works flawlessy too in XP but is a hassle in Linux and may not even be possible to ever get configured. 

Thanks for the reply.

---

### Post by handy on 2009-02-04
***@wolfvorkian1:***  I wonder if you can call the script in ~/.xinitrc ?

Give it a try, if that works then it will initialise sound for you every time you boot, which I'm sure will make you happy. :-) 

Make sure you put an "&" after the command or your .xinitrc won't work properly.

---

### Post by wolfvorkian1 on 2009-02-04
> **handy said:**
> ***@wolfvorkian1:***  I wonder if you can call the script in ~/.xinitrc ?

Give it a try, if that works then it will initialise sound for you every time you boot, which I'm sure will make you happy. :-) 

Make sure you put an "&" after the command or your .xinitrc won't work properly.

Thanks Handy. This alsaconf "script" though is one which requires manual intervention. You have to tell it to do this and that and my expertise with these machines isn't much more than being able to hit the button to start them and to click a mouse. ;)

Most of the "fixes" I've googled seem to revolve around modules. The few success stories come from blacklisting certain ones and I've done that 'til I'm blue in the face. So, I gotta keep googling until I find another fix, *if* there is one. It takes maybe a couple of minutes to run this alsaconf program, so I can always do it if I can't ever find one but not having something 'right' bothers me.

---

### Post by handy on 2009-02-05
If it's not a notebook, you could stick another sound card in it.

PCI sound cards are very cheap brand new, let alone what you might find 2nd hand.  For $5- you could be out of trouble. 

Just a thought.

---

### Post by wolfvorkian1 on 2009-02-06
> **handy said:**
> If it's not a notebook, you could stick another sound card in it.

PCI sound cards are very cheap brand new, let alone what you might find 2nd hand.  For $5- you could be out of trouble. 

Just a thought.

Those inexpensive PCI cards work fine for a desktop. I found the cheapest one available at Newegg a couple years ago and it is still going strong on an old desktop. 

Arch simply doesn't like the audio card ( Maestro3 ESS....) on this little laptop I'm finding out. Why, I just don't know and that is after hours of googling but Puppy finds it instantly and sends out sound. Arch though does like the cheapy card I mentioned and also likes a vanilla intel onboard on another old desktop. Arch hated the onboard video card on the 2 old desktops ( gparted live cd's too) but loves an old Nvidia. I'm finding out that matching the hardware and distributions up are more important than I originally realized. 

I quit using Mutt basically because of the hassle of cutting and pasting like you were asking about with Nano. So easy with a mouse but trying to remember the keyboard combinaions was a pia. I was never able to get the mouse to work in Nano but I never tried that hard either. 

But thanks anyhow for the suggestion. I appreciate any and all suggestions concerning the audio glitch I got on this like brand new 6 year old laptop that I got for exactly the right price. Zero dollars.

---

### Post by handy on 2009-02-06
You might be very lucky & find a cheap 2nd hand external sound module that plugs in via USB.

---

### Post by MisfitI38 on 2009-02-06
> **handy said:**
> ***@wolfvorkian1:***  I wonder if you can call the script in ~/.xinitrc ?

Give it a try, if that works then it will initialise sound for you every time you boot, which I'm sure will make you happy. :-) 

Make sure you put an "&" after the command or your .xinitrc won't work properly.
Just fyi- putting a script in .xinitrc will run it when starting X, not upon boot. ;)
You could put last minute scripts in /etc/rc.local. In this case, however, alsaconf is not a script which can be run at boot, (unless you want to run through an interactive ncurses program which probes for hardware and attempts to configure your soundcard.) ;)

---

### Post by handy on 2009-02-06
Thanks MisfitI38.

Forgive my inappropriate use of the terminology, but hey, I'll always be a beginner at this Linux stuff. :-)

---

### Post by MisfitI38 on 2009-02-06
> **handy said:**
> Thanks MisfitI38.

Forgive my inappropriate use of the terminology, but hey, I'll always be a beginner at this Linux stuff. :-)

lol. It is I who should be sorry, since you obviously knew what I posted, and merely erred in your terminology..
I'll always be a beginner too..why do you think I contributed so much to the *beginners guide*.

---

### Post by handy on 2009-02-06
> **MisfitI38 said:**
> lol. It is I who should be sorry, since you obviously knew what I posted, and merely erred in your terminology..
I'll always be a beginner too..why do you think I contributed so much to the *beginners guide*.

I'm sure that we ALL thank you for your extremely helpful contributions in the guide & elsewhere. 

If I don't keep looking at this stuff, I will VERY quickly forget the little that I do know. :-|  Occasionally being of use to someone else is a nice bonus. ;-)

---

### Post by wolfvorkian1 on 2009-02-08
> **handy said:**
> I'm sure that we ALL thank you for your extremely helpful contributions in the guide & elsewhere. 

If I don't keep looking at this stuff, I will VERY quickly forget the little that I do know. :-|  Occasionally being of use to someone else is a nice bonus. ;-)

Misfit certainly does have a unique talent for writing very clear directions. He is able to not make the mistake that many make ( unconsciously I believe) in leaving out a step that a non-computer literate fellow might not know. 

But Hallelujah Hardy, I found a fix for the laptop! The short of a very long was the addition of a line to my ~/.xinitrc file like you suggested except it was this.

```
aumix -v0 && aumix -v100 & 
```Get it? ;) All it does is mute sound and then unmute it . 

What I finally stumbled across after trying a zillion different fixes was that even though both alsamixer and aumix showed everything unmuted after a reboot, they were lying. 

Just for the hell of it, (sort of a last resort attempt) I muted and then unmuted a sound mixer and sound played without running alsaconf again! Actually alsaconf isn't needed, there is a glitch apparently in the Alsa program that does this on some machines during the booting process.Sound is muted but the mixers don't show this. My problem had nothing to do with modules or adding options to certain modprobe files. I tried them all I think. 

So I've got a work around. I have no idea if there is any hope to ever get it fixed correctly. Already a lot of bug reports sent in.

---

### Post by handy on 2009-02-08
That's great news wolfvorkian1. :-D

---

