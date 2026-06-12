---
title: "Ubuntu Locking Up"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by Tumpster on 2008-02-29
Hey there, I'm running Gutsy and lately since a reinstall Ubuntu locks up and I have to reset from the tower to get it back. There's no real rhyme or reason time wise or when I do something the only thing  I've seen is that  every time that Firefox is running when it does lock up, either in the background or fore front. Any ideas on what I can do to fix this??

I also ram mem test for a few hours to see if it was any of that but no errors were found. My hard drives are still realtively new and all my optical drives are clear of cds.

---

### Post by pytheas22 on 2008-02-29
You can take a look at the system logs to see if they record anything strange happening right before the system locks up.  You can look at logs by going to System>Administration>System Log.

You could also try using a different web browser for a while (like Konqueror or Opera) instead of Firefox in order to confirm that the latter is definitely related to the crashes.

---

### Post by Tumpster on 2008-03-02
I don't see anything serious showin up in the system logs, I just had it lock up a few times too while playing a game so maybe it's not completly firefox! Ideas?

---

### Post by pytheas22 on 2008-03-02
Bad drivers could be causing the problems.  Have you added any new hardware or installed new/different drivers since the problems began?  I used to have a wireless card that would cause sudden lock-ups because its driver was still in development and was flaky; switching to a stable version of the driver fixed the problem.  I assume you're familiar with the hardware in your machine and the status of its Linux support, since you seem to have used Ubuntu for a while, but if I'm wrong, post the output of lspci and maybe we can identify hardware that could be leading to inconsistent behavior.

Otherwise I don't know what else to look for, if the logs don't indicate anything and you've ruled out hardware failure.

By the way, do you run Windows on the same machine and if so does that have problems?  This would indicate for sure whether or not hardware could be to blame.

---

### Post by Tumpster on 2008-03-03
Well I fixed the drivers for Nvidia to the latest, most stable and I also ran other things and it still locked up while playing Enemy Territory. I've got a box fan blowing into the case to see if that changes anything or shows me it's over heating. But i've let the comp sit at the ubuntu login screen for an hour at a time and nothing happens. Its only when I'm doing stuff it locks up.....

I'm pretty familiar with everything in the case/on linux but I thought I'd do this anyway:

craig@craig-desktop:~$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
01:08.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
01:08.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)
01:09.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 15)
05:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
craig@craig-desktop:~$ 

Thanks for the help so far! :)


Well an hour into it so far and no locking up........
I'll update again in the morning.


OK UPDATE!
I was into about the 1hr 45 minute mark when everything locked up on me again WHILE i had the fan blowing on it so I'm back to square one. I'm open to anything!

---

### Post by Tumpster on 2008-03-04
Bump

---

### Post by PmDematagoda on 2008-03-04
When your PC freezes are you able to use the magic SysRq keys to manually restart the system?

This [thread]("http://ubuntuforums.org/showthread.php?t=617349") will explain as to what magic SysRq keys are and how to use them.

---

### Post by Tumpster on 2008-03-04
> **PmDematagoda said:**
> When your PC freezes are you able to use the magic SysRq keys to manually restart the system?

This [thread]("http://ubuntuforums.org/showthread.php?t=617349") will explain as to what magic SysRq keys are and how to use them.


No such luck, these did NOT work. Ideas?

---

### Post by PmDematagoda on 2008-03-04
That may be due to the RAM, just remove the memory modules and clean them and the slots out a bit and see if that solves your problem.

---

### Post by Tumpster on 2008-03-04
But I ram memtest and had no issues and it only seems to be locking when I play enemy territory or using firefox, it never freezes at any other point.......

---

### Post by welder_tim on 2008-03-04
Are you running the visual effects?

I have this same problem with my Dell laptop. The whole computer freezes when running Firefox, But when ever I turn off the visual effects, it never freezes. Don't know why though. Give it a try and see, might help narrow the problem down for someone.

---

### Post by Tumpster on 2008-03-04
I took out all the ram and cleaned the insides of the computer and reseated the ram in different slots than what they were in.

I do run visual effects but it'll freeze when I'm not running firefox now. HMmm....
Ideas?

---

### Post by myname on 2008-03-04
You are not alone, as I too am getting random lockups doing different things.  My system could run for hours, days or even weeks without a reset, then about a month, maybe 2 months ago I would start getting random freezes.  

I too first attributed to Firefox, as that's all I noticed it in.  Then after power cycling, I would not go into firefox and sometimes it's fine, other times I would freeze immediately after logging in, or while sitting at the Ubuntu login screen.

I also see random lockups in WoW, and sometimes while exiting Wolfenstein: Enemy Territory(which is another problem).  

I also opened my case, vacuumed it out, wasn't that dusty.

I think it may have something to do with the Xserver, and I was thinking it was my video drivers, since I have an ATI x1600.

I am going to shoot for a fresh install of Ubuntu this weekend, with clean drivers to see if that fixes it, then slowly add in other functionality like video playback.

If anyone has any ideas, I'm open.

--Kevin

---

### Post by Tumpster on 2008-03-04
So far since resetting all my ram and checking them I've had no troubles, I have yet to say it's fixed yet. No lockups yet but we'll see.....

---

### Post by Tumpster on 2008-03-06
Ok, since clearing out and reseating the ram it is STILL locking up. Any ideas?

---

### Post by Tumpster on 2008-03-06
I turned off pidgin which always runs in the background and it still locked up. I've now turned off all my effects and am looking to see how that works out for me! If it turns out never to lock then what are my alternatives to having effects? It looks like Gutsy comes with Compiz but I've gotten really attached to it. Ideas at all?

---

### Post by Tumpster on 2008-03-06
Well after turning it off, it took a lot longer but it still locked up. Can anyone help me?

---

### Post by Tumpster on 2008-03-07
No one can help me?

---

### Post by pytheas22 on 2008-03-07
I don't know what else you could experiment with in Ubuntu.  You might try however running a different operating system on the machine and see if it locks up.  Ideally you would install Windows on it (just to experiment, not to use!), but if that's not possible, at least try running some live CD's of different distributions, maybe even a BSD or Solaris too.  If possible, you should install one of these systems to the hard disk to rule out the possibility that the disk is to blame.

If it locks up running a different operating system, chances are that it's hardware; if it doesn't lock up, at least you'll know for (almost) sure that it's not hardware.  I know this is an extreme way to go, but if there are no errors reported in the system logs and you're unable to tie the lock-ups to any application or procedure, I don't know what else to do besides work to rule out hardware failure definitively.

---

### Post by Tumpster on 2008-03-07
> **pytheas22 said:**
> I don't know what else you could experiment with in Ubuntu.  You might try however running a different operating system on the machine and see if it locks up.  Ideally you would install Windows on it (just to experiment, not to use!), but if that's not possible, at least try running some live CD's of different distributions, maybe even a BSD or Solaris too.  If possible, you should install one of these systems to the hard disk to rule out the possibility that the disk is to blame.

If it locks up running a different operating system, chances are that it's hardware; if it doesn't lock up, at least you'll know for (almost) sure that it's not hardware.  I know this is an extreme way to go, but if there are no errors reported in the system logs and you're unable to tie the lock-ups to any application or procedure, I don't know what else to do besides work to rule out hardware failure definitively.

Thanks, I'll give that a try, maybe I'll try and older edition of ubuntu like feisty and run it on the live cd and see what happens! Thanks!

---

### Post by gaburko on 2008-03-07
random lockups here too. Ubuntu 7.10 on turion 64, ati x1300, 2 GB RAM (acer laptop). running dual-boot with Vista and there i don't have any problems, so Tumpster - don't bother installing another system - the problem is somewhere else. Nothing suspicious in the log file either.

---

### Post by pytheas22 on 2008-03-07
> random lockups here too. Ubuntu 7.10 on turion 64, ati x1300, 2 GB RAM (acer laptop). running dual-boot with Vista and there i don't have any problems, so Tumpster - don't bother installing another system - the problem is somewhere else. Nothing suspicious in the log file either.

if this is true, then what I suggested is probably not going to help.  Another thing to try might be to use a different kernel--I believe you should be able to pull the Hardy development kernel from the Hardy repositories to install it easily (there are how-to's around for this), or you could custom-compile one.  If there's something weird going on in the kernel causing the lock-ups, this would help isolate the problem.  If I were you, I'd back up the system before playing with the kernel.  I believe that there are also lots of things you can do to try to debug kernel problems, especially if you compile it for that (not sure what the default Ubuntu kernel has in terms of debugging options), but I've never done it myself.

---

### Post by Tumpster on 2008-03-08
Can you link me to a kernel from Hardy??? And possibly a how to?

---

### Post by pytheas22 on 2008-03-08
Here's a how-to on upgrading to Hardy's kernel: [http://ubuntuforums.org/showthread.php?t=646755](http://ubuntuforums.org/showthread.php?t=646755) .

If you still get freezes while running the Hardy kernel, I would next try running a non-Ubuntu kernel altogether.  This could be done most easily by running a live CD of Fedora or Mandriva or whatever.  Then, if you can run the live CD without problems, the next step would be to try custom-compiling a kernel on your Ubuntu system.  There are directions for this at [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu) and [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile).  If you're able to run a custom-compiled kernel on your Ubuntu system, using all of the same applications and devices, I'd say it would be fair to conclude that the problem lies with Ubuntu's build of the kernel.

---

### Post by Tumpster on 2008-03-09
Well that went smoothly and since I've had no troubles (so far) and I have the effects at full to see if that almost "temps" it to lock up. I'll keep you informed if it does lock at some point, until then, thank you! :)

---

### Post by Tumpster on 2008-03-10
Well after that i DID have it lock up a few times so I removed the tv tuner card and wireless card I wasn't using in the box. Looking to see if that helps at all.

---

### Post by Tumpster on 2008-03-12
One lock up so far since doing this.

---

### Post by pytheas22 on 2008-03-12
Try a different distro and/or version of Unix?

---

### Post by caffeinated_eric on 2008-03-12
I can confirm random lockups on Gutsy on my system.  I haven't found a solution yet, unfortunately.

I confirm the same steps:

- The fans are running
- The system temperature is low
- Firefox isn't running when lockups occur
- Lockups occur regardless of whether compiz is enabled
- Lockups do not happen with Feisty

I bumped the syslog levels up to debug with immediate flush on, but no more information has popped up.

Maybe some hardware or bad drivers common between our systems are causing problems?

System: Dell e1505n (A17 BIOS)
NVIDIA GeForce Go 7300 (Driver 100.14.19)
Intel PRO/Wireless 3945 (restricted drivers)

Here's my lsmod output:

Module                  Size  Used by
binfmt_misc            12936  1 
af_packet              24840  2 
ppdev                  10244  0 
acpi_cpufreq           10568  1 
cpufreq_conservative     8072  0 
cpufreq_ondemand        9612  1 
cpufreq_userspace       5280  0 
cpufreq_stats           7232  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       2688  0 
battery                11012  0 
button                  8976  0 
container               5504  0 
sbs                    19592  0 
ac                      6148  2 
dock                   10656  0 
video                  18060  14 
aes_i586               34304  0 
dm_crypt               14984  0 
aes                    28608  0 
i8k                     7320  1 
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
loop                   19076  0 
pl2303                 22148  0 
snd_hda_intel         291488  1 
snd_usb_audio          82944  0 
snd_pcm_oss            43008  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_seq_dummy           4740  0 
snd_pcm                80004  3 snd_hda_intel,snd_usb_audio,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_usb_lib            18304  1 snd_usb_audio
joydev                 11328  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
usb_storage            73024  0 
ide_core              116804  1 usb_storage
nvidia               6221648  36 
snd_seq                53360  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ipw3945               119840  1 
usbserial              34920  1 pl2303
snd_hwdep              10244  2 snd_hda_intel,snd_usb_audio
asix                   18304  0 
usbnet                 19976  1 asix
libusual               18448  1 usb_storage
agpgart                35016  1 nvidia
sdhci                  18828  0 
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
usbhid                 29536  0 
xpad                    9988  0 
hid                    28928  1 usbhid
ieee80211              35656  1 ipw3945
ieee80211_crypt         7040  1 ieee80211
usblp                  15104  0 
pcspkr                  4224  0 
mmc_core               28420  1 sdhci
i2c_core               26112  1 nvidia
snd                    54788  13 snd_hda_intel,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_hwdep,snd_timer,snd_seq_device
psmouse                39952  0 
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
soundcore               8800  1 snd
serio_raw               8068  0 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
evdev                  11136  8 
ext3                  133896  3 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sd_mod                 30336  3 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
ata_piix               17540  2 
ata_generic             8452  0 
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
b44                    28300  0 
mii                     6528  3 asix,usbnet,b44
ehci_hcd               36492  0 
libata                125168  2 ata_piix,ata_generic
scsi_mod              147084  6 sbp2,usb_storage,sg,sd_mod,sr_mod,libata
uhci_hcd               26640  0 
usbcore               138632  14 pl2303,snd_usb_audio,snd_usb_lib,usb_storage,usbserial,asix,usbnet,libusual,usbhid,xpad,usblp,ehci_hcd,uhci_hcd
dm_mirror              24448  0 
dm_snapshot            18980  0 
dm_mod                 58816  10 dm_crypt,dm_mirror,dm_snapshot
thermal                14344  0 
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor

---

### Post by Tumpster on 2008-03-15
> **caffeinated_eric said:**
> I can confirm random lockups on Gutsy on my system.  I haven't found a solution yet, unfortunately.

I confirm the same steps:

- The fans are running
- The system temperature is low
- Firefox isn't running when lockups occur
- Lockups occur regardless of whether compiz is enabled
- Lockups do not happen with Feisty

I bumped the syslog levels up to debug with immediate flush on, but no more information has popped up.

Maybe some hardware or bad drivers common between our systems are causing problems?

System: Dell e1505n (A17 BIOS)
NVIDIA GeForce Go 7300 (Driver 100.14.19)
Intel PRO/Wireless 3945 (restricted drivers)

Here's my lsmod output:

Module                  Size  Used by
binfmt_misc            12936  1 
af_packet              24840  2 
ppdev                  10244  0 
acpi_cpufreq           10568  1 
cpufreq_conservative     8072  0 
cpufreq_ondemand        9612  1 
cpufreq_userspace       5280  0 
cpufreq_stats           7232  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       2688  0 
battery                11012  0 
button                  8976  0 
container               5504  0 
sbs                    19592  0 
ac                      6148  2 
dock                   10656  0 
video                  18060  14 
aes_i586               34304  0 
dm_crypt               14984  0 
aes                    28608  0 
i8k                     7320  1 
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
loop                   19076  0 
pl2303                 22148  0 
snd_hda_intel         291488  1 
snd_usb_audio          82944  0 
snd_pcm_oss            43008  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_seq_dummy           4740  0 
snd_pcm                80004  3 snd_hda_intel,snd_usb_audio,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_usb_lib            18304  1 snd_usb_audio
joydev                 11328  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
usb_storage            73024  0 
ide_core              116804  1 usb_storage
nvidia               6221648  36 
snd_seq                53360  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ipw3945               119840  1 
usbserial              34920  1 pl2303
snd_hwdep              10244  2 snd_hda_intel,snd_usb_audio
asix                   18304  0 
usbnet                 19976  1 asix
libusual               18448  1 usb_storage
agpgart                35016  1 nvidia
sdhci                  18828  0 
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
usbhid                 29536  0 
xpad                    9988  0 
hid                    28928  1 usbhid
ieee80211              35656  1 ipw3945
ieee80211_crypt         7040  1 ieee80211
usblp                  15104  0 
pcspkr                  4224  0 
mmc_core               28420  1 sdhci
i2c_core               26112  1 nvidia
snd                    54788  13 snd_hda_intel,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_hwdep,snd_timer,snd_seq_device
psmouse                39952  0 
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
soundcore               8800  1 snd
serio_raw               8068  0 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
evdev                  11136  8 
ext3                  133896  3 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sd_mod                 30336  3 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
ata_piix               17540  2 
ata_generic             8452  0 
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
b44                    28300  0 
mii                     6528  3 asix,usbnet,b44
ehci_hcd               36492  0 
libata                125168  2 ata_piix,ata_generic
scsi_mod              147084  6 sbp2,usb_storage,sg,sd_mod,sr_mod,libata
uhci_hcd               26640  0 
usbcore               138632  14 pl2303,snd_usb_audio,snd_usb_lib,usb_storage,usbserial,asix,usbnet,libusual,usbhid,xpad,usblp,ehci_hcd,uhci_hcd
dm_mirror              24448  0 
dm_snapshot            18980  0 
dm_mod                 58816  10 dm_crypt,dm_mirror,dm_snapshot
thermal                14344  0 
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor



Let me give you a suggestion that worked for me, but it may not for all, I upgraded to Heron. I would await a few more days till the beta comes out but it's been nothing but smooth sailing here since I wiped away gutsy and went with heron.

---

### Post by caffeinated_eric on 2008-03-15
I just upgraded to Alpha 6 myself last night, and I haven't had a problem so far.

---

### Post by gerscht on 2008-03-15
I had similar problems and could narrow it down to sata_nv and ADMA/NCQ. This seems to be a common problem with 2.6.22 and causes lockups on mainboards with nforce chipset.
It has been fixed in 2.6.24, so a kernel upgrade (see [http://ubuntuforums.org/showthread.php?t=646755](http://ubuntuforums.org/showthread.php?t=646755)) did the trick.

---

### Post by Papa-san on 2008-03-15
Are there any lines starting with (EE) in /var/log/Xorg.0.log ?

You can check really quick with this command:
```
cat /var/log/Xorg.0.log | grep EE
```

My laptop had me ready to run it over with my tractor because of this lock-up thing... No rhyme nor reason to it at all...
 Check the above, and maybe I can help! Mine hasn't frozen in months.

---

### Post by Tumpster on 2008-03-15
I've since wiped my machine so with running the Alpha of Heron I've had no troubles at all.

---

### Post by Papa-san on 2008-03-15
Awesome!

Well, keep us posted!

---

### Post by Tumpster on 2008-03-16
Well I'm not having "problems" per say but just a general nusiance. 
Whenever I play any videos my colors on my videos are altered:
Examples
[http://img265.imageshack.us/img265/3189/screenshotmplayervideozj5.png](http://img265.imageshack.us/img265/3189/screenshotmplayervideozj5.png)
[http://img377.imageshack.us/img377/2899/screenshotinsidetheactork5.png](http://img377.imageshack.us/img377/2899/screenshotinsidetheactork5.png)

What is causing this or how can this be fixed? Everything else works just fine!

---

