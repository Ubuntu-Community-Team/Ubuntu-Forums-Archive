---
title: "No sound (7.04, iMac 24 inch)"
date: 2007-04-22
forum: Apple Intel Users
---

### Post by tuna74 on 2007-04-22
I just installed 7.04 on my 24 inch iMac, and with some xorg.config addition I got the desired resolution to work. However, sound does not work at all. Does anyone know what to do to enable sound?

---

### Post by rhebert on 2007-04-23
Try opening a terminal window and typing "alsamixer".  That should give you some sliders to adjust.  That's how I got my sound working after upgrading to Feisty.  Good luck!

---

### Post by tuna74 on 2007-04-23
I already tried that, didn't help. Has anyone got sound to work on a 24 iMac?

---

### Post by ronocdh on 2007-04-23
> **tuna74 said:**
> I already tried that, didn't help. Has anyone got sound to work on a 24 iMac?
I don't mean to be condescending, but have you tried all the terribly obvious things like messing around in the Sound Preferences and switching which hardware is being consulted? I know that I my C2D MacBook Pro I was going out of my mind for a whole morning trying to get sound up, and really smacked my forehead when I found out it was so simple. =)

Please post when you do figure it out.

---

### Post by tuna74 on 2007-04-24
Yeah, changing everything to ALC882 Analog seems to make sound working. However, it is really low, so you can almost not hear it. All volume sliders are set to around 95 %, is there another way to get a louder sound?

---

### Post by kent69 on 2007-04-24
1.Analog/Digital Output jack

2.apt-get install gstreamer0.10-plugins-ugly, gstreamer0.10-plugins-ugly-multiverse, msttcorefonts, flashplugin-nonfree, sun-java6-plugin

---

### Post by zAo on 2007-04-24
> **tuna74 said:**
> Yeah, changing everything to ALC882 Analog seems to make sound working. However, it is really low, so you can almost not hear it. All volume sliders are set to around 95 %, is there another way to get a louder sound?
Are both the Master and PCM channels at 95%?

---

### Post by nicfagn on 2007-04-24
> **tuna74 said:**
> Yeah, changing everything to ALC882 Analog seems to make sound working. However, it is really low, so you can almost not hear it. All volume sliders are set to around 95 %, is there another way to get a louder sound?

Where did you change the settings? I tried on the sound control panel but I couldn't hear anything at all...
For the record I have a 24'' iMac and I tried alsamixer too but with no luck. :( 

Thanks

---

### Post by tuna74 on 2007-04-24
In Preferences -> Sound

There is no "Master" channel I think....everything that matters is at around 95 %.

---

### Post by tuna74 on 2007-04-24
> **kent69 said:**
> 1.Analog/Digital Output jack

2.apt-get install gstreamer0.10-plugins-ugly, gstreamer0.10-plugins-ugly-multiverse, msttcorefonts, flashplugin-nonfree, sun-java6-plugin

What has this to do with getting any sound from the system?

---

### Post by ronocdh on 2007-04-24
> **tuna74 said:**
> What has this to do with getting any sound from the system?
Good question! I'm not sure which soundcard you guys are using in your machines, but I have read about certain Intel chipsets that start off with audio almost inaudible. 

[This]("http://ubuntuforums.org/showthread.php?t=416207") was all I found on a quick search; it does mention Intel hardware, but again, I'm not sure which cards the iMacs use. Good luck, post back. =)

---

### Post by nicfagn on 2007-04-25
Thanks for the replies. I tried to follow the instructions on the thread you said, ronocdh, but with no result.
The lspci output is the following:
```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:07.0 Performance counters: Intel Corporation Unknown device 27a3 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
03:00.0 Network controller: Broadcom Corporation Unknown device 4328 (rev 01)
04:03.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 01)
```
I could only add that sound didn't work with Fedora 7 test 3, nor Fedora 6, so it seems to be a common problem.
I'll be waiting for an upstream fix, thanks anyway.

Ciao

---

### Post by nicfagn on 2007-04-27
Today I had some luck googling around and found this interesting post:

[INDENT][http://mailman.alsa-project.org/pipermail/alsa-devel/2007-April/000602.html]("http://mailman.alsa-project.org/pipermail/alsa-devel/2007-April/000602.html")
[/INDENT]
confirming that the problem lies in alsa itself.
So I did as suggested in the post and downloaded the following source snapshot:

[INDENT][ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver/alsa-driver-hg20070427.tar.bz2]("ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver/alsa-driver-hg20070427.tar.bz2")
[/INDENT]
(EDITED: If you prefer an official release the necessary code patch is included since [alsa-driver-1.0.14rc4]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc4.tar.bz2") ) 
After expanding the sources and changing to the resulting directory, I did a configure for the HDA intel chipset:
 
```
./configure --with-cards=hda-intel
```

I had to Install the libc6 developer libraries and headers:

```
sudo apt-get install libc6-dev
```

since these are missing in the default installation but needed for compilation with the make command:

```
make
```

To Install the modules:

```
sudo make install-modules
```

I had to kill the processes using the snd_hda_intel module after retrieving their pids with:

```
fuser /dev/snd/*
```

typically that should be the mixer applet in tray area.If a dialog appears asking to reload the applet leave it alone, it will be useful later.
Then unloaded the old HDA modules with:

```
sudo rmmod snd_hda_intel
sudo rmmod snd_hda_codec
```

Reloaded only the snd_hda_intel module with a specific option:

```
sudo modprobe snd_hda_intel model=macpro
```

Reloaded the mixer applet (using the reload dialog or in some other way) and checked that the PCM and Front channel were not muted and the headphone switch was on.
At this point I was able, at last, to hear the sound flowing from the speakers :D

[INDENT][I]If you get this error:

FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.20-15-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

continue with the following steps (thanks Snorkr for pointing out).
[/I][/INDENT]

So far so good, but the module option is not persisted between system restarts so I added the file **/etc/modprobe.d/alsa_local** containing an "options" line:

```
options snd_hda_intel model=macpro
```

and after a reboot I was greeted by the usual sounds of Ubuntu.:popcorn:

---

### Post by tuna74 on 2007-04-30
Cool!


I want to try, but I have a question: What happens if there is a new kernel or alsa version available from ubuntu, do you have to do these steps over again?

---

### Post by nicfagn on 2007-04-30
What I did with the above procedure is to compile a specific version of alsa for a specific version of the kernel, so, as far as i know, the answer is: it depends.
To make a long story short, if the sound doesn't work anymore after a kernel or alsa update you should redo the above steps.
If you can confirm that this workaround is working, I could file a bug so that's fixed in an ubuntu update or in the next version.
If you decide to try, post the results here, please.

Bye
Nicola

---

### Post by nicfagn on 2007-05-01
For anyone interested, I just filed  [**bug 111511**]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/111511") on Launchpad.

---

### Post by Nasiom on 2007-05-01
HI,

this is just to concur.  No Sound on any Core2Duo MacBook or MacBook Pro or Mac Pro.

I did install today on a 3Ghz Mac Pro quad - no sound either but this machine fly man.

So it is generalized.

Thanks

-Nasiom

---

### Post by Gen2ly on 2007-05-01
sound should just work

---

### Post by Gen2ly on 2007-05-02
have you tried running alsaconf?

---

### Post by Snorkr on 2007-05-03
Hi. 

I followed the instructions here and everything went fine until 
```
 sudo modprobe snd_hda_intel model=macpro 
```

I got the error:
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.20-15-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

dmesg reveals:

[687683.072000] snd_hda_intel: disagrees about version of symbol snd_ctl_add
[687683.072000] snd_hda_intel: Unknown symbol snd_ctl_add
[687683.072000] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[687683.072000] snd_hda_intel: Unknown symbol snd_pcm_new
[687683.072000] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[687683.072000] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[687683.072000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[687683.072000] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[687683.072000] snd_hda_intel: disagrees about version of symbol snd_ctl_find_id
[687683.072000] snd_hda_intel: Unknown symbol snd_ctl_find_id
[687683.072000] snd_hda_intel: Unknown symbol snd_verbose_printk
[687683.072000] snd_hda_intel: disagrees about version of symbol snd_ctl_new1
[687683.072000] snd_hda_intel: Unknown symbol snd_ctl_new1
[687683.072000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages
[687683.072000] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[687683.072000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl
[687683.072000] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[687683.072000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages
[687683.072000] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[687683.072000] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops
[687683.072000] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[687683.072000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_list
[687683.072000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list
[687683.072000] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
[687683.072000] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[687683.076000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
[687683.076000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[687683.076000] snd_hda_intel: Unknown symbol snd_pci_quirk_lookup
[687683.076000] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
[687683.076000] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[687683.076000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
[687683.076000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step

Any clues?

Thanks in advance,
-Snorkr

> **nicfagn said:**
> Today I had some luck googling around and found this interesting post:

[INDENT][http://mailman.alsa-project.org/pipermail/alsa-devel/2007-April/000602.html]("http://mailman.alsa-project.org/pipermail/alsa-devel/2007-April/000602.html")
[/INDENT]
confirming that the problem lies in alsa itself.
So I did as suggested in the post and downloaded the following source snapshot:

[INDENT][ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver/alsa-driver-hg20070427.tar.bz2]("ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver/alsa-driver-hg20070427.tar.bz2")
[/INDENT]
After expanding the sources and changing to the resulting directory, I did a configure for the HDA intel chipset:
 
```
./configure --with-cards=hda-intel
```

I had to Install the libc6 developer libraries and headers:

```
sudo apt-get install libc6-dev
```

since these are missing in the default installation but needed for compilation with the make command:

```
make
```

To Install the modules:

```
sudo make install-modules
```

I had to kill the processes using the snd_hda_intel module after retrieving their pids with:

```
fuser /dev/snd/*
```

typically that should be the mixer applet in tray area.If a dialog appears asking to reload the applet leave it alone, it will be useful later.
Then unloaded the old HDA modules with:

```
sudo rmmod snd_hda_intel
sudo rmmod snd_hda_codec
```

Reloaded only the snd_hda_intel module with a specific option:

```
sudo modprobe snd_hda_intel model=macpro
```

Reloaded the mixer applet (using the reload dialog or in some other way) and checked that the PCM and Front channel were not muted and the headphone switch was on.
At this point I was able, at last, to hear the sound flowing from the speakers :D
So far so good, but the module option is not persisted between system restarts so I added the file **/etc/modprobe.d/alsa_local** containing an "options" line:

```
options snd_hda_intel model=macpro
```

and after a reboot I was greeted by the usual sounds of Ubuntu.:popcorn:

---

### Post by Snorkr on 2007-05-03
Hi.

I rebooted, tried the command again and bingo!!!! Sound works. Thanks nicfagn.

Regards,
-Snorkr

---

### Post by nicfagn on 2007-05-03
> **Dirk.R.Gently said:**
> have you tried running alsaconf?

Thanks for the suggestion, but it didn't work for me. Alsaconf detected the hda_intel sound card, whose modules where already loaded anyway, and created the file /etc/modprobe.d/sound containing a pair of lines, but nothing changed. :( 

> ** Snorkr said:**
> I rebooted, tried the command again and bingo!!!! Sound works. Thanks nicfagn.

I'm really happy to hear that. :)  
At least sound from speakers works with this method, I cannot verify the other out channels (headphones, S/PDIF). 
Another thing not working for me is sound recording, but I care less for the moment.
I hope the bug I filed will fix all that.

Good hearing!

---

### Post by tuna74 on 2007-05-28
I tried setting up ALSA (with the latest dev snapshot) and the sound works now! Unfortunately, only the front speakers can output anything, has anyone got the headphone out to work?

Tanks for posting the the guide BTW!

---

### Post by nicfagn on 2007-06-01
No, headphones don't work for me too. 
I got speakers and sound recording (after some tweaking with alsamixer) to work , but I could not try other outputs.
If I disable headphones with alsamixer, the speakers are muted, so I think the audio channels are misconfigured, but this is better that no sound at all!
I'd like to do something about that, but after looking at alsa documentation and source code I don't know where to start :(
Anyway, if you want to track the problem you can check:
[INDENT][https://bugs.launchpad.net/ubuntu/+s...er/+bug/111511]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/111511")[/INDENT]
and:
[INDENT][https://bugtrack.alsa-project.org/al...ew.php?id=2708]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2708") (login as guest)[/INDENT]

Bye

---

### Post by tehmacuser on 2007-06-01
try doing this and see if you hear anything if you do Ubuntu recognizes your speakers:

cat /bin/bash > /dev/dsp

if you hear anything then it's just a matter of a driver as far as i know

---

### Post by nicfagn on 2007-06-12
I worked out a patch to enable headphones and a somewhat louder sound level for the speakers. The patch mutes/unmutes the speakers on headphone jack insertion/removal.
Hope this helps.

P.S.: The patch is against alsa 1.0.14 code base

EDIT: The patch automatically recognizes the iMac 24, so the model option for the snd_hda_intel module must not be forced to macpro, otherwise it will work as before (no headphones, no jack detection).

---

### Post by Snorkr on 2007-06-14
Hi nicfagn.

I downloaded 1.4 newest and tried to apply the patch but gor errors:
[B]
mymachine:/tmp/alsa-driver-1.0.14rc4/alsa-kernel/pci/hda$[/B] patch  < /tmp/udiff-patch_realtek.txt
patching file patch_realtek.c
Hunk #1 FAILED at 144.
Hunk #2 FAILED at 5055.
Hunk #3 FAILED at 5399.
Hunk #4 succeeded at 5326 (offset -235 lines).
Hunk #5 succeeded at 5353 (offset -235 lines).
3 out of 5 hunks FAILED -- saving rejects to file patch_realtek.c.rej

Any hints?

Thanks in advance, 
-Snorkr

> **nicfagn said:**
> I worked out a patch to enable headphones and a somewhat louder sound level for the speakers. The patch mutes/unmutes the speakers on headphone jack insertion/removal.
Hope this helps.

P.S.: The patch is against alsa 1.0.14 code base

---

### Post by nicfagn on 2007-06-14
> **Snorkr said:**
> Hi nicfagn.

I downloaded 1.4 newest and tried to apply the patch but gor errors:
[B]
mymachine:/tmp/alsa-driver-1.0.14rc4/alsa-kernel/pci/hda$[/B] patch  < /tmp/udiff-patch_realtek.txt
patching file patch_realtek.c
Hunk #1 FAILED at 144.
Hunk #2 FAILED at 5055.
Hunk #3 FAILED at 5399.
Hunk #4 succeeded at 5326 (offset -235 lines).
Hunk #5 succeeded at 5353 (offset -235 lines).
3 out of 5 hunks FAILED -- saving rejects to file patch_realtek.c.rej

Any hints?

Thanks in advance, 
-Snorkr

My patch is made against the file patch_realtek.c in [alsa-driver-1.0.14]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2"), not the one in alsa-driver-1.0.14rc4, and the difference in these two versions makes the patch command complain.

Bye
Nicola

---

### Post by André Schnabel on 2007-06-14
Works perfect on my 24" iMac. Thanks a lot nicfagn!!! :D

---

### Post by nicfagn on 2007-06-14
Thanks André. It's good to know that it works for others too. :)

Bye

---

### Post by Snorkr on 2007-06-15
Works!

Thanks again Nicola.

Regs,
-Snorkr

> **nicfagn said:**
> My patch is made against the file patch_realtek.c in [alsa-driver-1.0.14]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2"), not the one in alsa-driver-1.0.14rc4, and the difference in these two versions makes the patch command complain.

Bye
Nicola

---

### Post by nicfagn on 2007-06-15
Thanks to you, for the positive feedback.

Bye
Nicola

---

### Post by Snorkr on 2007-06-21
Hmmmm.

I just tried headphones, and they don't work. No sound, and they don't mute the speakers when plugged in. In alsamixer the headphones don't have volume controls, only the box at the bottom where you can mute/unmute. 

Anything obvious to check?

Best regards,
-Snorri

---

### Post by nicfagn on 2007-06-21
Apparently you're not using the patched alsa-driver.
You can check the current alsa version with:
```
cat /proc/asound/version
```
If you updated your system to a new kernel version, all kernel modules were updated too including the alsa ones. So to regain the patch functionality you have to reinstall the patched modules you compiled.
Let me know if this helps.

Bye
Nicola

---

### Post by Snorkr on 2007-06-21
Hi Nicola.

```

$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.14.
Compiled on Jun 21 2007 for kernel 2.6.20-16-generic (SMP).

```

I'm pretty sure I did this according to intructions, but the headphones don't work. Sound level from the speaker is very good and I deffinately applid the pach before ./configure and make. 

Best regards,
-Snorkr

> **nicfagn said:**
> Apparently you're not using the patched alsa-driver.
You can check the current alsa version with:
```
cat /proc/asound/version
```
If you updated your system to a new kernel version, all kernel modules were updated too including the alsa ones. So to regain the patch functionality you have to reinstall the patched modules you compiled.
Let me know if this helps.

Bye
Nicola

---

### Post by nicfagn on 2007-06-21
Ops, I forgot to mention that with the patch you don't have to force the model to macpro anymore.
So, if you have the file /etc/modprobe.d/alsa_local still around, better rename or remove it.

Bye
Nicola

---

### Post by Snorkr on 2007-06-21
Hi Nocola.

This did the trick!

Thanks a lot.

Best regards,
-Snorkr

> **nicfagn said:**
> Ops, I forgot to mention that with the patch you don't have to force the model to macpro anymore.
So, if you have the file /etc/modprobe.d/alsa_local still around, better rename or remove it.

Bye
Nicola

---

### Post by ivesjd on 2007-06-21
Just wondering, is this problem with Core 2 Duo iMac's? Or all iMac's in general?

---

### Post by nicfagn on 2007-06-21
> **ivesjd said:**
> Just wondering, is this problem with Core 2 Duo iMac's? Or all iMac's in general?

For what I know, the problem in this post is specific of the iMac 24'' released on September 2006.

This model, like all Intel based models, has a sound system based on the **H**igh **D**efinition **A**udio standard.
An **HDA** system is composed by a **controller** chip and by one or more **codec** chips. The controller coordinates the audio flows going into and coming from the codecs that are wired to physical audio inputs and outputs.
As far as I know, all new Intel motherboards integrate a HDA controller but the codec itself is usually produced by another manufacturer eg. Sigmatel or Realtek.
Even if the codec is the same, it can be configured differently according to the specific model using it, and this is implemented in the audio driver.
  
Looking at the alsa-driver code, it seems that all intel iMacs use a Sigmatel codec chip, albeit with different configurations, except the iMac 24'' that uses a Realtek ALC885 codec like the Mac Pros.
So it has it's own kind of problems as far as the audio system is concerned. 

I learned all that trying to make sound work on my iMac 24, so there are certainly inaccuracies and oversimplifications, but that should give an idea of the differences that can exist between various Mac models.

---

### Post by tuna74 on 2007-07-07
Hi everybody, sorry for being a bit thick, but I don't really get what exactly you are supposed to do. Could anyone post (or link to) a step by step instruction?

---

### Post by nicfagn on 2007-07-07
> **tuna74 said:**
> Hi everybody, sorry for being a bit thick, but I don't really get what exactly you are supposed to do. Could anyone post (or link to) a step by step instruction?

Don't worry, I'll try to condense a short version here.
 
Download alsa sources from:
 [INDENT][ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2")[/INDENT] 
Expand the sources with:
```
tar --bzip2 -xvf alsa-driver-1.0.14.tar.bz2
```
Download the patch attached to this [post]("http://ubuntuforums.org/showpost.php?p=2831324&postcount=26"), copy it into **alsa-driver-1.0.14/alsa-kernel/pci/hda** and cd to that directory.
Apply the patch with:

```
patch < udiff-patch_realtek.txt
```

Install the libc6 developer libraries if missing:

```
sudo apt-get install libc6-dev
```

Cd back to the top **alsa-driver-1.0.14** dir and do a configure for the HDA intel chipset:
 
```
./configure --with-cards=hda-intel
```

Compile with the command:

```
make
```

For Gutsy or later, a little adjustment is needed to use the compiled module and not the one shipped with the system (in previous versions this command should fail):

```
sudo mv -v /lib/modules/$(uname -r)/ubuntu/media/snd-hda-intel/snd-hda-intel{,-ubuntu}.ko
```

Install the compiled modules:

```
sudo make install-modules
```

Reboot and you should be able to hear sound from the speakears and the headphone and record sound from the microphone (perhaps after adjusting mixer settings).


Bye
Nicola

---

### Post by tuna74 on 2007-07-07
Thanks nicfagn, I tried it and everthing works great!

---

### Post by dragonwings on 2007-07-07
open terminal and type 
sudo asoundconf list 
 
and you will get something like this

 Names of available sound cards:
Audigy2  <<NOTE FROM DRAGONWINGS THIS WHERE YOUR SOUND TO TYPE IN WILL BE
NVidia

in my case iv got a Audigy2 sound card so i would type 

sudo asoundconf set-default-card Audigy2

to get sound working.

in your case just replace Audigy2 with what ever your sound card is

---

### Post by jamminbean on 2007-07-13
Cool :)
I followed your instructions and I now have sound on internal speakers and headphones :)
Thanks!

---

### Post by tuna74 on 2007-07-19
OT: I should just add that the instructions work if you have Fedora 7 as well (you have to download the kernel devel package though...)

---

### Post by ashokcm on 2007-07-31
I could get sound only by changing to OSS. That too only with xmms. None of the other applications seem to make any kind of noise :(

---

### Post by nicfagn on 2007-07-31
> **ashokcm said:**
> I could get sound only by changing to OSS. That too only with xmms. None of the other applications seem to make any kind of noise :(

I assume you have already installed the patched alsa-driver-1.0.14 modules, and that you have unmuted and adjusted the master and PCM sound channels with alsamixer.
In that case could you post the output of:
```

cat /proc/asound/version
cat /proc/asound/card0/codec#0
amixer

```

Bye

---

### Post by Dingbats on 2007-08-15
Excuse me for bumping, but my sound isn't working either on my Mac Pro (running Feisty). I tried following the step-by-step guide, but ./configure --with-cards=hda-intel gives me:

```
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
```

What can I do about that? :?

---

### Post by nicfagn on 2007-08-15
Try installing libc6-dev before ./configure with:
```
sudo apt-get install libc6-dev
```
I'll update the guide accordingly.

Bye
Nicola

---

### Post by Dingbats on 2007-08-15
OK, I just did and it compiled fine after that. But I still don't get any sound after a reboot. I have all the outputs on max, and have tried all the options in the sound settings dialog.

---

### Post by nicfagn on 2007-08-15
You said to be on a Mac Pro. That system is apparently supported by alsa 1.0.14 but I saw contrasting reports about that.
I already failed to help another Mac Pro user, see [here]("http://ubuntuforums.org/showthread.php?t=472232") .
Unfortunately I don't have a Mac Pro to test, but ,if you don't mind, you could post some info to see if I can spot something:

- lspci -v
- cat /proc/asound/version
- cat /proc/asound/card0/codec#0
- ls -l /sys/module/snd_hda_intel/parameters
- amixer

Nicola

---

### Post by Dingbats on 2007-08-15
Ok.

lspci -v:

```
00:00.0 Host bridge: Intel Corporation 5000X Chipset Memory Controller Hub (rev 30)
	Subsystem: Intel Corporation Unknown device 7270
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:02.0 PCI bridge: Intel Corporation 5000 Series Chipset PCI Express x8 Port 2-3 (rev 30) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=06, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: 52400000-52dfffff
	Capabilities: <access denied>

00:03.0 Non-VGA unclassified device: Intel Corporation 5000 Series Chipset PCI Express x4 Port 3 (rev 30)
	!!! Invalid class 0000 for header type 01
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	Capabilities: <access denied>

00:04.0 PCI bridge: Intel Corporation 5000X Chipset PCI Express x16 Port 4-7 (rev 30) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: 50000000-520fffff
	Prefetchable memory behind bridge: 0000000040000000-000000004fffffff
	Capabilities: <access denied>

00:05.0 Non-VGA unclassified device: Intel Corporation 5000 Series Chipset PCI Express x4 Port 5 (rev 30)
	!!! Invalid class 0000 for header type 01
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	Capabilities: <access denied>

00:06.0 Non-VGA unclassified device: Intel Corporation 5000 Series Chipset PCI Express x4 Port 6 (rev 30)
	!!! Invalid class 0000 for header type 01
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=0
	Capabilities: <access denied>

00:07.0 Non-VGA unclassified device: Intel Corporation 5000 Series Chipset PCI Express x4 Port 7 (rev 30)
	!!! Invalid class 0000 for header type 01
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
	Capabilities: <access denied>

00:08.0 System peripheral: Intel Corporation 5000 Series Chipset DMA Engine (rev 30)
	Subsystem: Intel Corporation Unknown device 8086
	Flags: bus master, fast devsel, latency 0
	Memory at fe700000 (64-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:10.0 Host bridge: Intel Corporation 5000 Series Chipset Error Reporting Registers (rev 30)
	Subsystem: Intel Corporation Unknown device 8086
	Flags: fast devsel

00:10.1 Host bridge: Intel Corporation 5000 Series Chipset Error Reporting Registers (rev 30)
	Subsystem: Intel Corporation Unknown device 8086
	Flags: fast devsel

00:10.2 Host bridge: Intel Corporation 5000 Series Chipset Error Reporting Registers (rev 30)
	Subsystem: Intel Corporation Unknown device 8086
	Flags: fast devsel

00:11.0 Host bridge: Intel Corporation 5000 Series Chipset Reserved Registers (rev 30)
	Subsystem: Intel Corporation Unknown device 8086
	Flags: fast devsel

00:13.0 Host bridge: Intel Corporation 5000 Series Chipset Reserved Registers (rev 30)
	Subsystem: Intel Corporation Unknown device 8086
	Flags: fast devsel

00:15.0 Host bridge: Intel Corporation 5000 Series Chipset FBD Registers (rev 30)
	Subsystem: Intel Corporation Unknown device 8086
	Flags: fast devsel

00:16.0 Host bridge: Intel Corporation 5000 Series Chipset FBD Registers (rev 30)
	Subsystem: Intel Corporation Unknown device 8086
	Flags: fast devsel

00:1b.0 Audio device: Intel Corporation 631xESB/632xESB High Definition Audio Controller (rev 09)
	Flags: bus master, fast devsel, latency 0, IRQ 23
	Memory at 53100000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 631xESB/632xESB/3100 Chipset PCI Express Root Port 1 (rev 09) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=0
	Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 631xESB/632xESB/3100 Chipset PCI Express Root Port 2 (rev 09) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0d, subordinate=0d, sec-latency=0
	Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 631xESB/632xESB/3100 Chipset PCI Express Root Port 3 (rev 09) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0e, subordinate=0e, sec-latency=0
	Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 631xESB/632xESB/3100 Chipset PCI Express Root Port 4 (rev 09) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0f, subordinate=0f, sec-latency=0
	Memory behind bridge: 53000000-530fffff
	Prefetchable memory behind bridge: 0000000052e00000-0000000052efffff
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #1 (rev 09) (prog-if 00 [UHCI])
	Subsystem: Intel Corporation Unknown device 7270
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 30a0 [size=32]

00:1d.1 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #2 (rev 09) (prog-if 00 [UHCI])
	Subsystem: Intel Corporation Unknown device 7270
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 3080 [size=32]

00:1d.2 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #3 (rev 09) (prog-if 00 [UHCI])
	Subsystem: Intel Corporation Unknown device 7270
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 3060 [size=32]

00:1d.3 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #4 (rev 09) (prog-if 00 [UHCI])
	Subsystem: Intel Corporation Unknown device 7270
	Flags: bus master, medium devsel, latency 0, IRQ 22
	I/O ports at 3040 [size=32]

00:1d.7 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset EHCI USB2 Controller (rev 09) (prog-if 20 [EHCI])
	Subsystem: Intel Corporation Unknown device 7270
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at 53104800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d9) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=10, subordinate=10, sec-latency=32
	Memory behind bridge: 52f00000-52ffffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 631xESB/632xESB/3100 Chipset LPC Interface Controller (rev 09)
	Subsystem: Intel Corporation Unknown device 7270
	Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 631xESB/632xESB IDE Controller (rev 09) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Intel Corporation Unknown device 7270
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 30e8 [size=8]
	I/O ports at 30fc [size=4]
	I/O ports at 30e0 [size=8]
	I/O ports at 30f8 [size=4]
	I/O ports at 30c0 [size=16]

00:1f.2 IDE interface: Intel Corporation 631xESB/632xESB/3100 Chipset SATA Storage Controller IDE (rev 09) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Intel Corporation Unknown device 7270
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 21
	I/O ports at 30d8 [size=8]
	I/O ports at 30f4 [size=4]
	I/O ports at 30d0 [size=8]
	I/O ports at 30f0 [size=4]
	I/O ports at 3020 [size=16]
	Memory at 53104400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 631xESB/632xESB/3100 Chipset SMBus Controller (rev 09)
	Subsystem: Intel Corporation Unknown device 7270
	Flags: medium devsel, IRQ 11
	I/O ports at 3000 [size=32]

01:00.0 PCI bridge: Intel Corporation 6311ESB/6321ESB PCI Express Upstream Port (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=01, secondary=02, subordinate=05, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: 52400000-52cfffff
	Capabilities: <access denied>

01:00.1 PIC: Intel Corporation 6311ESB/6321ESB I/OxAPIC Interrupt Controller (rev 01) (prog-if 20 [IO(X)-APIC])
	Flags: bus master, fast devsel, latency 0
	Memory at 52d00000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

01:00.3 PCI bridge: Intel Corporation 6311ESB/6321ESB PCI Express to PCI-X Bridge (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=01, secondary=06, subordinate=06, sec-latency=64
	Capabilities: <access denied>

02:00.0 PCI bridge: Intel Corporation 6311ESB/6321ESB PCI Express Downstream Port E1 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=02, secondary=03, subordinate=03, sec-latency=0
	Capabilities: <access denied>

02:01.0 PCI bridge: Intel Corporation 6311ESB/6321ESB PCI Express Downstream Port E2 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=02, secondary=04, subordinate=04, sec-latency=0
	Capabilities: <access denied>

02:02.0 PCI bridge: Intel Corporation 6311ESB/6321ESB PCI Express Downstream Port E3 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=02, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: 52400000-52cfffff
	Capabilities: <access denied>

05:00.0 Ethernet controller: Intel Corporation 80003ES2LAN Gigabit Ethernet Controller (Copper) (rev 01)
	Subsystem: Intel Corporation Unknown device 3499
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at 52c20000 (32-bit, non-prefetchable) [size=128K]
	Memory at 52800000 (32-bit, non-prefetchable) [size=4M]
	I/O ports at 2020 [size=32]
	Capabilities: <access denied>

05:00.1 Ethernet controller: Intel Corporation 80003ES2LAN Gigabit Ethernet Controller (Copper) (rev 01)
	Subsystem: Intel Corporation Unknown device 3499
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at 52c00000 (32-bit, non-prefetchable) [size=128K]
	Memory at 52400000 (32-bit, non-prefetchable) [size=4M]
	I/O ports at 2000 [size=32]
	Capabilities: <access denied>

08:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7300 GT] (rev a1) (prog-if 00 [VGA])
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at 51000000 (32-bit, non-prefetchable) [size=16M]
	Memory at 40000000 (64-bit, prefetchable) [size=256M]
	Memory at 50000000 (64-bit, non-prefetchable) [size=16M]
	I/O ports at 1000 [size=128]
	[virtual] Expansion ROM at 52000000 [disabled] [size=128K]
	Capabilities: <access denied>

0f:00.0 Network controller: Broadcom Corporation Unknown device 4328 (rev 01)
	Subsystem: Apple Computer Inc. Unknown device 0087
	Flags: bus master, fast devsel, latency 0
	Memory at 53000000 (64-bit, non-prefetchable) [size=16K]
	Memory at 52e00000 (64-bit, prefetchable) [size=1M]
	Capabilities: <access denied>

10:0b.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 01) (prog-if 10 [OHCI])
	Flags: bus master, medium devsel, latency 248, IRQ 16
	Memory at 52f04000 (32-bit, non-prefetchable) [size=2K]
	Memory at 52f00000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
```

cat /proc/asound/version:

> Advanced Linux Sound Architecture Driver Version 1.0.14.
Compiled on Aug 15 2007 for kernel 2.6.20-15-generic (SMP).

cat /proc/asound/card0/codec#0:

```
Codec: Realtek ALC885
Address: 0
Vendor Id: 0x10ec0885
Subsystem Id: 0x106b0c00
Revision Id: 0x100103
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
Node 0x02 [Audio Output] wcaps 0x11: Stereo
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x03 [Audio Output] wcaps 0x11: Stereo
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x04 [Audio Output] wcaps 0x11: Stereo
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x05 [Audio Output] wcaps 0x11: Stereo
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
Node 0x07 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Amp-In caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0x80 0x80]
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Connection: 1
     0x24
Node 0x08 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Amp-In caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0x80 0x80]
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Amp-In caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0x80 0x80]
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Connection: 1
     0x22
Node 0x0a [Audio Input] wcaps 0x100391: Stereo Digital
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
  Connection: 1
     0x1f
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x97 0x97] [0x1f 0x1f] [0x1f 0x1f] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97]
  Connection: 10
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17
Node 0x0c [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80]
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80]
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Connection: 2
     0x04 0x0b
Node 0x0f [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80]
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Connection: 2
     0x05 0x0b
Node 0x10 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x11 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x12 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x08373c: IN OUT HP Detect
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x20: IN
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x15 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x08373c: IN OUT HP Detect
  Pin Default 0x01014150: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Green
  Pin-ctls: 0x40: OUT
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x16 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x083c: IN OUT HP Detect
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x20: IN
  Connection: 5
     0x0c 0x0d 0x0e* 0x0f 0x26
Node 0x17 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x083c: IN OUT HP Detect
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x20: IN
  Connection: 5
     0x0c 0x0d 0x0e 0x0f* 0x26
Node 0x18 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x08373c: IN OUT HP Detect
  Pin Default 0x02214040: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
  Pin-ctls: 0xc0: OUT HP
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x19 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x08373c: IN OUT HP Detect
  Pin Default 0x01813110: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
  Pin-ctls: 0x24: IN
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1a [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x08373c: IN OUT HP Detect
  Pin Default 0x90100130: [Fixed] Speaker at Int N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x40: OUT
  Connection: 5
     0x0c 0x0d 0x0e 0x0f 0x26*
Node 0x1b [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x08373c: IN OUT HP Detect
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x20: IN
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1c [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x0820: IN
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x20: IN
Node 0x1d [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x0820: IN
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x20: IN
Node 0x1e [Pin Complex] wcaps 0x400300: Mono Digital
  Pincap 0x0810: OUT
  Pin Default 0x0145e160: [Jack] SPDIF Out at Ext Rear
    Conn = Optical, Color = White
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x06
Node 0x1f [Pin Complex] wcaps 0x400200: Mono Digital
  Pincap 0x0820: IN
  Pin Default 0x01c5e120: [Jack] SPDIF In at Ext Rear
    Conn = Optical, Color = White
  Pin-ctls: 0x20: IN
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
Node 0x21 [Volume Knob Widget] wcaps 0x600080: Mono
Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x24 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x25 [Audio Output] wcaps 0x11: Stereo
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x26 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80]
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Connection: 2
     0x25 0x0b
```

ls -l /sys/module/snd_hda_intel/parameters:

> total 0
-r--r--r-- 1 root root 4096 2007-08-15 22:06 enable
-r--r--r-- 1 root root 4096 2007-08-15 22:06 id
-r--r--r-- 1 root root 4096 2007-08-15 22:06 index
-r--r--r-- 1 root root 4096 2007-08-15 22:06 model
-r--r--r-- 1 root root 4096 2007-08-15 22:06 position_fix
-r--r--r-- 1 root root 4096 2007-08-15 22:06 probe_mask
-r--r--r-- 1 root root 4096 2007-08-15 22:06 single_cmd

amixer:

```
Simple mixer control 'Headphone',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [on] Capture [off]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 0 [0%] [-16.00dB] [off]
  Front Right: Capture 0 [0%] [-16.00dB] [off]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 0 [0%] [-16.00dB] [off]
  Front Right: Capture 0 [0%] [-16.00dB] [off]
Simple mixer control 'Capture',2
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 0 [0%] [-16.00dB] [off]
  Front Right: Capture 0 [0%] [-16.00dB] [off]
Simple mixer control 'Input Source',0
  Capabilities: enum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: enum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Mic'
Simple mixer control 'Input Source',2
  Capabilities: enum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Mic'
```

That's quite a lot.

---

### Post by nicfagn on 2007-08-15
The data seems to correspond to the alsa code.
Indeed I derived the patch for the iMac24 right from the Mac pro code and after a lot of trial and error.
From this experience and looking at the Mac Pro code I would change this string (only one instance):

{0x1a, AC_VERB_SET_CONNECT_SEL, 0x04},

to

{0x1a, AC_VERB_SET_CONNECT_SEL, 0x00},

in the alsa-kernel/pci/hda/patch_realtek.c file, and then make, install and reload of the drivers.
Obviously, no guarantees. ;-)

By the way, can you at least hear the headphones?

Bye

---

### Post by Dingbats on 2007-08-15
I haven't done the things you said in the last post yet, but I tried the headphones and they work, but the volume is really low. Should I still do the things you said in the last post?

---

### Post by nicfagn on 2007-08-15
I think it doesn't cost much to try, and you can easily undo this change.
So, since at the moment I can't think of anything better, my answer is yes.

Bye

---

### Post by Dingbats on 2007-08-16
Yay, it works! :D Thanks a very lot! Is it safe to remove the alsa-driver-1.0.14 directory and the udiff patch I downloaded or do I have to leave them cluttering up my desktop?

---

### Post by nicfagn on 2007-08-16
> **Dingbats said:**
> Yay, it works! :D Thanks a very lot! Is it safe to remove the alsa-driver-1.0.14 directory and the udiff patch I downloaded or do I have to leave them cluttering up my desktop?

Great news !!! :popcorn:

About the patch, you don't need it at all since it is for the iMac 24'' (2006) that has the same audio hardware as the Mac Pro but with a different configuration.
The bad news is that you have to redo the entire procedure at every kernel update, at least until this problem is fixed in alsa itself or in the ubuntu alsa version. 
For this to happen you should open a bug  in alsa bugtracker and in ubuntu launchpad.
In the end, it is best that you keep the alsa-driver-1.0.14 directory at hand, but you can move it wherever you like.

Bye

Nicola Fagnani

---

### Post by Dingbats on 2007-08-16
Oh, so what I have to do after every kernel update is recompile the drivers with "make" and then install with "sudo make install-modules"? Do I have to run "./configure --with-cards=hda-intel" too?

---

### Post by nicfagn on 2007-08-16
You have to do "./configure --with-cards=hda-intel" as the first step to use the newly installed kernel headers during compilation.

Good hearing

---

### Post by Dingbats on 2007-08-17
Bumping again...

The headphones don't work after the alsa configuring and recompiling. When I connect my headphones to the jack, the sound still plays through the internal speakers. I updated the Linux kernel and recompiled the alsa kernel, but nothing changed. The headphone switch in the volume control panel is on.

---

### Post by nicfagn on 2007-08-17
> **Dingbats said:**
> 
The headphones don't work after the alsa configuring and recompiling. When I connect my headphones to the jack, the sound still plays through the internal speakers. I updated the Linux kernel and recompiled the alsa kernel, but nothing changed. The headphone switch in the volume control panel is on.

If you mean that the headphones don't work because the speakers aren't muted, that's not so strange.
In fact muting/unmuting of speakers on detection of jack insertion/removal, isn't implemented in the Mac Pro driver.
If you can't hear anything from headphones I don't know how to explain it, they should work as before AFAIK.

Anyway, if you really care about the speaker auto muting you can try the attached patch.
To apply this you have to issue the following command in the alsa-driver-1.0.14 directory:
```
patch -p1 < /path/to/macpro-automute.txt
```
Let me know if you get into trouble.

Bye

---

### Post by Dingbats on 2007-08-19
> **nicfagn said:**
> Anyway, if you really care about the speaker auto muting you can try the attached patch.
To apply this you have to issue the following command in the alsa-driver-1.0.14 directory:
```
patch -p1 < /path/to/macpro-automute.txt
```
Let me know if you get into trouble.
Still no difference.

Anyway, I don't necessarily need it to detect insertion/removal of headphones in the jack. But is there a way to switch the sound output manually? It doesn't matter if it's complicated, because when/if I get the headphones to work, that output is the only one I'll use.

---

### Post by nicfagn on 2007-08-19
> **Dingbats said:**
> Still no difference.

Oops. The patch wasn't compilable against 1.0.14 so I made a corrected one. 
You have to apply it to original alsa-driver-1.0.14 sources not the ones you have already changed. 

> Anyway, I don't necessarily need it to detect insertion/removal of headphones in the jack. But is there a way to switch the sound output manually? It doesn't matter if it's complicated, because when/if I get the headphones to work, that output is the only one I'll use.

With the current mixer configuration you can disable headphones independently from the speakers but not vice versa. 
I know, doesn't make much sense but you can deal with it using automuting. I hope this time it works.

Bye

---

### Post by Dingbats on 2007-08-20
> You have to apply it to original alsa-driver-1.0.14 sources not the ones you have already changed. 
Is that the totally unchanged driver sources found at [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2), or should I still apply the changes you describe in [this post](http://ubuntuforums.org/showpost.php?p=2978364&postcount=41)?

---

### Post by nicfagn on 2007-08-20
The totally unchanged driver sources found at [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2").

Bye

---

### Post by Dingbats on 2007-08-20
Ok, did the patching. I take it I should not run

```
./configure --with-cards=hda-intel
```

before compiling? Or should I?

---

### Post by nicfagn on 2007-08-20
The first time you compile some new sources you have to run ./configure to setup compilation.
So you should run:

```
./configure --with-cards=hda-intel
```

before the other steps.

---

### Post by Dingbats on 2007-08-20
Ok, recompiled and reinstalled. Progress! Now I get sound through the headphones and it automutes the internal speakers, but the headphone sound is extremely low. I have all volumes set at max. When I open the alsamixer, the headphones strip just shows the numbers [00] and there's no way to change it, but it has always been like that.

---

### Post by nicfagn on 2007-08-20
The headphones don't have a volume control in the mixer, just a switch to mute/unmute them.
You can control the headphones volume with the Front and the PCM volumes, but you said they are already at their max. :confused:
Excuse the silly question, but are you sure you don't have a slider on your headphones affecting the volume? Did you try with another pair of headphones?
I ask these questions because I tried the Mac Pro config on my iMac 24 and had no problems hearing the headphones. 
It's really a pity I can't afford a Mac Pro to effectively test this.;)

---

### Post by Dingbats on 2007-08-20
No, there's no volume slider on my headphones. I tried another pair too, but it's the same thing. So... I'm not sure what I'll do now. :(

---

### Post by Dingbats on 2007-08-20
Wait a minute! I tried plugging the headphones into the line out jack at the back of the box, and then I get normal-volumed sound through them! But it doesn't mute the internal speakers.

Is this the way to go? If I manage to manually mute the internal speakers I can connect my own speakers to the line out jack, right? It makes sense to me. But then how do I mute the internal speakers?

---

### Post by nicfagn on 2007-08-20
The simplest way is to plug another headphone into the headphones jack. :lolflag:
For a definitive solution the mixer configuration should be changed but this require some time to test.
If I manage to find a possible solution I'll post here.

Bye

---

### Post by nicfagn on 2007-08-20
The attached patch improves on the previous one, replacing the PC Speaker Volume (it never worked for me) with a PC Speaker Switch.
The switch should control the speaker output independently from other outputs.
You have to apply the patch to the totally unchanged alsa-driver-1.0.14 sources.

Bye

---

### Post by Dingbats on 2007-08-20
> **nicfagn said:**
> The simplest way is to plug another headphone into the headphones jack. :lolflag: 

Can't believe I didn't think of that! :biggrin: That'll do as a (hopefully) temporary solution!

---

### Post by Dingbats on 2007-08-20
> **nicfagn said:**
> The attached patch improves on the previous one, replacing the PC Speaker Volume (it never worked for me) with a PC Speaker Switch.
The switch should control the speaker output independently from other outputs.
You have to apply the patch to the totally unchanged alsa-driver-1.0.14 sources.

Bye

We just posted at the same time, so I'm a bit confused. Which attached patch?

---

### Post by nicfagn on 2007-08-20
Sorry, I had to reboot in Mac OS X to attach the patch, because Firefox under Ubuntu gives me a Bad Request Error when uploading the file.

P.S.: the patch is in the previous post.

---

### Post by Dingbats on 2007-08-20
It works! You're my hero! :D Thank you very very much!

I will probably still have to recompile and reinstall after every kernel update though, right?

EDIT: Except the headphones jack doesn't give any sound at all now. But I can live with that, I can still connect my speakers to the line out jack at the back. EDIT 2: That's actually not no sound, but very very little sound. Nonetheless, nevermind.

---

### Post by nicfagn on 2007-08-20
> I will probably still have to recompile and reinstall after every kernel update though, right?

Unfortunately, yes.
And if you move the alsa-driver-1.0.14 directory you probably have to redo the ./configure step (if in doubt redo it, it doesn't harm).

Ciao

Nicola

---

### Post by nicfagn on 2007-09-10
For anyone interested, now alsa-driver-1.0.15rc1 sources support the iMac 24'' out of the box, and they work with suspend and resume too. :-)

---

### Post by micheleo on 2007-10-02
I followed the instructions (imac 24") but still no sound. 
Here are the outputs

```
 cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.14.
Compiled on Oct  2 2007 for kernel 2.6.20-16-generic (SMP).
```

```
cat /proc/asound/card0/codec#0
Codec: Realtek ALC885
Address: 0
Vendor Id: 0x10ec0885
Subsystem Id: 0x106b3200
Revision Id: 0x100103
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
Node 0x02 [Audio Output] wcaps 0x11: Stereo
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x03 [Audio Output] wcaps 0x11: Stereo
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x04 [Audio Output] wcaps 0x11: Stereo
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x05 [Audio Output] wcaps 0x11: Stereo
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
Node 0x07 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Amp-In caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0x19 0x19]
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Connection: 1
     0x24
Node 0x08 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Amp-In caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0x19 0x19]
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Amp-In caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0x18 0x18]
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Connection: 1
     0x22
Node 0x0a [Audio Input] wcaps 0x100391: Stereo Digital
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
  Connection: 1
     0x1f
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x1d 0x1d] [0x00 0x00] [0x1f 0x1f] [0x00 0x00] [0x00 0x00] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97]
  Connection: 10
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17
Node 0x0c [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Connection: 2
     0x04 0x0b
Node 0x0f [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x05 0x0b
Node 0x10 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x11 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x12 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x08373c: IN OUT HP Detect
  Pin Default 0x90100140: [Fixed] Speaker at Int N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x40: OUT
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x15 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x08373c: IN OUT HP Detect
  Pin Default 0x012b4050: [Jack] HP Out at Ext Rear
    Conn = Comb, Color = Green
  Pin-ctls: 0xc0: OUT HP
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x16 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x083c: IN OUT HP Detect
  Pin Default 0x90100141: [Fixed] Speaker at Int N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x40: OUT
  Connection: 5
     0x0c 0x0d 0x0e* 0x0f 0x26
Node 0x17 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x083c: IN OUT HP Detect
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x20: IN
  Connection: 5
     0x0c 0x0d 0x0e 0x0f* 0x26
Node 0x18 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x08373c: IN OUT HP Detect
  Pin Default 0x90a00110: [Fixed] Mic at Int N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x24: IN
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x19 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x08373c: IN OUT HP Detect
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x20: IN
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1a [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x08373c: IN OUT HP Detect
  Pin Default 0x018b3020: [Jack] Line In at Ext Rear
    Conn = Comb, Color = Blue
  Pin-ctls: 0x20: IN
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1b [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x08373c: IN OUT HP Detect
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x20: IN
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1c [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x0820: IN
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x20: IN
Node 0x1d [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x0820: IN
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x20: IN
Node 0x1e [Pin Complex] wcaps 0x400300: Mono Digital
  Pincap 0x0810: OUT
  Pin Default 0x014be060: [Jack] SPDIF Out at Ext Rear
    Conn = Comb, Color = White
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x06
Node 0x1f [Pin Complex] wcaps 0x400200: Mono Digital
  Pincap 0x0820: IN
  Pin Default 0x01cbe030: [Jack] SPDIF In at Ext Rear
    Conn = Comb, Color = White
  Pin-ctls: 0x20: IN
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
Node 0x21 [Volume Knob Widget] wcaps 0x600080: Mono
Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x24 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x25 [Audio Output] wcaps 0x11: Stereo
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x26 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Connection: 2
     0x25 0x0b

```

```
amixer
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 29 [94%] [9.00dB] [on]
  Front Right: Playback 29 [94%] [9.00dB] [on]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [on] Capture [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 25 [54%] [9.00dB] [on]
  Front Right: Capture 25 [54%] [9.00dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 25 [54%] [9.00dB] [on]
  Front Right: Capture 25 [54%] [9.00dB] [on]
Simple mixer control 'Capture',2
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 24 [52%] [8.00dB] [on]
  Front Right: Capture 24 [52%] [8.00dB] [on]
Simple mixer control 'Input Source',0
  Capabilities: enum
  Items: 'Mic' 'Line'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: enum
  Items: 'Mic' 'Line'
  Item0: 'Mic'
Simple mixer control 'Input Source',2
  Capabilities: enum
  Items: 'Mic' 'Line'
  Item0: 'Mic'

```

Hope you can help me ;)

Michele

---

### Post by nicfagn on 2007-10-02
You probably have a new iMac 24'', isn't it? Your codec has a different subsystem id compared to my late 2006 iMac 24'', and a different pin configuration, so you can't use the previous patch.
It seems that someone has to write a new patch :-)

Bye

Nicola

---

### Post by nicfagn on 2007-10-02
Can you confirm that the attached patch is working?
In particular that speakers, headphones and microphone are functional and that speakers are muted on headphone insertion and unmuted on headphones removal.

Thanks

---

### Post by micheleo on 2007-10-02
> **nicfagn said:**
> You probably have a new iMac 24'', isn't it? Your codec has a different subsystem id compared to my late 2006 iMac 24'', and a different pin configuration, so you can't use the previous patch.
It seems that someone has to write a new patch :-)

Bye

Nicola

Yes, it is... 
Ok, i'll wait then ;)
Thank you

Michele

---

### Post by nicfagn on 2007-10-02
> **micheleo said:**
> Yes, it is... 
Ok, i'll wait then ;)
Thank you

Michele

Already done, the patch is in the previous post. :)
Can you check if it works?

Bye

---

### Post by micheleo on 2007-10-02
ohhh! now it works!
thank you so much!

Michele :popcorn:

PS: tested only speakers, I'm going to check the rest as soon as possible ( @work.. ).

---

### Post by nicfagn on 2007-10-08
> **micheleo said:**
> ohhh! now it works!
thank you so much!

Michele :popcorn:

PS: tested only speakers, I'm going to check the rest as soon as possible ( @work.. ).

Still working, or you didn't find the headphones to do the check? :roll:

---

### Post by micheleo on 2007-10-12
Sorry, i'm a little bit late.. :(
The headphones doesn't work at all and the speakers are not muted.
The sound from the speakers it's very metallic, seems a 80's radio..

M.

---

### Post by nicfagn on 2007-10-12
> **micheleo said:**
> Sorry, i'm a little bit late.. :(
The headphones doesn't work at all and the speakers are not muted.
The sound from the speakers it's very metallic, seems a 80's radio..

M.

Never mind :)
In fact there is an error in the patch preventing automuting, but I could not figure out why the headphones shouldn't work or the speakers sound be so strange :confused:

Anyway I posted a [patch]("http://ubuntuforums.org/showpost.php?p=3519262&postcount=24") fixing automuting in this [thread]("http://ubuntuforums.org/showthread.php?t=572081") where the discussion is more focused on the new iMac.

---

### Post by micheleo on 2007-10-14
Thank you very much. 
Tomorrow (@work) I'm going to check it out!

M. :)

---

### Post by micheleo on 2007-10-18
The automuting works... but no sound by the headphones Oo
:(

---

### Post by nicfagn on 2007-10-18
At the moment I don't know how to fix that, but If there is something new I'll post here.

Cheers

---

### Post by Sawta on 2007-10-26
In reply to [nicfagn's post]("http://ubuntuforums.org/showpost.php?p=2978364&postcount=41"):

**My situation**: I can hear a bit of sound using alsamixer on my headphones at full blast, but like most, it's only a whisper.

**A few questions/concerns about the posted solution**:

1) Will this work for Ubuntu 7.10?  1a) If no there an updated patch done/in the works for 7.10?

2) My iMac was shipped in June of 2007, it was a few months before the updated white and black one's, would mine be considered a 2006 model or 2007?  I'm asking because read one of your posts that mentioned that depending on when it was released could change how the codecs were configured for the 24" models.

3) I was reading over some of the files in the first file listed that I had downloaded.  It was labeled "WARNING", it disscused how you should mute all of your levels in alsamixer, does this mean turn them down to zero, or use a different command used in teriminal to mute them?

**Side note**: I did try to follow the instructions listed above, but failed quiet early on.  I downloaded the file, and put in the "tar --bzip2 -xvf alsa-driver-1.0.14.tar.bz2" command, but it didn't seem to work.  Not sure if I was supposed to type in cd (file name that was just downloaded) or just type in "tar --bzip2 -xvf alsa-driver-1.0.14.tar.bz2" when terminal first pops up.  Here's the message:

```
s@Habibi:~$ tar --bzip2 -xvf alsa-driver-1.0.14.tar.bz2
tar: alsa-driver-1.0.14.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

```

Terribly sorry if this seems obvious, I'm still getting used to using Command Prompt and Java at school for Windows..let alone Ubuntu and Terminal commands ;)
Advice, suggestions, whatever would be just peachy.

---

### Post by cyberdork33 on 2007-10-26
> **Sawta said:**
> 2) My iMac was shipped in June of 2007, it was a few months before the updated white and black one's, would mine be considered a 2006 model or 2007?  I'm asking because read one of your posts that mentioned that depending on when it was released could change how the codecs were configured for the 24" models.
You have the same model as he does then. He posted a patch for it early on, but I don't think it is needed anymore. I am suprised this was not fixed in Gutsy though.
[COLOR=Red]**DISCLAIMER: NOT FOR ALUMINUM IMACS**[/COLOR]
> **nicfagn said:**
> For anyone interested, now alsa-driver-1.0.15rc1 sources support the iMac 24'' out of the box, and they work with suspend and resume too. :-)
So you have to just compile the latest source it sounds like.
You can follow his earlier post, but you need to get the later sources from ALSA, and you don't need to apply any patch:
[http://ubuntuforums.org/showpost.php?p=2978364&postcount=41](http://ubuntuforums.org/showpost.php?p=2978364&postcount=41)

Newest source can be found here:
[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc3.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc3.tar.bz2)

---

### Post by nicfagn on 2007-10-26
> **Sawta said:**
> 
1) Will this work for Ubuntu 7.10?  1a) If no there an updated patch done/in the works for 7.10?


I edited the post, adding a step to make the instructions work on Gutsy too.

> 
2) My iMac was shipped in June of 2007, it was a few months before the updated white and black one's, would mine be considered a 2006 model or 2007?  I'm asking because read one of your posts that mentioned that depending on when it was released could change how the codecs were configured for the 24" models.


The date refers to the initial release of the model, when it was announced to the customers. 
So your model should be a late 2006 Intel iMac 24'' (a white iMac). This terminology is used by Apple in its technical documentation.
Anyway, what really counts are the vendor id and the subsystem id listed on the first lines of the output of the command:

```
cat /proc/asound/card0/codec#0
```

For that patch to work, they must be:

```

Vendor Id: 0x10ec0885
Subsystem Id: 0x106b1000

```


> 
3) I was reading over some of the files in the first file listed that I had downloaded.  It was labeled "WARNING", it disscused how you should mute all of your levels in alsamixer, does this mean turn them down to zero, or use a different command used in teriminal to mute them?


Perhaps the warning was to **unmute** all the channels in alsamixer, that is allow the sound to go trough all the possible paths to you ears.
Anyway, in alsamixer to mute/unmute a channel you press the M key while the channel is selected. When the channel is muted you should see a pair of M under it. 

> **Side note**: I did try to follow the instructions listed above, but failed quiet early on.  I downloaded the file, and put in the "tar --bzip2 -xvf alsa-driver-1.0.14.tar.bz2" command, but it didn't seem to work.  Not sure if I was supposed to type in cd (file name that was just downloaded) or just type in "tar --bzip2 -xvf alsa-driver-1.0.14.tar.bz2" when terminal first pops up.  Here's the message:

```
s@Habibi:~$ tar --bzip2 -xvf alsa-driver-1.0.14.tar.bz2
tar: alsa-driver-1.0.14.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

```


Probably you didn't issue the command in the directory containing the alsa-driver-1.0.14.tar.bz2 file.
To see the current directory in a terminal use the **pwd** command.
You can choose where to keep the alsa sources, e.g. your home directory, and change directory to there with:

cd /path/to/sources/

(cd without arguments to go to your home dir)
Then you can use the command:

tar --bzip2 -xvf **/path/to/file**/alsa-driver-1.0.14.tar.bz2

where **/path/to/file** is the absolute path of the directory containing the alsa-driver-1.0.14.tar.bz2 file.

> 
Terribly sorry if this seems obvious, I'm still getting used to using Command Prompt and Java at school for Windows..let alone Ubuntu and Terminal commands ;)
Advice, suggestions, whatever would be just peachy.

Don't worry, it's hard for everyone at the start. :)
Man pages are a great resource, use the man command to consult them:

```
man man
```

Ciao

---

### Post by Sawta on 2007-10-26
So should it go as follows:

```
tar --bzip2 -xvf alsa-driver-1.0.15.tar.bz
sudo apt-get install libc6-dev
./configure --with-cards=hda-intel
make
sudo mv -v /lib/modules/$(uname -r)/ubuntu/media/snd-hda-intel/snd-hda-intel{,-ubuntu}.ko
sudo make install-modules
```

I'm not sure if the process is accurate or not, since I don't need to install that patch and since some of the files have changed, I don't know if I've adjusted the name to the appropriate name or not.:confused:  *Edit* Oh, I've also tried the first command line that I listed, and it was giving me the same error that I had listed last time.  Do I need to extract a file before entering that or something?

---

### Post by nicfagn on 2007-10-26
That should do for the latest alsa release.
What is the output of:

```
ls -l alsa-driver-1.0.15.tar.bz
```

?

---

### Post by cyberdork33 on 2007-10-26
> **Sawta said:**
> I've also tried the first command line that I listed, and it was giving me the same error that I had listed last time.  Do I need to extract a file before entering that or something?

Your command sequence seems right at first look. 

you are getting the error because you are not typing the full filename.

The first command is extracting the archive (that is what the x option does).

Type:
tar --bzip -xvf alsa[TAB]
This will auto-complete the line (it looks at the files in the directory). if you have more than one file that starts with alsa, then hitting tab twice will list all the options, and you can refine it further.

---

### Post by Sawta on 2007-10-26
Whoops, post [94]("http://ubuntuforums.org/showpost.php?p=3639446&postcount=94") came in right as I was typing in my message.

For the cat /proc/asound/card0/codec#0 line, the vendor id and subsystem id matched up, so at the very least, it seems possible.

For the muted question, yes, I probably just read it wrong, I was just very apprehensive at first glance because I afraid it would get working with everything at full blast and blow my speakers/ear drums as a result.:lolflag:

For the question that nicfagn asked:
```
s@habibi:~$ ls -l alsa-driver-1.0.15.tar.bz
ls: alsa-driver-1.0.15.tar.bz: No such file or directory
```

As for this next part, I was kicking myself when I realized that instead of extracting anything from the archive manager, all I had to do was drag it to the desktop.  I believe that that would create an obvious problem to start.  After doing that I followed cyberdork33's advice (for using tab).  Here's what happened.

```
s@habibi:~$ cd Desktop
s@habibi:~/Desktop$ dir
alsa-driver-1.0.15rc3
s@habibi:~/Desktop$ tar --bzip -xvf alsa-driver-1.0.15rc3/tar: alsa-driver-1.0.15rc3/: Cannot read: Is a directory
tar: At beginning of tape, quitting now
tar: Error is not recoverable: exiting now

bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Invalid argument
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

tar: Child returned status 2
tar: Error exit delayed from previous errors
s@habibi:~/Desktop$ 

```

I appreciate all the help you guys are giving me, I have to leave for work in a few minutes, but I should be able to respond in a few hours if anyone wants to continue this without me.  Thanks for holding my hand through this :popcorn:

---

### Post by nicfagn on 2007-10-26
Dragging to the desktop from archive manager (File Roller I suppose), you already extracted the sources directory and you can skip the command:

```
tar --bzip2 -xvf alsa-driver-1.0.15.tar.bz2

```
and go on with 

```
sudo apt-get install libc6-dev
```

---

### Post by cyberdork33 on 2007-10-26
ok here is exactly, what I did. Note, I keep my sources in a 'Sources' directory in my home folder. you can put your wherever you want.

```

cd Sources
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc3.tar.bz2
tar -xvf alsa[TAB]
cd alsa[TAB]

```
from that point you can do the ./configure command and the remaining to compile. I hope this helps, I don't really understand where the wires are getting crossed.

---

### Post by cyberdork33 on 2007-10-26
> **nicfagn said:**
> Dragging to the desktop from archive manager (File Roller I suppose), you already extracted the sources directory and you can skip the command:

```
tar --bzip2 -xvf alsa-driver-1.0.15.tar.bz2

```and go on with 

```
sudo apt-get install libc6-dev
```
oh that's what he did... ok, yea that makes sense.

---

### Post by Sawta on 2007-10-27
> **cyberdork33 said:**
> ok here is exactly, what I did. Note, I keep my sources in a 'Sources' directory in my home folder. you can put your wherever you want.


Okay, so I used:
```

cd Desktop
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc3.tar.bz2

```

Seemed to go okay.  Took a while to load but worked.  Followed this with
"tar -xvf alsa[TAB]"

I believe that it said that there was 1 error detected after the tar -xvf alsa[TAB] command, so I closed Terminal and reffered back to the steps listed on page seven by nicfagn and thought that perhaps I had missed something in between.  Unfortunately, I didn't save the error message.

Put in the  following:
```
s@habibi:~$ pwd
/home/s
s@habibi:~$ cd Desktop
s@habibi:~/Desktop$ sudo apt-get install libc6-dev
[sudo] password for s:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-libc-dev
Suggested packages:
  glibc-doc manpages-dev
The following NEW packages will be installed:
  libc6-dev linux-libc-dev
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 3148kB of archives.
After unpacking 15.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com gutsy/main linux-libc-dev 2.6.22-14.46 [652kB]
Get:2 http://us.archive.ubuntu.com gutsy/main libc6-dev 2.6.1-1ubuntu9 [2496kB]
Fetched 3148kB in 4s (703kB/s)      
Selecting previously deselected package linux-libc-dev.
(Reading database ... 89358 files and directories currently installed.)
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.22-14.46_amd64.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.6.1-1ubuntu9_amd64.deb) ...
Setting up linux-libc-dev (2.6.22-14.46) ...
Setting up libc6-dev (2.6.1-1ubuntu9) ...

```

Followed by
```
s@habibi:~/Desktop$ cd alsa-driver-1.0.15rc3/
s@habibi:~/Desktop/alsa-driver-1.0.15rc3$ ./configure --with-cards=hda-intel
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /home/s/Desktop/alsa-driver-1.0.15rc3
checking cross compile... 
checking for directory with kernel source... /lib/modules/2.6.22-14-generic/build
checking for directory with kernel build... 
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.22-14-generic
checking for GCC version... Kernel compiler:  Used compiler: gcc (GCC) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... no
checking for existing ALSA module... yes
checking for Red Hat kernel... auto
checking for Red Hat kernel... no
checking for SUSE kernel... auto
checking for SUSE kernel... no
checking for CONFIG_EXPERIMENTAL... yes
checking for kernel linux/config.h... no
Creating <linux/config.h>...
checking to modify of kernel linux/kmod.h... no
checking for kernel linux/utsrelease.h... yes
checking for kernel linux/compiler.h... yes
checking for kernel linux/pm.h... yes
checking for kernel linux/spinlock.h... yes
checking for kernel linux/irq.h... yes
checking for kernel linux/threads.h... yes
checking for kernel linux/rwsem.h... yes
checking for kernel linux/gameport.h... yes
checking for kernel media/v4l2-dev.h... yes
checking for kernel linux/devfs_fs_kernel.h... no
Creating a dummy <linux/devfs_fs_kernel.h>...
checking for kernel linux/highmem.h... yes
checking for kernel linux/workqueue.h... yes
checking for kernel linux/dma-mapping.h... yes
checking for kernel asm/hw_irq.h... yes
checking for kernel linux/device.h... yes
checking for kernel linux/platform_device.h... yes
checking for kernel linux/isa.h... yes
checking for kernel linux/jiffies.h... yes
checking for kernel linux/compat.h... yes
checking for kernel linux/log2.h... yes
checking for kernel linux/adb.h... yes
checking for kernel linux/cuda.h... yes
checking for kernel linux/pmu.h... yes
checking for kernel linux/moduleparam.h... yes
checking for kernel linux/syscalls.h... yes
checking for kernel linux/firmware.h... yes
checking for kernel linux/err.h... yes
checking for kernel linux/bitmap.h... yes
checking for kernel linux/mutex.h... yes
checking for kernel linux/latency.h... yes
checking for kernel linux/kthread.h... yes
checking for kernel asm/irq_regs.h... yes
checking for kernel module symbol versions... yes
checking for has ioport support... yes
checking for PCI support in kernel... yes
checking for I2C driver in kernel... module
checking for I2C_POWERMAC in kernel... unknown
checking for firmware loader... yes
checking for input subsystem in kernel... yes
checking for directory to store kernel modules... /lib/modules/2.6.22-14-generic/kernel/sound
checking for verbose procfs... on
checking for verbose printk... on
checking for debug level... none
checking for ISA support in kernel... no
checking for processor type... x86_64
checking for ISA DMA API... yes
checking for 32bit compat support... yes
checking for SMP... yes
checking for Video device support in kernel... yes
checking for ISA PnP driver in kernel... yes
checking for PnP driver in kernel... yes
checking for Kernel ISA-PnP support... no
checking for Kernel ISA-PnP module support... no
checking for strlcpy... yes
checking for snprintf... yes
checking for vsnprintf... yes
checking for scnprintf... yes
checking for sscanf... yes
checking for vmalloc_to_page... yes
checking for old kmod... no
checking for PDE... yes
checking for pci_set_consistent_dma_mask... yes
checking for pci_dev_present... yes
checking for msleep... yes
checking for msleep_interrupt... yes
checking for msecs_to_jiffies... yes
checking for tty->count is the atomic type... no
checking for video_get_drvdata... yes
checking for V4L1 layer... yes
checking for io_remap_pfn_range... yes
checking for kcalloc... yes
checking for kstrdup... yes
checking for kzalloc... yes
checking for create_workqueue with flags... no
checking for saved_config_space in pci_dev... yes
checking for new pci_save_state... yes
checking for register_sound_special_device... yes
checking for driver version... 1.0.15rc3
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for OSS PCM plugin system inclusion... yes
checking for RTC callback support in kernel... yes
checking for HPET support... yes
checking for dynamic minor numbers... no
checking for support of old API... yes
checking for Procfs support... yes
checking for USB support... yes
checking for class_simple... no
checking for old driver suspend/resume callbacks... no
checking for removal of page-reservation for nopage/mmap... yes
checking for nested class_device... yes
checking for new IRQ handler... yes
checking for gfp_t... yes
checking for PnP suspend/resume... yes
checking for new unlocked/compat_ioctl... yes
checking for x86-compatible PC... yes
checking for High-Res timers... no
checking for kernel PCMCIA
checking for PCMCIA support... yes
checking for PC9800 support in kernel... no
checking for parallel port support... yes
checking for power management... yes
checking for which soundcards to compile driver for... hda-intel
configure: creating ./config.status
config.status: creating version
config.status: creating Makefile.conf
config.status: WARNING:  Makefile.conf.in seems to ignore the --datarootdir setting
config.status: creating snddevices
config.status: creating utils/alsa-driver.spec
config.status: creating utils/buildrpm
config.status: creating toplevel.config
config.status: creating utils/alsasound
config.status: creating utils/alsasound.posix
config.status: creating include/pci_ids_compat.h
config.status: creating include/i2c-id_compat.h
config.status: creating include/config.h
config.status: creating include/config1.h
config.status: creating include/version.h
config.status: include/version.h is unchanged
config.status: creating include/autoconf-extra.h
config.status: include/autoconf-extra.h is unchanged
Hacking autoconf.h...

```

When I was reading through after words, I noticed the following message, not sure if its addressed further on in process, but thought it would be worth mentioning.
"*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel." 

Things seemed to go wrong when I tried the make command.  I wasn't sure if the directions were telling me to skip that command if I was using gusty, or if I should use it after entering the one below it.  I figure it would be worth a try and entered "make".

```
s@habibi:~/Desktop/alsa-driver-1.0.15rc3$ make
if [ ! -d include/sound -a ! -L include/sound ]; then \
          ln -sf ../alsa-kernel/include include/sound ; \
        fi
cp -puvf include/version.h include/sound/version.h
`include/version.h' -> `include/sound/version.h'
make dep
make[1]: Entering directory `/home/s/Desktop/alsa-driver-1.0.15rc3'
make[2]: Entering directory `/home/s/Desktop/alsa-driver-1.0.15rc3/acore'
copying file alsa-kernel/core/info.c
/home/s/Desktop/alsa-driver-1.0.15rc3/utils/patch-alsa: 24: patch: not found
make[2]: *** [info.c] Error 1
make[2]: Leaving directory `/home/s/Desktop/alsa-driver-1.0.15rc3/acore'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/home/s/Desktop/alsa-driver-1.0.15rc3'
make: *** [include/sndversions.h] Error 2

```

After seeing this error, I tryed the next few steps.  

```
s@habibi:~/Desktop/alsa-driver-1.0.15rc3$ sudo mv -v /lib/modules/$(uname -r)/ubuntu/media/snd-hda-intel/snd-hda-intel{,-ubuntu}.ko
`/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko' -> `/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel-ubuntu.ko'
s@habibi:~/Desktop/alsa-driver-1.0.15rc3$ sudo make install-modules
find /lib/modules/2.6.22-14-generic/kernel/sound -name 'snd*.*o' | xargs rm -f
find /lib/modules/2.6.22-14-generic/kernel/sound -name 'snd*.*o.gz' | xargs rm -f
find /lib/modules/2.6.22-14-generic/kernel/sound -name 'ac97_bus.*o' | xargs rm -f
find /lib/modules/2.6.22-14-generic/kernel/sound -name 'ac97_bus.*o.gz' | xargs rm -f
make[1]: Entering directory `/home/s/Desktop/alsa-driver-1.0.15rc3/acore'
mkdir -p /lib/modules/2.6.22-14-generic/kernel/sound/acore
cp snd-hwdep.ko snd-page-alloc.ko snd-pcm.ko snd-rtctimer.ko snd-timer.ko snd.ko /lib/modules/2.6.22-14-generic/kernel/sound/acore
cp: cannot stat `snd-hwdep.ko': No such file or directory
cp: cannot stat `snd-page-alloc.ko': No such file or directory
cp: cannot stat `snd-pcm.ko': No such file or directory
cp: cannot stat `snd-rtctimer.ko': No such file or directory
cp: cannot stat `snd-timer.ko': No such file or directory
cp: cannot stat `snd.ko': No such file or directory
make[1]: *** [modules_install] Error 1
make[1]: Leaving directory `/home/s/Desktop/alsa-driver-1.0.15rc3/acore'
make: *** [install-modules] Error 1

```

And that's about where I stand right now.  I've got about an hour to kill before work, if anyone notices some major error in my logic, feel free to point it out.  Wouldn't be surprised if I missed something, its still early.  Oh, and on a second note, I'm not sure which command did it, I think it might have been "wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc3.tar.bz2", but I seem to have a second folder matching the first one on my desktop.  It's not bothersome, I can see it leading to problems(or confusion) later on.  Should I delete this second copy or leave it be for now?

*Update*  After reloading my computer, I'm now reciving error messages when I try to access the volume control.  When I double click on it, it reads "No volume control GStreamer plugins and/or devices found.  The volume level will not change when trying to turn it up from the keyboard or remote.  I'm assuming this is a side affect from the error message.  If worst comes to worst, after we figure out what the problem is, I can do a fresh install of everything and follow the process the proper way.  I'm just trying to figure out the exact method of going about installing sound before I do that (Which patches and programs to install, etc.) mainly so others don't have to ask the same things when others get 7.10 or later.

---

### Post by nicfagn on 2007-10-27
The problem is that with the version of alsa you are using, you need the patch program to successfully compile.
So you need to do:

```
sudo apt-get install patch
```

then go back to the alsa source dir:

```
cd /home/s/Desktop/alsa-driver-1.0.15rc3
```

clean up the results of the previous compilation:

```
make clean
```

redo compilation

```
make
```

after checking that the modules where successfully compiled (if so, the fact is stated by a message at the end of compilation output), you can go on with modules installation:

```
sudo make install-modules
```

(you don't need to rename the original module again with 'sudo mv ...')

Good luck :)

---

### Post by cyberdork33 on 2007-10-27
where i put [TAB] I mean to hit the Tab key. you are getting there though.

---

### Post by PeterKnaggs on 2007-10-28
I was running into the following error when loading the
snd-hda-intel.ko module when I built it using the alsa sources:
> 
[   68.388635] snd_hda_intel: disagrees about version of symbol snd_ctl_add
[   68.388639] snd_hda_intel: Unknown symbol snd_ctl_add

Instead, I ended up building by applying nicfagn's patch to the Ubuntu kernel 
sources. I added a "Gutsy" section to my iMac24 page to describe the steps:
[http://www.penlug.org/twiki/bin/view/Main/LinuxHardwareInfoAppleiMac24](http://www.penlug.org/twiki/bin/view/Main/LinuxHardwareInfoAppleiMac24)



The audio patch to alsa unfortunately still hasn't made it into the Ubuntu 7.10 kernel 2.6.22-14. Once it does, suspend and resume would work too. But in the meantime, I used nicfagn's patch (the same patch that worked fine with Feisty), but the steps to build it are a bit longer:

>   sudo apt-get install build-essential fakeroot linux-source

We should now have the linux sources installed, as package linux-source-2.6.22.

There's quite a few steps. Overall, we have to unpack and patch the kernel sources, then set up a configuration file to build them with.

Let's start by unpacking the kernel sources, as follows:
> 
  cd $HOME
  tar jxvf /usr/src/linux-source-2.6.22.tar.bz2
  cd $HOME/linux-source-2.6.22

Now we set up the kernel build configuration file and enable the SND_HDA_INTEL module, as follows:

>   cat /boot/config-2.6.22-14-generic|sed 's/# CONFIG_SND_HDA_INTEL is not set/CONFIG_SND_HDA_INTEL=m/' > .config

Next, we patch the kernel driver sources for the snd-hda-intel.ko module:

>   cd $HOME/linux-source-2.6.22/sound/pci/hda/
  wget [http://www.penlug.org/twiki/pub/Main/LinuxHardwareInfoAppleiMac24/udiff-patch_realtek.txt](http://www.penlug.org/twiki/pub/Main/LinuxHardwareInfoAppleiMac24/udiff-patch_realtek.txt)
  patch < udiff-patch_realtek.txt

We're now ready to launch the kernel build, as follows. Perhaps there's a shortcut, as we only really need to build one module (snd-hda-intel.ko in this case). The machine is very speedy so building the entire kernel package doesn't take too long (less than half an hour).

>   cd $HOME/linux-source-2.6.22
  fakeroot make-kpkg --initrd kernel_image modules_image

Once the kernel build has completed, all we need is the snd-hda-intel.ko module. Since the $HOME/linux-source-2.6.22/Makefile has the setting "EXTRAVERSION = .9", we can find the module and copy it into the kernel modules directory as follows:

>   cd $HOME/linux-source-2.6.22/debian/linux-image-2.6.22.9/lib/modules/2.6.22.9/kernel/sound/pci/hda/
  cp /lib/modules/$(uname -r)/ubuntu/media/snd-hda-intel/snd-hda-intel.ko snd-hda-intel.ko_safe
  sudo cp snd-hda-intel.ko /lib/modules/$(uname -r)/ubuntu/media/snd-hda-intel

Now we need to install the module. The steps to do this are similar to those shown in the Audio section for Feisty
at my [http://www.penlug.org/twiki/bin/view/Main/LinuxHardwareInfoAppleiMac24](http://www.penlug.org/twiki/bin/view/Main/LinuxHardwareInfoAppleiMac24) page, basically:

>   sudo killall mixer_applet2

  sudo rmmod snd_hda_intel
  sudo rmmod snd_hda_codec
  sudo rmmod snd_pcm_oss
  sudo rmmod snd_mixer_oss
  sudo rmmod snd_pcm
  sudo rmmod snd_seq_dummy
  sudo rmmod snd_seq_oss
  sudo rmmod snd_seq_midi
  sudo rmmod snd_rawmidi
  sudo rmmod snd_seq_midi_event
  sudo rmmod snd_seq
  sudo rmmod snd_timer
  sudo rmmod snd_seq_device
  sudo rmmod soundcore
  sudo rmmod snd
  sudo rmmod snd_page_alloc
  sudo rmmod soundcore

  sudo modprobe snd_hda_intel

---

### Post by Sawta on 2007-10-28
SUCCESS!

I've never actually heard ubuntu start up before.  It's a very nice melody :)

I just want to thank you guys for all the help.  Took me a bit longer than it did for most, but as long as it's working, I'm happy.

If I can find the time, I might retrace my steps and make a more detailed guide for people that know as little as I do, but at the moment, I'd rather just tool around with this for a bit.

Thanks again everyone!:KS

---

### Post by Sawta on 2007-11-23
I just re-installed ubuntu 7.10 and figured that since the guide on this page can be a tad hard to follow at times that perhaps this one would hold the readers hand a little bit more. :P  This isn't trying to be insulting towards anyone, I just wanted to do a step by step of what I had to do to get sound working on my computer.

***This guide is only intended for people using the 24" iMac (Non-aluminum version, *it DOES make a difference*) who are trying to get sound working on ubuntu 7.10***
If you are using ubuntu 7.04 please refer to **[this guide]("http://ubuntuforums.org/showpost.php?p=2978364&postcount=41").**

*Before I begin, I would like to thank nicfagn and cyberdork33 for their constant help with my questions, as well as providing some excellent reference material for me to use while creating this guide*.

First of all, we are going to make a folder.  I'm doing this to eliminate any confusion about directory's and such that I and others have been having problems with.

Go to **Places->Home Folder** (Right click)**->Create New Folder** (Name it "Sources" the capitalization *might* make a difference.  If you really hate the name "Sources", name it whatever you choose, but keep in mind that you will have to modify this guide to follow what the new name of your file is.)

**Open terminal**
(Applications->Accessories->Terminal)

*Type in the following:*
```
cd Sources
```

*The "cd" of this command is telling your computer to go to the Sources folder that you have created and to put the following data into that folder.*

```
ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc3.tar.bz2
```

*What the above step is doing is accessing a website through your terminal and downloading a file from the site.  You will see an active loading sign after a few seconds.*

```
tar -xvf alsa[TAB]
```
*[TAB] means hit the tab key, NOT to literally put in the phrase "[TAB]"!:lolflag:*

*From what I understand, this step is very similar to "unzipping" a folder in Windows.  If you've never done that, don't worry about it.  Essentially, it just means that you downloaded a small file, and want to extract a larger file out of the small one, but again, don't worry too much about what it's doing and just DO IT.;)*

```
cd alsa[TAB]
```

*This line of code is telling your terminal to take a look at this larger file that you have just extracted*

```
./configure --with-cards=hda-intel
```

*This is telling this program to use a specific piece of hardware..I think.  Again, these explnations aren't of vital importance, I'm just hoping that you start to understand why you are entering what you are entering.*

```
make
```

```
sudo make install-modules
```

*Please make sure you enter this command correctly.*

Restart your computer and you should be fine.

*Note: although I did follow this guide, I haven't received any feedback from other users yet.  If you find a problem while using this guide at any point, please post your problem in this thread immediately.*

---

### Post by nicfagn on 2007-11-23
Thanks for the contribution, it surely helps in this long thread.
I noticed you used the rc3 version of the sources but you could have used the final alsa-driver-1.0.15 release as well.
For the rest, great guide!

Ciao
Nicola

---

### Post by Sawta on 2008-02-07
Thought it would be worth updating this:

Just fresh installed 7.10 again.  there was a problem with```
ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc3.tar.bz2
```
I directed my browser at the link to download the file.  It seemed to work okay (after sticking the files into the sources folder), but ran into another problem soon after.```
saw@FruitFuckerPrime-desktop:~/Sources/alsa-driver-1.0.15rc3$ sudo make install-modules
rm -f /snd*.*o /persist.o /isapnp.o
rm -f /snd*.*o.gz /persist.o.gz /isapnp.o.gz
make[1]: Entering directory `/home/saw/Sources/alsa-driver-1.0.15rc3/acore'
Makefile:6: /home/saw/Sources/alsa-driver-1.0.15rc3/Makefile.conf: No such file or directory
/home/saw/Sources/alsa-driver-1.0.15rc3/Rules.make:75: /Rules.make1: No such file or directory
make[1]: *** No rule to make target `/Rules.make1'.  Stop.
make[1]: Leaving directory `/home/saw/Sources/alsa-driver-1.0.15rc3/acore'
make: *** [install-modules] Error 1
```
I tried to remove it and follow the steps again, keeping an eye out for an error and saw this```
saw@FruitFuckerPrime-desktop:~$ cd Sources
saw@FruitFuckerPrime-desktop:~/Sources$ cd alsa-driver-1.0.15/
saw@FruitFuckerPrime-desktop:~/Sources/alsa-driver-1.0.15$ ./configure --with-cards=hda-intel
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
```
Not sure if the two are related, but it sure would be nice if I could get sound working again.

(Yesh, it's always such a production getting sound running on this thing :lolflag:)

---

### Post by cyberdork33 on 2008-02-07
the first error you posted is a result of the second error.

The second is a result of having not installed the build-essential package that enables the compiler to compile.
```
sudo aptitude install build-essential
```

---

### Post by Sawta on 2008-02-07
Thanks for the help.  The two commands that were not running ran this time around, however, I'm still without sound.

Here's the steps that I followed: (**I had cd'ed into  /home/saw/Sources/alsa-driver-1.0.15rc3/ not sure if that makes a difference or not.**)```
sudo aptitude install build-essential
``````
./configure --with-cards=hda-intel
``````
sudo make install-modules
```Followed by a reboot.  The volume control seems muted.  Nether the apple remote, nor the keyboard control/mute button will affect it.

I figure that perhaps since I just re-installed the OS it wouldn't be too painful to fresh install..again, besides, I need to modify the guide that I had posted so others don't have to go through this.  However before I do, I was hoping to get a double check on what I should put in before proceeding.

```
ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc3.tar.bz2
``` wasn't working, so I figure this command would be altered, but I'm not sure to what.  Maybe ```
ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.9rc4a.tar.bz2
``` since it seems to be the newest driver(?) on there.  I am unsure if these are all the same thing that the user is supposed to download except newer, updated versions and how they would affect the proceeding steps in the guide.

After the reinstall, I should put in ```
sudo aptitude install build-essential
``` immediately before ```
./configure --with-cards=hda-intel
``` while in  /home/saw/Sources/alsa-driver-1.0.15rc3/ or do I need to cd somewhere else?

(Sorry for all of these inexperienced questions.  I'm still on the verge of learning about UNIX at my university, so this is all a bit of a struggle (but still exciting) for me.)

---

### Post by cyberdork33 on 2008-02-08
> **Sawta said:**
> The volume control seems muted.  Nether the apple remote, nor the keyboard control/mute button will affect it.Make sure that channels are open. run 'alsamixer'. you can mute/unmute with the m key and adjust volumes, and navigate with the arrows.

> **Sawta said:**
> ```
ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc3.tar.bz2
``` wasn't working, so I figure this command would be altered, but I'm not sure to what.  Maybe ```
ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.9rc4a.tar.bz2
``` since it seems to be the newest driver(?) on there.  I am unsure if these are all the same thing that the user is supposed to download except newer, updated versions and how they would affect the proceeding steps in the guide.
1.0.9 < 1.0.15, so no, that is not newer. It looks like 1.0.16 was released just two days ago. One the main alsa page, the latest releases are on the right:
[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)

> **Sawta said:**
>  After the reinstall, I should put in ```
sudo aptitude install build-essential
``` immediately before ```
./configure --with-cards=hda-intel
``` while in  /home/saw/Sources/alsa-driver-1.0.15rc3/ or do I need to cd somewhere else?you do not need to install the build-essential package more than once, but yes, you need to install it before you can compile anything. you also need to make sure that the linux-source package is installed, or things will not able to link to the kernel properly (This is found in the "INSTALL" documentation in the alsa source archive).

OK, so here is the full procedure I would use.
Open a terminal (should be in your home directory) and navigate to the directory you want to keep the alsa source (I keep them in a directory called "Sources". Make sure that the build-essential package and linux-source packages are isntalled.
```
cd Sources
sudo aptitude install build-essential linux-source
```

Now download the latest alsa-driver release, (right now it is 1.0.16) and extract it.
```
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2
cd alsa-driver-1.0.16
```

Configure and build the source for your system:
```
./configure --with-cards=hda-intel
make
```

Now install the new modules. Normally, when compiling, you would use 'make install' but this package has a special option for if you are upgrading from a system with a set alsa system already:
```
sudo make install-modules
```

Now you can reboot, and hopefully, the replacement modules have loaded, and you can start alsamixer and make sure you channels are unmuted.
```
alsamixer
```

Good luck

---

### Post by nicfagn on 2008-02-15
> **Sawta said:**
> 
Here's the steps that I followed: (**I had cd'ed into  /home/saw/Sources/alsa-driver-1.0.15rc3/ not sure if that makes a difference or not.**)```
sudo aptitude install build-essential
``````
./configure --with-cards=hda-intel
``````
sudo make install-modules
```Followed by a reboot.  The volume control seems muted.  Nether the apple remote, nor the keyboard control/mute button will affect it.


It seems that you missed the step of the [previous post]("http://ubuntuforums.org/showpost.php?p=2978364&postcount=41"), needed only on 7.10 (Gutsy):

```
sudo mv -v /lib/modules/$(uname -r)/ubuntu/media/snd-hda-intel/snd-hda-intel{,-ubuntu}.ko
```

After that you have to redo also:

```
sudo make install-modules
```

and then reboot.

If you want to know why you have to do that, you can read this [post]("http://ubuntuforums.org/showpost.php?p=3552607&postcount=16").

Bye

---

### Post by AlexMorin on 2008-03-10
> **tuna74 said:**
> OT: I should just add that the instructions work if you have Fedora 7 as well (you have to download the kernel devel package though...)
I second that.
And you can safely skip the 'mv' step that isn't required for Fedora.
We still only get very weak audio out of the headphone jack.

Thanks!

---

