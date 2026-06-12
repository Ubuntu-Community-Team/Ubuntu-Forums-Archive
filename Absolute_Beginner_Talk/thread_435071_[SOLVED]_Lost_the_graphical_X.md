---
title: "[SOLVED] Lost the graphical X"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by forestpixie on 2007-05-06
Help - please!!!
Got Ubuntu installed and everything was going really well and then - I tried to get the the S-Video output working on my graphics card and it's all gone horribly wrong :)

I followed the instructions in a thread by tseliot's HOW TO NVIDIA TV OUT - including backing up the xorg.conf

Glad about that at least!

when i rebooted i lost the graphic display, found a thread to replace xorg.conf with xorg.conf.backup

it said
cd /etc/x11/
dir xorg*.*
sudo mv cp xorg.conf.backup xorg.conf

and i got "no such directory" after the cd /etc/x11/

i was at my kevin@kevin-desktop:$ prompt 

question is how to get to right place in directory structure using to command line to replace xorg.conf with it's backup?

Had to go back to windows to do this - really want to get back to ubuntu now i've got it working

---

### Post by taurus on 2007-05-06
It's a capital **X**.

```
sudo mv /etc/**X**11/xorg.conf.backup /etc/**X**11/xorg.conf
```

---

### Post by forestpixie on 2007-05-06
thanks i'll try that - hope to thank again from within ubuntu - didn't realise that it was all case sensistive

---

### Post by forestpixie on 2007-05-06
Thanks and thrice thanks - back in Ubuntu - phew

i'll leave trying things out for a while - up until that point I was very pleased with getting everything to work as I wanted even being able to save and read from my windows partitions

tried to get it sorted reading the forum threads but sometimes better to stop and ask

one grateful newbie

---

