---
title: "I need Audio Drivers for Motherboard Asus P5ND2-SLI Deluxe"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2007-02-13
Hello!

I am trying to get some Audio output from my Mobo...
The Mobo is [color=blue]Asus P5ND2-SLI Deluxe[/color].
Product info, here: [http://uk.asus.com/search.aspx?searchitem=1&searchkey=p5nd2-sli+deluxe](http://uk.asus.com/search.aspx?searchitem=1&searchkey=p5nd2-sli+deluxe)
I activated everything inside "[color=blue]alsamixer[/color]".
But Nothing!
The Mobo is installed a [color=blue]Realtek ALC850 AC 97 Audio Codec[/color].
The Mobo does NOT use an Intel Chipset.
The Mobo uses an Nvidia Chipset.
I don't know if that helps, but from what I have been told, by the time Nvidia created a chip to support SLI, Intel did not have one...
That is why Asus selected to install Nvidia chipset on the Mobo instead of installing an Intel one... (I don't know if this helps...)

I tried to record sound using:

```
arecord a.wav
aplay a.wav
```

... but can NOT hear anything...

Using "[color=blue]aplay -l[/color]" prints the following:

```
tony@tony-desktop:~$ [color=blue]aplay -l[/color]
**** List of PLAYBACK Hardware Devices ****
card 0: MCP04 [[color=blue]NVidia MCP04[/color]], device 0: [color=red]Intel ICH[/color] [[color=blue]NVidia MCP04[/color]]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: MCP04 [NVidia MCP04], device 2: Intel ICH - IEC958 [NVidia MCP04 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

This does **NOT** look like the [color=red]Intel HDA[/color] audio...
So, what do I do?
I do NOT think I can use this:
[http://ubuntuforums.org/showthread.php?t=258878](http://ubuntuforums.org/showthread.php?t=258878)
...because it talks about Intel HDA audio, and I don't think that I could follow this...
Can I?

Thanks.

P.S.> BTW, _even_ in Windows XP SP2, the audio out does NOT work!!!
I used the attached CD-Rom to install drivers.
The drivers installed perfectly in Windows (i.e. inside Device Manager I don't have any exclamations marks).
BUT I can't get any audio out from my speakers...:confused:
What do I do?
BTW, the jacks are installed correctly on the Machine... (I am NOT soooo dumb... :))

---

### Post by renzokuken on 2007-02-13
i have the same / similar chipset in my laptop. sound didnt work at all initially, then i compiled the latest alsa-driver from source, rebooted and it worked perfectly.

if you need help doing this let me know

---

### Post by dvarsam on 2007-02-13
[QUOTE=renzokuken]I have the same / similar chipset in my laptop. sound didnt work at all initially, then i compiled the latest alsa-driver from source, rebooted and it worked perfectly.

if you need help doing this let me know[/QUOTE]

Hello & thanks for your reply!

_Questions_:
1. Did your Audio did NOT work in Windows too?
2. Does alsa support this: "[color=red]Intel ICH[/color] [[color=blue]NVidia MCP04[/color]]" too?
3. Where can I find the latest alsa driver, to try them out?
4. Is there any easy step-by-step install howto, to guide me through?
5. Is there anything else I need to know?

Thanks.

---

### Post by renzokuken on 2007-02-13
sadly mine DID work in XP, just not ubuntu, but this may be worth a try anyway.

1. download the following file to your desktop [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc2.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc2.tar.bz2)

2. extract it 
```
cd Desktop
```
```
tar xjvf alsa-driver-1.0.14rc2.tar.bz2
```
change to that directory
```
cd alsa*
```

3. compile it
```
./configure
make
sudo make install
```

4. reboot and see what happens

---

### Post by dvarsam on 2007-02-13
> **renzokuken said:**
> ...
3. compile it
```
./configure
make
sudo make install
```
...

What about the "[color=blue]./configure[/color]" command:

What options should I use:

1. ./configure --with-cards=[color=red]hda-intel[/color]
2. ./configure --with-cards=[color=red]intel8x0[/color]

The above 2 I used in diff Mobos...
What option should I use for this one?
Mine looks like it is from [color=red]Nvidia[/color]...
I also tried to look through "[color=blue]man configure[/color]", for options, but got nothing...!!!

Thanks.

---

### Post by dvarsam on 2007-02-13
Hello again!

I thought that the HowTo link I provided was supposed to be used _only_ for [color=blue]Intel HDA[/color] (High Definition Audio) Drivers.
But I guess that it can be used in any Mobo - no matter what Audio Chip is embedded...
Please correct me if I am wrong here.

So I followed that how to & opened the file in:
"[color=blue]home/tony/Desktop/alsa-driver-1.0.14rc2/alsa-kernel/Documentation/ALSA-Configuration.txt[/color]".

I found the following:

```
Module [color=blue]snd-intel8x0[/color]
  -------------------

    Module for AC'97 motherboards from Intel and compatibles.
			* Intel i810/810E, i815, i820, i830, i84x, MX440
				ICH5, ICH6, ICH7, ESB2
			* SiS 7012 (SiS 735)
			* NVidia NForce, NForce2, NForce3, [color=blue]MCP04[/color], CK804
				 CK8, CK8S, MCP501
			* AMD AMD768, AMD8111
			* ALi m5455

    [color=blue]ac97_clock[/color]	  - AC'97 codec clock base (0 = auto-detect)
    [color=blue]ac97_quirk[/color]    - AC'97 workaround for strange hardware
		    See "AC97 Quirk Option" section below.
    buggy_irq     - Enable workaround for buggy interrupts on some
                    motherboards (default yes on nForce chips,
		    otherwise off)
    buggy_semaphore - Enable workaround for hardwares with buggy
		    semaphores (e.g. on some ASUS laptops)
		    (default off)
    spdif_aclink  - Use S/PDIF over AC-link instead of direct connection
		    from the controller chip
		    (0 = off, 1 = on, -1 = default)

    This module supports one chip and autoprobe.

    Note: the latest driver supports auto-detection of chip clock.
    if you still encounter too fast playback, specify the clock
    explicitly via the module option "ac97_clock=41194".

    Joystick/MIDI ports are not supported by this driver.  If your
    motherboard has these devices, use the ns558 or snd-mpu401
    modules, respectively.

    The power-management is supported.
```

So, based on the above, in the step of your "./configure", I need to use instead "[color=blue]./configure --with-cards=[/color][color=red]intel8x0[/color]".

Before I went with the installation, I first installed:

1. [color=blue]gawk_1%3a3.1.5.dfsg-4_i386.deb[/color]
2. [color=blue]libncurses5-dev_5.5-2ubuntu1_i386.deb[/color]
    (with all required dependencies)

I then installed:

1. [color=blue]alsa-driver-1.0.14rc2.tar.bz2[/color]
2. [color=blue]alsa-lib-1.0.14rc2.tar.bz2[/color]
3. [color=blue]alsa-utils-1.0.14rc2.tar.bz2[/color]

I then edited the file named "[color=blue]/etc/modprobe.d/alsa-base[/color]" & added at the end of the file:

[color=blue]options[/color] [color=red]snd-intel8x0[/color] [color=blue]model=[/color][color=red]ac97_clock[/color]

I restarted the Ubuntu PC & on the Top Panel the Volume Control has a big X on it...
Also, I can't run "[color=blue]alsamixer[/color]".

I then tried adding instead:

[color=blue]model=[/color][color=red]ac97_quirk[/color]

I restarted the Ubuntu PC & got the same results.... :-k

I then disabled that line & restarted my Ubuntu PC.
I can now run "[color=blue]alsamixer[/color]".
I un-muted everything & setup all volume levels to Max.
Still can NOT hear a thing!!!

Any ideas?

Thanks.
P.S.> As I have previously mentioned, I can't hear audio NOT even in Windows...
... with NO exclamation mark showing on Windows Device Manager.

---

### Post by renzokuken on 2007-02-13
could even be something to do with your bios then.......weird

---

### Post by Rhubarb on 2007-02-13
If you can't get the sound working from a clean install of windows, then things sound bad for you (pun intended).

Go to the manufacturer's website [http://www.asus.com/](http://www.asus.com/) and download the latest windows audio drivers.  Get them installed (in windows).  If sound still does not work, then consider plugging in some headphones (instead of speakers) and play a test audio file again.

If there's still no success, then you just may have a faulty motherboard there.

Edit: renzokuken could be right, download and install the latest BIOS update from Asus' website too.
PS, if there's any n-force motherboard drivers on Asus' website, download and install them in windows as well.
Your first priority is to get sound working in windows (as is advertised).

---

### Post by dvarsam on 2007-02-13
[QUOTE=Rhubarb]If you can't get the sound working from a clean install of windows, then things sound bad for you (pun intended).

Go to the manufacturer's website [http://www.asus.com/](http://www.asus.com/) and download the latest windows audio drivers.  Get them installed (in windows).  If sound still does not work, then consider plugging in some headphones (instead of speakers) and play a test audio file again.

If there's still no success, then you just may have a faulty motherboard there.[/QUOTE]

Well, on a Clean Windows install, Device Manager has an exclamation mark for Audio...
Then I install the Audio Drivers either from Asus Site or from CD.
The exclamation mark disappears from Device Manager, but still can't get any sound from the speakers.
Oh, and I tested 2 speakers, so it can't be a faulty speaker... :)

Regarding the BIOS, I haven't upgraded, so I guess I will go ahead & do that.
But i don't think that would change anything.

Thanks.

P.S.> BTW, how could anyone find out whether his Mobo is faulty or not?

---

### Post by Rhubarb on 2007-02-13
Don't use the drivers on the CD, there's a small chance that these drivers don't work for some reason or another.  Download the latest drivers from Asus' website.

> P.S.> BTW, how could anyone find out whether his Mobo is faulty or not?
If you can't hear / record any sound in windows using **the latest drivers**, then your motherboard is faulty.
You'd need to return it back to the shop your bought it from / the Manufacturer if it's still within the warranty period.

---

### Post by dvarsam on 2007-02-13
Hello again!

I would like to ask you guys:

Does anybody know of any Linux Distro that is famous for having good Audio Drivers?
I mean, I have tried Ubuntu & things don't work...
Is there any other Linux Distro that is famous for its good Audio Drivers?
I hope that things get auto-detected....
In which Linux Distro do I have more chances that Audio will work out of the box?

Thanks.

---

### Post by Rhubarb on 2007-02-13
Well, if the manufactur's drivers don't work in windows, you will never be able to get sound working in any other linux distro / operating system.

I've found Xandros quite good at detecting hardware (this was a couple of years ago though).
It doesn't really matter what distro you use, because they all rely on ALSA to get your sound working, if compiling the newest version of ALSA yourself doesn't work, then there's a slim chance that another distro may work (because that other distro may have configured ALSA differently).

To sum things up:  If sound doesn't work in windows, your motherboard needs to be returned.  The audio part of your motherboard is dead.
If your motherboard is out of warranty, get a cheap PCI sound card and use that.

---

### Post by pay on 2007-02-13
Make sure that the sound card is enabled in the bios.

---

### Post by dvarsam on 2007-02-15
[QUOTE=Rhubarb]Well, if the manufactur's drivers don't work in windows, you will never be able to get sound working in any other linux distro / operating system.

I've found Xandros quite good at detecting hardware (this was a couple of years ago though).
It doesn't really matter what distro you use, because they all rely on ALSA to get your sound working, if compiling the newest version of ALSA yourself doesn't work, then there's a slim chance that another distro may work (because that other distro may have configured ALSA differently).

To sum things up:  If sound doesn't work in windows, your motherboard needs to be returned.  The audio part of your motherboard is dead.
If your motherboard is out of warranty, get a cheap PCI sound card and use that.[/QUOTE]

Yeap!
You were right man...
The sound was dead for some reason...
So, I went to the shop & returned the Mobo...
It took them 6 hours to figure out...
... that it can't be fixed... :)
In the end I got it replaced!
Problem Solved!
Thanks

P.S.> And "yes" the Audio was activated from the BIOS ;)

---

