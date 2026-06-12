---
title: "Graphics card running at full blast (hot) in Ubuntu Server install on 2009 iMac"
date: 2015-06-04
forum: Apple Hardware Users
---

### Post by ryan162 on 2015-06-04
Hi, thanks in advance for your assistance. I had an older 27" iMac collecting dust in my basement, so I decided to install ubuntu server on it. It's a 2009 model with radeon mobility 4850 graphics.

After install, I first had an issue with black screen after GRUB. That issue was solved by adding "nomodeset" into the correct parameter in the grub config. 

However, I soon began to notice that the computer was running extremely hot with GPU temp hovering around 80degC. Since I'm running server edition with no GUI, there is obviously no reason for the graphics card to be reaching such temperatures. 

When I look at the hardware using > lshw -c video or > lshw -c display, it shows the ATI card as "UNCLAIMED" even though I have the open source drivers installed. 

I have read lots of forum entries similar to my topic but I'm unable to come up with a fix that allows the drivers to be detected properly or that will allow me to dial back the throttle on the GPU. 

Booting without including the nomodeset parameter still results in black screen. 


The current workaround is boosting the minimum fan speed for the GPU in applesmc just to keep temps down. Obviously I'd like to find the actual cause for the GPU running full blast all the time for no reason. 

What I have tried:

Installing proprietary drivers instead of open source

enabling radeon.dpm in GRUB config

Several other fixes before I realized I can't configure anything related to the driver since it isn't being detected

I'm new to troubleshooting linux but I think once I can get to the point where I am detecting the driver, there are options I can try such as changing the power management profile manually in the driver config file perhaps.

TIA for your help, if I've left off any important information let me know.

---

### Post by rican-linux on 2015-06-04
Post the output of this 

```
dmesg |grep -e radeon -e drm
```

---

### Post by ryan162 on 2015-06-04
> **rican-linux said:**
> Post the output of this 

```
dmesg |grep -e radeon -e drm
```

Here:

[SIZE=3]```

[COLOR=#ff0000][FONT=Menlo][    1.999973] [drm] Initialized drm 1.1.0 20060810
[/FONT][FONT=Menlo][    2.054151] [drm] VGACON disable radeon kernel modesetting.[/FONT]
[FONT=Menlo][    2.056128] [drm:radeon_init] *ERROR* No UMS support in radeon module![/FONT]
[FONT=Menlo][   39.426715] [drm] VGACON disable radeon kernel modesetting.[/FONT]
[FONT=Menlo][   39.430206] [drm:radeon_init] *ERROR* No UMS support in radeon module![/FONT]
[FONT=Menlo][   47.428203] [drm] VGACON disable radeon kernel modesetting.[/FONT]
[/COLOR][FONT=Menlo][COLOR=#ff0000][   47.428207] [drm:radeon_init] *ERROR* No UMS support in radeon module![/COLOR]
[/FONT]
```[/SIZE]

---

### Post by rican-linux on 2015-06-04
hmmm did you look through [this]("http://ubuntuforums.org/showthread.php?t=2243922") post?

---

### Post by ryan162 on 2015-06-04
I read through and it did lead me to find a small piece of the fglrx driver still hiding. It was fglrx-core, which for some reason wasn't caught when I ran ```
 aptitude purge fglrx* 
```

I purged it and reinstalled all the packages for the open source drivers. 

I rebooted to a black screen after removing "nomodeset" but was able to run lshw over ssh and the driver is in fact being detected. 

So that leaves me now trying to configure the driver so that I get rid of the black screen, but I'm not really sure where to begin. Obviously "nomodeset" isn't an option...

---

### Post by ryan162 on 2015-06-04
new output of the log file -c radeon -c drm

Everything looks nice and the GPU temp is dropping with the fan at the same fixed speed it was before. Aside from black screen it's functioning great I think. As soon as the driver loads the screen cuts out from what I can tell. Is there some way to configure the driver to boot up in a display "safe mode" without enabling nomodeset?

```

[FONT=Menlo]
[COLOR=#ff0000][SIZE=3][    1.982449] [[/SIZE][/COLOR][/FONT][COLOR=#ff0000][SIZE=3][FONT=Menlo]drm] Initialized drm 1.1.0 20060810
[/FONT][/SIZE][/COLOR][FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.032553] [drm] radeon kernel modesetting enabled.[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.044577] fb: switching to radeondrmfb from EFI VGA[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.047002] [drm] initializing kernel modesetting (RV770 0x1002:0x944A 0x106B:0x00B5).[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.047012] [drm] register mmio base: 0xD0620000[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.047014] [drm] register mmio size: 65536[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.348955] radeon 0000:01:00.0: VRAM: 512M 0x0000000000000000 - 0x000000001FFFFFFF (512M used)[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.348958] radeon 0000:01:00.0: GTT: 1024M 0x0000000020000000 - 0x000000005FFFFFFF[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.348960] [drm] Detected VRAM RAM=512M, BAR=256M[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.348962] [drm] RAM width 256bits DDR[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.349118] [drm] radeon: 512M of VRAM memory ready[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.349119] [drm] radeon: 1024M of GTT memory ready.[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.349128] [drm] Loading RV770 Microcode[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.349176] [drm] External GPIO thermal controller with fan control[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.349183] [drm] radeon: power management initialized[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.349187] [drm] GART: num cpu pages 262144, num gpu pages 262144[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.350412] [drm] enabling PCIE gen 2 link speeds, disable with radeon.pcie_gen2=0[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.368308] [drm] PCIE GART of 1024M enabled (table at 0x0000000000040000).[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.368361] radeon 0000:01:00.0: WB enabled[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.368363] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000020000c00 and cpu addr 0xffff880036336c00[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.368366] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000020000c0c and cpu addr 0xffff880036336c0c[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.368369] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.368371] [drm] Driver supports precise vblank timestamp query.[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.368372] radeon 0000:01:00.0: radeon: MSI limited to 32-bit[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.368387] radeon 0000:01:00.0: irq 46 for MSI/MSI-X[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.368394] radeon 0000:01:00.0: radeon: using MSI.[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.368414] [drm] radeon: irq initialized.[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.414965] [drm] ring test on 0 succeeded in 1 usecs[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.414972] [drm] ring test on 3 succeeded in 2 usecs[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.415202] [drm] ib test on ring 0 succeeded in 0 usecs[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.415219] [drm] ib test on ring 3 succeeded in 0 usecs[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.415924] [drm] radeon atom DIG backlight initialized[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.415929] [drm] Radeon Display Connectors[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.415932] [drm] Connector 0:[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.415934] [drm]   DP-1[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.415936] [drm]   HPD2[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.415939] [drm]   DDC: 0x7e60 0x7e60 0x7e64 0x7e64 0x7e68 0x7e68 0x7e6c 0x7e6c[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.415943] [drm]   Encoders:[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.415945] [drm]     DFP1: INTERNAL_UNIPHY[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.415947] [drm] Connector 1:[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.415949] [drm]   eDP-1[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.415950] [drm]   HPD3[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.415953] [drm]   DDC: 0x7e20 0x7e20 0x7e24 0x7e24 0x7e28 0x7e28 0x7e2c 0x7e2c[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.415956] [drm]   Encoders:[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.415958] [drm]     LCD1: INTERNAL_UNIPHY[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.415960] [drm] Connector 2:[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.415962] [drm]   VGA-1[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.415964] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.415967] [drm]   Encoders:[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.415969] [drm]     CRT1: INTERNAL_KLDSCP_DAC1[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.564330] [drm] fb mappable at 0xC0241000[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.564333] [drm] vram apper at 0xC0000000[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.564334] [drm] size 14745600[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.564336] [drm] fb depth is 24[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.564337] [drm]    pitch is 10240[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.564592] fbcon: radeondrmfb (fb0) is primary device[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.618375] radeon 0000:01:00.0: fb0: radeondrmfb frame buffer device[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.618395] radeon 0000:01:00.0: registered panic notifier[/COLOR][/SIZE][/FONT]
[FONT=Menlo][SIZE=3][COLOR=#ff0000][    2.620248] [drm] Initialized radeon 2.39.0 20080528 for 0000:01:00.0 on minor 0
[/COLOR][/SIZE][/FONT]
```

---

### Post by ryan162 on 2015-06-05
After more investigation, I beginning to wonder if it's inability to utilize the display on startup is related to either the resolution of the display not being supported by the org radeon driver (2560x1440)

or it's the proprietary 2-way DisplayPort connection utilized in the iMac that is causing problems. 

Theoretically, there should be some workaround since I'm able to use the display as desired with "nomodeset" enabled, but I'm not sure how to troubleshoot it. 

I have a hunch that if I had another display which took a MiniDisplayPort input and connected it to the iMac, the second display would function properly....

---

