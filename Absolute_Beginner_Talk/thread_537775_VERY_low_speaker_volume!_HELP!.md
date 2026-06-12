---
title: "VERY low speaker volume! HELP!"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by Roasted on 2007-08-29
I have a home stereo system hooked up via auxillary outputs to my computer. When I saw the dial on my radio to 30 on the volume scale (halfway) and I put my volume settings on my operating system to about half way, I get the walls to shake.

Right now it's at 45 and my controls on the operating system are cranked. Yet, it's so damn quiet. It's eqvuivalent to what level I'd listen to if there were 9 other people in the house trying to sleep while I was still up on the computer.

I have no idea what happened. Why is it so damn low?

---

### Post by tyggna1 on 2007-08-29
You could've blown out your speakers--having them cranked too high will do that.

I'd try using a different set for a few days, and then going back to your stereo.  Also, you're going to want to inspect the speakers themselves to see if the cone broke loose from it's casing.

---

### Post by forestpixie on 2007-08-29
I guess you've checked that you haven't muted channels with alsamixer 

it'd help to know what you have looked at ;)

---

### Post by Roasted on 2007-08-29
Speakers are fine. I'm listening to Hinder on an FM station now and it about blew my ears out once I hit the FM button.

I really don't know what to tell you guys that I looked for. I never had to troubleshoot audio like this. It always just... worked...

---

### Post by forestpixie on 2007-08-29
are you listening to fm through your pc?

did you check alsamixer? looked for muted channels - I know I had problems with front volume affecting me

just fishing really - only probs I had with soundcards was at beginning, so am assuming you've checked simple stuff - but you can never be sure

---

### Post by Roasted on 2007-08-29
No. My stereo gets set to Video/AUX, where it then plays the output from my computer. I just hit the FM button to switch from AUX to FM, where Hinder came on blaring my ears out.

Everything still works in windows, so it's got to be a linux thing. I was on the other day and cranked it just to see while I was on counterstrike, and the footsteps alone from the speakers caused cans on my desk to rattle off and fall on the ground.

I really don't know what to check that would be linux-specific, because like I said, it's functioning in windows, so it can't be a hardware failure.

---

### Post by deadgobby on 2007-08-29
What is your cound card? If you do not know. Open up the  terminal and copy and paste this command

 aplay --list-devices

Please copy and paste the reply back

Gobby

---

### Post by Roasted on 2007-08-29
Onboard audio on an MSI K8n Neo4 motherboard.


jason@jason:~$ aplay --list-devices
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
jason@jason:~$

---

### Post by deadgobby on 2007-08-29
[http://pennsylvania.ubuntuforums.com/showthread.php?t=513044](http://pennsylvania.ubuntuforums.com/showthread.php?t=513044)
[http://ubuntuforums.org/showthread.php?p=3214156](http://ubuntuforums.org/showthread.php?p=3214156)

[http://ubuntuforums.org/showthread.php?t=445192](http://ubuntuforums.org/showthread.php?t=445192)

Gobby

---

### Post by Roasted on 2007-08-30
All of these links are dealing with NO sound. I have sound. It's just quiet. I had perfectly working sound, then magically out of the blue (seriously), it got quieter. 

I need to test other speakers tomorrow. This is a little ridiculous. My headphone speakers are blasting in this, however my radio wasn't touched. The sound is perfect and clear, it's just not loud. I can't imagine that something happened to them...

---

### Post by funrider on 2007-08-30
is it a desktop or laptop? i hook up my laptop with my stereo system to watch movie daily.......
i would check the followings whenever volume is low:

1. increase volume for Headphone section
2. increase the master volume of course
3. check if the keyboard volume control is maximum ( i mean that Fn + the volume control button)

hope this helps

---

### Post by Roasted on 2007-08-30
On the main stereo, volume is 45/52. Volume on the computer is maxed at 100%. Yet, Billy Joel's Piano Man sounds like such a soft song. At those volume levels, I should have the neighbors calling the police that I'm being that much of an annoyance with the noise level.

The thing that confuses me is this. I was in Audacious, and I was trying to hit CTRL T to create another tab in Firefox, however at the time I didn't realize Audacious was my active window. Nothing visibly happened, no beeps were made, no sounds, but that's when the sound randomly died. Is there perhaps ANOTHER volume meter, kind of like in windows? In windows I have two bars that equally control the sound level. Perhaps there's another in Linux?

---

### Post by forestpixie on 2007-08-30
what are you actually physically using at the moment to control vol in linux?

---

### Post by Roasted on 2007-08-30
> **forestpixie said:**
> what are you actually physically using at the moment to control vol in linux?

I set hot keys to page up/page down to adjust the volume. The volume bar is in the top right corner by the clock. There's 3 ways to control volume... I have the volume on audacious, which is at 50% and I don't touch, I have the volume dial on the actual stereo which has a max of 52, I normally leave it at 25 and RARELY touch it, and then I use the linux system volume that's located in the upper right corner as my primary means of adjusting volume.

---

### Post by forestpixie on 2007-08-30
ok - and what controls, incl switches on other tabs do you actually have on the mixer if you dbl clik the vol icon

---

### Post by Roasted on 2007-08-30
Double clicking the icon button yields nothing.

Where do you want me to go to find the tabs and whatnot?

---

### Post by forestpixie on 2007-08-31
What I'm trying to get to is this - 2 scrnshts of vol controls, 1 of alsamixer - are you saying that you don't have any of these controls available to you?

This is all really odd - and no doubt frustrating.

What does ```
lspci -v
``` in terminal give?

Have you seen this page - [http://sidux.com/PNphpBB2-viewtopic-t-4911.html](http://sidux.com/PNphpBB2-viewtopic-t-4911.html)

Is it a digital output? If so have you seen these
[http://alsa.opensrc.org/index.php/Intel8x0#Digital_output_not_working_.28Realtek_ALC850.29](http://alsa.opensrc.org/index.php/Intel8x0#Digital_output_not_working_.28Realtek_ALC850.29)

[http://alsa.opensrc.org/index.php/Intel8x0#nForce_4_digital_output](http://alsa.opensrc.org/index.php/Intel8x0#nForce_4_digital_output)


Have you seen [this]("http://ubuntuforums.org/showthread.php?t=205449") - 

maybe the > Getting the ALSA drivers from a *fresh* kernel part might help

---

### Post by Roasted on 2007-08-31
reinstalling alsi didn't work.


jason@jason:~$ lspci -v
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7125
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7125
        Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7125
        Flags: 66MHz, fast devsel, IRQ 3
        I/O ports at ff00 [size=32]
        I/O ports at 4c00 [size=64]
        I/O ports at 4c40 [size=64]
        Capabilities: <access denied>

00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2) (prog-if 10 [OHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7125
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at febff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3) (prog-if 20 [EHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7125
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at feb00000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7585
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        I/O ports at ea00 [size=256]
        I/O ports at ee00 [size=256]
        Memory at febfd000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2) (prog-if 8a [Master SecP PriP])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7125
        Flags: bus master, 66MHz, fast devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at fb00 [size=16]
        Capabilities: <access denied>

00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7125
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        I/O ports at 09f0 [size=8]
        I/O ports at 0bf0 [size=4]
        I/O ports at 0970 [size=8]
        I/O ports at 0b70 [size=4]
        I/O ports at f600 [size=16]
        Memory at febfb000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7125
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
        I/O ports at 09e0 [size=8]
        I/O ports at 0be0 [size=4]
        I/O ports at 0960 [size=8]
        I/O ports at 0b60 [size=4]
        I/O ports at f100 [size=16]
        Memory at febfa000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fe900000-fe9fffff
        Prefetchable memory behind bridge: fea00000-feafffff

00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7125
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
        Memory at febf9000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at f000 [size=8]
        Capabilities: <access denied>

00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: fe800000-fe8fffff
        Prefetchable memory behind bridge: 00000000fe700000-00000000fe7fffff
        Capabilities: <access denied>

00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: fe600000-fe6fffff
        Prefetchable memory behind bridge: 00000000fe500000-00000000fe5fffff
        Capabilities: <access denied>

00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: fe400000-fe4fffff
        Prefetchable memory behind bridge: 00000000fe300000-00000000fe3fffff
        Capabilities: <access denied>

00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: f4000000-fbffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel

05:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2) (prog-if 00 [VGA])
        Subsystem: XFX Pine Group Inc. Unknown device 2112
        Flags: bus master, fast devsel, latency 0, IRQ 20
        Memory at f4000000 (32-bit, non-prefetchable) [size=64M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at fa000000 (64-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at f8000000 [disabled] [size=128K]
        Capabilities: <access denied>

jason@jason:~$

---

### Post by forestpixie on 2007-08-31
I'm at a loss really - have you tried changing the playback in sound preferences _ mine is set to autodetect (which i suspect is default) - you could try changing to OSS or try the others.

One other thing you could try if you've still got the disc - is booting the livecd and checking sound playback in there - at the least it would prove that it's in your system.

---

### Post by xcape on 2007-08-31
I have the same issue.  After I installed alsa-tools and also-utils my audio output was a little better.

I ran:   /etc/init.d/alsa-utils start

-xCape

---

### Post by forestpixie on 2007-08-31
If you don't get anywhere - I wonder if the Ubuntu Studio setup would have more luck dealing with your audio  - touch drastic - but you can get bits through aptitude apparently - post 8 of [this]("http://ubuntuforums.org/showthread.php?t=539624")

---

### Post by Roasted on 2007-08-31
Okay, so I ran the thing that was posted a few posts about, and now I have no video. When I go to see videos that are on embedded sites, I have a big red X.

This is getting ridiculous. Even Windows didn't have this much trouble. :mad:

---

### Post by forestpixie on 2007-09-01
I assume you're talking about the /etc/init.d/alsa-utils start I have no idea about that myself. - but I just don't know what else to suggest. I would have reinstalled by now :(

Edit - ps - have you tried running the livecd to see if it all works there?

did you try to  do this > have you tried changing the playback in sound preferences _ mine is set to autodetect (which i suspect is default) - you could try changing to OSS or try the others.

---

### Post by forestpixie on 2007-09-01
There are suddenly a few threads appearing with no sound - and yes I know you've got sound just not very much

[http://ubuntuforums.org/showthread.php?t=539986](http://ubuntuforums.org/showthread.php?t=539986)

a good point made in one of these, have you tried booting in to the old kernel and seeing if sound works ok there - that'd be easy to try :)

---

### Post by Roasted on 2007-09-01
> **forestpixie said:**
> There are suddenly a few threads appearing with no sound - and yes I know you've got sound just not very much

[http://ubuntuforums.org/showthread.php?t=539986](http://ubuntuforums.org/showthread.php?t=539986)

a good point made in one of these, have you tried booting in to the old kernel and seeing if sound works ok there - that'd be easy to try :)

It may be easy, however I have no idea how to do that. Is there anyway I can revert back to what I had before? Because my embedded videos are goofy now, and pose a big red X. 

Is there perhaps a link somewhere that tells me the EXACT audio files, EXACT video files, etc that I need to make videos and stuff work? It seems everytime I need help someone randomly chimes in and says oh yeah, install your grubalbauo file and BAM it works. Yet, I wonder how they knew that. Were they using a site that specifies exactly what files are needed to accomplish certain tasks? I just want my video back. :(

---

### Post by Roasted on 2007-09-01
Arg. So I found out that my power tripped a few days ago. Then the power gets tripped, all settings on the stereo go to default. I had no clue. I checked all settings, however there was one seting I set a long time ago and never tinkered with again. I have 7 video settings. Each setting as you increase, the built in amplifier gives more output. It was set to 1... I had it on 6 before.

Case closed.

Now, to get my video with the red X working again....




I do however greatly thank those who stuck it out and tried their best to help me. Had I known the power tripped, this wouldn't of been an issue, but I had no idea.

---

### Post by forestpixie on 2007-09-02
> It may be easy, however I have no idea how to do that

when you boot - grub will give you at list - new and old kernels and recovery options - pick one

> Yet, I wonder how they knew that. Were they using a site that specifies exactly what files are needed to accomplish certain tasks?

 I use google a lot - also - when I find something new I append it to a simple text document I have on my desktop. Also I have a bit of spare time on my hands so I read odd threads 


> I do however greatly thank those who stuck it out and tried their best to help me. 

Just sorry it seemed to take a long time and that I couldn't help too much

As I said - by now I would have reinstalled - :)

If you do come back here - perhaps you could mark the thread solved.

---

### Post by mnk0 on 2008-06-10
ok first of .. change your sound output to ALSA.

run alsamixer from the terminal, and then press page up and use the arrows to make sure that all the channels are full. i had the same problem my PCM volume was low.


--
MNK0

---

