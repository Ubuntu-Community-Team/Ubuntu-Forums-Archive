---
title: "5-in-1 Card reader"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by mevets on 2007-04-17
I have a Gateway MX6931
---
[http://support.gateway.com/s/Mobile/Q106/BladeC/1013918Rnv.shtml](http://support.gateway.com/s/Mobile/Q106/BladeC/1013918Rnv.shtml)
---

There are some indications that the card reader works, but ultimatley when I stick cards into it, nothing happens. inside the device DB it recognizes the name of the card reader and the driver info is tifm_7xx1.

What must I to do get the card reader working?

---

### Post by klytu on 2007-04-18
> **mevets said:**
> I have a Gateway MX6931
---
[http://support.gateway.com/s/Mobile/Q106/BladeC/1013918Rnv.shtml](http://support.gateway.com/s/Mobile/Q106/BladeC/1013918Rnv.shtml)
---

There are some indications that the card reader works, but ultimatley when I stick cards into it, nothing happens. inside the device DB it recognizes the name of the card reader and the driver info is tifm_7xx1.

What must I to do get the card reader working?

[[COLOR="Red"]_This HowTo_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=315497") should work for you.

---

### Post by mevets on 2007-04-18
Didnt work for me, even though it didnt explicitly say it didnt. after running the  second command there wasnt any output.

Im running feisty, could that be the culpret?

---

### Post by klytu on 2007-04-18
> **mevets said:**
> Didnt work for me, even though it didnt explicitly say it didnt. after running the  second command there wasnt any output.

Im running feisty, could that be the culpret?

I'm not sure, but I doubt if card reader support was added in Edgy that it would disappear in Feisty. Midway through that HowTo thread Rhubarb posted in January 2007 another method to try:

1. Make a backup of your 'modules' in case something goes wrong:```
sudo cp /etc/modules /etc/modules.backup
```
2. Then: ```
sudo gedit /etc/modules
``` 3. and add the following entry to the end of the file:> tifm_sd 4. Save and close the file and restart. Rhubarb states the reader is found as /dev/mmcblk0 (but that may be slightly different for you if this works) and that it's mounted automatically when a card is inserted.

---

### Post by mevets on 2007-04-18
Never seems to mount. I tried having nautalis open to /dev and mmcblk0 seemed to appear and then disappear when I inserted a card. I think these instructions apply to me:
```

Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

To get the TI 5in1 Card Reader (like it is built in the Z61m) to work, you need a recent kernel (I use 2.6.19 on Debian Sid here, should work with 2.6.18 too) with some special options enabled:

Device Drivers &#8594; Misc devices &#8594; [M]TI Flash Media interface support (EXPERIMENTAL) (CONFIG_TIFM_CORE)

Device Drivers &#8594; Misc devices &#8594; [M]TI Flash Media PCI74xx/PCI76xx host adapter support (EXPERIMENTAL) (CONFIG_TIFM_7XX1)

Device Drivers &#8594; MMC/SD Card support &#8594; [M]MMC support (CONFIG_MMC)

Device Drivers &#8594; MMC/SD Card support &#8594; [M]MMC block device driver (CONFIG_MMC_BLOCK)

Device Drivers &#8594; MMC/SD Card support &#8594; [M]TI Flash Media MMC/SD Interface support (EXPERIMENTAL) (CONFIG_MMC_TIFM_SD)

After rebuilding your kernel, you should get some new modules: tifm_core, tifm_7xx1, mmc_core, mmc_block, tifm_sd. The first two will get autoloaded on boot, if you use some kind of hardware-autodetection, the others won't, so edit your /etc/modules (or however the file where the modules to load on boot are listed is called by your distribution) and add these modules there.

After a reboot, or after you've loaded the modules by-hand with modprobe, you can put a SD-Card into the slot and see the light blink once. You should see something like this in your $ dmesg output:

 tifm_7xx1: sd card detected in socket 1
 mmcblk0: mmc0:b368 SMI   999424KiB
  mmcblk0: p1
 mmcblk0: error 4 sending stop command
 end_request: I/O error, dev mmcblk0, sector 1998840
 Buffer I/O error on device mmcblk0, logical block 249855}}

Don't care about the errors, my card is still working. Now you can mount the card with # mount /dev/mmcblk0p1 /somewhere and work with it.
NOTE!
This works only for SD cards at the moment, the driver isn't able to handle MMC/MS/MS PRO/xD yet.


```
from [http://www.thinkwiki.org/wiki/How_to_get_the_internal_SD-CARD_working](http://www.thinkwiki.org/wiki/How_to_get_the_internal_SD-CARD_working)

Is Device Drivers &#8594; Misc devices &#8594; [M]TI Flash Media interface support (EXPERIMENTAL) (CONFIG_TIFM_CORE) and all the rest something Debian speciific or am I just not seeing it in Ubuntu?

My dmesg output:
```

[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 8036287
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 8036288
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 8036289
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 8036290
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 8036291
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 8036292
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 8036293
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 8036294
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 8036335
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 8036336
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 8036337
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 8036338
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 8036339
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 8036340
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 8036341
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 8036342
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 8036351
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 8036351
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 63
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 64
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 65
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 66
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 67
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 68
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 69
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 70
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 63
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 64
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 65
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 66
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 67
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 68
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 69
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 70
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 63
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 64
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 65
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 66
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 67
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 68
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 69
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 70
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 63
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 64
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 65
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 66
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 67
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 68
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 69
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 70
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 63
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 64
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 65
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 66
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 67
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 68
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 69
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 70
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 63
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 64
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 65
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 66
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 67
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 68
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 69
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 70
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 63
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 64
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 65
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 66
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 67
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 68
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 69
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 70
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 63
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 64
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 65
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 66
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 67
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 68
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 69
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 70
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 63
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 64
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 65
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 66
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 67
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 68
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 69
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 70
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 63
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 64
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 65
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 66
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 67
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 68
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 69
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 70
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 63
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 64
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 65
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 66
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 67
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 68
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 69
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 70
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 63
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 64
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 65
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 66
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 67
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 68
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 69
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 70
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 63
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 64
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 65
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 66
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 67
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 68
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 69
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 70
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 63
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 64
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 65
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 66
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 67
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 68
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 69
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 70
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 63
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 64
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 65
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 66
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 67
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 68
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 69
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 70
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 63
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 64
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 65
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 66
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 67
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 68
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 69
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 70
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 63
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 64
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 65
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 66
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 67
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 68
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 69
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 70
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 63
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 64
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 65
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 66
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 67
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 68
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 69
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 70
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 63
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 64
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 65
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 66
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 67
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 68
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 69
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 70
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 63
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 64
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 65
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 66
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 67
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 68
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 69
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 70
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 63
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 64
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 65
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 66
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 67
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 68
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 69
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 70
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 63
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 64
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 65
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 66
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 67
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 68
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 69
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 70
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 63
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 64
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 65
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 66
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 67
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 68
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 69
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 70
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 63
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 64
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 65
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 66
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 67
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 68
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 69
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 70
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 63
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 64
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 65
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 66
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 67
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 68
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 69
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 70
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 63
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 64
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 65
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 66
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 67
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 68
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 69
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 70
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 63
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 64
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 65
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 66
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 67
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 68
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 69
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 70
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 63
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 64
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 65
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 66
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 67
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 68
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 69
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 70
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 0
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 8
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 16
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 24
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 0
[21248.840000] mmcblk0: error 1 sending read/write command
[21248.840000] end_request: I/O error, dev mmcblk0, sector 0
[21249.828000] tifm_7xx1: sd card detected in socket 1
[21249.876000] mmcblk0: mmc0:1234 SD04G 4018176KiB 
[21249.876000]  mmcblk0: p1


```

---

### Post by klytu on 2007-04-19
> Is Device Drivers &#8594; Misc devices &#8594; [M]TI Flash Media interface support (EXPERIMENTAL) (CONFIG_TIFM_CORE) and all the rest something Debian speciific or am I just not seeing it in Ubuntu?

Yeah, that looks like a Debian specific menu. Unfortunately, the original poster in the HowTo thread first linked is, as of a week ago, still having difficulty getting the reader to work under Feisty. Maybe upgrading to the newest version just released will work better?

---

### Post by mevets on 2007-04-19
ive been running herd 5. would the update manager have upgraded me to the offcial release?

---

### Post by yachoo on 2007-04-22
Everything was fine on Edgy. After:
setpci -s 07:06.2 4c.b=02
everything was working.
Now (on Feisty) after that I got nothing. The glimmer just flash, and the syslog tells me nothing about that. Can someone tell me what to do with that? Did anyone worked it out?

---

### Post by macogw on 2007-04-23
Go [here](http://ubuntulinuxtipstricks.blogspot.com/2007/04/texas-instruments-sdmmc-card-reader.html) for instructions on making your TI SD card reader work with Feisty.  I copied the newer version of the driver plus included fixed kernel modules and tarred them up with a bash script.  The bash script will fix the kernel headers and install the new drivers.  Let me know if you have any trouble.

---

