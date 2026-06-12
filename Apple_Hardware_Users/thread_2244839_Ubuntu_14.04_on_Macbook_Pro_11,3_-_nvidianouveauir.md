---
title: "Ubuntu 14.04 on Macbook Pro 11,3 - nvidia/nouveau/iris issues"
date: 2014-09-19
forum: Apple Hardware Users
---

### Post by zyghom on 2014-09-19
Hi there,

I have installed Ubuntu 14.04-MAC on freshly new Mackbook Pro 11,3 (15", SSD, Iris/Nvidia) with the command: ubiquity -b (to avoid installation of GRUB).
Everything almost works - except camera.
Few sssues:
1-temperature - it is quite hot - related rather to graphics I believe
2-suspend - after opening the lid it is hanging - not possible to enter password in login window
3-video - this is the biggest issue
Although in "Software & Updates" you can choose among 3 drivers: 2 nvidia and 1 nouveau, it is always nouveau in use:
```

09:45:43 papio@mb15papio:~$ dpkg -l | grep -i nvid
ii  bbswitch-dkms                                               0.7-2ubuntu1                                        amd64        Interface for toggling the power on nVidia Optimus video cards
ii  libcuda1-331                                                331.38-0ubuntu7.1                                   amd64        NVIDIA CUDA runtime library
rc  libcuda1-331-updates                                        331.38-0ubuntu7.1                                   amd64        NVIDIA CUDA runtime library
ii  nvidia-331                                                  331.38-0ubuntu7.1                                   amd64        NVIDIA binary driver - version 331.38
rc  nvidia-331-updates                                          331.38-0ubuntu7.1                                   amd64        NVIDIA binary driver - version 331.38
ii  nvidia-libopencl1-331                                       331.38-0ubuntu7.1                                   amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-opencl-icd-331                                       331.38-0ubuntu7.1                                   amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                                0.6.2                                               amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                             331.20-0ubuntu8                                     amd64        Tool for configuring the NVIDIA graphics driver
09:45:45 papio@mb15papio:~$ lsmod | grep nou
nouveau              1097199  3 
mxm_wmi                13021  1 nouveau
wmi                    19177  2 mxm_wmi,nouveau
i2c_algo_bit           13413  1 nouveau
ttm                    85115  1 nouveau
drm_kms_helper         53081  1 nouveau
drm                   303102  5 ttm,drm_kms_helper,nouveau
video                  19476  2 nouveau,apple_gmux
09:45:52 papio@mb15papio:~$ 

```

Few questions:
1-what to change and where to get nvidia working with binary driver?
2-how to change nvidia to iris 
3-how to decrease the temperature:
```

10:11:45 papio@mb15papio:~$ sensors
nouveau-pci-0100
Adapter: PCI adapter
temp1:        +58.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +62.0°C  (high = +84.0°C, crit = +100.0°C)
Core 0:         +61.0°C  (high = +84.0°C, crit = +100.0°C)
Core 1:         +59.0°C  (high = +84.0°C, crit = +100.0°C)
Core 2:         +62.0°C  (high = +84.0°C, crit = +100.0°C)
Core 3:         +59.0°C  (high = +84.0°C, crit = +100.0°C)

applesmc-isa-0300
Adapter: ISA adapter
Left side  : 2155 RPM  (min = 2160 RPM, max = 6156 RPM)
Right side : 1997 RPM  (min = 2000 RPM, max = 5700 RPM)
TB0T:         +34.0°C  
TB1T:         +34.0°C  
TB2T:         +32.8°C  
TBXT:         +34.0°C  
TC0E:         +63.0°C  
TC0F:         +64.5°C  
TC0P:         +54.8°C  
TC1C:         +60.0°C  
TC2C:         +60.0°C  
TC3C:         +62.0°C  
TC4C:         +58.0°C  
TCGC:         +60.0°C  
TCSA:         +62.0°C  
TCTD:          -0.2°C  
TCXC:         +62.2°C  
TG0D:         +57.5°C  
TG0P:         +55.2°C  
TG1D:         +64.0°C  
TG1F:         +63.8°C  
TG1d:         +58.0°C  
TH0A:         +38.8°C  
TH0B:         +38.8°C  
TH0F:         -42.2°C  
TH0R:         -42.2°C  

10:11:50 papio@mb15papio:~$ 

```

I've gone through many howtos but cannot find the right answer
Thanks

---

### Post by este.el.paz on 2014-09-19
> **zyghom said:**
> Hi there,

I have installed Ubuntu 14.04-MAC on freshly new Mackbook Pro 11,3 (15", SSD, Iris/Nvidia) with the command: ubiquity -b (to avoid installation of GRUB).
Everything almost works - except camera.
Few sssues:
1-temperature - it is quite hot - related rather to graphics I believe
2-suspend - after opening the lid it is hanging - not possible to enter password in login window
3-video - this is the biggest issue
Although in "Software & Updates" you can choose among 3 drivers: 2 nvidia and 1 nouveau, it is always nouveau in use:
Few questions:
1-what to change and where to get nvidia working with binary driver?
2-how to change nvidia to iris 
3-how to decrease the temperature:


I've gone through many howtos but cannot find the right answer
Thanks

@zyghom:

I guess that answers the question as to whether the MAC iso has the "mactel" repository installed for the fan control items . . . but there is a sticky at the top of the page for the issues of running hot on Mac . . . .  I also have had a thread here on getting the fan/temp control issues straightened out, so you should be able to search that out for the step by step details . . . .  I didn't mess around with fine tuning it . . . but it can be . . . .

Usually for MBPro it is "Nvidia" that you would want, that used to be handled in the "additional drivers" app, but now seems to be in Software Updater . . . which I may have had an issue with in my PPC iBook . . . so I can't exactly help with that.  When I did my 14.04 install on my MBPro "Additional drivers" was still working and it was easy enough to add the Nvidia driver and wifi broadcom stuff . . . .  It looks like you would have the CLI skills to do it that way, or perhaps in Synaptics????

e.e.p.

---

### Post by zyghom on 2014-09-19
thank you e.e.p - let me look further
the funny think is: when I first installed Ubu it was nouveau, then I changed to nvidia (one of that 2) and for 1 time I saw nvidia-settings working
next reboot it never worked anymore - always nouveau loaded 
there is no /etc/X11/xorg.conf anymore in Ubu so maybe this would be the way of forcing nvidia driver to load?

---

### Post by este.el.paz on 2014-09-19
> **zyghom said:**
> thank you e.e.p - let me look further
the funny think is: when I first installed Ubu it was nouveau, then I changed to nvidia (one of that 2) and for 1 time I saw nvidia-settings working
next reboot it never worked anymore - always nouveau loaded 
there is no /etc/X11/xorg.conf anymore in Ubu so maybe this would be the way of forcing nvidia driver to load?

@z:

You should find something about "macfancntrl" . . . something like that, the fellow who seemed to have that one aced is "mike braxton"???  something like that, so if you see his thread(s) or mine, that should get you going on adding the "mactel repository" stuff.

But, right, there may not be an xorg.conf file, although in PPC for 14.04 I had to "borrow" one to get it to work; so you could try to do that and pick the driver . . . otherwise, perhaps if it's working it might not "matter"????  Perhaps looking again through the "Software Updater" app and see if somewhere in there you might be able to select the video driver . . . in the GUI . . . ????  That is also where you can add the "mactel ppa" stuff, etc.

e.e.p.

---

### Post by zyghom on 2014-10-11
macfanctrl did the job regarding temperature - thanks mate

---

### Post by este.el.paz on 2014-10-11
> **zyghom said:**
> macfanctrl did the job regarding temperature - thanks mate

@zyghom:

Great, glad to hear that, thanks for the update as well.

e.e.p.

---

