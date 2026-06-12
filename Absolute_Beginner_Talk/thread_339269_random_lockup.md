---
title: "random lockup"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by bkeithly on 2007-01-15
My system is randomly locking up.

Currently I am running edgy 64bit, 
computer: hp6040dv
kernel:
Linux laptop 2.6.17-10-generic #2 SMP Tue Dec 5 21:16:35 UTC 2006 x86_64 GNU/Linux
upgraded nvidia driver, and wifi workign with ndiswrapper

Things were running fine for about a month, but starting this week the system just freezes.   Most of the time the mouse still works but that is it.

The only way to fix the freeze is to reboot.

any Suggestions???

---

### Post by lyceum on 2007-01-16
I am having the same problem. I run the 32 bit edgy and it happened right after installing crossoveroffice. I did an up date and added MS office and crossover did the "pretending to re-start windows" and everything but the mouse froze. I thought it was crossover, as it happened again when I installed Frontpage, then it happened again later when I shut Firefox down. 

Do you you have crossover also? how long has this been going on?

:-k

---

### Post by bkeithly on 2007-01-16
I have not installed crossover linux. 

For me it seems to be a pretty random thing, really wish I could find a pattern.

On a previous install of ubuntu I had beryl running, and that seemed to be causing the crashes...

Now I can not find any patterns.

---

### Post by lyceum on 2007-01-17
I am trying to think of the other stuff I did right before it happened, I installed KDE then took it off. I installed a bunch of Gnome stuff that I will never remember... Well if nothing else, this post will bump the tread. Do you know when it started happening? I am wondering if it had anything to do with the update? are there and programs you use, like Automatix2 that are not native to Ubuntu?

---

### Post by bkeithly on 2007-01-17
I am pretty much using standard ubuntu apps.  I want to get more into some of the special features, but I really like having a good linux shell and a nice desktop to browse.

As far as I can tell the lockups have been going on for a while.   There seems to be some other posts that have "gone cold" that mentioned this issue.  

The most common thing I have seen in these threads seems to be firefox.

Maybe future versions releases of firefox will fix the issue.

---

### Post by lyceum on 2007-01-17
Hopefully. I was using FF, so maybe that is the problem. I don't seem to use any computer without having the Internet up. As no one else seems to have anything to say, I'll keep my ear to the ground til it stops.

---

### Post by riven0 on 2007-01-17
bkeithly, doing CTRL + ALT + Backspace doesn't work? Have you checked the xserver logs for error messages?

---

### Post by theOtherMarino on 2007-01-18
Hello,

I had the same problem. It happened to be a video driver problem with a GF4 MX 420 - 64 MB. Then I switched to a good'ol Matrox Millenium II I've found in a dumpster, and the problem disappeared.

I'm stuck with a 1024x768 resolution, but it works.

Always remember the motto "Linux works best with trusted configurations". "Trusted" means "old".

Marino


> **bkeithly said:**
> My system is randomly locking up.

Currently I am running edgy 64bit, 
computer: hp6040dv
kernel:
Linux laptop 2.6.17-10-generic #2 SMP Tue Dec 5 21:16:35 UTC 2006 x86_64 GNU/Linux
upgraded nvidia driver, and wifi workign with ndiswrapper

Things were running fine for about a month, but starting this week the system just freezes.   Most of the time the mouse still works but that is it.

The only way to fix the freeze is to reboot.

any Suggestions???

---

### Post by phansiizwe on 2007-01-18
I have random lockups too, started a few weeks ago.
I found some strange messages in /var/log/messages (see below), could these have anything to do with that?

Directly after the strange messages you can see a restart message (at the bottom), which probably was initiated by my hard-reset.

The next time this happens I will check the logs directly after the crash...
Any pointers where I might find some more information?

I'm running: 
Linux wlinux 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux
Latest Nvidia drivers
Wireless via ndiswrapper/wpasupplicant


```
Jan 17 22:11:02 wlinux kernel: [17183005.936000] Attempt to release TCP socket in state 1 da557b80
Jan 17 22:11:02 wlinux kernel: [17183006.044000] Attempt to release TCP socket in state 1 da556980
Jan 17 22:11:02 wlinux kernel: [17183006.380000] Attempt to release TCP socket in state 1 da557b80
Jan 17 22:11:03 wlinux kernel: [17183006.780000] Attempt to release TCP socket in state 1 da557b80
Jan 17 22:11:03 wlinux kernel: [17183006.884000] Attempt to release TCP socket in state 1 da556980
Jan 17 22:11:04 wlinux kernel: [17183007.376000] Attempt to release TCP socket in state 1 da557b80
Jan 17 22:11:04 wlinux kernel: [17183007.492000] Attempt to release TCP socket in state 1 da556980
Jan 17 22:11:04 wlinux kernel: [17183007.492000] BUG: warning at include/net/dst.h:153/dst_release()
Jan 17 22:11:04 wlinux kernel: [17183007.492000]  <c026cade> __kfree_skb+0xfe/0x110  <c02b7530> inet_sock_destruct+0x30/0x1f0
Jan 17 22:11:04 wlinux kernel: [17183007.492000]  <e08d1945> ehci_work+0xc5/0x7e0 [ehci_hcd]  <c0269691> sk_free+0x21/0x110
Jan 17 22:11:04 wlinux kernel: [17183007.492000]  <c026ca2a> __kfree_skb+0x4a/0x110  <e0cc966f> free_tx_packet+0x3f/0x60 [ndiswrapper]
Jan 17 22:11:04 wlinux kernel: [17183007.492000]  <e0cbb4fc> NdisMSendComplete+0x8c/0xf0 [ndiswrapper]  <e0ccc7a2> tx_worker+0x332/0x570 [ndiswrapper]
Jan 17 22:11:04 wlinux kernel: [17183007.492000]  <c0132702> run_workqueue+0x72/0xf0  <e0ccc470> tx_worker+0x0/0x570 [ndiswrapper]
Jan 17 22:11:04 wlinux kernel: [17183007.492000]  <c01331d0> worker_thread+0x0/0x140  <c0135f8b> kthread+0xab/0xe0
Jan 17 22:11:04 wlinux kernel: [17183007.492000]  <c0135ee0> kthread+0x0/0xe0  <c0101005> kernel_thread_helper+0x5/0x10
Jan 17 22:11:04 wlinux kernel: [17183007.492000] c0153cb2
Jan 17 22:11:04 wlinux kernel: [17183007.492000] Modules linked in: vfat fat usb_storage libusual nls_cp437 isofs udf binfmt_misc speedstep_lib cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sbs sony_acpi pcc_acpi i2c_ec hotkey dev_acpi button battery container ac asus_acpi af_packet nls_utf8 ntfs md_mod w83627hf hwmon_vid eeprom i2c_isa i2c_i801 truecrypt dm_mod raw1394 ndiswrapper sr_mod sbp2 parport_pc lp parport snd_emu10k1_synth snd_emux_synth snd_seq_virmidi snd_seq_midi_emul snd_seq_dummy snd_seq_oss snd_seq_midi snd_seq_midi_event snd_seq snd_emu10k1 snd_rawmidi snd_ac97_codec snd_ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_device snd_timer snd_page_alloc snd_util_mem snd_hwdep snd sg tsdev emu10k1_gp gameport soundcore nvidia 8139cp 8139too skge psmouse serio_raw mii i2c_core evdev intel_agp agpgart floppy hw_random shpchp pci_hotplug pcspkr ext3 jbd ohci1394 ieee1394 ehci_hcd uhci_hcd usbcore ide_generic sd_mod ata_piix libata
Jan 17 22:11:04 wlinux kernel: scsi_mod ide_cd cdrom piix generic thermal processor fan fbcon tileblit font bitblit softcursor vesafb capability commoncap
Jan 17 22:11:04 wlinux kernel: [17183007.492000] EIP:    0060:[put_page+2/64]    Tainted: PF     VLI
Jan 17 22:11:04 wlinux kernel: [17183007.492000] EFLAGS: 00010202   (2.6.17-10-generic #2) 
Jan 17 22:11:04 wlinux kernel: [17183007.492000]  <6>recvmsg bug: copied 3E79AC29 seq 3E79B769
Jan 17 22:11:04 wlinux kernel: [17183007.496000] recvmsg bug: copied 3E79AC29 seq 3E79B769
Jan 17 22:11:04 wlinux last message repeated 94 times
Jan 17 22:11:04 wlinux kernel: [17183007.500000] recvmsg bug: copied 3E79AC29 seq 3E79B769
Jan 17 22:11:04 wlinux last message repeated 123 times
Jan 17 22:11:04 wlinux kernel: [17183007.504000] recvmsg bug: copied 3E79AC29 seq 3E79B769
Jan 17 22:11:04 wlinux last message repeated 88 times
Jan 17 22:11:04 wlinux kernel: [17183007.508000] recvmsg bug: copied 3E79AC29 seq 3E79B769
Jan 17 22:11:04 wlinux last message repeated 79 times
Jan 17 22:11:04 wlinux kernel: [17183007.564000] recvmsg bug: copied 3E79AC29 seq 3E79B769
Jan 17 22:11:04 wlinux kernel: [17183007.568000] recvmsg bug: copied 3E79AC29 seq 3E79B769
Jan 17 22:11:04 wlinux last message repeated 13 times
Jan 17 22:11:04 wlinux kernel: [17183007.572000] recvmsg bug: copied 3E79AC29 seq 3E79B769
Jan 17 22:11:04 wlinux last message repeated 15 times
Jan 17 22:11:04 wlinux kernel: [17183007.576000] recvmsg bug: copied 3E79AC29 seq 3E79B769
Jan 17 22:11:04 wlinux last message repeated 13 times
Jan 17 22:11:04 wlinux kernel: [17183007.580000] recvmsg bug: copied 3E79AC29 seq 3E79B769
Jan 17 22:11:04 wlinux last message repeated 16 times
Jan 17 22:11:04 wlinux kernel: [17183007.584000] recvmsg bug: copied 3E79AC29 seq 3E79B769
Jan 17 22:11:04 wlinux last message repeated 18 times
Jan 17 22:11:04 wlinux kernel: [17183007.588000] recvmsg bug: copied 3E79AC29 seq 3E79B769
Jan 17 22:11:04 wlinux last message repeated 13 times
Jan 17 22:11:04 wlinux kernel: [17183007.592000] recvmsg bug: copied 3E79AC29 seq 3E79B769
Jan 17 22:11:04 wlinux last message repeated 9 times
Jan 17 22:11:04 wlinux kernel: [17183007.596000] recvmsg bug: copied 3E79AC29 seq 3E79B769
Jan 17 22:11:04 wlinux last message repeated 5 times
Jan 17 22:11:04 wlinux kernel: [17183007.600000] recvmsg bug: copied 3E79AC29 seq 3E79B769
Jan 17 22:11:05 wlinux last message repeated 176 times
Jan 17 22:11:05 wlinux kernel: [17183007.604000] recvmsg bug: copied 3E79AC29 seq 3E79B769
Jan 17 22:11:05 wlinux last message repeated 185 times
Jan 17 22:11:05 wlinux kernel: [17183007.608000] recvmsg bug: copied 3E79AC29 seq 3E79B769
Jan 17 22:11:05 wlinux last message repeated 44 times
Jan 17 22:11:05 wlinux kernel: [17183007.608000] recvmsg bug: cg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copieg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copied g: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copieg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copied g: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copied 3E79AC29 seq 3E79B769
Jan 17 22:11:05 wlinux kernel: [17183007.608g: copied g: copied g: copieg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copied g: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copiedg: copied 3E79AC29 seq 3E79B769

```

SNIP

```
Jan 17 22:11:18 wlinux kernel: [17g: copied 3E79AC29 seq 3E79B769
Jan 17 22:11:18 wlinux kernel: [17183021.464000g: copied 3E79AC29 seq g: copied 3E79AC29 seq 3E79B769
Jan 17 22:11:18 wlinux kernel: [17183021.464000] recvg: copied 3E79AC29 seq 3Eg: copied 3E79AC29 seq 3E79B769
Jan 17 22:11:18 wlinux kernel: [17183021.464000] recvg: copied 3E79AC29 seq 3g: copied 3E79AC29 seq 3E79B769
Jan 17 22:11:18 wlinux kernel: [17183021.464000] recvg: copied 3E79AC29 seq 3g: copied 3E79AC29 seq 3E79B769
Jan 17 22:11:18 wlinux kernel: [17183021.464000] recg: copied 3E79AC29 seq 3g: copied 3E79AC29 seq 3E79B769
Jan 17 22:11:18 wlinux kernel: [17183021.464000] recg: copied 3E79AC29 seq 3g: copied 3E79AC29 seq 3E79B769
Jan 17 22:11:18 wlinux kernel: [17183021.464000] recvg: copied 3E79AC29 seq 3g: copied 3E79AC29 seq 3E79B769
Jan 17 22:11:18 wlinux kernel: [17183021.464000] recvg: copied 3E79AC29 seq g: copied 3E79AC29 seq 3E79B769
Jan 17 22:11:18 wlinux kernel: [17183021.464000] recvg: copied 3E79AC29 seq 3g: copied 3E79AC29 seq 3E79B769
Jan 17 22:11:18 wlinux kernel: [17183021.464000] reg: copied 3E79AC29 seq g: copied 3E79AC29 seq 3E79B769
Jan 17 22:11:18 wlinux kernel: [17183021.464000] recvmsg bug: copied 3E79AC29 seq 3E79B769
Jan 17 22:13:21 wlinux syslogd 1.4.1#18ubuntu6: restart.
```

---

### Post by bkeithly on 2007-01-18
CRTL + ALT + BACKSPACE

does nothing...  I have tried it over and over....

also can't ssh into the machine after the screen locks up.

The only error I have been able to find in any logs is something in regards to flash libraries and java libraries not loading correctly.


I loaded SWIFT FOX and it seems to be a little more stable...  Now that I have said this the system will probably lock up before I finish typing this message.

But things have been stable for about 24 hours now.  AND flash working after install.  Didn't have to do anything special to get it to work!!!

---

### Post by bkeithly on 2007-01-18
phansiizwe, 

your errors appear to be network related...

have you tried disabling your nic and seeing if your system stabilizes?

---

### Post by lyceum on 2007-01-19
> **bkeithly said:**
> CRTL + ALT + BACKSPACE

does nothing...  I have tried it over and over....

also can't ssh into the machine after the screen locks up.

The only error I have been able to find in any logs is something in regards to flash libraries and java libraries not loading correctly.


I loaded SWIFT FOX and it seems to be a little more stable...  Now that I have said this the system will probably lock up before I finish typing this message.

But things have been stable for about 24 hours now.  AND flash working after install.  Didn't have to do anything special to get it to work!!!

I have not had any lock ups either, but I have not been conected to the net with that machine. Either the last update fixed it, or the net is the problem. I will find out this evening.

---

### Post by phansiizwe on 2007-01-20
> **bkeithly said:**
> phansiizwe, 

your errors appear to be network related...

have you tried disabling your nic and seeing if your system stabilizes?


Thank you for the info bkeithly. I figure it might be a problem with ndiswrapper/wpasupplicant, for instance when I perform a normal restart, my USB WLAN Stick (german AVM stick) does not function correctly. After a full shutdown/start the stick function fine.

The lockups appear only very seldom, so I can't really say that my system is instable in the first place...

---

### Post by napzilla on 2007-01-20
I'm in the middle of researching this random lockup issue myself. I am using Ubuntu Edgy Eft on a machine that has no known history of malicious behaviour. Here's what I've learned from various forums, websites and trial & error (mostly trial & error ](*,)  ). Let me preface this with a disclaimer: I am very much a novice when it comes to Linux; I converted from Windows XP to Ubuntu almost two months ago.

1.  Troubles during the installation phase convinced me that the video card was probably the culprit in my case. I finally managed to stop the complete freezes (including the mouse) during setup by instructing the BIOS to run the install with only 256 MB of ram. Once I changed the video drivers, I went from complete freezes to the more common lockups (mouse moves, but nothing responds).

2.  ATI Radeon cards seem to be intimately involved in many of these lockups (or perhaps AGP cards). I personally am on a Dell Precision 360 with a Radeon R300 NG by ATI, and I have been plagued by lockups since I converted to Ubuntu.  It must say something for Ubuntu that, in spite of these random lockups, I still think that Linux is the greatest thing to happen to computers since the Commodore 64.

3.  I have tried configuring xorg.conf with the radeon, ati and fglrx drivers. While none of these drivers have eliminated the lockups, the fglrx driver has reduced their frequency to once every day or two. Other users have sworn that adding the following line to the "Device" settings has made the difference:
[INDENT]Option    "KernelModuleParm" "agplock=0"[/INDENT]
I personally haven't observed any difference with this option enabled.

4.  While I haven't had this problem, many users report that their screen-savers trigger lockups. I'm using one of the generic Ubuntu screen-savers that just cycles through NASA images--perhaps other users are using more high-end screen-savers.

5.  Mozilla Firefox also seems to be a strong trigger. I have noticed that using my mouse-wheel to scroll through a long web page will almost invariably trigger a lockup.

6.  Ctl + Alt + Backspace doesn't evoke a response, nor does any other keyboard input. The only solution I've found is toggling the good old power switch.

Of the suggested solutions that I've found, here is the only I haven't tried yet:
  1.	When grub comes up, choose your kernel and press "e". Then find the kernel line and press "e" again
  2.	Try adding either of these to the end of your boot string:
		pci=noacpi pci=usepirqmask
	OR (well, you could do AND if you like)
		iommu=off
  3.	Press enter, then "b" to boot.
Unfortunately, I was having an airhead moment and forgot to note the source on that suggestion. If you're out there, and this works, I apologise for not crediting you properly.

I'm planning on trying out this suggestion out the next time I have a lockup (shouldn't be long now). If it or anything else I discover seems to resolve the issue, I'll be sure to post here again. Until then, save often and try learning to type with your fingers crossed.

  -Brian

---

### Post by lyceum on 2007-01-21
I think the issue may have been resolved, as I have not had a lock up in a while now, and I started with 3 in one day.

And, Napzilla, welcome to Ubuntu! Sorry about the mess. :)

---

### Post by napzilla on 2007-02-23
Hello again. I just wanted to follow-up on my previous post. I swapped my ATI card out for a NVIDIA card, and the lock-ups stopped immediately. I think it was more the particular make and model of the ATI card than it was ATI in general, as I have converted my Dell Inspiron (which has a 256 MB ATI card) into an Ubuntu machine and have not had any lock-ups there, either. It could also be that this particular computer bears a grudge against me. I do tend to insult it a lot.

As a side note, I have been pleased to find that the more I use Ubuntu (and Linux in general), the *more* I like it, as opposed to my experiences with my previous OS.

---

