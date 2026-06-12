---
title: "Cant start x-server after nvidia driver update?"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by nyxynyx on 2006-12-17
hello, i have a problem after the auto update for nvidia drivers i think. I'm using 6600GT AGP. When i boot, after that long list of msgs that scroll past the screen, i get a blue screen saying x server cant start. Here;s something from the error msg:

(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
(EE) xf860OpenSerial: Cannot open device /dev/wacom No suck file or directory.
...
....
Fatal server error:
no GLX visuals avaliable

I had something similar before, then i edited xorg.conf replacing 'Nvidia' with 'nv'. Then i typed startx and it ran. Then i reset the system and i got the error above. Before all these problems came, i updated beryl using synaptic from beryl's unofficial ubuntu repos.


Thanks for any help!!

---

### Post by maxamillion on 2006-12-17
make sure the "Nvidia" is actually "nvidia" ... all lower case

---

### Post by nyxynyx on 2006-12-17
thnx maxamillion! i typed in 'nvidia' instead of 'Nvidia' and i still cant start x. It says

FATAL: Module nvidia not found.
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  ***Aborting***
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
XIO: fatal IO error 104 (Connection reset by peer) on X server ":0,0 after 0 requests(0 known processed) with 0 events remaining.

Btw, I have 2 monitors connected to the video card, but my ubuntu is not set up for dual monitor.

---

### Post by nyxynyx on 2006-12-17
Btw, i used 'nv' instead of 'nvidia' and did startx and it runs! However, after restarting my computer, i get the error again... This keeps happening, help pls! Thanks!

---

### Post by maxamillion on 2006-12-17
the dual monitor shouldn't matter for now, all that it would do is just display on one monitor until you configure it otherwise.

it claims that it is failing to find the nvidia module. try doing this:

sudo aptitude update
sudo aptitude dist-upgrade
sudo aptitude update
sudo aptitude install nvidia-glx

enter each command one at a time at the command line, its a little redundant but it will double check everything, tell me if the last one installs anything or says its already at its newest version. I am thinking there might be an inconsistency with a kernel update or something of the sort and would like to rule that option out.

---

### Post by nyxynyx on 2006-12-17
Thanks again maxamillion. I did what you told me to, and nothing required updating. However, i still get the same error. Seems that i have to start x from the cmd prompt. I get the blue error screen when x starts itself automatically... What else should i do?

EDIT: The blue error screen says(same as before)

Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?

<Yes> <No>

(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
...
....
Fatal server error:
no GLX visuals avalia

---

### Post by dannystaple on 2006-12-17
> **nyxynyx said:**
> Thanks again maxamillion. I did what you told me to, and nothing required updating. However, i still get the same error. Seems that i have to start x from the cmd prompt. I get the blue error screen when x starts itself automatically... What else should i do?

EDIT: The blue error screen says(same as before)

Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?

<Yes> <No>

(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
...
....
Fatal server error:
no GLX visuals avalia
Okay - what happens if you type the following:
```
lsmod | grep -i nv
```

---

### Post by nyxynyx on 2006-12-17
hi dannystaple! I got the following printed on the screen:

nvidia 4551028 0
i2c_core 21904 3 ic2_acpi_ec,nvidia,i2c_nforce2
agpgart 34888 2 nvidia,nvidia_agp
sata_nv 9732 0
libata 78992 2 sata_nv,sata_sil

---

### Post by dannystaple on 2006-12-17
> **nyxynyx said:**
> hi dannystaple! I got the following printed on the screen:

nvidia 4551028 0
i2c_core 21904 3 ic2_acpi_ec,nvidia,i2c_nforce2
agpgart 34888 2 nvidia,nvidia_agp
sata_nv 9732 0
libata 78992 2 sata_nv,sata_sil
Thanks, okay, what is the device section of your /etc/X11/xorg.conf file?

That is everything between ```
Section "Device"
```
and the next ```
EndSection
```. Thanks again.

---

### Post by nyxynyx on 2006-12-17
Thanks dannystaple!

Heres what i have

Identifier "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600GT]"
Driver "nv"

---

### Post by dannystaple on 2006-12-17
> **nyxynyx said:**
> Thanks dannystaple!

Heres what i have

Identifier "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600GT]"
Driver "nv"

Okay, that should be ```
Driver "nvidia"
```
What are the contents of ```
Section "Module"
```

---

### Post by nyxynyx on 2006-12-17
Section "Module"
Load "i2c"
Load "bitmap"
Load "dcc"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
Load "dbe"

EndSection

---

### Post by dannystaple on 2006-12-17
> **nyxynyx said:**
> Section "Module"
Load "i2c"
Load "bitmap"
Load "dcc"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
Load "dbe"

EndSection
Hmm - that seems the same as mine. So what happened when you changed "nv" for "nvidia" in the device section?

---

### Post by nyxynyx on 2006-12-17
Omg dannystaple it works lol. Really wierd, it didnt work with 'nvidia' before... except that now it displays on the other monitor... I restarted a few times just to be sure its working. Thanks dannystaple & maxamillion!

---

