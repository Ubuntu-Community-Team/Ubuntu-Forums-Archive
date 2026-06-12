---
title: "Problems with installing ubuntu"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by yetterben on 2006-07-02
:(  hello all,

new to linux and cant even install the program or run the live cd :(

this is the xserver error i get:no device section for instance Bus id pci 2:11:0 nodevice detected:


my card is here and windows picks it up with the same id so i dont understand
my onboard is disabled in bios and that wouldnt even work :(

have run apt-get nvidia-glx and so forth but nothing seems to work. please help thanx

Nvidia fx5200

---

### Post by yetterben on 2006-07-02
i do also have a PCMCIA fail on boot up?

---

### Post by Apple 101 on 2006-07-03
Try reconfiguring your xorg.conf file:  *sudo dpkg-reconfigure xserver-xorg*

---

### Post by HereInOz on 2006-07-03
As far as I know, you will get the PCMCIA fail on boot if you have no PCMCIA devices installed. I get the same thing on a desktop.

Cheers,

Alan

---

### Post by yetterben on 2006-07-03
ive done that to no avail i do get this error when its loading in the begining
hw randowm:FAILED rng not detected

---

### Post by tseliot on 2006-07-03
Please post the output of this command:
```
lspci
```

and your entire /etc/X11/xorg.conf

---

### Post by yetterben on 2006-07-03
lspci shos my nvidia on the last line. i am running in windows how can i post my files from linux. hand written the only way it dosent even install so i would have to try to load it up again and write it down get back to me

---

### Post by yetterben on 2006-07-03
the conf file is stock until i run dpkg and then the info is changed to nvidia what are you looking for inside of it

---

### Post by yetterben on 2006-07-03
new findings seems ubuntu will run and install on my old pc athlon 900. it is my belief that it is becasue there is no onboard video. this must be my problem on my newer cpu. is there a way to blacklist my onboard and make ubuntu pick up my pci card. its there is lsbci so i dunno ?

clues anyone

---

