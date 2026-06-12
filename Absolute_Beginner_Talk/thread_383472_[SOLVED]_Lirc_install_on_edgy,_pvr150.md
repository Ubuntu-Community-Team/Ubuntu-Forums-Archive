---
title: "[SOLVED] Lirc install on edgy, pvr150"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by Beezleblub on 2007-03-13
I am trying to get lirc to work for few nights in a row now,  still no luck. :( . 

I have a PVR150 model 1055. 

I have seen all the erros you find in all the forums, just no solution would work out...  aaargh :confused: 

right now I get :

irw
connect : connection refused.

dmesg | grep lirc
[17179593.816000] lirc_dev: IR Remote Control driver registered, at major 61 
[17179593.820000] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.

how do you know for sure if you need i2c or MCeusb or gpio ? 

Anybody got the pvr150 with lirc working on edgy can share how they did it ?

Thanks.

---

### Post by pulpinator on 2007-03-25
I'm getting the same error, so if you ever figure it out, please post it here!

---

### Post by Beezleblub on 2007-04-24
I had to drop my Myth Project due to travelling, but back on the job now. 

I decided to start over with Feisty, as it has better support for Pvr150.

yes, PVR150 works out of the box, at least the IVTV part does. 
It only needed a COLD reboot (plug out the power !) before the nvm was recognized correctly. 

Getting LIRC to work is still a mystery, looks I got closer, but still no Cigar. 

few things noticed : 
I was using my local server (Singapore) 
That seems to load older packages, and no PVr150 option available in the lirc Setup. 
Changed to the Main server, slower, but then Lirc gives an option to select PVR150.

what options do you need to select and compile in Lirc ? both  I2C and PVR150 ?  or is only PVR150 enough ? 
and the settings in lircd.conf ? 
the settings in the latest how-to did not do it for me... 

also, some remotes are supported directly by the kernel, no Lirc needed.  
anybody has a list of which Remotes are supported by the kernel, and if pvr150 with integrated IR needs Lirc or not ? 

I think I will check the card's functionality in my windows pc next, see if anything wrong with my card...  Will keep digging !

Thanks !

---

### Post by superm1 on 2007-04-25
Basically, It comes down to this:

If you have a USB receiver hooked up to the computer that came with your pvr150:
you need either the mceusb2 or mceusb driver.  Most commonly you will need the mceusb2.

If you have IR built directly to the pvr150, then you will need the lirc_i2c module.

If you want to use an IR transmitter cable that comes directly from the pvr150, you will need both lirc_i2c and lirc_pvr150.

---

### Post by spottedcow on 2007-05-18
I had the same problem after upgrading from Edgy to Feisty.  Everything was working but my remote.
With Edgy, I followed this guide and it seemed to work:
[https://help.ubuntu.com/community/Install_Lirc_Edgy]("https://help.ubuntu.com/community/Install_Lirc_Edgy")
I have 2 PVR-150 PCI cards with the IR receiver you plug into the PCI card (not the USB IR one)

After the upgrade, I had no lirc devices listed in /dev, and a irw command ended with the following:
```
/$ sudo irw
connect: Connection refused
```

I installed the lirc_i2c module and everything is working:
```
$ sudo modprobe lirc_i2c
```

This added the 2 lirc devices into the /dev directory and was confirmed at the end of my message log:
```
[ 4000.355252] lirc_dev: IR Remote Control driver registered, at major 61 
[ 4000.356261] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.
[ 4000.393519] bttv: driver version 0.9.16 loaded
[ 4000.393524] bttv: using 8 buffers with 2080k (520 pages) each for capture
[ 4000.431030] cx2388x v4l2 driver version 0.0.6 loaded
[ 4000.449199] lirc_i2c: chip found @ 0x71 (Hauppauge IR (PVR150))
[ 4000.449232] lirc_dev: lirc_register_plugin: sample_rate: 10
[ 4000.502207] lirc_i2c: chip found @ 0x71 (Hauppauge IR (PVR150))
[ 4000.502237] lirc_dev: lirc_register_plugin: sample_rate: 10
```

To keep this setting over a reboot, add the lirc_i2c module to the /etc/modules file.

---

### Post by superm1 on 2007-05-20
> **spottedcow said:**
> I had the same problem after upgrading from Edgy to Feisty.  Everything was working but my remote.
With Edgy, I followed this guide and it seemed to work:
[https://help.ubuntu.com/community/Install_Lirc_Edgy](https://help.ubuntu.com/community/Install_Lirc_Edgy)
I have 2 PVR-150 PCI cards with the IR receiver you plug into the PCI card (not the USB IR one)

After the upgrade, I had no lirc devices listed in /dev, and a irw command ended with the following:
```
/$ sudo irw
connect: Connection refused
```I installed the lirc_i2c module and everything is working:
```
$ sudo modprobe lirc_i2c
```This added the 2 lirc devices into the /dev directory and was confirmed at the end of my message log:
```
[ 4000.355252] lirc_dev: IR Remote Control driver registered, at major 61 
[ 4000.356261] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.
[ 4000.393519] bttv: driver version 0.9.16 loaded
[ 4000.393524] bttv: using 8 buffers with 2080k (520 pages) each for capture
[ 4000.431030] cx2388x v4l2 driver version 0.0.6 loaded
[ 4000.449199] lirc_i2c: chip found @ 0x71 (Hauppauge IR (PVR150))
[ 4000.449232] lirc_dev: lirc_register_plugin: sample_rate: 10
[ 4000.502207] lirc_i2c: chip found @ 0x71 (Hauppauge IR (PVR150))
[ 4000.502237] lirc_dev: lirc_register_plugin: sample_rate: 10
```To keep this setting over a reboot, add the lirc_i2c module to the /etc/modules file.
There is a setting in /etc/lirc/hardware.conf to automatically modprobe the driver when starting lirc.  This is an alternative to adding to /etc/modules.

In order to use it, you will have to make sure lirc_i2c is in the listed modules to be loaded at lirc start in /etc/lirc/hardware.conf

---

### Post by Ray Frenden on 2007-05-29
I'm smack dab in the middle of my first Ubuntu installation (Feisty) and am trying to get MythTV up and running. I have everything configured except that I can't run the backend setup because my IR Blaster doesn't work (so scanning for/adding channels isn't happening). 

I read that Feisty doesn't require installing LIRC with my PVR150 card, because of inherent support, so what DOES one have to do to get it going? [The community install docs I can find ]("https://help.ubuntu.com/community/MythTV_Feisty_hardware_list#head-6d34a57c5684f0eab989f8091c4ff39893b16521")seem pretty obtuse for an outsider. 

If this goes according to plan, I am going to convert five of my PCs to Ubuntu (and dual boot it on my 24" iMac). I certainly feel as though I learned a lot about the OS in the last three days of fighting with remotes and tuners and myth and...

If this isn't the correct place for such a question, let me know and I'll start a thread there.

Thanks!

---

### Post by superm1 on 2007-05-30
> **Ray Frenden said:**
> I'm smack dab in the middle of my first Ubuntu installation (Feisty) and am trying to get MythTV up and running. I have everything configured except that I can't run the backend setup because my IR Blaster doesn't work (so scanning for/adding channels isn't happening). 

I read that Feisty doesn't require installing LIRC with my PVR150 card, because of inherent support, so what DOES one have to do to get it going? [The community install docs I can find ]("https://help.ubuntu.com/community/MythTV_Feisty_hardware_list#head-6d34a57c5684f0eab989f8091c4ff39893b16521")seem pretty obtuse for an outsider. 

If this goes according to plan, I am going to convert five of my PCs to Ubuntu (and dual boot it on my 24" iMac). I certainly feel as though I learned a lot about the OS in the last three days of fighting with remotes and tuners and myth and...

If this isn't the correct place for such a question, let me know and I'll start a thread there.

Thanks!
Hi, so you are looking for pvr-150 blaster support?  You will need to use lirc for this indeed.  The feisty lirc page has a section explaining what is necessary.

---

### Post by Beezleblub on 2007-06-01
Thanks SuperM1,

Maybe I need to re-install from scratch because my Lirc might be messed up a bit again. 

My biggest problem with the PVR 150 is sometimes it gets recognized, and vlc player will manage to open the device and play TV,  sometimes after reboot the whole card detection just doesn't do it, and I need to do a cold reboot (complete power off), after wich it *might* be ok again.. 

So far I failed  gettng the IR receiver to work.. 
But also my windows PC failed to get the remote to work. 
I must say also the Windows drivers for the PVR150 are quite a mess to install.

I will have another go at it this weekend, and post the logs of a good and failing card here, in case anyone hase bright ideas.. 

cheers ! 

B.

---

### Post by Beezleblub on 2007-06-02
Okay, 
Reinstalled Feisty from scratch, 
brought the machine up to date, 
then installed Lirc. 
Installed VLC. 
VLC can open the pvr150 and shows picture from the CVBS input. 
But still NO RC in Lirc...- sigh-
see logs below,  it seems it does not recognize module lirc_i2c ?  
lirc_pvr150 seems to be loaded, so the blaster part could work..  ??
any thoughts ?

IVTV message:
dirk@meemee:~$ dmesg |grep ivtv
[   11.920765] ivtv:  ==================== START INIT IVTV ====================
[   11.920770] ivtv:  version 0.10.1 (tagged release) loading
[   11.920772] ivtv:  Linux version: 2.6.20-16-generic SMP mod_unload 586
[   11.920774] ivtv:  In case of problems please include the debug info between
[   11.920777] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[   11.920779] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[   11.920841] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   11.921316] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   12.610573] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   12.826144] ivtv0: Encoder revision: 0x02050032
[   12.826147] ivtv0: Recommended firmware version is 0x02060039.
[   12.892491] ivtv0: Invalid EEPROM
[   12.917082] tuner 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   12.921447] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   12.959136] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   17.871965] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   17.936522] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   17.936711] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   17.936937] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   17.937027] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   17.937276] ivtv0: Registered device radio0 for encoder radio
[   18.326994] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[   18.327007] ivtv:  ====================  END INIT IVTV  ====================
 

Lirc message : 
dirk@meemee:~$ dmesg |grep lirc
[   31.292253] lirc_dev: IR Remote Control driver registered, at major 61
[   31.294934] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.
[   31.428555]  [<f98320b8>] init_module+0x48/0x50 [lirc_pvr150]
dirk@meemee:~$

---

### Post by Beezleblub on 2007-06-02
and then, couple of reboots later , I get this, and VLC will not play any video anymore...
seems somehow, no more i2c hardware is found ?


[   13.065601] ivtv:  ==================== START INIT IVTV ====================
[   13.065606] ivtv:  version 0.10.1 (tagged release) loading
[   13.065608] ivtv:  Linux version: 2.6.20-16-generic SMP mod_unload 586
[   13.065610] ivtv:  In case of problems please include the debug info between
[   13.065612] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[   13.065614] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[   13.065679] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   13.073083] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   13.736497] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   13.953956] ivtv0: Encoder revision: 0x02050032
[   13.953959] ivtv0: Recommended firmware version is 0x02060039.
[   14.017172] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   14.017174] ivtv0: reopen i2c bus for IR-blaster support
[   14.530022] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   14.530219] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   14.530417] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   14.530499] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   14.530749] ivtv0: Registered device radio0 for encoder radio
[   14.530767] ivtv0: i2c hardware 0x00000001 (cx2584x) not found for command 0xc008561c!
[   14.530771] ivtv0: i2c addr 0x44 not found for command 0x4008646f!
[   14.530775] ivtv0: i2c hardware 0x00000020 (wm8775) not found for command 0x4008646d!
[   14.530778] ivtv0: i2c hardware 0x00000001 (cx2584x) not found for command 0x4008646d!
[   14.640629] ivtv0: i2c hardware 0x00000001 (cx2584x) not found for command 0xc008561c!
[   14.640636] ivtv0: i2c hardware 0x00000001 (cx2584x) not found for command 0xc008561c!
[   14.748387] ivtv0: i2c hardware 0x00000001 (cx2584x) not found for command 0xc008561c!
[   14.748391] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[   14.748405] ivtv:  ====================  END INIT IVTV  ====================
[   28.068720] lirc_pvr150: ivtv i2c driver #0: no devices found

---

### Post by Beezleblub on 2007-07-15
Okay, I finally found time to return my card to Hauppauge service, as it wasn't going anywhere.
They were kind enough to replace the card, and now the IR receiver works flawless.
All I had to do was plug it in and startup, so the PC settings were all good. 

Thanks all for the reply's and help in debugging !
Cheers!

B.

---

