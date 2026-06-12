---
title: "PVR 150, mythtv, ivtv help"
date: 2005-08-14
forum: Absolute Beginner Talk
---

### Post by xnszxdotnet on 2005-08-14
I have been following along the tutorial I found here:
ivtv Setup
[http://www.abarbaccia.com/content/view/19/31/](http://www.abarbaccia.com/content/view/19/31/)
on the last step 

dmesg | grep ivtv

I get this error:

```

...
ivtv: Configuring WinTV PVR 150 card with 5 streams
ivtv: Registered v4l2 device, streamtype 0 minor 0
ivtv: Create DMA stream 0 using 1024 16384 byte buffers  0 kbytes total
ivtv: Allocate DMA stream 0 using 1024 16384 byte buffers  16777216 kbytes total
ivtv: Registered v4l2 device, streamtype 1 minor 32
ivtv: Create DMA stream 1
ivtv: Allocate DMA stream 1
 [<d4be9c1c>] ivtv_stream_alloc+0xb3/0x1d5 [ivtv]
 [<d4bee700>] ivtv_streams_setup+0xeb/0x120 [ivtv]
 [<d4beb543>] ivtv_probe+0x555/0x80f [ivtv]
 [<d4bebc34>] module_start+0x154/0x183 [ivtv]
ivtv: Could not allocate SGarray
ivtv: Error -12 setting up streams
Modules linked in: wm8775 sha1 cx25840 tuner tveeprom ivtv i2c_algo_bit videodev proc_intf freq_table cpufreq_userspace cpufreq_ondemand cpufreq_powersave video sony_acpi pcc_acpi button battery container ac ipv6 ohci1394 ehci_hcd ohci_hcd snd_ens1371 snd_rawmidi snd_seq_device snd_ac97_codec af_packet snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd soundcore snd_page_alloc gameport 8139cp 8139too mii tsdev i2c_piix4 usbhid i2c_core uhci_hcd usbcore pci_hotplug intel_agp agpgart floppy pcspkr rtc md dm_mod capability commoncap sr_mod sbp2 scsi_mod evdev ieee1394 psmouse mousedev parport_pc lp parport ide_cd cdrom ext3 jbd ide_generic piix ide_disk ide_core unix thermal processor fan fbcon font bitblit vesafb cfbcopyarea cfbimgblt cfbfillrect
 <3>ivtv: Error -12 on initialization
ivtv-iTVC15_16_mpg2_encoder_card: probe of 0000:00:0f.0 failed with error -12
ivtv: ====================  END INIT IVTV  ====================
``` 

I seem to have mythtv install just fine and same with mysql.

any help would help alot.

thanx

---

### Post by tom-ubuntu on 2005-08-16
Which versions of ivtv have you installed? I think the PVR150 needs the 0.3 releases...

---

### Post by xnszxdotnet on 2005-08-16
ivtv-0.3.3k

---

