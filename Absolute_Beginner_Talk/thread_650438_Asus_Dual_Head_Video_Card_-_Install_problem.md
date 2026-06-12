---
title: "Asus Dual Head Video Card - Install problem"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by paulbuk on 2007-12-26
Hello people,
I'm having a problem with a nu-build for a dual system winXP and Ubuntu (hardy) running an Asus EN6200TC512 Dual-head Video Card (V/C) (powered by nVidia GeForce 6200) and being a new Ubuntu *nix 'virgin' I'm stumped at the mo as to which way to move next to get the Asus V/C to work dual headed in Ubuntu Studio. The head works aok in WinXP so I presume it's a Ubuntu prob. I've scanned these forums for some similiar prob but then thinks it's an Asus model problem.
Also, the system (hardy) restricted drivers says there are no drivers and I've scanned the Asus website, but no Linux drivers.

FYI, the comp build is for a dedicated music DAW using Ardour and I'm keen to keep it clean and away from the internet so I can't access auto upgrades via Linux but can do so via a 'dirty' older winXP, which is networked to the *nix box.
I'm running an Asus M2N-E SLI MoBo with an AMD AM2 4.8 dual core.

Any help on getting the dual-head V/C working is much appreciated. I'm excited about Ubuntu and it's audio prospects it's a lovely interface.
Regards

Paul B,
UK

---

### Post by overdrank on 2007-12-26
> **paulbuk said:**
> Hello people,
I'm having a problem with a nu-build for a dual system winXP and Ubuntu (hardy) running an Asus EN6200TC512 Dual-head Video Card (V/C) (powered by nVidia GeForce 6200) and being a new Ubuntu *nix 'virgin' I'm stumped at the mo as to which way to move next to get the Asus V/C to work dual headed in Ubuntu Studio. The head works aok in WinXP so I presume it's a Ubuntu prob. I've scanned these forums for some similiar prob but then thinks it's an Asus model problem.
Also, the system (hardy) restricted drivers says there are no drivers and I've scanned the Asus website, but no Linux drivers.

FYI, the comp build is for a dedicated music DAW using Ardour and I'm keen to keep it clean and away from the internet so I can't access auto upgrades via Linux but can do so via a 'dirty' older winXP, which is networked to the *nix box.
I'm running an Asus M2N-E SLI MoBo with an AMD AM2 4.8 dual core.

Any help on getting the dual-head V/C working is much appreciated. I'm excited about Ubuntu and it's audio prospects it's a lovely interface.
Regards

Paul B,
UK

HI and I installed hardy the other day on a nvidia 6100 and had a little trouble with the drivers. If you search synaptic manager (located under system, administration) for nvidia. Then I believe it is the nvidia-glx-new and install it. I had to reconfigure my xorg a couple of times but that may have been my system. Then you can use the command ```
gksudo nvidia-settings
``` and use twinview to set up the dual monitors. Hope this helps. Good luck!

---

### Post by paulbuk on 2007-12-29
Thank you for your reply. I have now solved this issue with your assistance, but would like to bring some points to the attention for others.

Asus/NVidia dual head PCI-e card
The problem appeared to stem from me not allowing auto updates to d/l the drivers from the Ubuntu repositories online (I either ignored this or chose on installation,  to deselect it, probably because I'm building a music DAW with winXP on the sata drives and ideally wanted no internet on the DAW).
So although the NVidia card worked, the only had one monitor with the message 'out of range' on the righthand side one.
I suggest anyone with a similar problem check the auto updates are selected 'on' from the "software sources" under administration. Once I did this the NVidia updates installed and after a re-boot, I had two monitors communicating.

You will need  to use Terminal (from accessories) to make commands and I found that the X-Config also loaded with the NVidia tool to make the necessary "Twinview" setup in the X-Config tool. Once I saved it, I had an extended desktop across 2*17" TFT's.

I have a lot to learn in *nix flavour, but Ubuntu is very nice and I'm sure it will go far.
Good luck

Paul B,
Livercool, UK.

---

