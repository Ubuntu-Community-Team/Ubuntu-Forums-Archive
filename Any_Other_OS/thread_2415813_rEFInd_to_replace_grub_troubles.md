---
title: "rEFInd to replace grub troubles?"
date: 2019-04-01
forum: Any Other OS
---

### Post by frank105 on 2019-04-01
HI all,

I have a problem...  I am a distro-hopper.  But every time I try a new distro I screw up my grub install and end up unable to boot.  
I am running a  HP Pavilion x2 12-b020nr 12" Detachable Laptop with Intel Core M3, 4 GB RAM, 128GB SSD.
My HD is partitioned:
SDA1 - EFI - 537MB
SDA2 - Linux root - 21GB 
SDA5 - /media
SDA6 - /home =  33 GB
SDA4 - Android-X86 - 36GB
SDA3 - Swap

Latest troubles:  I replaced my Ubuntu install with Robolinux on SDA2.  During install it asked if I wanted grub installed and where.  1st time I tried SDA (thinking somehow wholistic?)
Reboot results with grub bash prompt. 
I tried a reinstall and this time choose SDA2 for grub install. 
Reboot results with grub bash prompt.
Rebooted - hit esc and tried every single boot possibility listed in the Bios and inside the EFI file listings (lots of remnants of past distros - more later)

Next I booted with my Ubuntu USB disk and tried grub repair... same bash prompt.
tried Ubuntu again and reinstalled grub... same bash prompt

Anyway - I learned somewhere around here (sorry - you deserve some credit... but I forgot where)  I can boot from the bash prompt:[INDENT]ls -  [to show your hd partitions and names - pick the one which your linux distro is installed on) 
set prefix=(hd0,gpt2)/boot/grub 
insmod normal 
normal
[/INDENT]

Boots into the robolinux grub screen just fine.   I tried running grub update after booting but reboots result in the grub bash prompt again. 

Anyway - since I always seem to mess up grub I have been reading about other alternatives.  I found some stuff on rEFInd and it sounds interesting.  Any testimonials out there?  The side story is I would like to be able to select my OS with my touch screen since I don't always have my keyboard attached - long story.  

Sorry - trying to focus.
I'd like to fix grub or try rEFInd.  I'd also like to clean up all my past distro install efi files and the list shown inside BIOS too.  Bonus points also for getting my Android X86 install to boot easily with one solution.  Currently I have to hit esc and load the android.efi file... 

Okay - and if the answer is to keep Grub - what is the proper answers during install for grub?  Should I never install it again and then boot at the bash prompt and run grub update? 

Thanks in advance,
Frank

---

### Post by oldfred on 2019-04-01
I have used rEFInd when I UEFI & grub got confused. But it is only for UEFI boot, but may also be able to reboot into UEFI to boot another BIOS install.

I keep one LTS version of Ubuntu as main working install and have its grub as default boot. My other installs of Ubuntu often overwrite that grub, but I immediately reset back to my main working grub and update it to add the new install.

Grub update, just updates menu and runs os-prober to find other installs.

You probably just need the grub install commands.

This is really for BIOS, not sure about UEFI. It should work with UEFI if defaults ok, but normal UEFI also specify a lot more parameters.

       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sda but use your drive not partitions):
sudo parted -l
#if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
#If that returns any errors run:
sudo grub-install --recheck /dev/sda
sudo update-grub

---

### Post by VMC on 2019-04-01
Frank, I enjoyed reading your post. Not the pain but wording. 
You have a fairly large esp partition. You could look into systemd-boot. Its very simple and easy, but one cavet, you need to copy kernels/initrd to esp. My esp is only 100mb.
With all that aside, I've had similar issues with distros. The worst was Fedora. I couldn't wrench its hands frrom grub. Then deepin. it worked but I was then installing kubuntu, and it wouldn't boot deepin. It saw it but the "you need to boot kernel first" popped up.
What I found worked the best was to remove all folders from esp (/boot/efi/EFI) and then install deepin. Both deepin and ubuntu, which it creates had reference to deepin. Strange but now two ubuntu's and deepin works.

Another oddity of efi. Even though everything booted ok, I go the "Couldn't get size: 0x800000000000000e" from every distro. I found several bug reports and it didn't seem to be my issue. Then looking at firmware, I found out it had ubuntu as first boot instead of deepin, who controls booting.
Once I changed that to deepin, then no more "Couldn't get size: 0x800000000000000e".!?

I do have Windows installed and don't even look in its direction. Leave it completely alone. It boots up fine no matter what. The more I mess around with efi and screw it up the more I learn. Used BIOS for 30 years or how every long its been around.

---

### Post by frank105 on 2019-04-01
Mornin' Fred!

You always get me out of trouble - so thanks for that and thanks in advance. 

Okay - I ran the commands above.  My internal drive is sda but I am not 100% on the lingo so I am going to echo it back to ya. 

In the terminal I ran:[INDENT]sudo parted -l   <---- this gave me a list of all of my partitions and shows sda1 as my EFI partition.
sudo grub-install /dev/sda
sudo update-grub
[/INDENT]
Commands all ran showed no errors.  Grub update showed success.  But reboot got me right back to the bash command. 

I wanted to get you more info on the setup so I installed and ran ubuntu boot repair and did a repair (which I think just did exactly the steps above for reinstalling grub...) 

Anyway - here is the report it makes [http://paste.ubuntu.com/p/CjfPkhspbK/](http://paste.ubuntu.com/p/CjfPkhspbK/)

I am not 100% sure I understand ya here:
> I have used rEFInd when I UEFI & grub got confused. But it is only  for UEFI boot, but may also be able to reboot into UEFI to boot another  BIOS install.

Is my laptop booting in UEFI by default or because I enabled legacy it is doing something else?   Does disable legacy solve the problem (but does that prohibit USB boot?).  

> 
I keep one LTS version of Ubuntu as main working install and have its  grub as default boot. My other installs of Ubuntu often overwrite that  grub, but I immediately reset back to my main working grub and update it  to add the new install.
Okay - this was happening to me all of the time.  So are you saying all I need to do is boot using the bash commands and then run the grub update commands you gave and it will make it all good again?  That is an awesome trick to learn.  Always learning from you Fred!

Anyway - what should I try next.  

Thanks again!

---

### Post by frank105 on 2019-04-01
Hey VMC.

Welcome to the party.  

Sorry - my lingo dictionary is still not 100% but - I do have a spare small partition available.  So maybe I should put Deepin in it?  Does that install the SystemMD ?

I did resize my EFI partition last time I did a clean wipe because I read something on having better options with a larger EFI partition.  I wish I would have saved those notes to know what I was supposed to do next. 

But the long of the short is - I think I need to learn a lot more about GRUB or I need to install and learn about something else...  rEFInd or SystemMD or??  As mentioned earlier - bonus points for the possibility of my boot being touch screen enabled...  (That may be a no go anyway since it is so early in the boot... but I'd chase a "it might work" for the learning)

Deepin is on my distro hopping list.  Did you love it?

Okay - focus - anyway a couple other notes - the SSD is a but snug to fit all my wants.  I need to get Win10 back on here for the wife.  She has gotten much smarter...  I used to just tell her "This is the NEW Win10..."  Doesn't work anymore...  I have a larger HD coming in a few months (world travel... have to wait until we get to the US)  focus...  What I mean is - I want to have a solution for the future that does eventually include Win10/Linux flavor de jour/Android flavor de jour... Anyway - all this said to say if it is Grub or whatever - it needs to support all the future plans.  

Okay - now I am rambling.  

I think I am going to download Deepin - might be the next hop anyway...

Thanks in advance,
Frank

---

### Post by frank105 on 2019-04-01
Just for fun - those playing along might find this useful:

/boot/efi
# tree
.
&#9500;&#9472;&#9472; boot
&#9474;   &#9492;&#9472;&#9472; grub
&#9474;       &#9500;&#9472;&#9472; fonts
&#9474;       &#9474;   &#9492;&#9472;&#9472; DejaVuSansMono-18.pf2
&#9474;       &#9500;&#9472;&#9472; grubenv
&#9474;       &#9500;&#9472;&#9472; theme
&#9474;       &#9474;   &#9500;&#9472;&#9472; android-x86.png
&#9474;       &#9474;   &#9500;&#9472;&#9472; icons
&#9474;       &#9474;   &#9474;   &#9500;&#9472;&#9472; android.png
&#9474;       &#9474;   &#9474;   &#9500;&#9472;&#9472; android-x86.png
&#9474;       &#9474;   &#9474;   &#9500;&#9472;&#9472; arch.png
&#9474;       &#9474;   &#9474;   &#9500;&#9472;&#9472; centos.png
&#9474;       &#9474;   &#9474;   &#9500;&#9472;&#9472; debian.png
&#9474;       &#9474;   &#9474;   &#9500;&#9472;&#9472; fedora.png
&#9474;       &#9474;   &#9474;   &#9500;&#9472;&#9472; forward.png
&#9474;       &#9474;   &#9474;   &#9500;&#9472;&#9472; frugalware.png
&#9474;       &#9474;   &#9474;   &#9500;&#9472;&#9472; gentoo.png
&#9474;       &#9474;   &#9474;   &#9500;&#9472;&#9472; gnu-linux.png
&#9474;       &#9474;   &#9474;   &#9500;&#9472;&#9472; kubuntu.png
&#9474;       &#9474;   &#9474;   &#9500;&#9472;&#9472; linuxmint.png
&#9474;       &#9474;   &#9474;   &#9500;&#9472;&#9472; mageia.png
&#9474;       &#9474;   &#9474;   &#9500;&#9472;&#9472; mandriva.png
&#9474;       &#9474;   &#9474;   &#9500;&#9472;&#9472; opensuse.png
&#9474;       &#9474;   &#9474;   &#9500;&#9472;&#9472; openthos.png
&#9474;       &#9474;   &#9474;   &#9500;&#9472;&#9472; os.png
&#9474;       &#9474;   &#9474;   &#9500;&#9472;&#9472; reboot.png
&#9474;       &#9474;   &#9474;   &#9500;&#9472;&#9472; sabayon.png
&#9474;       &#9474;   &#9474;   &#9500;&#9472;&#9472; setup.png
&#9474;       &#9474;   &#9474;   &#9500;&#9472;&#9472; shutdown.png
&#9474;       &#9474;   &#9474;   &#9500;&#9472;&#9472; slackware.png
&#9474;       &#9474;   &#9474;   &#9500;&#9472;&#9472; theme.png
&#9474;       &#9474;   &#9474;   &#9500;&#9472;&#9472; ubuntu.png
&#9474;       &#9474;   &#9474;   &#9492;&#9472;&#9472; windows.png
&#9474;       &#9474;   &#9500;&#9472;&#9472; menu_bkg_c.png
&#9474;       &#9474;   &#9500;&#9472;&#9472; menu_bkg_e.png
&#9474;       &#9474;   &#9500;&#9472;&#9472; menu_bkg_ne.png
&#9474;       &#9474;   &#9500;&#9472;&#9472; menu_bkg_n.png
&#9474;       &#9474;   &#9500;&#9472;&#9472; menu_bkg_nw.png
&#9474;       &#9474;   &#9500;&#9472;&#9472; menu_bkg_se.png
&#9474;       &#9474;   &#9500;&#9472;&#9472; menu_bkg_s.png
&#9474;       &#9474;   &#9500;&#9472;&#9472; menu_bkg_sw.png
&#9474;       &#9474;   &#9500;&#9472;&#9472; menu_bkg_w.png
&#9474;       &#9474;   &#9500;&#9472;&#9472; progress_bar_c.png
&#9474;       &#9474;   &#9500;&#9472;&#9472; progress_bar_e.png
&#9474;       &#9474;   &#9500;&#9472;&#9472; progress_bar_ne.png
&#9474;       &#9474;   &#9500;&#9472;&#9472; progress_bar_n.png
&#9474;       &#9474;   &#9500;&#9472;&#9472; progress_bar_nw.png
&#9474;       &#9474;   &#9500;&#9472;&#9472; progress_bar_se.png
&#9474;       &#9474;   &#9500;&#9472;&#9472; progress_bar_s.png
&#9474;       &#9474;   &#9500;&#9472;&#9472; progress_bar_sw.png
&#9474;       &#9474;   &#9500;&#9472;&#9472; progress_bar_w.png
&#9474;       &#9474;   &#9500;&#9472;&#9472; progress_highlight_c.png
&#9474;       &#9474;   &#9500;&#9472;&#9472; progress_highlight_e.png
&#9474;       &#9474;   &#9500;&#9472;&#9472; progress_highlight_w.png
&#9474;       &#9474;   &#9500;&#9472;&#9472; sb_frame_c.png
&#9474;       &#9474;   &#9500;&#9472;&#9472; sb_frame_n.png
&#9474;       &#9474;   &#9500;&#9472;&#9472; sb_frame_s.png
&#9474;       &#9474;   &#9500;&#9472;&#9472; sb_thumb_c.png
&#9474;       &#9474;   &#9500;&#9472;&#9472; sb_thumb_n.png
&#9474;       &#9474;   &#9500;&#9472;&#9472; sb_thumb_s.png
&#9474;       &#9474;   &#9500;&#9472;&#9472; select_bkg_c.png
&#9474;       &#9474;   &#9500;&#9472;&#9472; select_bkg_e.png
&#9474;       &#9474;   &#9500;&#9472;&#9472; select_bkg_ne.png
&#9474;       &#9474;   &#9500;&#9472;&#9472; select_bkg_n.png
&#9474;       &#9474;   &#9500;&#9472;&#9472; select_bkg_nw.png
&#9474;       &#9474;   &#9500;&#9472;&#9472; select_bkg_se.png
&#9474;       &#9474;   &#9500;&#9472;&#9472; select_bkg_s.png
&#9474;       &#9474;   &#9500;&#9472;&#9472; select_bkg_sw.png
&#9474;       &#9474;   &#9500;&#9472;&#9472; select_bkg_w.png
&#9474;       &#9474;   &#9492;&#9472;&#9472; theme.txt
&#9474;       &#9492;&#9472;&#9472; x86_64-efi
&#9474;           &#9492;&#9472;&#9472; grub.cfg
&#9500;&#9472;&#9472; EFI
&#9474;   &#9500;&#9472;&#9472; Android
&#9474;   &#9474;   &#9500;&#9472;&#9472; android.cfg
&#9474;   &#9474;   &#9500;&#9472;&#9472; bootia32.efi
&#9474;   &#9474;   &#9500;&#9472;&#9472; BOOTx64.EFI
&#9474;   &#9474;   &#9492;&#9472;&#9472; grubx64.efi
&#9474;   &#9500;&#9472;&#9472; BOOT
&#9474;   &#9474;   &#9500;&#9472;&#9472; bkpbootx64.efi
&#9474;   &#9474;   &#9500;&#9472;&#9472; bootia32.efi
&#9474;   &#9474;   &#9500;&#9472;&#9472; bootx64.efi
&#9474;   &#9474;   &#9500;&#9472;&#9472; efi.img
&#9474;   &#9474;   &#9500;&#9472;&#9472; fbx64.efi
&#9474;   &#9474;   &#9500;&#9472;&#9472; grub.cfg
&#9474;   &#9474;   &#9492;&#9472;&#9472; grubx64.efi
&#9474;   &#9500;&#9472;&#9472; robolinux_10
&#9474;   &#9474;   &#9500;&#9472;&#9472; BOOTX64.CSV
&#9474;   &#9474;   &#9500;&#9472;&#9472; grub.cfg
&#9474;   &#9474;   &#9500;&#9472;&#9472; grubx64.efi
&#9474;   &#9474;   &#9500;&#9472;&#9472; mmx64.efi
&#9474;   &#9474;   &#9492;&#9472;&#9472; shimx64.efi
&#9474;   &#9492;&#9472;&#9472; ubuntu
&#9474;       &#9500;&#9472;&#9472; BOOTX64.CSV
&#9474;       &#9500;&#9472;&#9472; fw
&#9474;       &#9500;&#9472;&#9472; fwupx64.efi
&#9474;       &#9500;&#9472;&#9472; grub.cfg
&#9474;       &#9500;&#9472;&#9472; grubx64.efi
&#9474;       &#9500;&#9472;&#9472; mmx64.efi
&#9474;       &#9492;&#9472;&#9472; shimx64.efi
&#9492;&#9472;&#9472; startup.nsh


Reading up on this right now:  [https://blog.linuxserver.io/2018/05/17/how-to-configure-systemd-boot/](https://blog.linuxserver.io/2018/05/17/how-to-configure-systemd-boot/)

I already have the larger EFI partition and blowing it away and starting over is an option that I am fine with...  My only caveat is - keep me out the deep water - my /Home (SDA6) partition has some stuff I'd rather not lose and I left my back up external HD at home - otherwise I'd follow the age old wisdom of "back it up before you try it"... 

Always learning.

Anyway - just an update....

Thanks to everyone.
Frank

---

### Post by oldfred on 2019-04-01
You are showing a grub in the gpt protective MBR for a BIOS boot. Which looks correct for a BIOS boot, but may not work as grub on a gpt partitioned drive really wants the 1MB unformatted partition with the bios_grub flag.

And your UEFI boot uses this:
```
       **[SIZE=1]sda1/EFI/ubuntu/grub.cfg:[/SIZE]**

search.fs_uuid 8cfbeea5-c647-4d98-b744-b46f89774321 root hd0,gpt2 
 set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg 
    
```
At end of report Boot-Repair says it correctly reinstalled grub for sda2 in UEFI mode. So above may now be correct if you boot in UEFI mode?

This is your UEFI boot for install in sda2, but UUID does not exist. So an old install?
This is the file I now edit for every new UEFI install of Ubuntu as they all use grub, so I just have to update UUID.

This is an example of mine where new install in sdb8 overwrote my working install in sda4:
```
#search.fs_uuid 687ae18c-ab0d-4127-a22a-8eb5943e4db3 root hd1,gpt8 
search.fs_uuid c29fc361-ea05-420b-b919-850aeef65dd4 root hd0,gpt4
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
```

So it looks like you have mixed UEFI installs & BIOS installs.  And you are booting with either BIOS and grub in MBR not quite right since missing bios_grub partition or booting in UEFI mode and entry uses a missing partition so will not boot.

You have a lot of UEFI entries. Report runs this to see them. There used to be a major issue if you got too many and filled UEFI's memory.
sudo efibootmgr -v
I would delete all duplicates and any related to old installs.
       sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr

---

### Post by frank105 on 2019-04-01
Thanks again - 

I think my current boot is EFI - I ran this:
```
$ dmesg | grep -i EFI
[    0.000000] efi: EFI v2.40 by American Megatrends
[    0.000000] efi:  ESRT=0x87f69098  ACPI=0x87335000  ACPI 2.0=0x87335000  SMBIOS=0xf05e0  MPS=0xfc980 
[    0.000000] ACPI: UEFI 0x000000008736ADA8 000042 (v01 HPQOEM 8181     00000000 HP   00000000)
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.176024] pci 0000:00:02.0: BAR 2: assigned to efifb
[    0.205506] Registered efivars operations
[    1.287646] efifb: probing for efifb
[    1.287656] efifb: framebuffer at 0xc0000000, using 1920k, total 1920k
[    1.287657] efifb: mode is 800x600x32, linelength=3200, pages=1
[    1.287657] efifb: scrolling: redraw
[    1.287659] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    1.287799] fb0: EFI VGA frame buffer device
[    1.401728] EFI Variables Facility v0.08 2004-May-17
[    1.420484] Loaded UEFI:db cert 'Hewlett-Packard Company: HP UEFI Secure Boot 2013 DB key: 1d7cf2c2b92673BLAHBLAHBLAHb6' linked to secondary sys keyring
[    1.420509] Loaded UEFI:db cert 'Microsoft Windows Production PCA 2011: a92902398e16cBLAHBLAHBLAH9ae17c55' linked to secondary sys keyring
[    1.420534] Loaded UEFI:db cert 'Microsoft Corporation UEFI CA 2011: 13adbf4309bdBLAHBLAHBLAHd522988a' linked to secondary sys keyring
[    1.420648] MODSIGN: Couldn't get UEFI MokListRT
[    2.495999] fb: switching to inteldrmfb from EFI VGA
[    6.114328] Initialized Arguments for Method [HWMC]:  (2 arguments defined for method invocation)
[    6.121776] Initialized Arguments for Method [HWMC]:  (2 arguments defined for method invocation)
[    6.123305] Initialized Arguments for Method [HWMC]:  (2 arguments defined for method invocation)
[    6.123796] Initialized Arguments for Method [HWMC]:  (2 arguments defined for method invocation)
[    6.124024] Initialized Arguments for Method [HWMC]:  (2 arguments defined for method invocation)


```

Based on what I read - looks like my machine UEFI boots.  If it was BIOS booted - it won't show many UEFI entries... 

YES - way too many entries in my boot... 
```
$ sudo efibootmgr -v
BootCurrent: 000F
Timeout: 5 seconds
BootOrder: 000F,0018,000E,0005,0001,0015,9999,0019,0000
Boot0000  Windows Boot Manager    HD(2,GPT,291284de-7e36-44f0-8147-395dad19ffc4,0xfa000,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...a................
Boot0001* Solid State Disk    PciRoot(0x0)/Pci(0x17,0x0)/Sata(1,65535,0)/HD(1,GPT,68bd3d12-7f75-4b58-86ec-1982a7e8a0bc,0x800,0x100000)..BO
Boot0002  USB Drive (UEFI) - Hard Drive    BBS(HD,,0x0)..GO..NO........o.S.a.n.D.i.s.k. .S.D.8.S.N.A.T.-.1.2.8.G.-.1.0.0.6....................A...........................>..Gd-.;.A..MQ..L.6.1.3.3.2.6.2.4.1.0.5.2. . . . . . . . ........BO..NO........c.U.S.B. .2...0. .U.S.B. .F.l.a.s.h. .D.r.i.v.e. .1.1.0.0....................A.......................6..Gd-.;.A..MQ..L.A.A.1.1.0.2.1.7.1.0.0.0.0.2.8.5........BO
Boot0003  USB Drive (UEFI) - Hard Drive    BBS(HD,,0x0)..GO..NO........o.S.a.n.D.i.s.k. .S.D.8.S.N.A.T.-.1.2.8.G.-.1.0.0.6....................A...........................>..Gd-.;.A..MQ..L.6.1.3.3.2.6.2.4.1.0.5.2. . . . . . . . ........BO
Boot0004  USB Drive (UEFI) - Hard Drive    BBS(HD,,0x0)..GO..NO........o.S.a.n.D.i.s.k. .S.D.8.S.N.A.T.-.1.2.8.G.-.1.0.0.6....................A...........................>..Gd-.;.A..MQ..L.6.1.3.3.2.6.2.4.1.0.5.2. . . . . . . . ........BO
Boot0005* Android-x86 8.1-r1    HD(1,GPT,68bd3d12-7f75-4b58-86ec-1982a7e8a0bc,0x800,0x100000)/File(\efi\Android\BOOTx64.EFI)
Boot0006  USB Drive (UEFI) - Hard Drive    BBS(HD,,0x0)..GO..NO........o.S.a.n.D.i.s.k. .S.D.8.S.N.A.T.-.1.2.8.G.-.1.0.0.6....................A...........................>..Gd-.;.A..MQ..L.6.1.3.3.2.6.2.4.1.0.5.2. . . . . . . . ........BO..NO........k.S.a.n.D.i.s.k. .C.r.u.z.e.r. .G.l.i.d.e. .1...2.7....................A.......................>..Gd-.;.A..MQ..L.2.0.0.4.4.3.1.7.0.2.1.6.3.8.6.1.7.5.A.0........BO
Boot0007  USB Drive (UEFI) - Hard Drive    BBS(HD,,0x0)..GO..NO........o.S.a.n.D.i.s.k. .S.D.8.S.N.A.T.-.1.2.8.G.-.1.0.0.6....................A...........................>..Gd-.;.A..MQ..L.6.1.3.3.2.6.2.4.1.0.5.2. . . . . . . . ........BO
Boot0008  USB Drive (UEFI) - Hard Drive    BBS(HD,,0x0)..GO..NO........o.S.a.n.D.i.s.k. .S.D.8.S.N.A.T.-.1.2.8.G.-.1.0.0.6....................A...........................>..Gd-.;.A..MQ..L.6.1.3.3.2.6.2.4.1.0.5.2. . . . . . . . ........BO..NO........c.L.e.x.a.r. .J.u.m.p.D.r.i.v.e. .1.1.0.0....................A.......................6..Gd-.;.A..MQ..L.A.A.M.H.E.O.0.P.E.D.W.9.3.Y.9.W........BO
Boot0009  USB Drive (UEFI) - Hard Drive    BBS(HD,,0x0)..GO..NO........o.S.a.n.D.i.s.k. .S.D.8.S.N.A.T.-.1.2.8.G.-.1.0.0.6....................A...........................>..Gd-.;.A..MQ..L.6.1.3.3.2.6.2.4.1.0.5.2. . . . . . . . ........BO
Boot000A  USB Drive (UEFI) - Hard Drive    BBS(HD,,0x0)..GO..NO........o.S.a.n.D.i.s.k. .S.D.8.S.N.A.T.-.1.2.8.G.-.1.0.0.6....................A...........................>..Gd-.;.A..MQ..L.6.1.3.3.2.6.2.4.1.0.5.2. . . . . . . . ........BO
Boot000B  USB Drive (UEFI) - Hard Drive    BBS(HD,,0x0)..GO..NO........o.S.a.n.D.i.s.k. .S.D.8.S.N.A.T.-.1.2.8.G.-.1.0.0.6....................A...........................>..Gd-.;.A..MQ..L.6.1.3.3.2.6.2.4.1.0.5.2. . . . . . . . ........BO
Boot000C  USB Drive (UEFI) - Hard Drive    BBS(HD,,0x0)..GO..NO........o.S.a.n.D.i.s.k. .S.D.8.S.N.A.T.-.1.2.8.G.-.1.0.0.6....................A...........................>..Gd-.;.A..MQ..L.6.1.3.3.2.6.2.4.1.0.5.2. . . . . . . . ........BO..NO........k.S.a.n.D.i.s.k. .C.r.u.z.e.r. .G.l.i.d.e. .1...2.7....................A.......................>..Gd-.;.A..MQ..L.2.0.0.4.4.3.1.7.0.2.1.6.3.8.6.1.7.5.A.0........BO
Boot000D  USB Drive (UEFI) - Hard Drive    BBS(HD,,0x0)..GO..NO........o.S.a.n.D.i.s.k. .S.D.8.S.N.A.T.-.1.2.8.G.-.1.0.0.6....................A...........................>..Gd-.;.A..MQ..L.6.1.3.3.2.6.2.4.1.0.5.2. . . . . . . . ........BO..NO........k.U.F.D. .U.S.B. .F.l.a.s.h. .D.r.i.v.e. .3.0.0.0....................A.......................>..Gd-.;.A..MQ..L.Z.7.M.L.4.Y.H.N.4.D.K.H.U.L.H.O.6.O.N.S........BO
Boot000E* ubuntu    HD(1,GPT,68bd3d12-7f75-4b58-86ec-1982a7e8a0bc,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)
Boot000F* robolinux_10    HD(1,GPT,68bd3d12-7f75-4b58-86ec-1982a7e8a0bc,0x800,0x100000)/File(\EFI\robolinux_10\shimx64.efi)
Boot0010  USB Drive (UEFI) - Hard Drive    BBS(HD,,0x0)..GO..NO........o.S.a.n.D.i.s.k. .S.D.8.S.N.A.T.-.1.2.8.G.-.1.0.0.6....................A...........................>..Gd-.;.A..MQ..L.6.1.3.3.2.6.2.4.1.0.5.2. . . . . . . . ........BO..NO........c.L.e.x.a.r. .J.u.m.p.D.r.i.v.e. .1.1.0.0....................A.......................6..Gd-.;.A..MQ..L.A.A.M.H.E.O.0.P.E.D.W.9.3.Y.9.W........BO
Boot0011  USB Drive (UEFI) - Hard Drive    BBS(HD,,0x0)..GO..NO........o.S.a.n.D.i.s.k. .S.D.8.S.N.A.T.-.1.2.8.G.-.1.0.0.6....................A...........................>..Gd-.;.A..MQ..L.6.1.3.3.2.6.2.4.1.0.5.2. . . . . . . . ........BO
Boot0012  USB Drive (UEFI) - Hard Drive    BBS(HD,,0x0)..GO..NO........o.S.a.n.D.i.s.k. .S.D.8.S.N.A.T.-.1.2.8.G.-.1.0.0.6....................A...........................>..Gd-.;.A..MQ..L.6.1.3.3.2.6.2.4.1.0.5.2. . . . . . . . ........BO
Boot0013  USB Drive (UEFI) - Hard Drive    BBS(HD,,0x0)..GO..NO........o.S.a.n.D.i.s.k. .S.D.8.S.N.A.T.-.1.2.8.G.-.1.0.0.6....................A...........................>..Gd-.;.A..MQ..L.6.1.3.3.2.6.2.4.1.0.5.2. . . . . . . . ........BO..NO........c.L.e.x.a.r. .J.u.m.p.D.r.i.v.e. .1.1.0.0....................A.......................6..Gd-.;.A..MQ..L.A.A.M.H.E.O.0.P.E.D.W.9.3.Y.9.W........BO
Boot0014  MX17    HD(1,GPT,68bd3d12-7f75-4b58-86ec-1982a7e8a0bc,0x800,0x100000)/File(\EFI\MX17\grubx64.efi)
Boot0015* Solid State Disk    PciRoot(0x0)/Pci(0x17,0x0)/Sata(1,65535,0)/HD(1,GPT,68bd3d12-7f75-4b58-86ec-1982a7e8a0bc,0x800,0x100000)..BO
Boot0016  USB Drive (UEFI) - Hard Drive    BBS(HD,,0x0)..GO..NO........o.S.a.n.D.i.s.k. .S.D.8.S.N.A.T.-.1.2.8.G.-.1.0.0.6....................A...........................>..Gd-.;.A..MQ..L.6.1.3.3.2.6.2.4.1.0.5.2. . . . . . . . ........BO
Boot0017  USB Drive (UEFI) - Hard Drive    BBS(HD,,0x0)..GO..NO........o.S.a.n.D.i.s.k. .S.D.8.S.N.A.T.-.1.2.8.G.-.1.0.0.6....................A...........................>..Gd-.;.A..MQ..L.6.1.3.3.2.6.2.4.1.0.5.2. . . . . . . . ........BO..NO........S.G.e.n.e.r.i.c. .F.l.a.s.h. .D.i.s.k. .8...0.7....................A.......................&..Gd-.;.A..MQ..L.0.8.5.F.0.3.4.5........BO
Boot0018* ubuntu    HD(1,GPT,68bd3d12-7f75-4b58-86ec-1982a7e8a0bc,0x800,0x100000)/File(\EFI\robolinux_10\shimx64.efi)
Boot0019* USB Drive (UEFI) - Hard Drive    BBS(HD,,0x0)..GO..NO........o.S.a.n.D.i.s.k. .S.D.8.S.N.A.T.-.1.2.8.G.-.1.0.0.6....................A...........................>..Gd-.;.A..MQ..L.6.1.3.3.2.6.2.4.1.0.5.2. . . . . . . . ........BO
Boot9999* USB Drive (UEFI)    PciRoot(0x0)/Pci(0x1d,0x0)/USB(16,0)..BO

```

Sorry this is getting so long but...

Anyway - I tried deleting 0014... old install... Seemed to work.  
```
$ sudo efibootmgr -b 0014 -B
BootCurrent: 000F
Timeout: 5 seconds
BootOrder: 000F,0018,000E,0005,0001,0015,9999,0019,0000
Boot0000  Windows Boot Manager
Boot0001* Solid State Disk
Boot0002  USB Drive (UEFI) - Hard Drive
Boot0003  USB Drive (UEFI) - Hard Drive
Boot0004  USB Drive (UEFI) - Hard Drive
Boot0005* Android-x86 8.1-r1
Boot0006  USB Drive (UEFI) - Hard Drive
Boot0007  USB Drive (UEFI) - Hard Drive
Boot0008  USB Drive (UEFI) - Hard Drive
Boot0009  USB Drive (UEFI) - Hard Drive
Boot000A  USB Drive (UEFI) - Hard Drive
Boot000B  USB Drive (UEFI) - Hard Drive
Boot000C  USB Drive (UEFI) - Hard Drive
Boot000D  USB Drive (UEFI) - Hard Drive
Boot000E* ubuntu
Boot000F* robolinux_10
Boot0010  USB Drive (UEFI) - Hard Drive
Boot0011  USB Drive (UEFI) - Hard Drive
Boot0012  USB Drive (UEFI) - Hard Drive
Boot0013  USB Drive (UEFI) - Hard Drive
Boot0015* Solid State Disk
Boot0016  USB Drive (UEFI) - Hard Drive
Boot0017  USB Drive (UEFI) - Hard Drive
Boot0018* ubuntu
Boot0019* USB Drive (UEFI) - Hard Drive
Boot9999* USB Drive (UEFI)

```

Should I wash/rinse/repeat with all the other ones except 000F (Robolinux) and 0005 (Android X86) ?  What about all those USB ones?  That won't prevent me from USB booting will it?  

Oh and - what about the nuking SDA1 concept - any good/bad thoughts on that? 

Anyway - thanks again for all your help. 

Regards,
Frank

---

### Post by frank105 on 2019-04-01
**_[SIZE=2]FRED YOU ARE A GENIUS!!![/SIZE]_**

Okay - so you said.... 

> This is your UEFI boot for install in sda2, but UUID does not exist. So an old install?
This is the file I now edit for every new UEFI install of Ubuntu as they all use grub, so I just have to update UUID.

Sure enough - that UUID does not exist.  So I found the new UUID of SDA2 and I went to the EFI partition and edited the file /boot/efi/EFI/ubuntu/grub.cfg in a text editor (made a backup of the file first...)
and changed the UUID to the correct one for SDA2 - c205b398-acd4-4c73-bdd2-c418b64cdd4e

BOOM - we have a booting machine.  Goes right into GRUB and I can select Robolinux.  No more bash commands needed!!

Okay - we are out of the woods but I am still energized to learn more and do some more cleanup.  I will wait what everyone is thinking.  I think I still have about 64 dozen half baked questions out there. 

Next half baked question - why is it using the grub.cfg of the ubuntu install when robolinux was the most recently installed OS?

Anyway - I will keep studying.  

Thanks again,
Frank

---

### Post by oldfred on 2019-04-01
Was RoboLinux a BIOS install and we converted it to UEFI using Ubuntu's UEFI grub?
The configfile just looks for another grub.cfg to load.
Not sure what then is going on.

You should have /EFI/ubuntu/grub.cfg which is obsolete.
But then should have a new /EFI/robolinux/grub.cfg that has correct partition to boot from.
Or is system booting ubuntu by default but it had wrong UUID?
Check your grub.cfg in /EFI/xxxx or  each install.

If that is using ubuntu entry do not delete, yet.

I would delete all but one of every duplicate entry in UEFI.
Not sure if when you boot USB if it creates new entry or not.

My UEFI only has 4 entries, and I can boot USB flash drive, but have to choose it in UEFI boot menu. External devices normally use /EFI/Boot/bootx64.efi, but that entry can be a fallback or hard drive boot entry. So a drive boot entry may use that.
Full install entries remain in UEFI's memory, until drive is disconnected. Then they seem to be chjanged to some default entry, not sure if that ever works again or not.

---

### Post by frank105 on 2019-04-01
Still learning...

Okay - I know for sure that I edited the grub.cfg file from boot/efi/EFI/ubuntu as it was the one that had the wrong UUID - and where I have a backup...  Looking at the grub.cfg file in boot/efi/EFI/robolinux it is now identical to the corrected one in boot/efi/EFI/ubuntu (that makes sense...)  

Pretty sure that the Robolinux did a standard UEFI install.  

I am sure - that even now I can not boot my Android X86 install normally.  I still have to hit esc/F9 and choose the Android EFI file to boot.  I'd love to clean that up (and learn how)

There is no grub.cfg inside boot/efi/EFI/Android.  There are 3 .efi files:  bootia32.efi, BOOTx64.efi and grubx64.efi.   I don't know how to read inside those files as they don't open in a text editor...
There is one more file - Android.cfg.  It seems "grub-ish" : 
```
# $1 Kernel dir
# $2 Title
# $3... Kernel cmdline
function add_boot_entry {
    menuentry "$2" "$@" --class android-x86 {
        savedefault
        set root=$android
        if [ -e $2/kernel ]; then
            true
        else
            search --no-floppy --set root -f $2/kernel
        fi
        set kd=$2
        shift 3
        linux $kd/kernel root=/dev/ram0 androidboot.selinux=permissive $src $@
        initrd $kd/initrd.img
    }
}

# $1 Title
# $2... Kernel cmdline
function add_entry {
    set title="Android-x86 8.1-r1 $1"
    shift 1
    add_boot_entry "$kdir" "$title" "$@"
}

# $1 EFI to chainload
# $2 OS name
# $3 Class
function add_os_if_exists {
    # Is there a better way to find ESP?
    for d in hd0,gpt1 hd0,gpt2 hd1,gpt1 hd1,gpt2 hd0,msdos1 hd0,msdos2 hd1,msdos1 hd1,msdos2; do
        if [ "($d)$1" != "$cmdpath/$bootefi" -a -e ($d)$1 ]; then
            menuentry "$2 at $d ->" "$d" "$1" --class "$3" {
                savedefault
                set root=$2
                chainloader ($root)$3
            }
            break
        fi
    done
}

function savedefault {
    if [ -s $prefix/grubenv -a "$chosen" != "$default" ]; then
        set default="$chosen"
        save_env default
    fi
}

function load_theme {
    loadfont DejaVuSansMono-18
    set gfxmode=1024x768
    terminal_output gfxterm
    set theme=$prefix/theme/theme.txt
    export theme
}

if [ "$root" == "loop0" ]; then
    set prefix=($root)/boot/grub
fi

if [ -s $prefix/theme/theme.txt ]; then
    load_theme
fi

if [ -s $prefix/grubenv ]; then
    load_env
fi

if [ "$grub_cpu" = "i386" ]; then
    set bootefi=bootia32.efi
    set grub=grubia32
else
    set bootefi=BOOTx64.EFI
    set grub=grubx64
fi

if [ -z "$src" -a -n "$isofile" ]; then
    set src=iso-scan/filename=$isofile
fi

search --no-floppy --set android -f $kdir/kernel
export android bootefi grub kdir live src

# Create main menu
add_entry "$live" quiet
add_entry "$debug_mode" DEBUG=2
if [ -s ($android)$kdir/install.img ]; then
    add_entry "Installation" INSTALL=1
fi

submenu "Advanced options -> " --class forward {
    add_entry "$live - Vulkan support (experimental)" quiet VULKAN=1
    add_entry "$live - No Setup Wizard" quiet SETUPWIZARD=0
    add_entry "$live - No Hardware Acceleration" quiet nomodeset HWACCEL=0
    if [ -s ($android)$kdir/install.img ]; then
        add_entry "Auto Install to specified harddisk" AUTO_INSTALL=0
        add_entry "Auto Update" AUTO_INSTALL=update
    fi
    add_os_if_exists /EFI/BOOT/$bootefi "UEFI OS" os
    add_os_if_exists /EFI/BOOT/fallback.efi "UEFI Fallback" os
    add_os_if_exists /EFI/BOOT/fallback_x64.efi "UEFI Fallback" os
    menuentry "Reboot" --class reboot { reboot }
    menuentry "Poweroff" --class shutdown { halt }
    menuentry "UEFI firmware settings" --class setup { fwsetup }
}

# Add other OSes boot loaders if exist
add_os_if_exists /EFI/fedora/${grub}.efi Fedora fedora
add_os_if_exists /EFI/centos/${grub}.efi CentOS centos
add_os_if_exists /EFI/ubuntu/${grub}.efi Ubuntu ubuntu
add_os_if_exists /EFI/debian/${grub}.efi Debian debian
add_os_if_exists /EFI/gentoo/${grub}.efi Gentoo gentoo
add_os_if_exists /EFI/opensuse/${grub}.efi openSUSE opensuse
add_os_if_exists /EFI/linuxmint/${grub}.efi "Linux Mint" linuxmint
add_os_if_exists /EFI/boto/bootx64.efi OPENTHOS openthos
add_os_if_exists /EFI/Microsoft/Boot/bootmgfw.efi Windows windows

for d in $cmdpath $prefix; do
    if [ -f $d/custom.cfg ]; then
        source $d/custom.cfg
    fi
done
```

The grub file that is booting is definitely the Robolinux one and looks like this: 

```
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}
function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}
function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_gpt
insmod ext2
set root='hd0,gpt2'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  c205b398-acd4-4c73-bdd2-c418b64cdd4e
else
  search --no-floppy --fs-uuid --set=root c205b398-acd4-4c73-bdd2-c418b64cdd4e
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=1920x1080
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
insmod part_gpt
insmod ext2
set root='hd0,gpt2'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  c205b398-acd4-4c73-bdd2-c418b64cdd4e
else
  search --no-floppy --fs-uuid --set=root c205b398-acd4-4c73-bdd2-c418b64cdd4e
fi
insmod png
background_image -m stretch /etc/PinguyBuilder/grub.png
if [ "${recordfail}" = 1 ] ; then
  set timeout=10
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=10
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=10
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_gpt
insmod ext2
set root='hd0,gpt2'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  c205b398-acd4-4c73-bdd2-c418b64cdd4e
else
  search --no-floppy --fs-uuid --set=root c205b398-acd4-4c73-bdd2-c418b64cdd4e
fi
insmod png
if background_image /etc/PinguyBuilder/grub.png; then
  true
else
  set menu_color_normal=cyan/blue
  set menu_color_highlight=white/blue
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=1
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Robolinux_10 GNU/Linux' --class robolinux_10 --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-c205b398-acd4-4c73-bdd2-c418b64cdd4e' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  c205b398-acd4-4c73-bdd2-c418b64cdd4e
    else
      search --no-floppy --fs-uuid --set=root c205b398-acd4-4c73-bdd2-c418b64cdd4e
    fi
        linux    /boot/vmlinuz-4.15.0-43-generic root=UUID=c205b398-acd4-4c73-bdd2-c418b64cdd4e ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-4.15.0-43-generic
}
submenu 'Advanced options for Robolinux_10 GNU/Linux' $menuentry_id_option 'gnulinux-advanced-c205b398-acd4-4c73-bdd2-c418b64cdd4e' {
    menuentry 'Robolinux_10 GNU/Linux, with Linux 4.15.0-43-generic' --class robolinux_10 --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-43-generic-advanced-c205b398-acd4-4c73-bdd2-c418b64cdd4e' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  c205b398-acd4-4c73-bdd2-c418b64cdd4e
        else
          search --no-floppy --fs-uuid --set=root c205b398-acd4-4c73-bdd2-c418b64cdd4e
        fi
        echo    'Loading Linux 4.15.0-43-generic ...'
            linux    /boot/vmlinuz-4.15.0-43-generic root=UUID=c205b398-acd4-4c73-bdd2-c418b64cdd4e ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.15.0-43-generic
    }
    menuentry 'Robolinux_10 GNU/Linux, with Linux 4.15.0-43-generic (recovery mode)' --class robolinux_10 --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-43-generic-recovery-c205b398-acd4-4c73-bdd2-c418b64cdd4e' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  c205b398-acd4-4c73-bdd2-c418b64cdd4e
        else
          search --no-floppy --fs-uuid --set=root c205b398-acd4-4c73-bdd2-c418b64cdd4e
        fi
        echo    'Loading Linux 4.15.0-43-generic ...'
            linux    /boot/vmlinuz-4.15.0-43-generic root=UUID=c205b398-acd4-4c73-bdd2-c418b64cdd4e ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.15.0-43-generic
    }
    menuentry 'Robolinux_10 GNU/Linux, with Linux 4.15.0-39-generic' --class robolinux_10 --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-39-generic-advanced-c205b398-acd4-4c73-bdd2-c418b64cdd4e' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  c205b398-acd4-4c73-bdd2-c418b64cdd4e
        else
          search --no-floppy --fs-uuid --set=root c205b398-acd4-4c73-bdd2-c418b64cdd4e
        fi
        echo    'Loading Linux 4.15.0-39-generic ...'
            linux    /boot/vmlinuz-4.15.0-39-generic root=UUID=c205b398-acd4-4c73-bdd2-c418b64cdd4e ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.15.0-39-generic
    }
    menuentry 'Robolinux_10 GNU/Linux, with Linux 4.15.0-39-generic (recovery mode)' --class robolinux_10 --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-39-generic-recovery-c205b398-acd4-4c73-bdd2-c418b64cdd4e' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  c205b398-acd4-4c73-bdd2-c418b64cdd4e
        else
          search --no-floppy --fs-uuid --set=root c205b398-acd4-4c73-bdd2-c418b64cdd4e
        fi
        echo    'Loading Linux 4.15.0-39-generic ...'
            linux    /boot/vmlinuz-4.15.0-39-generic root=UUID=c205b398-acd4-4c73-bdd2-c418b64cdd4e ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.15.0-39-generic
    }
    menuentry 'Robolinux_10 GNU/Linux, with Linux 4.15.0-38-generic' --class robolinux_10 --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-38-generic-advanced-c205b398-acd4-4c73-bdd2-c418b64cdd4e' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  c205b398-acd4-4c73-bdd2-c418b64cdd4e
        else
          search --no-floppy --fs-uuid --set=root c205b398-acd4-4c73-bdd2-c418b64cdd4e
        fi
        echo    'Loading Linux 4.15.0-38-generic ...'
            linux    /boot/vmlinuz-4.15.0-38-generic root=UUID=c205b398-acd4-4c73-bdd2-c418b64cdd4e ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.15.0-38-generic
    }
    menuentry 'Robolinux_10 GNU/Linux, with Linux 4.15.0-38-generic (recovery mode)' --class robolinux_10 --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-38-generic-recovery-c205b398-acd4-4c73-bdd2-c418b64cdd4e' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  c205b398-acd4-4c73-bdd2-c418b64cdd4e
        else
          search --no-floppy --fs-uuid --set=root c205b398-acd4-4c73-bdd2-c418b64cdd4e
        fi
        echo    'Loading Linux 4.15.0-38-generic ...'
            linux    /boot/vmlinuz-4.15.0-38-generic root=UUID=c205b398-acd4-4c73-bdd2-c418b64cdd4e ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.15.0-38-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/25_custom ###

menuentry "EFI/BOOT/bkpbootx64.efi" {
search --fs-uuid --no-floppy --set=root 7A0A-6071
chainloader (${root})/EFI/BOOT/bkpbootx64.efi
}

menuentry "EFI/Android/bootia32.efi" {
search --fs-uuid --no-floppy --set=root 7A0A-6071
chainloader (${root})/EFI/Android/bootia32.efi
}

menuentry "EFI/BOOT/bootia32.efi" {
search --fs-uuid --no-floppy --set=root 7A0A-6071
chainloader (${root})/EFI/BOOT/bootia32.efi
}

menuentry "EFI/BOOT/fbx64.efi" {
search --fs-uuid --no-floppy --set=root 7A0A-6071
chainloader (${root})/EFI/BOOT/fbx64.efi
}

menuentry "EFI/robolinux_10/mmx64.efi" {
search --fs-uuid --no-floppy --set=root 7A0A-6071
chainloader (${root})/EFI/robolinux_10/mmx64.efi
}

menuentry "EFI/ubuntu/fwupx64.efi" {
search --fs-uuid --no-floppy --set=root 7A0A-6071
chainloader (${root})/EFI/ubuntu/fwupx64.efi
}

menuentry "EFI/ubuntu/mmx64.efi" {
search --fs-uuid --no-floppy --set=root 7A0A-6071
chainloader (${root})/EFI/ubuntu/mmx64.efi
}
### END /etc/grub.d/25_custom ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
    fwsetup
}
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
```


Working in Grub Customizer to see if I can get it to make it boot but this is what I have so far. 

Thanks again for all of the help!
Frank

---

### Post by frank105 on 2019-04-01
Feels like I have been here before....

Anyway - all the time I have for today but...  We have a winner!!

Okay - so I used Grub Customizer to add an entry for my android install.  

Got it this far:
```
set root='(hd0,4)'
search --no-floppy --fs-uuid --set=root 033e8fc7-4cfe-9454-bc59-df7329ca862d
linux /android-8.1-r1/kernel root=/dev/ram0
androidboot.selinux=permissive
initrd /android-8.1-r1/initrd.img
```

Looked like it might boot... but no go. 

So - seems like I remembered this from somewhere - I hit esc and F9 during boot and booted the Android EFI file.  Got the android grub screen - hit e to edit the boot - wrote it down word for word... 

Rebooted into Linux and did the Grub Customizer again - added new "other" entry and retyped it back in word for word:

```
setparams 'Android-x86 8.1-r1 ' '/android-8.1-r1' 'Android-x86 8.1-r1 ' 'quiet'

      savedefault
      set root=$android
      if [ -e $2/kernel ]; then
            true
      else
            search --no-floppy --set root -f $2/kernel
      fi
      set kd=$2
      shift 3
      linux $kd/kernel root=/dev/ram0 androidboot.selinux=permissive $src $@
      initrd $kd/initrd.img


```

Save/reboot....
That did it.  I hate it - since it is the nonsensical style - but it works for today.  

Tomorrow we start again on clean up etc.  

Thanks for everything
Frank

(PS - I like to update these things to remind me next month when I forget it all over again... and to help the next guy that hits this same problem)

---

### Post by oldfred on 2019-04-01
Boot-Repair in 25_custom adds all the .efi boot files it sees. You can delete 25_custom or edit out entries in it to make grub menu smaller.
You do not need the bootia32.efi as that is for 32 bit.
Not sure if UEFI for Android was using bootx64.efi or /Android/grubx64.efi.
If it was using /EFI/Boot/bootx64.efi that is a fallback entry and now grub copies its shimx64.efi or grubx64.efi to bootx64.efi.
And then Boot-Repair checks bootx64.efi and if no bkpbootx64.efi, copies bootx64.efi to the bkpbootx64.efi and makes bootx64.efi a copy of shimx64.efi from Ubuntu. Not sure then what boot repair does if other installs, it may just copy file from system you are using to update UEFI.

Grub has both chainload and configfile type entries. Just like the configfile in UEFI just loads a full grub.cfg from an install, you can use that type of entry to boot using any other installs grub.cfg. Not sure if then it can boot Android.

Did this entry boot Android directly from UEFI?
       Boot0005* Android-x86 8.1-r1    HD(1,GPT,68bd3d12-7f75-4b58-86ec-1982a7e8a0bc,0x800,0x100000)/File(efiAndroidBOOTx64.EFI) 
    
That is made up of a GUID and the path to the .efi boot file in the ESP. The slashes or backslashes seem to be optional.
You can use efibootmgr to create new UEFI entries also.
See
man efibootmgr
also some examples in the link in my signature, but none for Android as I have not seen many with that.

       # Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkp25_custom
# turn off execute bit or it will run backup also
sudo chmod a-x /etc/grub.d/bkp25_custom
sudo nano /etc/grub.d/25_custom
# or if none wanted turn off execute bit on 25_custom
# Then do:
sudo update-grub

---

### Post by frank105 on 2019-04-01
Hey Fred.

Thanks as always.  Sorry - but you are talking over my head again.  I have got the hang of grub customizer and put all the stuff I don't think I need in a subfolder labeled "junk" or something.  All good there.  I am going to skip all the stuff about 25_custom part of grub.  

as for:  > Did this entry boot Android directly from UEFI?
       Boot0005* Android-x86 8.1-r1     HD(1,GPT,68bd3d12-7f75-4b58-86ec-1982a7e8a0bc,0x800,0x100000)/File(efiAndroidBOOTx64.EFI)

Yes - this was the way I always booted Android.  Painful and awkward - I would hit esc then F9 during boot up and then click on the Android X86 boot...  I presume this loads one of the files from SDA1 in the subfolder for Android - looks like BOOTx64.efi .  Is there any way to see inside an .efi file?  

Anyway - as poorly described above - my solution was to select this file and let the grub screen load and then using the grub bash commands - I highlighted "Boot Android X86" and tapped 'e' and it shows the grub command line.....
```
setparams 'Android-x86 8.1-r1 ' '/android-8.1-r1' 'Android-x86 8.1-r1 ' 'quiet'       savedefault
      set root=$android.....etc
```That is what I copied into grub customizer and it works like a champ.  I don't have problems - but I don't want to mark solved yet - since I want to keep pushing onto the next level. I am learning here and want to get over and onto the next level so....  

[LIST=1]
[*]Cleanup - Should I delete a bunch of EFI folders?  Ubuntu and Android seem to be the only ones I am using
[*]When I install a new distro - what is the easy answer.  Should I have it install grub?  In my EFI partition or in the root partition of the new distro? Or ??
[*]Should I push into rEFInd - any success stories out there?
[*]Is there a better solution out there for obsessive distro hoppers?  What should I know about SysteMD?
[/LIST]

Okay - getting late here in Central America.  Gonna check on this in the morning.  

Thanks again!

Regards,
Frank

---

### Post by oldfred on 2019-04-02
Those that have had major issues with grub, often use rEFInd. I keep a flash drive or two with rEFInd. I was able to finally reuse one of my first, now tiny, flash drives that otherwise is too small for much else.

You can delete an folders in /EFI/... that you do not use. Keep /EFI/Boot and any actual installs you still have.
Delete all duplicates and old installs in UEFI with efibootmgr.

With UEFI and Ubuntu's ubiquity or grub, it only installs to the first ESP, usually sda or first NVMe drive, no matter what settings you use (I have tried). I just tried 19.04 to see if any improvements. Grub even says it is installing to sdb in ubiquity when installing, but it still overwrote my /EFI/ubuntu folder on sda. 
I believe the ubiquity -b command still works in the installer, which does not install grub. That then only works if you have another grub that you can update to boot new install.

I am changing my grub entries to boot by label & configfile, which works well for my multiple reinstalls to test 19.04 and how it installs grub.

Do not know systeMD?
Note that Grub Customizer, replaces all the grub scripts with its own (proxy files). So you now do not have standard grub2.
[https://ubuntuforums.org/showthread.php?t=2279347&page=3](https://ubuntuforums.org/showthread.php?t=2279347&page=3)

---

### Post by frank105 on 2019-04-02
New wrinkle - 


I tried to boot to a USB drive today - I hit esc  like normal and then F9 like normal.  But the familiar black with blue  screen listing my boot options - where I would select USB is just not  there.  It is a blank black screen.  Nothing happens.  Eventually I have  to hit ctrl+alt+del and it reboots and it will boot to grub where I can select Robolinux  and that all works fine.  

I went into bios and confirmed  USB boot was enabled.  Switched off and back on for good measure.  Still  nothing.   

This sounds really weird - But Fred - you mentioned that things can go wacky if your UEFI files filled the memory or something... 
> You have a lot of UEFI entries. Report runs this to see them. There used  to be a major issue if you got too many and filled UEFI's memory.

Could this be the dilemma?  My EFI folder is 19.2MB it says...

I would clean up and delete some EFI files but that sounds serious so I want ask first.
Here is what I have:
```
$ tree 
.
&#9500;&#9472;&#9472; Android
&#9474;   &#9500;&#9472;&#9472; android.cfg
&#9474;   &#9500;&#9472;&#9472; bootia32.efi
&#9474;   &#9500;&#9472;&#9472; BOOTx64.EFI
&#9474;   &#9492;&#9472;&#9472; grubx64.efi
&#9500;&#9472;&#9472; BOOT
&#9474;   &#9500;&#9472;&#9472; bkpbootx64.efi
&#9474;   &#9500;&#9472;&#9472; bootia32.efi
&#9474;   &#9500;&#9472;&#9472; bootx64.efi
&#9474;   &#9500;&#9472;&#9472; efi.img
&#9474;   &#9500;&#9472;&#9472; fbx64.efi
&#9474;   &#9500;&#9472;&#9472; grub.cfg
&#9474;   &#9492;&#9472;&#9472; grubx64.efi
&#9500;&#9472;&#9472; robolinux_10
&#9474;   &#9500;&#9472;&#9472; BOOTX64.CSV
&#9474;   &#9500;&#9472;&#9472; grub.cfg
&#9474;   &#9500;&#9472;&#9472; grubx64.efi
&#9474;   &#9500;&#9472;&#9472; mmx64.efi
&#9474;   &#9492;&#9472;&#9472; shimx64.efi
&#9492;&#9472;&#9472; ubuntu
    &#9500;&#9472;&#9472; BOOTX64.CSV
    &#9500;&#9472;&#9472; fw
    &#9500;&#9472;&#9472; fwupx64.efi
    &#9500;&#9472;&#9472; grub.cfg
    &#9500;&#9472;&#9472; grubx64.efi
    &#9500;&#9472;&#9472; mmx64.efi
    &#9492;&#9472;&#9472; shimx64.efi


```
So based on what we have learned so far - my pc is actually using the ubuntu files to boot... 95% sure...  So I am guessing that I could delete the actual robolinux_10 folder?  Guessing I could also delete the BOOT folder too?  

But here is where it gets scary - if I mess this up and it doesn't boot AND it won't boot to a thumb drive - I could be left with a paper weight until I get my new hard drive?

Maybe I will delete only the robolinux_10 folder?  I could copy it to the HD just in case - but of course if it won't boot and won't boot via usb I could be into that paper weight scenario again. 


Can I add an echo line to one of the grub files or something to prove which file I am booting or... I am in over my head at this point...
 

Any ideas? 

Thanks in advance!
Frank

---

### Post by VMC on 2019-04-02
> **oldfred said:**
>  ESP, usually sda or first NVMe drive, no matter what settings you use (I have tried). I just tried 19.04 to see if any improvements. Grub even says it is installing to sdb in ubiquity when installing, but it still overwrote my /EFI/ubuntu folder on sda. 
I believe the ubiquity -b command still works in the installer, which does not install grub. That then only works if you have another grub that you can update to boot new install.
 I found out that the hard way. I pointed grub to install on sdb, and it did, but also installed itself on esp and messed up my sda boot. From now on I will unplug sda and ONLY have sdb active.
> I am changing my grub entries to boot by label & configfile, which works well for my multiple reinstalls to test 19.04 and how it installs grub. That's an interesting idea. Is the configfile between menus?

---

### Post by oldfred on 2019-04-02
The issue with full UEFI, was with UEFI's NVRAM on motherboard. It really seemed to apply to certain brand of UEFI, and then only a few brands of computers. And issue was that UEFI NVRAM was only half full, but only fix was send system back to vendor. Orginally blamed on Linux, but found Windows could also cause issue.

For your ESP, you just have to make sure it is not too full, just like any other partition. And most backup software does not back it up, so I regularly copy it to my ESP on sdb which may not directly boot installs on sdb without adding entries to UEFI, but then should work.
This quickly shows use.
df -h

Since I reinstall Disco to same partition and reformat it, I have to remember to add partition label. And then in 40_custom of main working install I already have a boot entry. I also boot ISO, and edit just a text file with standard grub boot stanza. I always forgot to run update-grub when changing ISO, but with text file, and configfile in grub menu, I do not have to update grub with every edit.
      ```
 # spacer line
menuentry " " {
set root= 
} 

 menuentry "Ubuntu 19.04 Disco  (on /dev/sdb8)" {
 search --set=root --label disco --hint hd1,gpt8
configfile /boot/grub/grub.cfg 
 } 

 menuentry 'Live ISOs on SSD' {
configfile (hd0,3)/ISO/livecdimage.cfg
}  
    
   
```

---

### Post by frank105 on 2019-04-02
Thanks again.

Sorry for being such a newbee but I am still trying to translate your reply Fred.  

It is starting to feel like my NVRAM is too full?  Not sure how to clean it up.

Here is my current list from efibootmgr

```
$ sudo efibootmgr -v
[sudo] password for rj: 
BootCurrent: 0018
Timeout: 5 seconds
BootOrder: 0018,000E,000F,0005,0015,0001,9999,0019,0000,0003,0002,0006,000B,000D,0013
Boot0000  Windows Boot Manager    HD(2,GPT,291284de-7e36-44f0-8147-395dad19ffc4,0xfa000,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...a................
Boot0001* Solid State Disk    PciRoot(0x0)/Pci(0x17,0x0)/Sata(1,65535,0)/HD(1,GPT,68bd3d12-7f75-4b58-86ec-1982a7e8a0bc,0x800,0x100000)..BO
Boot0002  USB Drive (UEFI) - Hard Drive    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)..GO
Boot0003  USB Drive (UEFI) - Hard Drive    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)..GO
Boot0004  USB Drive (UEFI) - Hard Drive    BBS(HD,,0x0)..GO..NO........o.S.a.n.D.i.s.k. .S.D.8.S.N.A.T.-.1.2.8.G.-.1.0.0.6....................A...........................>..Gd-.;.A..MQ..L.6.1.3.3.2.6.2.4.1.0.5.2. . . . . . . . ........BO
Boot0005* Android-x86 8.1-r1    HD(1,GPT,68bd3d12-7f75-4b58-86ec-1982a7e8a0bc,0x800,0x100000)/File(\efi\Android\BOOTx64.EFI)
Boot0006  USB Drive (UEFI) - Hard Drive    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)..GO
Boot0007  USB Drive (UEFI) - Hard Drive    BBS(HD,,0x0)..GO..NO........o.S.a.n.D.i.s.k. .S.D.8.S.N.A.T.-.1.2.8.G.-.1.0.0.6....................A...........................>..Gd-.;.A..MQ..L.6.1.3.3.2.6.2.4.1.0.5.2. . . . . . . . ........BO
Boot0008  USB Drive (UEFI) - Hard Drive    BBS(HD,,0x0)..GO..NO........o.S.a.n.D.i.s.k. .S.D.8.S.N.A.T.-.1.2.8.G.-.1.0.0.6....................A...........................>..Gd-.;.A..MQ..L.6.1.3.3.2.6.2.4.1.0.5.2. . . . . . . . ........BO..NO........c.L.e.x.a.r. .J.u.m.p.D.r.i.v.e. .1.1.0.0....................A.......................6..Gd-.;.A..MQ..L.A.A.M.H.E.O.0.P.E.D.W.9.3.Y.9.W........BO
Boot0009  USB Drive (UEFI) - Hard Drive    BBS(HD,,0x0)..GO..NO........o.S.a.n.D.i.s.k. .S.D.8.S.N.A.T.-.1.2.8.G.-.1.0.0.6....................A...........................>..Gd-.;.A..MQ..L.6.1.3.3.2.6.2.4.1.0.5.2. . . . . . . . ........BO
Boot000A  USB Drive (UEFI) - Hard Drive    BBS(HD,,0x0)..GO..NO........o.S.a.n.D.i.s.k. .S.D.8.S.N.A.T.-.1.2.8.G.-.1.0.0.6....................A...........................>..Gd-.;.A..MQ..L.6.1.3.3.2.6.2.4.1.0.5.2. . . . . . . . ........BO
Boot000B  USB Drive (UEFI) - Hard Drive    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)..GO
Boot000C  USB Drive (UEFI) - Hard Drive    BBS(HD,,0x0)..GO..NO........o.S.a.n.D.i.s.k. .S.D.8.S.N.A.T.-.1.2.8.G.-.1.0.0.6....................A...........................>..Gd-.;.A..MQ..L.6.1.3.3.2.6.2.4.1.0.5.2. . . . . . . . ........BO..NO........k.S.a.n.D.i.s.k. .C.r.u.z.e.r. .G.l.i.d.e. .1...2.7....................A.......................>..Gd-.;.A..MQ..L.2.0.0.4.4.3.1.7.0.2.1.6.3.8.6.1.7.5.A.0........BO
Boot000D  USB Drive (UEFI) - Hard Drive    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)..GO
Boot000E* ubuntu    HD(1,GPT,68bd3d12-7f75-4b58-86ec-1982a7e8a0bc,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)
Boot000F* robolinux_10    HD(1,GPT,68bd3d12-7f75-4b58-86ec-1982a7e8a0bc,0x800,0x100000)/File(\EFI\robolinux_10\shimx64.efi)
Boot0010  USB Drive (UEFI) - Hard Drive    BBS(HD,,0x0)..GO..NO........o.S.a.n.D.i.s.k. .S.D.8.S.N.A.T.-.1.2.8.G.-.1.0.0.6....................A...........................>..Gd-.;.A..MQ..L.6.1.3.3.2.6.2.4.1.0.5.2. . . . . . . . ........BO..NO........c.L.e.x.a.r. .J.u.m.p.D.r.i.v.e. .1.1.0.0....................A.......................6..Gd-.;.A..MQ..L.A.A.M.H.E.O.0.P.E.D.W.9.3.Y.9.W........BO
Boot0011  USB Drive (UEFI) - Hard Drive    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)..GO
Boot0012  USB Drive (UEFI) - Hard Drive    BBS(HD,,0x0)..GO..NO........o.S.a.n.D.i.s.k. .S.D.8.S.N.A.T.-.1.2.8.G.-.1.0.0.6....................A...........................>..Gd-.;.A..MQ..L.6.1.3.3.2.6.2.4.1.0.5.2. . . . . . . . ........BO
Boot0013  USB Drive (UEFI) - Hard Drive    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)..GO
Boot0015* Solid State Disk    PciRoot(0x0)/Pci(0x17,0x0)/Sata(1,65535,0)/HD(1,GPT,68bd3d12-7f75-4b58-86ec-1982a7e8a0bc,0x800,0x100000)..BO
Boot0016  USB Drive (UEFI) - Hard Drive    BBS(HD,,0x0)..GO..NO........o.S.a.n.D.i.s.k. .S.D.8.S.N.A.T.-.1.2.8.G.-.1.0.0.6....................A...........................>..Gd-.;.A..MQ..L.6.1.3.3.2.6.2.4.1.0.5.2. . . . . . . . ........BO
Boot0017  USB Drive (UEFI) - Hard Drive    BBS(HD,,0x0)..GO..NO........o.S.a.n.D.i.s.k. .S.D.8.S.N.A.T.-.1.2.8.G.-.1.0.0.6....................A...........................>..Gd-.;.A..MQ..L.6.1.3.3.2.6.2.4.1.0.5.2. . . . . . . . ........BO..NO........S.G.e.n.e.r.i.c. .F.l.a.s.h. .D.i.s.k. .8...0.7....................A.......................&..Gd-.;.A..MQ..L.0.8.5.F.0.3.4.5........BO
Boot0018* ubuntu    HD(1,GPT,68bd3d12-7f75-4b58-86ec-1982a7e8a0bc,0x800,0x100000)/File(\EFI\robolinux_10\shimx64.efi)
Boot0019* USB Drive (UEFI) - Hard Drive    BBS(HD,,0x0)..GO..NO........o.S.a.n.D.i.s.k. .S.D.8.S.N.A.T.-.1.2.8.G.-.1.0.0.6....................A...........................>..Gd-.;.A..MQ..L.6.1.3.3.2.6.2.4.1.0.5.2. . . . . . . . ........BO
Boot9999* USB Drive (UEFI)    PciRoot(0x0)/Pci(0x1d,0x0)/USB(16,0)..BO


```

The only 2 things that I did between being able to boot with a USB and not were:
[LIST=1]
[*]Edit grub using the grub customizer - which Fred you pointed out changes the entire file (makes it bigger?) 
[*]I deleted "Boot0014".  It was from my MX Linux install from maybe 2 months ago. 
[/LIST]
```
Boot0014  MX17    HD(1,GPT,68bd3d12-7f75-4b58-86ec-1982a7e8a0bc,0x800,0x100000)/File(\EFI\MX17\grubx64.efi)
```

So - I asked previously if I should delete a bunch of those other entries including the USB Drive ones?  Looks like I should stay away from any of the ones marked with a "*" - as it seems the PC thinks those are active (and some are).  

But I am starting to worry a bit about messing it up.  Right now my PC boots and all is good.  Of course - I am itching to try another distro... but I can't without booting to usb.  I can't format my HD - but I can do that in June... but not sure that will help.  So maybe I have to wait?  Or is deleting some of the EFI files a real likely and safe thing to try?

VMC - are you suggesting that it is possible to backup or move my ESP to a thumb drive?

I am over my head here...

I posted a question on HP's support site - but no one has answered yet.  Not sure that any one will - but worth a shot.  Googling more on the NVRAM on the motherboard... never heard of it before today.  

Anyway - anybody got any ideas?

Thanks as always!
Frank

---

### Post by oldfred on 2019-04-02
Look at each of the identical ones.
And delete all but one. 
2 & 3 & B & D look identical.
4 and 6 thru A, 10, 12, 16, and 19 which has *. Or maybe only keep 19.

It almost looks like every time you boot from flash drive your UEFI is saving that as a new entry.
Most UEFI delete entries when a drive is disconnected, so not sure why you have so many USB boot entries.

---

### Post by VMC on 2019-04-02
Frank, I think oldfred mentioned usb backup, but I also backed up partition, then realize all I need to do is backup the files, so I 'tar'ed' the partition or rather "/boot/efi/"

One thing I can't do and it appears oldfred can is boot live iso using his configfile method. I tried using the old mbr method. That will work if Secure Boot is off.

---

### Post by oldfred on 2019-04-06
Frank,
I gather you have not housecleaned duplicates.
Deleting an entry from some old install, should never make a difference. Worst case is that your new install would have to have grub reinstalled to be first in UEFI boot order.
You should always be able to boot USB flash drive.
They do not normally boot from saved UEFI boot menu, but separately from UEFI boot entry. It looks like your UEFI may save the entry, but then when you disconnect flash drive, it reverts to a default .
All UEFI systems boot from /EFI/Boot/bootx64.efi. My system will show another hard drive in boot options  called UEFI PMAP, but most use label or name of flash drive.
If UEFI not booting, you may need to create new flash drive. Some cases an install writes incorrectly to the flash drive since it gets promoted to sda.

---

