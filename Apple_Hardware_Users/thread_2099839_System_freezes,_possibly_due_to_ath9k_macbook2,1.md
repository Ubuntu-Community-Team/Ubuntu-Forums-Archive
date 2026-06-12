---
title: "System freezes, possibly due to ath9k: macbook2,1"
date: 2012-12-30
forum: Apple Hardware Users
---

### Post by clumsyNInja on 2012-12-30
EDIT: It appears I found a way to stop the crashes, I found from this thread: [https://bugzilla.redhat.com/show_bug.cgi?id=755370](https://bugzilla.redhat.com/show_bug.cgi?id=755370) that setting power management off should fix the problem. For anyone having issues similar to this give that a shot, and here are some methods to permanently disable power management [http://askubuntu.com/questions/85214/how-can-i-prevent-iwconfig-power-management-from-being-turned-on](http://askubuntu.com/questions/85214/how-can-i-prevent-iwconfig-power-management-from-being-turned-on)
Hope this helps.
So I recently installed Lubuntu on my macbook2,1. It runs flawlessly except it crashes multiple times a day. When it crashes it hops to a tty looking console and dumps a bunch of info, I am unable to interact with it at this point and have to do a hard reboot. Looking over the text it appears to happen while the network is doing some kind of switching, I am not entirely sure because nothing ends up being logged so I can't look at it again or post it.
It is a 2,1 with 1.83 GHz core 2 duo, it has 2 GB of ram and lspci listed below:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:07.0 Performance counters: Intel Corporation Device 27a3 (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
02:00.0 Network controller: Atheros Communications Inc. AR5418 Wireless Network Adapter [AR5008E 802.11(a)bgn] (PCI-Express) (rev 01)
03:03.0 FireWire (IEEE 1394): LSI Corporation FW322/323 [TrueFire] 1394a Controller (rev 61)

```Uname -a
```
Linux lubook 3.5.0-21-generic #32-Ubuntu SMP Tue Dec 11 18:52:46 UTC 2012 i686 i686 i686 GNU/Linux
```I have only used it on one network which is WEP secured and only b/g enabled. (I learned from searching that n may be a problem but it is not enabled)
I found this thread [http://ubuntuforums.org/showthread.php?t=1941698](http://ubuntuforums.org/showthread.php?t=1941698) which led me to this bug report [https://bugzilla.kernel.org/show_bug.cgi?id=42903](https://bugzilla.kernel.org/show_bug.cgi?id=42903) but the last post says the fix is merged in 3.5-r6 and I am running 3.5.0.21, so I would assume that is fixed but I am new to Ubuntu so I may be wrong. 
Just to be thorough here is the output of lsmod
```
Module                  Size  Used by
btusb                  17986  0 
snd_hda_codec_idt      59761  1 
rfcomm                 37276  12 
bnep                   17707  2 
parport_pc             31968  0 
bluetooth             183228  22 btusb,rfcomm,bnep
ppdev                  12817  0 
coretemp               13168  0 
kvm_intel             126745  0 
kvm                   357806  1 kvm_intel
joydev                 17161  0 
applesmc               18778  0 
input_polldev          13648  1 applesmc
microcode              18209  0 
appletouch             17366  0 
nls_utf8               12493  1 
arc4                   12473  2 
hfsplus                83154  1 
snd_hda_intel          32515  1 
snd_hda_codec         111547  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80163  2 snd_hda_intel,snd_hda_codec
ath9k                 116557  0 
snd_seq_midi           13132  0 
snd_rawmidi            25382  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
snd_timer              24411  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    61991  11 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              461161  1 ath9k
apple_bl               13425  0 
ath9k_common           13783  1 ath9k
ath9k_hw              376155  2 ath9k,ath9k_common
ath                    19187  3 ath9k,ath9k_common,ath9k_hw
cfg80211              175375  3 ath9k,mac80211,ath
i915                  457181  2 
lpc_ich                16925  0 
drm_kms_helper         47303  1 i915
drm                   238768  3 i915,drm_kms_helper
i2c_algo_bit           13197  1 i915
soundcore              14599  1 snd
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
video                  18847  1 i915
mac_hid                13037  0 
lp                     13299  0 
parport                40753  3 parport_pc,ppdev,lp
hid_generic            12445  0 
hid_apple              13045  0 
usbhid                 41702  0 
hid                    82142  3 hid_generic,hid_apple,usbhid
firewire_ohci          35521  0 
firewire_core          57492  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sky2                   52926  0 
```Let me know if any more info is needed, thanks in advance.

EDIT: It crashed again a few minutes after posting, I took some pictures of the call trace.

---

### Post by clumsyNInja on 2013-01-01
So it seems like nobody has any ideas on what might be causing this, can someone point me in the right direction as far as getting more info on the crash? I can't seem to find anything about replacing the sysrq key on macbooks so is there another way to partially recover the system enough to log what is happening?

---

