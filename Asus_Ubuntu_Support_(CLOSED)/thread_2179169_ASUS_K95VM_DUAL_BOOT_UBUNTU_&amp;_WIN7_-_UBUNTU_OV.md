---
title: "ASUS K95VM DUAL BOOT UBUNTU &amp; WIN7 - UBUNTU OVERHEATS IN 20 sec &amp; CRASHES, WIN7 COLD"
date: 2013-10-06
forum: Asus Ubuntu Support (CLOSED)
---

### Post by ccNFNhT on 2013-10-06
[B]Hi 
dear gurus and holy folk, I defer to your revered views for any advice and/or help,[/B]

I have installed Ubuntu 12.04 through windows (not Wubi, of course).
 I just popped in the DVD and to my surprise it worked and just asked me to install linux, which it did within 15 minutes side by side to Windows 7, creating a neat dual boot, and not using Grub but the standard windows boot menu, which is fine by me. So far, great!

However, windows 7 is stable as a rock, and leaves my laptop cold as an iceberg, unless i push it to its limits. No fans ever run, unless I really make this beast of a laptop struggle.

**As soon as I boot into Ubuntu though, I have about 20 seconds or less before the fans sound like a steam engine, then my laptop suddenly powers off because it has (seemingly) overheated (??). Sometimes I don't even have time to type my password to log in!**

I assume, Ubuntu is making my system run on overdrive for some reason.. or for no reason. I'm afraid to keep trying, in case it destroys one of my HDDs as it shuts off abruptly.

here are my system specs:
--------------

ASUSTeK K95VM (laptop Model)
BIOS: American Megatrends Latest Version (230) 
Main HDD 3.5'' Toshiba 1TB @ 7200 rpm: SATA AHCI EFI GPT (NTFS, OEM Windows 7 Ultimate x64 SP1) 
Secondary HDD 2.5'' Seagate 1TB @ 7200 rpm: SATA AHCI GPT (NTFS, empty for the time being)
Memory: 16GB DDR3 DUAL RAM
Main Graphics Card: NVIDIA GeForce GT 630M (327.23)
Secondary Graphics Card (onboard graphics) Intel HD Graphics 4000, rev.9
Mainboard: ASUSTek Computer INC/ k95VM 1.0
Chipset: Intel, Ivy Bridge, Rev. 09
Southbridge: Intel, HM76, Rev. 04
CPU: Intel Core i7 3610QM @ 2.30GHz (I think it has 4 cores and 8 threads, but was sold to me as 8-core...)
Sound: I don't think it matters for our purposes here, some "Realtek HD Audio" thing..
________________

Ok, so guys, I'm a complete idiot to some linux code stuff. I'm just a graphic designer. Some windowz running software is becoming super expensive to keep buying new versions for, and I've started using freebies in Ubuntu as an alternative to layout for brochures at least... If you could get Ubuntu up and running for me (without burning my machine or HDDs), I'd love you for it and spread the good digital voice around!

1) Is this happening due to some kind of Kernel problem? Or is it lack of drivers for my Intel CPUs or Nvidia GPU? How do I find out what's the cause?
2) can this be fixed from Grub? because I can't even run ubuntu long enough before it crashes to make any changes, I've even put a giant fan under my laptop keeping it cool... to no avail, it lasted about 1 minute longer, then shut off
3) Is it related to my graphics card(s)?
4) Is is BIOS related?
5) Is it HDD related?
6) in any case, can we find out what causes the crashes/unexpected shutdown in Ubuntu? Is there a log file? If yes, How do I get it to send it to you here?
7) could it be hardware related?
8) Could the thermal sticky putty stuff that rests on top of the cPUs (or the gPU) be worn out? and perhaps Ubunutu is asking for a bit tad much more than Windows and it shuts off? (when I touch underneath it is still relatively cold. just the fans screaming, and the air that comes out is warm-hot-ish, not hot; i've felt it hotter, way hotter in windows when doing some intense stuff in photoshop on 20GB files...) If it's this sticky thermal putty thing, how can I fix it myself? (yes I'm broke, and it doesn't hurt fixing this in addition to other stuff listed above)

It's mostly the left fan going wonka when in ubuntu. (maybe this matters)

thank yoU!

---

### Post by oldfred on 2013-10-08
I do not have dual video but many post that Bumblebee works. Do not know if the very latest nVidia drivers work better, but they may need newest kernel that will be in the current beta of 13.10.
 nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)

Bumblebee:
 [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)
12.10 with bumblebee
[http://ubuntuforums.org/showthread.php?t=2077451](http://ubuntuforums.org/showthread.php?t=2077451)
NVIDIA Confirms It's Working On Optimus Linux Support - Aug 31, 2012
[http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY](http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY)
Released 319.12 Beta April 2013
[http://www.phoronix.com/scan.php?page=news_item&px=MTM0NzE](http://www.phoronix.com/scan.php?page=news_item&px=MTM0NzE)
Released 319.17 certified driver May 2013 only uses nVidia so power consumption high
[http://www.nvidia.com/object/linux-display-amd64-319.17-driver.html](http://www.nvidia.com/object/linux-display-amd64-319.17-driver.html)
Some discussion of limits of new nVidia driver with some Optimus support
[http://ubuntuforums.org/showthread.php?t=2142215](http://ubuntuforums.org/showthread.php?t=2142215)

---

### Post by Linuxisfast on 2013-10-08
Nvidia works well in Ubuntu 12.04.3 LTS with current implementation of Optimus, it uses nvidia-prime and patched 3.8 kernel to run nvidia 319 driver. However bear in mind that temps go higher due to the Nvidia card always being on. If you wish to keep temps down, your best bet is to use Bumblebee but that won't work with 319 in Ubuntu so you need to use newer driver.

---

### Post by ccNFNhT on 2013-10-12
Like I say in my post, I DO NOT EVEN HAVE enough time on ubuntu to do anything, let alone install nvidia drives or bumblebee, before the fans start screaming and the motherboard failsafe kicks in and shuts everything off abruptly! Is there any way I could have/set up a Ubuntu distro with my Nvidia drivers/bumblebee drivers already set up, so upon install everything will be working smoothly?

---

### Post by ccNFNhT on 2013-10-12
I have cleaned my fans down to the very last spec of dust, but still no change; 
besides, the fans and the laptop interior were very very clean to begin with.

Any ideas?

I also discovered that this problem does not only happen when I load ubuntu. 

My fans start spinning very high and my motherboard failsafe kicks in within a few seconds to shut the laptop off, 
if i am running ANYTHING outside windows. 

Seriously, If I stay in the boot options for too long, the fans roar, system shuts off,
 be it GRUB, Windows bootloader, or whatever options from any boot CD! 

If i start from a boot disk, i.e. BartPE windows, Gparted, Ubuntu Live, Acronis True Image Live, Caine, Windows recovery Disk, ...ANYTHING it always results in the fans running high
 and then the system shutting off. &#921;t even happens if i linger in the BIOS settings for too long!!!

However, if I am in windows, everything is STABLE!! the fans as smooth, or not running at all,
 and I have never had a system crash thus far that I can remember (at least never after the fans were going nuts).
In fact, I have had my fan speeds roar and my laptop get really hot while in windows, either when playing games
or when working and doing some really intensive graphics editing, but my system NEVER crashes!

What could be causing this?!???????

---

### Post by Linuxisfast on 2013-10-12
Try downloading latest Ubuntu 13.10 beta which has newer kernel, then install Bumblebee and nvidai driver to see if this issue persists.

---

### Post by CDR Services on 2013-10-25
If the overheat even happens while in the bios settings it sounds like a hardware problem that somehow windows is minimizing! My guess would be a faulty heatsink or heatpipe. I wonder if windows is throttling the CPU to keep it cooler! Does the exhaust from the vents feel warm, if it's blowing out cold air but still overheating it means the cooler isn't working properly. If it is blowing warm air I would maybe look for a bios update!

---

