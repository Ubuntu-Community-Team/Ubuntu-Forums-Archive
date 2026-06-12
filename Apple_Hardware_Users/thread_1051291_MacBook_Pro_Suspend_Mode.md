---
title: "MacBook Pro Suspend Mode"
date: 2009-01-26
forum: Apple Hardware Users
---

### Post by ubuntüser on 2009-01-26
I installed ubuntu in my windows partition using wine on my MacBook Pro (4,1).
This is my partition scheme:
206GB Mac OS
25GB Windows
Ubuntu takes up 6GB on my Windows partition.

Ubuntu runs fine, but it cannot resume from sleep mode. My computer goes to a black screen, and 5 seconds later, it restarts! Any help will be very... um... helpful.

Thanks in advance!
ubuntüser

---

### Post by ubuntüser on 2009-02-01
Anyone?

---

### Post by hyperboloid on 2009-02-01
Why not install ubuntu in its own partition? Makes more sense to me...

Anyway, I had a problem with flaky suspend issues on my MBP 4,1 that proved to be caused by the "sky2" module. When I started unloading that module on suspend, my problems went away entirely. You could try that: it can't hurt.

Here are detailed instructions:

Edit the file /etc/pm/config.d/00sleep_module (using sudo or as root) and add the line:

SUSPEND_MODULES="sky2"

to the end of the file. Save the file and then try to suspend. If it doesn't work, you can always remove that line again.

Please report the outcome here in case other folks have similar issues.

---

### Post by Toe Knee on 2009-04-17
Worked for me. Cheers!

---

### Post by makajawanjack on 2009-06-08
The sky2 line worked great. Thanks!

---

### Post by igor@polevoy.org on 2009-08-26
Unfortunately this did not work for me. 

MacBook Pro 3.1, Ubuntu 9.04. 
The machine suspends all right, but when I try to wake it up - Space, open/close lid, mouse, external keyboard, own keyboard, etc., the screen is blank. Yet, it is running, because if I press and hold a power button, it shuts down completely.

Any help is appreciated

cheers

---

### Post by Toe Knee on 2009-08-26
Can you pase the contents of your /etc/pm/config.d/00sleep_module in here please?

---

### Post by igor@polevoy.org on 2009-08-26
Entire contents looks like this:

[FONT="Courier New"]================================================================
# The sleep/wake system to use.  Valid values are:
#   kernel    The built-in kernel suspend/resume support.
#             Use this if nothing else is supported on your system.
#   uswsusp   If your system has support for the userspace
#             suspend programs (s2ram/s2disk/s2both), then use this.
#   tuxonice  If your system has support for tuxonice, use this.
#
# The system defaults to "kernel" if this is commented out.
# SLEEP_MODULE="kernel"
 SUSPEND_MODULES="sky2"
================================================================[/FONT]

thanks,
igor

---

### Post by Toe Knee on 2009-08-26
Hmmm, same as mine...  Not really sure where to go from there.

---

### Post by igor@polevoy.org on 2009-08-26
thanks for looking, Tony.

Anyone else can help?

thanks,
igor

---

### Post by amd-64 on 2009-08-27
May be you can post /var/log/pm-suspend.log as well.

---

### Post by igor@polevoy.org on 2009-08-28
This is the contents of my [FONT="Courier New"]pm-suspend.log[/FONT] file 
I also attached content of the file [FONT="Courier New"]pm-powersave.log[/FONT]  below if this helps.

**cat /var/log/pm-suspend.log**

[FONT="Courier New"]Initial commandline parameters: --quirk-vbe-post
Thu Aug 27 08:51:08 CDT 2009: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000record suspend suspend: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk suspend suspend: success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: Linux igor-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc            16776  1 
ppdev                  15620  0 
btusb                  19608  2 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
hid_apple              14336  0 
coretemp               13952  0 
usbhid                 42336  0 
bcm5974                15872  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         435636  1 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
arc4                    9856  2 
snd_seq_dummy          10756  0 
ecb                    10752  2 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
ath9k                 282804  0 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
applesmc               29360  0 
lbm_cw_mac80211       227364  1 ath9k
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
led_class              12036  2 ath9k,applesmc
uvcvideo               63240  0 
intel_agp              34108  0 
joydev                 18368  0 
input_polldev          11912  1 applesmc
mbp_nvidia_bl           9988  0 
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
compat_ioctl32          9344  1 uvcvideo
agpgart                42696  1 intel_agp
lbm_cw_cfg80211        73760  2 ath9k,lbm_cw_mac80211
pcspkr                 10496  0 
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
appletouch             18436  0 
appleir                12416  0 
snd                    62628  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
video                  25360  0 
output                 11008  1 video
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
sky2                   54916  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
             total       used       free     shared    buffers     cached
Mem:       3079900     363756    2716144          0      14696     174564
-/+ buffers/cache:     174496    2905404
Swap:      6386564          0    6386564
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
/usr/lib/pm-utils/sleep.d/45iwlist suspend suspend: /sbin/iwlist
not applicable.
/usr/lib/pm-utils/sleep.d/48hid2hci suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
success.
/usr/lib/pm-utils/sleep.d/90chvt suspend suspend: success.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode suspend suspend: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video suspend suspend: not applicable.
/etc/pm/sleep.d/99laptop-mode suspend suspend: success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend: kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend: success.
Thu Aug 27 08:51:10 CDT 2009: performing suspend
Thu Aug 27 08:51:26 CDT 2009: Awake.
Thu Aug 27 08:51:26 CDT 2009: Running hooks for resume
/etc/pm/sleep.d/action_wpa resume suspend: success.
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
/etc/pm/sleep.d/99laptop-mode resume suspend: Laptop mode disabled, active
success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video resume suspend: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode resume suspend: success.
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: /usr/lib/pm-utils/sleep.d/95hdparm-apm: 50: get_power_status: not found

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
success.
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
/usr/lib/pm-utils/sleep.d/90chvt resume suspend: success.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: not applicable.
/usr/lib/pm-utils/sleep.d/48hid2hci resume suspend: Switching device 05ac:1000 to HCI mode failed (Invalid or incomplete multibyte or wide character)
success.
/usr/lib/pm-utils/sleep.d/45iwlist resume suspend: /sbin/iwlist
wlan0     Interface doesn't support scanning : Device or resource busy

success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk resume suspend: success.
/usr/lib/pm-utils/sleep.d/000record resume suspend: success.
Thu Aug 27 08:51:27 CDT 2009: Finished.[/FONT]

**~$ cat /var/log/pm-powersave.log **
[FONT="Courier New"]
/usr/lib/pm-utils/power.d/anacron false: success.
/usr/lib/pm-utils/power.d/laptop-mode false: success.
/usr/lib/pm-utils/power.d/sched-powersave false: **sched policy powersave OFF
success.[/FONT]

---

### Post by amd-64 on 2009-08-28
Hmm. According to [https://help.ubuntu.com/community/MacBook3-1/Jaunty]("https://help.ubuntu.com/community/MacBook3-1/Jaunty") it should work out of the box.  I did not get any clues from your pm-suspend and pm-powersave, but may be others will. 

Do you need powersaved, if not remove it. Make sure hal is up to date. It will affect the quirks loaded by pm-utils. In your file, there is only --quirk-vbe-post. On my MBP5,3 the following quirks are applied

--quirk-dpms-suspend
--quirk-dpms-on
--quirk-vbestate-restore
--quirk-vbemode-restore
--quirk-vga-mode3
--quirk-vbe-post

Try reinstalling pm-utils and updating your graphics driver. Sorry, this is not much help.

---

### Post by igor@polevoy.org on 2009-08-31
I re-installed the pm-utils and hal, but have the same effect. Powersave is not installed. 

The behavior can shed some light into it, I hope. When I set it to suspend, it seems to be doing the right thing. The screen dims 'till black. When I close the lead, the LED on the latch starts pulsing (just like on Mac OS).
When I open the lid, the LED stops pulsing, but the screen is still black. 
Apparently the video driver is not waking up.

BTW, how do you set the quirks:
--quirk-dpms-suspend
--quirk-dpms-on
--quirk-vbestate-restore
--quirk-vbemode-restore
--quirk-vga-mode3
--quirk-vbe-post

??

Thanks,
Igor

---

### Post by Toe Knee on 2009-09-01
Which video driver are you using?  I am using - the closed source nvidia one (180).

---

### Post by igor@polevoy.org on 2009-09-01
[FONT="Courier New"]$lsmod | grep vid
uvcvideo               63240  0 
mbp_nvidia_bl           9988  0 
compat_ioctl32          9344  1 uvcvideo
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev
video                  25360  0 
output                 11008  1 video[/FONT]

I was not using any proprietary drivers. However, installing NVidia 180 now, will update on results once done.

Thanks for a tip.

igor

---

### Post by igor@polevoy.org on 2009-09-01
Success!!! MB can suspend and resume now. The problem was that I was not using the NVidia 180 driver. As soon as I installed it, the problem went away.

Thanks all for help!

igor

---

### Post by jtayl22 on 2010-05-21
Suspend was fine on my macbook with Ubuntu 9.10 (Karmic Koala) but when I upgraded to 10.04 (Lucid Lynx), I had the symptom described in this string: the screen would turn black when I attempted to suspend, but the laptop kept running at full power and the screen would turn on again when I moved the mouse.

In "System -> Administration -> Software Sources" on the "Other Software" tab, three of the [http://ppa.launchpad.net/mactel-support/](http://ppa.launchpad.net/mactel-support/)... respositories were clearly commented with "disabled on upgrade to lucid"

When I checked the boxes to re-enable the mactel repositories and ran "System -> Administration -> Update Manager" everything was again fine after reboot.

---

### Post by xavi on 2010-05-22
Oh well, suspend and hibernate didn't work for me at all in karmic lastly (I guess, after some upgrade I made to nvidia package), and after I upgraded to Lucid, I can ensure that it was not working either with latest drivers (190.x, or 195.x, that the version number seems to be different if you look at the configuration screen or at the package number through synaptic). It came back to work properly (suspend/resume, even quickly + hibernate, although slowly) once I managed to get back some 180.x drivers installed (from the nvidia website, since I couldn't find them any more already compiled for lucid)

My 2 cents.

P.S: already documented in the wiki some days ago:
[https://help.ubuntu.com/community/MacBookPro5-5/Lucid#Video](https://help.ubuntu.com/community/MacBookPro5-5/Lucid#Video)

---

### Post by Seamyst on 2010-10-03
I'm having the same problem, on my MacBook1,1 with Lucid. It doesn't happen every time I leave the computer alone for an extended period of time, but it's now automatically shutting off (or at least not coming out of suspend/hibernate) more than half the time.

Here's the output of my pm-suspend.log.1
> Initial commandline parameters: 
Thu Sep 16 21:13:03 EDT 2010: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux jessica-laptop 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:24:04 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
hfsplus                70800  0 
nls_iso8859_1           3249  0 
nls_cp437               4919  0 
vfat                    8933  0 
fat                    47767  1 vfat
nls_utf8                1069  0 
udf                    78785  0 
crc_itu_t               1371  1 udf
usb_storage            39425  0 
binfmt_misc             6587  1 
rfcomm                 33421  0 
ppdev                   5259  0 
sco                     7885  0 
bridge                 45582  0 
stp                     1655  1 bridge
bnep                    9436  0 
l2cap                  30624  4 rfcomm,bnep
btusb                  10925  0 
bluetooth              49892  5 rfcomm,sco,bnep,l2cap,btusb
snd_hda_codec_idt      51978  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
arc4                    1153  2 
snd_hda_intel          21941  4 
snd_hda_codec          74201  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ath5k                 121792  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  285586  3 
drm_kms_helper         29297  1 i915
mac80211              205146  1 ath5k
ath                     7611  1 ath5k
joydev                  8708  0 
snd                    54148  19 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   162409  4 i915,drm_kms_helper
cfg80211              126517  3 ath5k,mac80211,ath
applesmc               20069  0 
input_polldev           2482  1 applesmc
intel_agp              24119  2 i915
led_class               2864  2 ath5k,applesmc
agpgart                31724  2 drm,intel_agp
i2c_algo_bit            5028  1 i915
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
tpm_infineon            7745  0 
tpm                    13484  1 tpm_infineon
tpm_bios                5266  1 tpm
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
hid_apple               4346  0 
usbhid                 36110  0 
hid                    67032  2 hid_apple,usbhid
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
sky2                   40775  0 
             total       used       free     shared    buffers     cached
Mem:        994928     786592     208336          0      13396     317516
-/+ buffers/cache:     455680     539248
Swap:       499992     143176     356816
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend:success.
Thu Sep 16 21:13:08 EDT 2010: performing suspend
Thu Sep 16 21:13:41 EDT 2010: Awake.
Thu Sep 16 21:13:41 EDT 2010: Running hooks for resume
/etc/pm/sleep.d/action_wpa resume suspend:success.
/usr/lib/pm-utils/sleep.d/99video resume suspend:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:success.
/usr/lib/pm-utils/sleep.d/95led resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron resume suspend:success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:success.
/usr/lib/pm-utils/sleep.d/90clock resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/75modules resume suspend:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:success.
/etc/pm/sleep.d/10_grub-common resume suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend:success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend:success.
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:success.
Thu Sep 16 21:13:42 EDT 2010: Finished.

It looks like I don't have an nvidia driver, but an... i915? Googling that doesn't bring up anything that looks useful to this situation.

---

