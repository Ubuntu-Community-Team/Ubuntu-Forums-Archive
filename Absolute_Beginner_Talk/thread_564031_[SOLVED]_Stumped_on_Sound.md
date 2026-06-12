---
title: "[SOLVED] Stumped on Sound"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by squirage on 2007-09-30
Sorry if I am not following proper protocol but I've tried a lot of different things and nothing has worked.

It started out with losing sound every other time I booted up, usually a reboot fixed it. Then no sound became the rule instead of the exception. Then no sound. I tried following the comprehensive sound guide, did fix it. In the interim I received some updates and sound was back. I think it was a kernel and or some various libraries that came out on Sept 29th.

I then tried to install a video editing program and after reboot, no sound.

So I followed the instructions in [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) to manually compile alsa manually. Now it shows I have no sound card. On the plus side I was finally able to compile and install something.

aplay -l used to show I had an ICH7 type sound chip, I think it was a 82801G and categorized as an hda-intel.

Sound preferences used to show an hda generic but now only show alsa, oss etc.

I've also tried setting the device but that didn't work either. The long and short of it is that I've tried so many things I've lost my way and made it worse, in that it doesn't even see a sound device.

Any thoughts on how I can get out of this or go back to square one?

I'm running:

Toshiba Satellite A135-S4477
Dual Boot: Vista Home Premium (Longhorn)/ Ubuntu 6.10 (Edgy-Eft)
Intel® Core™ Duo 2 T5200 1.60GHz 1.60GHz
2048MB SDRAM PC4200 DDR2
180GB SATA HDD (80GB Primary + 100GB Secondary)
Mobile Intel® 945GM Express Chipset
Intel® Graphics Media Accelerator 950 with 8MB-256MB dynamically allocated shared graphics memory, v7.14.10.1132 (updated 8-6-07)
Matshita DVD-RAM UJ-850S ATA 

Thanks in advance for any help you can give. I long for the days when I could actually get stuff done and not have to spend time working around buggy programs. I'm hoping with some sweat I can get back to a place where I feel in control of the computer again.
:confused:

---

### Post by squirage on 2007-10-02
Okay,

I'm not really sure why I get no response for this post? Is there a way to re-install the os to repair the problem?

I've been working on this the last few days and saving my stuff into a Open Office Document. It is now 31 pages long. I'll try and give you all the edited version.

Refound help topic: [http://ubuntuforums.org/showthread.php?t=205449&highlight=.asoundrc](http://ubuntuforums.org/showthread.php?t=205449&highlight=.asoundrc)

Comprehensive Sound Problem Solutions Guide v0.5e

By the way [http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide) is dead, or at least not re-directing.

This is what I am working on.

After typing 
```
 lspci -v

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff01
        Flags: fast devsel, IRQ 50
        Memory at dc440000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
```

I then tried some of the things from [http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel)
that I had tried before. This page is generic enough to be pretty confusing.

Apparently I cannot use the terminal editor “vi” command like it says to, so I used gksudo gedit ~/.asoundrc to add the lines:
```

pcm.hda-intel {
          type hw
          card 0
       }
       
       ctl.hda-intel {
          type hw
          card 0
       }
```
to .asoundrc

When I looked back at my terminal after editing it said this:
```

(gedit:17292): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
ALSA lib confmisc.c:769:(parse_card) cannot find card ''
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default
```

The other thing I noticed is that all the files and folders in /proc/asound are completely empty, i.e. there but 0 bytes.

Next I typed: 
```
 sudo modprobe snd-ICH7
FATAL: Module snd_ICH7 not found. 
```

and the second line is what I received back. So how do I find a proper name for my sound chip?

It also talks about various edits or creating files in /etc/modutils or etc/modules.conf

This is my file simply labeled modules in /etc:
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
sbp2
```

I have no idea what it means or what it is for.

It is also interesting that their instructions for editing the modules.conf at [http://www.alsa-project.org/alsa-doc/doc-php/file-edit.php](http://www.alsa-project.org/alsa-doc/doc-php/file-edit.php) is dead.

I even saw where someone had a solution to use Synaptic to install asoundconf-gtk, but for me a search of Synaptic showed nothing for asoundconf-gtk.

04:11:12 PM10/01/07

Okay, so I've been out for awhile doing something besides being frustrated at the computer. As I mostly expected I still have no recognizable sound device. So on to try another step, re-installing from a “fresh” Kernel as listed in the afore mentioned post [http://ubuntuforums.org/showthread.php?t=205449&highlight=.asoundrc](http://ubuntuforums.org/showthread.php?t=205449&highlight=.asoundrc)

```
 sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
```

I'll spare you the long output, but it seemed to do its thing.

And boy are they not kidding, you can see that it removed basically the entire gnome desktop, Nautilus and all. I wonder if there is a better way to do that? 

The next step is to re-install what was uninstalled:
```

sudo apt-get install linux-sound-base alsa-base alsa-utils
```

And the first thing I notice here is that when I did my manual compile the alsa version was 1.0.14, Feisty perhaps?

Then I need to follow the next step, fixing 'gdm' and 'ubuntu-desktop' as the guide noted has happened to some. We do this:
```

sudo apt-get install gdm ubuntu-desktop
```

I was concerned by this portion somewhat:
```

Setting up gdm (2.16.1-0ubuntu4.1) ...
grep: /etc/X11/default-display-manager: No such file or directory
Adding group `gdm' (113)...
Done.
Warning: The home dir you specified already exists.
Adding system user `gdm' with uid 108...
Adding new user `gdm' (108) with group `gdm'.
The home directory `/var/lib/gdm' already exists.  Not copying from `/etc/skel'
adduser: Warning: that home directory does not belong to the user you are currently creating
 * Reloading GNOME Display Manager configuration...                              * Changes will take effect when all current X sessions have ended.
                                                                         [ ok ]
```

And these had also come up twice:
```
The following packages were automatically installed and are no longer required:
(followed by a lot of stuff)
Use 'apt-get autoremove' to remove them.
```

I'm a little worried by the WARNING I received, but I did have to re-install. So I'm going to cross my fingers and reboot.

10/02/07 06:49:09 AM

Okay, I rebooted yesterday afternoon and everything seems to be the same. So I guess I did not have to worry about the warning. Unfortunately I still have no sound. So I've gone back through the forums and found the link to the help file I used that lost me my sound card:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Like I said earlier the only positive to that was that it was the first time I was able to actually manually compile anything.

At this point I am thinking that the only way out of my predicament is a “repair” installation of Ubuntu.

I will first try to look up another link: [https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)

This one and the previous one were both submitted by Pumalite, who is very helpful by the way, in the Sound has disappeared thread: [http://ubuntuforums.org/showthread.php?t=557149&highlight=sound](http://ubuntuforums.org/showthread.php?t=557149&highlight=sound)

On the second page Pumalite recommends:

```
sudo lshw
```

It returned more than I ever wanted to know, I think that this is the relevant portion:
```
*-multimedia UNCLAIMED
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: cap_list
             resources: iomemory:dc440000-dc443fff irq:50
```

Next I went and took a look at /etc/group and I assume that the line( audio:x:29:sean ) means that I have audio permission. So that ain't it.

For the hell of it I'm going to try the ALSA driver compilation again using alsa-source as described in:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

 ```
sudo apt-get install build-essential linux-headers-$(uname -r) module-assistant alsa-source
```

Does some stuff, mentions the 'apt-get autoremove' thing again.

Okay, next step:

```
sudo dpkg-reconfigure alsa-source 
```

This did something for me. It looks like I need to be running intel8x0. The only thing that was not clear from the description was that, after saying yes twice, you need to tab to the OK button to get to the selection screen. I spent a minute wondering why I couldn't select with my spacebar.

Next step:

```
sudo module-assistant a-i alsa-source
```

I stepped away for a second, lost in some kind of reverie, so I'm assuming it got to 100%. Not sure about the highlighted line? It says to go to General Help Step 4. Of course they are not numbered but it makes sense that next you check the sound module, so:
```

sudo modprobe snd-intel8x0
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.17-12-generic/updates/alsa/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_intel8x0 (/lib/modules/2.6.17-12-generic/updates/alsa/pci/snd-intel8x0.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

>:( That SUCKS!

dmesg gives me: a lot more stuff the relevant portion of which is
```

[17232342.124000] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[17232342.124000] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[17232342.124000] pcmcia: see http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html for details.
[17235292.752000] snd_ac97_codec: Unknown symbol snd_hidden_kzalloc
[17235292.752000] snd_ac97_codec: disagrees about version of symbol snd_info_register
[17235292.752000] snd_ac97_codec: Unknown symbol snd_info_register
[17235292.752000] snd_ac97_codec: disagrees about version of symbol snd_ctl_add
[17235292.752000] snd_ac97_codec: Unknown symbol snd_ctl_add
[17235292.752000] snd_ac97_codec: disagrees about version of symbol snd_info_free_entry
[17235292.752000] snd_ac97_codec: Unknown symbol snd_info_free_entry
[17235292.752000] snd_ac97_codec: Unknown symbol snd_hidden_kcalloc
[17235292.756000] snd_ac97_codec: Unknown symbol snd_hidden_kfree
[17235292.756000] snd_ac97_codec: disagrees about version of symbol snd_ctl_find_id
[17235292.756000] snd_ac97_codec: Unknown symbol snd_ctl_find_id
[17235292.756000] snd_ac97_codec: disagrees about version of symbol snd_ctl_new1
[17235292.756000] snd_ac97_codec: Unknown symbol snd_ctl_new1
[17235292.756000] snd_ac97_codec: disagrees about version of symbol snd_ctl_remove_id
[17235292.756000] snd_ac97_codec: Unknown symbol snd_ctl_remove_id
[17235292.756000] snd_ac97_codec: disagrees about version of symbol snd_component_add
[17235292.756000] snd_ac97_codec: Unknown symbol snd_component_add
[17235292.756000] snd_ac97_codec: disagrees about version of symbol snd_pcm_hw_rule_add
[17235292.756000] snd_ac97_codec: Unknown symbol snd_pcm_hw_rule_add
[17235292.756000] snd_ac97_codec: disagrees about version of symbol snd_iprintf
[17235292.756000] snd_ac97_codec: Unknown symbol snd_iprintf
[17235292.756000] snd_ac97_codec: disagrees about version of symbol snd_device_new
[17235292.756000] snd_ac97_codec: Unknown symbol snd_device_new
[17235292.756000] snd_ac97_codec: disagrees about version of symbol snd_info_create_card_entry
[17235292.756000] snd_ac97_codec: Unknown symbol snd_info_create_card_entry
[17235292.756000] snd_ac97_codec: Unknown symbol snd_info_unregister
[17235292.756000] snd_ac97_codec: disagrees about version of symbol snd_info_get_line
[17235292.756000] snd_ac97_codec: Unknown symbol snd_info_get_line
[17235292.760000] snd_intel8x0: Unknown symbol snd_verbose_printd
[17235292.760000] snd_intel8x0: Unknown symbol snd_hidden_kzalloc
[17235292.760000] snd_intel8x0: Unknown symbol snd_ac97_pcm_close
[17235292.760000] snd_intel8x0: Unknown symbol snd_ac97_resume
[17235292.760000] snd_intel8x0: disagrees about version of symbol snd_pcm_new
[17235292.760000] snd_intel8x0: Unknown symbol snd_pcm_new
[17235292.760000] snd_intel8x0: disagrees about version of symbol snd_pcm_limit_hw_rates
[17235292.760000] snd_intel8x0: Unknown symbol snd_pcm_limit_hw_rates
[17235292.760000] snd_intel8x0: disagrees about version of symbol snd_card_register
[17235292.760000] snd_intel8x0: Unknown symbol snd_card_register
[17235292.760000] snd_intel8x0: disagrees about version of symbol snd_card_free
[17235292.760000] snd_intel8x0: Unknown symbol snd_card_free
[17235292.760000] snd_intel8x0: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[17235292.760000] snd_intel8x0: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[17235292.760000] snd_intel8x0: disagrees about version of symbol snd_card_proc_new
[17235292.760000] snd_intel8x0: Unknown symbol snd_card_proc_new
[17235292.760000] snd_intel8x0: Unknown symbol snd_ac97_pcm_open
[17235292.760000] snd_intel8x0: Unknown symbol snd_ac97_set_rate
[17235292.760000] snd_intel8x0: Unknown symbol snd_ac97_update_bits
[17235292.760000] snd_intel8x0: Unknown symbol snd_hidden_kfree
[17235292.760000] snd_intel8x0: Unknown symbol snd_ac97_mixer
[17235292.760000] snd_intel8x0: Unknown symbol snd_ac97_bus
[17235292.760000] snd_intel8x0: Unknown symbol snd_ac97_pcm_double_rate_rules
[17235292.760000] snd_intel8x0: disagrees about version of symbol snd_card_new
[17235292.760000] snd_intel8x0: Unknown symbol snd_card_new
[17235292.764000] snd_intel8x0: Unknown symbol snd_ac97_suspend
[17235292.764000] snd_intel8x0: disagrees about version of symbol snd_iprintf
[17235292.764000] snd_intel8x0: Unknown symbol snd_iprintf
[17235292.764000] snd_intel8x0: disagrees about version of symbol snd_pcm_lib_malloc_pages
[17235292.764000] snd_intel8x0: Unknown symbol snd_pcm_lib_malloc_pages
[17235292.764000] snd_intel8x0: disagrees about version of symbol snd_pcm_lib_ioctl
[17235292.764000] snd_intel8x0: Unknown symbol snd_pcm_lib_ioctl
[17235292.764000] snd_intel8x0: disagrees about version of symbol snd_pcm_lib_free_pages
[17235292.764000] snd_intel8x0: Unknown symbol snd_pcm_lib_free_pages
[17235292.764000] snd_intel8x0: disagrees about version of symbol snd_pcm_set_ops
[17235292.764000] snd_intel8x0: Unknown symbol snd_pcm_set_ops
[17235292.764000] snd_intel8x0: disagrees about version of symbol snd_pcm_hw_constraint_list
[17235292.764000] snd_intel8x0: Unknown symbol snd_pcm_hw_constraint_list
[17235292.764000] snd_intel8x0: disagrees about version of symbol snd_device_new
[17235292.764000] snd_intel8x0: Unknown symbol snd_device_new
[17235292.764000] snd_intel8x0: Unknown symbol snd_ac97_get_short_name
[17235292.764000] snd_intel8x0: disagrees about version of symbol snd_pcm_suspend_all
[17235292.764000] snd_intel8x0: Unknown symbol snd_pcm_suspend_all
[17235292.764000] snd_intel8x0: Unknown symbol snd_ac97_pcm_assign
[17235292.764000] snd_intel8x0: disagrees about version of symbol snd_pcm_hw_constraint_integer
[17235292.764000] snd_intel8x0: Unknown symbol snd_pcm_hw_constraint_integer
[17235292.764000] snd_intel8x0: disagrees about version of symbol snd_pcm_hw_constraint_msbits
[17235292.764000] snd_intel8x0: Unknown symbol snd_pcm_hw_constraint_msbits
[17235292.764000] snd_intel8x0: disagrees about version of symbol snd_pcm_period_elapsed
[17235292.764000] snd_intel8x0: Unknown symbol snd_pcm_period_elapsed
[17235292.764000] snd_intel8x0: Unknown symbol snd_ac97_tune_hardware
```

Nine pages of crap. I don't understand what the “Unknown symbol” is all about.

I'll try the configuring step.

Unfortunately ```
cat /proc/asound/modules 
```gives me absolutely nothing just another line with a blinking cursor.

So the next command```
 sudo nano /etc/modprobe.d/alsa-base 
```shows:

```
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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
```

So did I need to do the intel8x0m instead of the intel8x0? The reason I picked the non-m version was because it said something about ICH, whereas the m variant did not. I have also heard of AC97 before, but not M(whatever) did I just do the wrong one? 

I really am going in circles here, it's not just my imagination. It is now 10/02/07 08:29:33 AM. I am going  to reboot and see what happens.

And that is where I ended this topic for the day and went about trying to figure out my partition problem.

I hope that this demonstrates that I really am trying everything I can think of, I'm not just whining and asking you all to solve my problem for me.

If you get this far, thanks for reading.

Sean.

---

### Post by squirage on 2007-10-05
I fixed this problem.

I posted how here [http://ubuntuforums.org/showthread.php?p=3482677](http://ubuntuforums.org/showthread.php?p=3482677)

You're not crazy if you post to yourself, only if you start answering your own posts.

---

### Post by breaking on 2008-01-13
Thanks for taking the time to make a detailed post about your experience following the "comprehensive sound problem solutiuon guide", and for the follow up.

Posts like this are much more helpful that the ones that go unanswered and/or are left unresolved.

---

