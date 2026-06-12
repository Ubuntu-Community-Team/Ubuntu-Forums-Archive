---
title: "2 apparently old problems: no sound &amp; dual cpu shows 1 not 2 cpu"
date: 2007-09-22
forum: Apple PPC Users
---

### Post by imacQ on 2007-09-22
G4 MDD duall 1ghz only shows one cpu instead of 2. Is there a patch/work around,  fix for this now? I did read the sticky here on the forum, and was under the impression that dual cpu install was no longer a prob. Would so much like to use both cpus. :( 

 The sound is not working at all. :confused: Must I go back to edgy or dapper to get sound? Googling showed me there is a way to fix sound issue on a Powerbook. PPC FAQ: [https://wiki.ubuntu.com/PowerPCFAQ#head-6b2faa0d86d3136075bf337a5809dad01738f83d](https://wiki.ubuntu.com/PowerPCFAQ#head-6b2faa0d86d3136075bf337a5809dad01738f83d) 

Will the Powerbook sound fix work for me on the MDD? Everything else after install (alt. cd) seems to be working very well.

---

### Post by stmiller on 2007-09-22
For the G4 dual processor boxes try this:
```

sudo apt-get install linux-image-powerpc-smp

```
and that should install a smp aware kernel. I don't have one of these machines to verify.

---

### Post by frog_pilot on 2007-09-22
There are some more metapackages you have to install for full smp-support. For full smp-support I installed the following metapackages in synaptics (G4 MDD Dual 1,25):

```
linux-image-powerpc-smp
linux-headers-powerpc-smp
linux-restricted-modules-powerpc-smp
linux-powerpc-smp
```
and simultaneously  uninstalled the corresponding normal metapackages. You have to only change these metapackages, otherwise you wont get the right kernelupdates

and for sound on internal onboard soundcard you have to type```
sudo modprobe snd-powermac
```to load the driver once or add the line```
snd-powermac
```to your /etc/modules to load the driver on system start. Or try my /etc/modules:```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

snd-powermac
apm_emu
sbp2
therm_windtunnel
fuse
```

---

### Post by imacQ on 2007-09-22
Thanks frog_pilot; I'm in the process of doing the synaptic installs and uninstalls now with finger crossed for smp kernel, image, etc. now. Do I need to do something with yaboot before restart? have message saying "want to abort removal now?" and if in doubt answer yes. or if you know what you're doing and prepared to hose your system then answer no :shock: ?

LATER after above message this is what happened
AuOh... well after downloading and starting install/uninstall i get an error: E: linux-image-2.6.20-16 powerpc: subprocess pre-removal scripy returned error exit status 1 

got suggestions?

---

### Post by frog_pilot on 2007-09-22
the first message about aborting removal you can answer "no" if you not only marked the items to remove. You have to mark also the packages you want to install before applying the system changes. You don't have to change yaboot.conf manually after changing your kernel-metapakages.

Can you restart your system? For the second message I have no clear suggestions. But it seems on your system occurred an error while removing the old kernel. The new kernel-packages name would be ```
linux-image-2.6.20-16-powerpc-smp
```

There is obviously a problem with the pre-removal skript of apt-get. But  have no idea, what exactly "exit status 1" for this particular program means. May be a dependency with other packages caused this error. It seems that the removal of the old kernel package wasn't successful. Retry this removal ```
sudo dpkg -r linux-image-2.6.20-16-powerpc
```

Are there now 2 processors listed under SYSTEM > ADMIN > SYSTEMMONITOR in the ressources-tab?

---

### Post by imacQ on 2007-09-22
YES! after running ybin, restarting and then going through synaptic to install smp packages (oddly it showed I had no kernel), restarting again and i'm now working with 2 cpus. Thanks very much! now it's on to the sound.

---

### Post by frog_pilot on 2007-09-22
Than this is your choice

> **frog_pilot said:**
>  for sound on internal onboard soundcard you have to type```
sudo modprobe snd-powermac
```to load the driver once or add the line```
snd-powermac
```to your /etc/modules to load the driver on system start. Or try my /etc/modules:```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

snd-powermac
apm_emu
sbp2
therm_windtunnel
fuse
```

---

### Post by imacQ on 2007-09-23
Thanks again frog_pilot. Sound is now working. :cool:  Looking for suggestions for getting sound to use my harmond kardon sound sticks via the hk usb subwoofer. With volume at full I do hear sounds, but only from internal speaker. I have "SoundSticks (Alsa mixer)" selected as device under Default Mixer Tracks?  Do you know the answer frog_pilot, or can you point me towards more information? I've checked out the Alsa wiki [http://alsa.opensrc.org/index.php/Main_Page](http://alsa.opensrc.org/index.php/Main_Page) 
but... can't seem to find anything on specific hardware.

---

### Post by frog_pilot on 2007-09-23
Ok, where can you choose HK Soundsticks in Alsa-Mixer-app??

In System > Settings > Audio I have only two choices at device-section:

> PowerMac Snapper (Alsa mixer)
or
> PowerMac Snapper (OSS mixer)

But I also have to turn the volume-Level of my Amp very high to hear any sound. If you have DRC-channel activated, then you have to turn it on highest level to hear anything. You can check this out when you start Alsa-mixer in a terminal with ```
alsamixer
```. When you scroll to the right, you will find the DRC-level. If it is not muted turn it up!!

But for the very quiet sound I didn't find a fix yet... Its about half the Value of OS X. And it seems, that the sound-quality isn't the best either :cry:

This sound issue ist one of the biggest problem with ppc-Linux for me. If you have any more suggestions I would be very happy ):P

---

