---
title: "Experiments in refit shell to enable 9400M on MBP 5,1"
date: 2009-02-21
forum: Apple Hardware Users
---

### Post by alexmurray on 2009-02-21
So I've been experimenting with the refit shell to see if its possible to enable the 9400M instead of the 9600M GT.

The refit shell is part of the standard refit installation and you can load it by choosing the little terminal icon from the refit menu when you first boot. The following will walk you through using the shell to try and activate the 9400M on the MBP 5,1. 

**<disclaimer>Warning: If you are not very familiar with things like hex editors and low level stuff, or if you are just careless, you could mess with your EFI in a bad way, so please proceed with caution (if you are careful and know what you're doing it is perfectly safe).</disclaimer>**.

First thing to know if you're using the shell is that most shell commands can take the option **-b** which means to break each output page. They all also take the option **-?** which means to show a help page about the command. ie. from the refit shell do:

```

help -? -b

```

to get info about the help command or you can just do

```

help -b

```

which will show you all the different commands the shell supports. The first one to look at is

```

pci -b

```

which will show us that we can see both display controllers (9400 & 9600) with pci id's **00 02 00 00** and **00 03 00 00** respectively.

If we do

```

pci 00 02 00 -i

```

we find that the 9400M just has 0xFF for all values, and so I think is not power up maybe, whereas the 9600M GT has some sane information.

The next thing we can do is get a list of all the efi devices:

```

devices -b

```

Which again lists the 2 video controllers with handles **e5** and **e7** respectively. You can get some more info by doing:

```

dh -b e5

```

and same for e7 - this seems to show that handle e7 is being used as the active graphics card (which is the 9600M GT from what I can tell).

Next we can see all the EFI variables with

```

dmpstore -b

```

and there are 2 pretty interesting ones there - **gpu-power-prefs** and **LEGACYVGAHANDLE**. If you look carefully you'll notice that the value of **LEGACYVGAHANDLE** (on my machine it is **18 4A 6D 7E 00 00 00 00** - where the first 4 bytes are the same as the handle shown when you do a **dh -b e7** - 7E6D4A18 - but just in reverse byte order since it's little endian). The other thing to note is that **gpu-power-prefs** is stored in NVRAM (indicated by the NV) whereas **LEGACYVGAHANDLE** is not, and from what I've been able to gather **LEGACYVGAHANDLE** gets set as a result of the value of **gpu-power-prefs**. The default value of **gpu-power-prefs** is **01 00 00 00** (ie 1) and I've been experimenting with different values to see if we can get the 9400M powered up at boot (since I assume it is powered down normally).

You can use **dmpstore** to save a variable to a file or to load a variable from a file, so we can use this to change the values of these variables. So try something like the following to save the original value of **gpu-power-prefs** to a file and edit a copy of the file to set a new value from:

```

dmpstore gpu-power-prefs -s fs0:\gpu-power-prefs.orig
cp fs0:\gpu-power-prefs.orig fs0:\gpu-power-prefs
hexedit fs0:\gpu-power-prefs

```

now change the **01 00 00 00** and the end of the file to **00 00 00 00** (ie effectively change the value from 1 to 0). You can check that you didn't make any major screwups by doing a:

```

comp fs0:\gpu-power-prefs.orig fs0:\gpu-power-prefs

```

and it should show just a single byte change from 01 to 00.

We can now set the value of gpu-power-prefs to our new value by using **dmpstore** again:

```

dmpstore gpu-power-prefs -l fs0:\gpu-power-prefs

```

So with this new value you can exit the shell and power on and off the machine. Now go back into the shell and do a **dmpstore gpu-power-prefs** and you'll see its got your new value of **00 00 00 00** AND if you do a **dmpstore legacyvgahandle** you can see the handle should now be changed to that of the device e5 (ie the 9400M) instead of the device e7 (the 9600M GT). 

So at this point it looks like we've got the 9400M enabled as the legacy mode GPU - YAY - BUT unfortunately though when I then go and boot into Ubuntu it still only lists the 9600M GT and there is still no sign of the 9400M.

So after all that I still can't seem to get it to use the 9400M over the 9600M GT - I've posted the instructions here though in case anyone else can get further with it or wants to experiment more.

---

### Post by pxwpxw on 2009-02-21
> **alexmurray said:**
> So I've been experimenting with the refit shell to see if its possible to enable the 9400M instead of the 9600M GT.


So after all that I still can't seem to get it to use the 9400M over the 9600M GT - I've posted the instructions here though in case anyone else can get further with it or wants to experiment more.

Hi, very interesting/useful. 

Question - is grub legacy pc-bios ubuntu linux boot actually using EFI legacyvgahandle. 

But thanks for the info on using EFI shell, can use some of that to look at grub.efi booting video and other issues. I have only single video display MBP4,1/iMac8.1, not much help for your topic,

---

### Post by poliocough on 2009-02-21
Interesting thread. I got MB 5.1 (not pro). I think I might be having only one graphics card?

One thing I wanted to ask - where do the commands "pci" and "devices" come from?
I don't have them by default. I searched for them with the Synaptic thing and it returned way too much stuff...

---

### Post by alexmurray on 2009-02-22
The commands are in the refit shell - not in Ubuntu - if you've got refit installed, when you power on, instead of selecting Linux to boot, choose the little terminal icon on the second row which will drop you into the refit shell.

---

### Post by cyberdork33 on 2009-02-22
> **pxwpxw said:**
> Question - is grub legacy pc-bios ubuntu linux boot actually using EFI legacyvgahandle. This is what I was thinking too. It may be that the legacy loader ignores these, or even sets them "appropriately" when it is activated.

I bet if you boot from EFI that Alex's method would work. You might at least be able to get to a commandline and do lspci to see if the device is seen in Linux (that is if you have a working keyboard).

> **pxwpxw said:**
> But thanks for the info on using EFI shell, can use some of that to look at grub.efi booting video and other issues. I have only single video display MBP4,1/iMac8.1, not much help for your topic,and on that note, I wanted to point out that there is a command to change the resolution in the efi terminal, so you can see a bit more at once.

> **alexmurray said:**
> The commands are in the refit shell - not in Ubuntu - if you've got refit installed, when you power on, instead of selecting Linux to boot, choose the little terminal icon on the second row which will drop you into the refit shell.
Yes, and I think that a warning is in order to users that do not know what they are doing. If you are not careful, you may be able to change some EFI variable that causes problems with your machine. Happy Hacking.

---

### Post by Nikos.Alexandris on 2009-03-24
Great experiment. Hopefully it will be useful at some point.

> **alexmurray said:**
> The commands are in the refit shell - not in Ubuntu - if you've got refit installed, when you power on, instead of selecting Linux to boot, choose the little terminal icon on the second row which will drop you into the refit shell.

I can't see any terminal icon!? Out of my memory I have only OSX, Linux and on the bottom row there are 4 icons. The terminal is missing. I 've checked the refit.conf file and there is no disabled shell option or similar.

Is it supposed to appear by default?

Cheers, Nikos

---

### Post by Nikos.Alexandris on 2009-03-24
Interesting: **...switch between graphics processors on the "Unibody" MacBook Pro without restarting?**

[http://i.gizmodo.com/5067433/confirmed-apple-can-enable-dual-gpu-and-on+the+fly-switching-in-macbook-pro]("http://i.gizmodo.com/5067433/confirmed-apple-can-enable-dual-gpu-and-on+the+fly-switching-in-macbook-pro")

> [...]
It can support up to 8GB of RAM. It can do on-the-fly GPU switching. And it can work together with the MacBook Pro's discrete 9600M GT. But it doesn't do any of those things. Yet.
[...]
But since it's Apple it's also entirely possible we'll never see any of this to come to pass...
[...]

Imagine that Linux can make the break-through :-) Imagine that Linux will make the break-through :D

Common, let's set-up a project to attract dev's on it. There are many geeks who like apple-machines out there.

Cheers, Nikos
---

Look also at [http://www.everymac.com/systems/apple/macbook_pro/macbook-pro-unibody-faq/macbook-pro-unibody-switching-between-graphics-processors.html]("http://www.everymac.com/systems/apple/macbook_pro/macbook-pro-unibody-faq/macbook-pro-unibody-switching-between-graphics-processors.html")

---

### Post by cyberdork33 on 2009-03-24
> **Nikos.Alexandris said:**
> Interesting: **...switch between graphics processors on the "Unibody" MacBook Pro without restarting?**

[http://i.gizmodo.com/5067433/confirmed-apple-can-enable-dual-gpu-and-on+the+fly-switching-in-macbook-pro](http://i.gizmodo.com/5067433/confirmed-apple-can-enable-dual-gpu-and-on+the+fly-switching-in-macbook-pro)



Imagine that Linux can make the break-through :-) Imagine that Linux will make the break-through :D

Common, let's set-up a project to attract dev's on it. There are many geeks who like apple-machines out there.

Cheers, Nikos
---

Look also at [http://www.everymac.com/systems/apple/macbook_pro/macbook-pro-unibody-faq/macbook-pro-unibody-switching-between-graphics-processors.html](http://www.everymac.com/systems/apple/macbook_pro/macbook-pro-unibody-faq/macbook-pro-unibody-switching-between-graphics-processors.html)
I think that it will not be possible in legacy OS mode. You will need to boot Ubuntu via EFI. See the EFI booting thread. We have made quite a bit of progress there...

---

### Post by Nikos.Alexandris on 2009-03-24
> **cyberdork33 said:**
> I think that it will not be possible in legacy OS mode. You will need to boot Ubuntu via EFI. See the EFI booting thread. We have made quite a bit of progress there...

Well, yes whatever will work :-D

---

### Post by desys on 2009-10-31
Hi to all, is there any progress on this problem ?
My experiments finished at the point, when I was starting ubuntu after enabling 9400 GPU through rEfi.
I noticed some interesting things:
1. changing 'gpu-power-prefs' to my 9400 value, after that 'dmpstore legacyvgahandle' shows my 9400 value
a) when I run rEfit shell -> than exit rEfit shell -> than try from menu linux lounch -> it stucks, nothing happens and macbook freeze with rEfit pinguins image.
b) when I run linux from menu, skiping rEfit shell -> than ubuntu starting OK
2. changing 'gpu-power-prefs' to my 9600 value, after that 'dmpstore legacyvgahandle' shows my 9600 value
 a) when I run rEfit shell -> than exit rEfit shell -> than try from menu linux lounch -> it stucks, nothing happens, but macbook freeze with black screen, like when we boot linux.
 b) when I run linux from menu, skiping rEfit shell -> than ubuntu starting OK

From that results, I'm thinking that rEfit uses another values than our values which we changing through rEfit shell, because in two cases we stuck, and in other two cases we run ubuntu without any problems.
But when we look at cases when we stuck, we can result that in one case was more progress than in other.

I think need to dig in refit startup, when I'll have time, I would look. And for purity of experiment I whant to reinstall rEfit, because I could corrupt something in the past - I must satisfy that linux stucks after we run rEfit shell.

 
MBP 5.2, rEfit 0.13

---

### Post by metatechbe on 2010-07-31
Thank Alex for the helpful research work !

I also did my own experiments, and I have different results on my MacBookPro 5,3.

I first looked in "About This Mac" under MacOS X, select "Hardware" in the left tree, then "Graphics/Displays".
Select "NVIDIA GeForce 9400M", and look the value of the "Device ID" field.  I have 0x0863.
Select "NVIDIA GeForce 9600M GT", and look the value of the "Device ID" field.  I have 0x0647.

Then I go to the rEFIt shell.

When I type "pci -b" I see two entries for display controllers :
00 02 00 00 ==> Display Controller - VGA/8514 controller
          Vendor 10DE Device 0647 Prog Interface 0
00 03 00 00 ==> Display Controller - VGA/8514 controller
          Vendor 10DE Device 0863 Prog Interface 0

and therefore the 2 cards are identified as follows : 
00 02 00 : 9600M GT (0x647)
00 03 00 : 9400M (0x0863)
This is the opposite conclusion to yours. Thomas Gerlach seems to agree with me in his post "drivers/video/efifb.c: Framebuffer for NVIDIA 9400M in MacBook Pro 5,1".

Like you, when I do a "pci 00 02 00" or "pci 00 03 00",  I have either all "0xFF" bytes for the disabled card, and an output starting with "DE 10" for the enabled one.  The enabled card is the one activated in MacOS X, depending on the "Energy saver" preference pane radio button ("better battery life" or "higher performance").

Then I do a "devices -b" and I see two entries for NVIDIA :
E6 B - - 1 2 5 NVIDIA GPU  
E8 B - - 1 5 6 NVIDIA GPU  

Then I do a "dh -b e8" when the 9400M is enabled in "Energy saver", and I see the following parameters : 
Handle E8 (AE6B7498 )
HorizontalResolution 1440
VerticalResolution 900
PixelsPerScanLine: 2048
FrameBufferBase 0xD0010000
FrameBufferSize 0x708000
PCI 00 03 00

Then I do a "dmpstore  -b gpu-power-prefs" and its value is : 01 00 00 00
Then I do a "dmpstore  -b legacyvgahandle" and its value is : 98 74 6B AE 00 00 00 00

Then I do a "dh -b e6" when the 9600M GT is enabled in "Energy saver", and I see the following parameters :: 
Handle E6 (AE6B7B98 )
HorizontalResolution 1440
VerticalResolution 900
PixelsPerScanLine: 2048
FrameBufferBase 0xC0030000
FrameBufferSize 0x708000
PCI 00 02 00

Then I do a "dmpstore  -b gpu-power-prefs" and it value is : 00 00 00 00
Then I do a "dmpstore  -b legacyvgahandle" and its value is : 98 7B 6B AE 00 00 00 00

My conclusion is that all EFI variables have the correct values to refer the 9400M or the 9600M GT depending on the card chosen in "Energy Saver", but that the BIOS is not using them :-(  
The only option left is to trying and boot Linux in EFI mode.

Regards,

metatech

---

### Post by emrys on 2010-08-02
Guys, I opened a bug related to this to try to give it more visibility:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/592086](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/592086)

Maybe you could share your progress there also to help move this forward.

Cheers.

---

### Post by metatechbe on 2010-08-05
I did another experiment to try and activate the 9400M in the BIOS.

My reasoning was the following : 
The MacBook Pro 15 (2009) comes in two flavours : 9400M only or 9400M+9600M GT.
The firmware version is the same (MBP53.00AC.B03).
The BIOS emulation layer running on top of EFI must therefore automatically detect whether the 9600M is present.  If yes, it activates it; if no, the 9400M is used instead.
To do that, it can check at the PCI address for the 9600M (02 00 00) whether a card is present.
On the other side, RivaTuner contains a NVStrap driver that can change the PCI DeviceID ("Use ROM straps for PCI DeviceID programming" option), maybe using a the NVIDIA "soft  strap" registers.

So I tried to extract the BIOS of my NVIDIA card, by following the steps : 
- Download a MS-DOS boot disk (FreeDos does not work, the keyboard freezes in DOS mode).
I downloaded the "The Standard MS-DOS 7.10 Boot Disk" from [http://ms-dos7.hit.bg/](http://ms-dos7.hit.bg/) (The other flavours do not work because they contain a grub bootloader).

Then you need to add nvflash to it and burn it to a CD-ROM :
[FONT="Courier New"]- hdiutil attach ~/Documents/DOS71ISO/boot/boot.img # displays diskX, for instance disk2
- sudo cp ~/Documents/DOS71ISO/nvflash5/nvflash.exe /Volumes/MSDOS710
- sudo cp ~/Documents/DOS71ISO/nvflash5/CWS*.EXE /Volumes/MSDOS710
- diskutil unmount /dev/disk2
- dd if=/dev/disk2  of=~/Documents/DOS71ISO/boot/boot2.img bs=10k count=144
- disktool -e disk2
- mv ~/Documents/DOS71ISO/boot/boot2.img ~/Documents/DOS71ISO/boot/boot.img
- mkisofs -J -r -R -v -T -b boot/boot.img -o ~/MSDOS71.iso ~/Documents/DOS71ISO
[/FONT]
Then use Apple's Disk Utility to burn the ISO file to a CD
Reboot the MacBook and press immediately "C".

It should boot in DOS mode.
[FONT="Courier New"]A:\>nvflash --directpci --list

NVIDIA Firmware Update Utility (Version 5.95)

NVIDIA display adapters present in system:
<0> GeForce 9600M GT     (10DE,0647,106B,00BC) H:--:NRM B:02,PCI,D:00,F:00
[/FONT]

Only the 9600M is present, so it looks like the BIOS PCI calls filter out the 9400M.

[FONT="Courier New"]A:\>nvflash --pciblocks

NVIDIA Firmware Update Utility (Version 5.95)

Adapter: GeForce 9600M GT    (10DE,0647,106B,00BC) H:--:NRM B:02,PCI,D:00,F:00 

The display may go *BLANK* on and off for up to 10 seconds during access to the EEPROM depending on your display adapter and output device.

Identifying EEPROM…
EEPROM ID (20,0000) : Unknown

ERROR : Supported EEPROM not found
[/FONT]

So nvflash cannot access the 9600M GT at all :-(

With wfflash V4.8 another error is displayed : 
[FONT="Courier New"]Cannot find NV device
Programming is Fail (X)
DOS/16M error: [26]  8042 timeout 
CPU error: incorrect opcode, killing process.
[/FONT]

So nothing works :-(

Hint : if you wish to try to boot in rEFIt or DOS shell, your CPU will reach high temperatures in a few minutes (80 degrees Celsius or even more).  Before doing it, set your CPU fan speed to 5000 RPM (for example in Linux) and then reboot.

---

### Post by metatechbe on 2010-08-07
Hello,

I managed to extract the BIOS of the NVIDIA card on my MacBook Pro 5,1.

Here are the steps : 

Boot into rEFIt shell, and type the following commands : 
[FONT="Courier New"]- "devices -b"
E6 B - - 1 2 5 NVIDIA GPU 
E8 B - - 1 5 6 NVIDIA GPU 

- "dh -b e6"
     ROM Size......: FE00
     ROM Location..: AE62C018

- "fs0:"
- "mem AE62C018 FE00 > 9600_output.txt"
[/FONT]

Now reboot to MacOS X and type the following commands : 
[FONT="Courier New"]
- "sudo mkdir /Volumes/EFI"
- "sudo mount -t msdos /dev/disk0s1 /Volumes/EFI"
- Download attachment from this post and extract file from ZIP.
- "javac HexToBinary.java"
- "java /Volumes/EFI/9600_output.txt 9600.rom"
[/FONT]

Now you can view it with NiBiTor.
It is indeed recognized as Device 0x0647.

I tried to change the ROM in-memory and boot into Linux but it only gives a black screen.
In rEFIT shell : 
[FONT="Courier New"]
- mm AE62C20C
DE -> <press enter>
10 -> <press enter>
47 -> 48
06 -> 07
00 -> q
- reconnect -r E6
[/FONT]

Anyone has ideas ?

Metatech

---

### Post by metatechbe on 2010-08-17
The easiest way to extract the BIOS is on Linux : 
[FONT="Courier New"]dd if=/dev/mem of=/boot/bios.bin bs=65536 skip=12 count=1[/FONT]

Alternately, from MacOS X, you can use nvflash

Download CharlesSoft Pacifist at [http://www.charlessoft.com/](http://www.charlessoft.com/)
Download "Graphics Firmware Update 1.0 (iMac and Mac Pro) compatibility with Windows 7" at [http://support.apple.com/kb/DL978](http://support.apple.com/kb/DL978)
Open "GraphicsFirmwareUpdate.dmg"
Open Pacifist, drag and drop "GraphicsFirmwareUpdate.pkg" on Pacifist window
Expand "Packet contents", "Contents", "Applications", "Utilities", "Graphics Firmware Update.app"
Go to Finder, Right-click on "Graphics Firmware Update.app", select "Show packet contents", then browse to "Contents" / "Resources".
Copy nvFlashDriver.kext and nvcmdflasher into ~/Documents/temp

[FONT="Courier New"]
cd ~/Documents/temp
sudo chown -R root:wheel nvFlashDriver.kext/
sudo chmod -R 755 nvFlashDriver.kext/
sudo kextutil -l nvFlashDriver.kext/
sudo kextload  nvFlashDriver.kext
[/FONT]

Enable GeForce 9400M

[FONT="Courier New"]./nvcmdflasher --list[/FONT]
[FONT="Courier New"]
NVIDIA Firmware Update Utility (Version 5.70d6)

NVIDIA display adapters present in system:
<0> GeForce 9400M        (10DE,0863,106B,00BB) H:--:NRM B:03,PCI,D:00,F:00
[/FONT]

Enable GeForce 9600M GT

[FONT="Courier New"]./nvcmdflasher --list

NVIDIA Firmware Update Utility (Version 5.70d6)

NVIDIA display adapters present in system:
<0> GeForce 9600M GT     (10DE,0647,0000,0000) H:--:NRM B:02,PCI,D:00,F:00
<1> GeForce 9400M        (10DE,0863,106B,00BB) H:--:NRM B:03,PCI,D:00,F:00
[/FONT]

Without the BIOS layer on top of the EFI, both cards are visible.

[FONT="Courier New"]./nvcmdflasher -i 0 --save 9600.rom

NVIDIA Firmware Update Utility (Version 5.70d6)

Adapter: GeForce 9600M GT     (10DE,0647,0000,0000) H:--:NRM B:02,PCI,D:00,F:00

The display may go *BLANK* on and off for up to 10 seconds during access to the EEPROM depending on your display adapter and output device.

Identifying EEPROM...
EEPROM ID (20,0000) : Unknown

ERROR: Supported EEPROM not found
./nvcmdflasher -i 1 --save 9400.rom

NVIDIA Firmware Update Utility (Version 5.70d6)

Adapter: GeForce 9400M        (10DE,0863,106B,00BB) H:--:NRM B:03,PCI,D:00,F:00

The display may go *BLANK* on and off for up to 10 seconds during access to the EEPROM depending on your display adapter and output device.

Identifying EEPROM...
EEPROM ID (20,0000) : Unknown

ERROR: Supported EEPROM not found
[/FONT]


Open an hex editor and change the following line : 
[FONT="Courier New"]000A2480  20 00 05 00 80 00 20 00 01 00 01 00 19 8e 07 00 [/FONT]
by
[FONT="Courier New"]000A2480  20 00 00 00 80 00 20 00 01 00 01 00 19 8e 07 00 [/FONT]
in order to change
[FONT="Courier New"]   ST        M25P05  512Kx1S     2.7-3.6V, 128B page, 32k blk, ID=(20,0005)[/FONT]
into 
[FONT="Courier New"]   ST        M25P05  512Kx1S     2.7-3.6V, 128B page, 32k blk, ID=(20,0000)[/FONT]

[FONT="Courier New"]./nvcmdflasher --check

NVIDIA Firmware Update Utility (Version 5.70d6)

Adapter: GeForce 9400M        (10DE,0863,106B,00BB) H:--:NRM B:03,PCI,D:00,F:00

The display may go *BLANK* on and off for up to 10 seconds during access to the EEPROM depending on your display adapter and output device.

Identifying EEPROM...
EEPROM ID (20,0000) : ST M25P05 2.7-3.6V 512Kx1S, page

./nvcmdflasher --save 9400.rom

NVIDIA Firmware Update Utility (Version 5.70d6)

Adapter: GeForce 9400M        (10DE,0863,106B,00BB) H:--:NRM B:03,PCI,D:00,F:00

The display may go *BLANK* on and off for up to 10 seconds during access to the EEPROM depending on your display adapter and output device.

Identifying EEPROM...
EEPROM ID (20,0000) : ST M25P05 2.7-3.6V 512Kx1S, page
Reading adapter firmware image...
Image Type            : Unavailable (Unknown)
Version               : Unavailable (Invalid)
Image Size            : 0 bytes
~CRC32                : 00000000
Subsystem Vendor ID   : FAFC
Subsystem ID          : 741A
Hierarchy ID          : None
Image Type            : Unavailable (Unknown)
Version               : Unavailable (Invalid)
Saving of image completed.
[/FONT]

So the firmware parameters have invalid values, so it still does not work :-(
Maybe by hex editing with the correct guess for the set of EEPROM parameters, it could work ?

---

### Post by emrys on 2010-08-17
Wow, thanks metatechbe. It seems you are moving forward... Keep up the great work!

If you manage to do it you'll be my hero ;)

---

### Post by metatechbe on 2010-08-18
Hello,

I found a much easier way to find the FrameBufferBase address than the rEFIt shell way.
Only two commands must be run from a Terminal (sudo is even not necessary) :
[FONT="Courier New"]sudo ioreg -lw0 |grep manufacturer|cut -b25-80;sudo ioreg -lw0|grep "product-name"|cut -b 25-80;sudo dtrace -qn 'BEGIN{boot_args=((struct boot_args*)(`PE_state).bootArgs);printf("FrameBufferBase: 0x%08x\nPixelsPerScanLine: %d\nHorizontalResolution: %d\nVerticalResolution: %d", boot_args->Video.v_baseAddr, boot_args->Video.v_rowBytes/4, boot_args->Video.v_width, boot_args->Video.v_height);exit(0)} '[/FONT]
This can allow to easily populate the missing entries in the Linux kernel framebuffer driver (drivers/video/efifb.c)

On my machine, when the 9400M is active at boot time the output is the following :
<"Apple Inc.">
<"MacBookPro5,3">
FrameBufferBase: 0xd0010000
PixelsPerScanLine: 2048
HorizontalResolution: 1440
VerticalResolution: 900

On my machine, when the 9600M is active at boot time the output is the following :
<"Apple Inc.">
<"MacBookPro5,3">
FrameBufferBase: 0xc0030000
PixelsPerScanLine: 2048
HorizontalResolution: 1440
VerticalResolution: 900

If the graphic card is switched after boot time (in "Energy Saving" preference pane or with gfxCardStatus), the FrameBufferBase value does not change anymore, it keeps its previous value.

Please contribute the results on your own machine !

Here is the mapping between the different parameter names : rEFIt, MacOS X kernel, Linux kernel MacOS X API :
PixelsPerScanLine -> v_rowBytes -> efifb_dmi_info.stride -> CGDisplayBytesPerRow
FrameBufferBase -> v_baseAddr -> efifb_dmi_info.base -> CGDisplayBaseAddress

Thanks,

metatech

---

### Post by emrys on 2010-08-18
Hi, mine says exactly the same:

 <"MacBookPro5,3">
FrameBufferBase: 0xd0010000


Although, I needed sudo privileges for the second line.

---

### Post by Sidolin on 2010-08-18
<"MacBookPro6,2">
FrameBufferBase: 0x90030000

---

### Post by metatechbe on 2010-08-20
Thanks Sidolin,
Was it with the integrated or the discrete graphics activated at boot time ?
Thanks.
metatech

---

### Post by Nikos.Alexandris on 2010-08-20
Booting with "energy save" mode (=with the integrated 9400M card active):
 <"Apple Inc.">
 <"MacBookPro5,1">
FrameBufferBase: 0xc0010000

Switching the "energy saving" preference to "performance" (dunno remember the setting-name exactly, anyhow I mean the discrete 9600M GT card), log-out, log-in does not change the above!

Rebooting and re-executing the "ioreg" command(s) returns:

9600M GT:
 <"Apple Inc.">
 <"MacBookPro5,1">
FrameBufferBase: 0xb0030000

Regards, Nikos

---

### Post by metatechbe on 2010-08-21
Hello,

Thanks to all the people who gave an early feedback in this thread.  They allowed me to validate the method on other machines than mine.

Now I created a [new thread]("http://ubuntuforums.org/showthread.php?t=1557326") calling for volunteers, hoping to broaden the audience and get more results.

Thanks again,

metatech

---

### Post by tmg1981 on 2010-09-10
Hi everybody,

I think I found the most easiest way to disable the 9600M GT of MBP5,1 (or any other one depending on MBP version)  in EFI-Mode.
As you might know, the second card is still powered, even if you use the 9400M, and consumes some amount of energy, reducing the battery life.

Ok, here we go...

```

sudo -s
echo 1 > /sys/bus/pci/devices/<pci_addr_of_card>/remove

```It's simple, isn't it?
Unfortunately it doesn't seem to work just with
```

sudo echo 1 > /sys/bus/pci/devices/<pci_addr_of_card>/remove

```since it says "Permission denied".
A simple
```

lspci

```will confirm that the device has been removed.

Of course, you can do this with most of the other PCI hardware as well.

To reactivate the removed devices, do a
```

sudo -s
echo 1 > /sys/bus/devices/rescan

```I still have to verify the drop in the power consumption. What makes me suspicious is that the "NVIDIA X Server Settings" still show the second GPU, including temperature and clock frequency...

Please post if it's working for you or not.


Cheers,

Thomas Gerlach

EDIT:
Well, it seems not to have the effect I wanted to. At least not in EFI mode.
I checked the disabling strategy in BIOS mode (9600M GT only) by disabling the graphics device. It worked, the screen blanked. But immediately after that, the screen came back online, however spawning a console to log in. So something happens, but the graphis driver seems to enable the device again. 
In EFI mode using the 9400M, when trying to disable the graphca, nothing happens. Although the device is not listed by "lspci" anymore. So I assume it doesn't work for the 9600M GT either.

Anyway, seems to go into the right direction...keep you posted. :)

EDIT2:
Ok, just tested something. The problem is - oh my - related to the nvidia-drivers.
Here is what I did:
1) Boot in BIOS mode, with "nouveau" activated.
Do the "remove" trick.
-> Screen blanks (and stays so). System is still up (pommed still working; power-button and ENTER shuts down MBP).
2) Boot in BIOS mode, with "nvidia" enabled.
Do the "remove" trick again.
-> Nothing happens (but device is removed from output of "lspci").

Well, the nvidia-drivers have a different behavior in EFI mode than in BIOS mode. BTW, display backlight dimming doesn't work in EFI mode. And let me guess: Might have something to do with nvidia-drivers???

---

### Post by metatechbe on 2010-09-18
Thomas,

Thanks for your research&#8230;

There is another very promising track to try and disable the 9600M, which was proposed by Sidolin in this thread (his work is much more ambitious in that he is implementing dynamic graphic card switching).
[http://ubuntuforums.org/showthread.php?t=1564298](http://ubuntuforums.org/showthread.php?t=1564298)

If you look at the attached source code, 
[http://andreas.meetr.de/gmux/apple_gmux.c](http://andreas.meetr.de/gmux/apple_gmux.c)
The two following lines should do the magic to disable the 9600M.
#define PORT_DISCRETE_POWER 0x750
outb(0, PORT_DISCRETE_POWER);
[edited:replaced 1 by 0 according to tmg1981's feedback]

On a MBP 6,2 the power consumption goes from 28 W to 10 W !!
[http://www.mail-archive.com/hybrid-graphics-linux@lists.launchpad.net/msg00174.html](http://www.mail-archive.com/hybrid-graphics-linux@lists.launchpad.net/msg00174.html)

Regards,

metatech

---

### Post by tmg1981 on 2010-09-21
Hi,

well, this sounds really very promising. I checked it (by writing a small program which accesses the corresponding port), and it seems to work, the 9600M GT seems to be disabled!!! Great job, Sidolin, and thanks Metatechbe for posting this.

However, I did the following:

#define PORT_DISCRETE_POWER 0x750
outb(0, PORT_DISCRETE_POWER);
        ^--- 0, not 1 

I didn't try the driver sources attached to the threads pointed to in your last post. I'll check that soon.


Greetings,

Thomas

---

### Post by metatechbe on 2010-09-21
Hi Thomas,

Can you please post your program ?
I thought a kernel driver was needed in order to access these memory ranges...

Thanks,

metatechbe

---

### Post by metatechbe on 2010-09-22
Hi all,

Here is the small program called "gpupwr" that can disable the discrete graphic card.  Linux must be booted in EFI mode on the integrated graphic card.  The program must be run as root, otherwise you will get a "ioperm failed" error.

On a MacBookPro5,3 the power consumption reported by "powertop" is greatly reduced.
9600M enabled and used : 23 Watt
9400M used : 19 Watt
9400M used + 9600 disabled  : 16 Watt

Also the temperatures are much lower (these measures are taken during typical web browsing + "ondemand" CPU governor + Bluetooth disabled) :
9600M enabled and used : 55 degrees Celsius
9400M used : 50 degrees Celsius
9400M used + 9600 disabled  : 42 degrees Celsius

The program should normally also work on MacBookPro 2010 with Intel integrated graphics.

[edit : alternative]
Alternatively, you can add the following line in grub.cfg. Without it, the "suspend" and the "logout" do not work anymore. 
```

outb 0x750 0 

```

Thanks to Sidolin for finding the "magic" offsets of the gmux device.

metatech

---

### Post by tmg1981 on 2010-09-22
Hi Metatech,

sorry for the delay...but I see, you already found the solution how to access IO without building a kernel driver.
It's quite the same what I did...

I attached my version just for comparison...there's also some stuff inside to read the current intensity. However, changing it doesn't work for me yet.
Maybe you can try and write some value to 0x774 and see if the brightness changes.

Thanks so far and cheers,

Thomas

---

### Post by emrys on 2011-03-04
Any news out there? Someone managed to use his/her dual GPU laptop using the 9400?

---

### Post by metatechbe on 2011-03-10
Update : by adding in grub.cfg : 
outb 0x750 0 

The suspend/resume works fine !

---

### Post by emrys on 2011-03-10
Metatechbe, it would be possible for you to post a step by step guide starting with a clean system?

It would be great to have the guide here in the forums and also, include it in the bug report.

Thanks!

---

### Post by metatechbe on 2011-03-11
> **emrys said:**
> Metatechbe, it would be possible for you to post a step by step guide starting with a clean system?



The step-by-step is here :
[http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook)

metatech

---

### Post by emrys on 2011-03-11
Thanks!

> **metatechbe said:**
> The step-by-step is here :
[http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook)

metatech

---

### Post by emrys on 2011-03-11
Metatechbe, I am following the step by step guide and I am having problems in one of the steps. According to the guide, in the Installing GRUB section you have to run the following two commands:

cd grub-core
../grub-mkimage -O $EFI_ARCH-efi -d . -o grub.efi -p "" part_gpt hfsplus fat ext2 normal chain boot configfile linux multiboot

I am in ~/grub/grub-core/ but the last command gives me an error:

bash: ../grub-mkimage: No such file or directory

Should I create manually the directory? Any ideas?

Thanks a lot.

---

### Post by metatechbe on 2011-03-11
> **emrys said:**
> 
bash: ../grub-mkimage: No such file or directory

Are you sure you are using grub 1.99 RC1 ?

---

### Post by emrys on 2011-03-11
I followed the guide so I got GRUB using:

bzr branch --revision -1 [http://bzr.savannah.gnu.org/r/grub/trunk/grub](http://bzr.savannah.gnu.org/r/grub/trunk/grub)

Also, in the NEWS file it says: "New in 1.99:" so it should be 1.99...

> **metatechbe said:**
> Are you sure you are using grub 1.99 RC1 ?

---

### Post by emrys on 2011-03-11
OK. I started all over again and this time the error (in the same step "../grub-mkimage -O $EFI_ARCH-efi -d . -o grub.efi -p "" part_gpt hfsplus fat ext2 normal chain boot configfile linux multiboot") changed to:

unknown target format -efi
Try `../grub-mkimage --help' for more information.

Any ideas?

Thanks.

---

### Post by emrys on 2011-03-11
OK, this is probably my own fault. Using this I managed to advance:

../grub-mkimage -O x86_64-efi -d . -o grub.efi -p "" part_gpt hfsplus fat ext2 normal chain boot configfile linux multiboot


> **emrys said:**
> OK. I started all over again and this time the error (in the same step "../grub-mkimage -O $EFI_ARCH-efi -d . -o grub.efi -p "" part_gpt hfsplus fat ext2 normal chain boot configfile linux multiboot") changed to:

unknown target format -efi
Try `../grub-mkimage --help' for more information.

Any ideas?

Thanks.

---

### Post by emrys on 2011-03-11
OK. Finally everything worked, sort of.

I had to modify the menu entries for grub.cfg as my / partition is sda5 instead of sda3... so, if anyone gets a "noinit found. Try passing init= bootarg" error, it might be this.

Another quirk is that when the system boots, a process named v86d is using 100% cpu...

Finally, the temperature, as reported by NVIDIA X Server Settings is about 50º, not 42º as expected.

Suspend/resume works but after resuming, the temperature goes up to >57º. I tried to use gpupwr but the following error appears:
ioperm failed
Segmentation fault

Brightness does not work, as advertised.

Other than that, great work guys.

---

### Post by metatechbe on 2011-03-11
> **emrys said:**
> 
Finally, the temperature, as reported by NVIDIA X Server Settings is about 50º, not 42º as expected.


After 10-20 minutes after boot, the temperature should be around 40-42 degrees Celsius.  Did you kill the v86d process and waited long enough for the machine to stabilize its temperature ?

> **emrys said:**
> 
Suspend/resume works but after resuming, the temperature goes up to >57º. I tried to use gpupwr but the following error appears:
ioperm failed
Segmentation fault


You need to run the gpupwr command with "sudo"

---

### Post by emrys on 2011-03-12
Thanks metatechbe.

Yes, I did kill v86d and waited for a while. Even when leaving the computer alone (doing nothing), the temperature never goes under 44º. Using the computer in normal browsing (NYtimes, flash blocked) makes the temperature go up to about 50-52º.

Running gpupwr using sudo works fine but, again, the temperature is stable in ~52º during normal use.

Could you post your xorg.conf and grub.cfg files to see if I got something wrong?

And a last thing, there is any way to control the screen brightness?

Thanks a lot for the help.

> **metatechbe said:**
> After 10-20 minutes after boot, the temperature should be around 40-42 degrees Celsius.  Did you kill the v86d process and waited long enough for the machine to stabilize its temperature ?



You need to run the gpupwr command with "sudo"

---

### Post by metatechbe on 2011-03-12
> **emrys said:**
> 
Could you post your xorg.conf and grub.cfg files to see if I got something wrong?

And a last thing, there is any way to control the screen brightness?


Here are the custom settings I define : 
- "On demand" governor for each CPU core (thanks to CPU Frequency Scaling Monitor applet from GNOME) : gain of 3 degrees
```

echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo ondemand > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor

```- Disable Bluetooth : gain of 5 degrees
```

rfkill block 0

```- The following "PowerMizer"/"coolbits" options in xorg.conf :  : gain of 2 degrees
```

Section "Device"
    Identifier     "Device9400M"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "NVIDIA 9400M"
Option     "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x2222; PowerMizerDefault=0x3; PowerMizerDefaultAC=0x3"
Option "coolbits" "1"
BusID "PCI:3:0:0"
EndSection

```
In total about 10 degrees colder ! QED :-)

Screen brightness does not work but I did not try.

---

### Post by Nikos.Alexandris on 2011-03-15
> **emrys said:**
> 
Yes, I did kill v86d and waited for a while.

Apologies for the indirectly relevant question: why is v86d eating up the CPUs?

I've tried to "fix" the plymouth boot splash yesterday [*] by changing some parameters in [FONT="Courier New"]/etc/default/grub[/FONT] including the use of *uvesafb*. This required *v86d* which ate up the CPUs and caused the fans to run at full speed. In the past I've done the same thing without any obvious v86d-problem.

Thanks, Nikos


[*] [[COLOR="Blue"]post on idyllictux blog[/COLOR]]("http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/")

---

### Post by Nikos.Alexandris on 2011-03-23
> **metatechbe said:**
> The step-by-step is here :
[http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook)

metatech

Successfully booted via EFI on MBP 5,1 (last week -- sorry for not taking the time to report this earlier) :-)
I also (as emrys [[COLOR="Blue"]post 41[/COLOR]]("http://ubuntuforums.org/showpost.php?p=10551550&postcount=41")) see not less than 52 degrees. Did not try all suggestions at [[COLOR="blue"]post 42[/COLOR]]("http://ubuntuforums.org/showpost.php?p=10552118&postcount=42").

Cheers, Nikos

---

### Post by Teefs on 2011-05-20
> **metatechbe said:**
> The step-by-step is here :
[http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook)

metatech

I've been anxious to try this out on my Macbook Pro, but it looks like the link to the guide doesn't work anymore.

Do you know where I can find the instructions I need to follow?

---

### Post by metatechbe on 2011-05-21
> **Teefs said:**
> I've been anxious to try this out on my Macbook Pro, but it looks like the link to the guide doesn't work anymore.

Do you know where I can find the instructions I need to follow?

New location is here :
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

metatech

---

### Post by tmg1981 on 2011-06-30
hi metatech,

thanks for the detailed community documentation post. really nice work!
hopefully, i can contribute some more information soon. been a while since i played with EFI, currently i'm running ubuntu in BIOS mode on my MBP5,1 (due to heavy load at work...).

anyway, way to go!


cheers,

thomas

---

### Post by emrys on 2011-10-16
Any news regarding a simplified (aka PPA or similar) way to enable 9400M in Oneiric?

The solid >62º I am getting in my MBP5,3 are killing me (and the battery).

Also, the affected people can mark this bug as affecting them in: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/592086](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/592086)

Cheers.

---

### Post by emrys on 2011-11-22
Just found out about Ironhide... but is seems there is no support for Macbook Pro 5,3 or similar... [https://launchpad.net/~mj-casalogic/+archive/ironhide/](https://launchpad.net/~mj-casalogic/+archive/ironhide/)

Anyone has been successful using Ironhide, Bumblebee or similar?

---

### Post by emrys on 2012-05-16
Any news for 12.04?

This thing is a battery killer!

---

