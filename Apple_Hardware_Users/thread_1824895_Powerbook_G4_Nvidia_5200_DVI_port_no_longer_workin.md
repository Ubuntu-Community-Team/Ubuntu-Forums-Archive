---
title: "Powerbook G4 Nvidia 5200 DVI port no longer working"
date: 2011-08-14
forum: Apple Hardware Users
---

### Post by BM_Bailey on 2011-08-14
I'm a complete newbie with regards to Ubuntu, but I installed it on my PowerPC Mac Powerbook G4, which is has an NVIDIA Geo Force 5200 monitor/graphics chip (according to the lspci command). Everything is working fine on the computer except for the external monitor port, which had been working fine with OS X. Now the computer can't recognize the monitor; the screen simply goes white for a few moments before saying "no signal." I've tried download and running Nvidia drivers but they don't have any that support the combination of PPC Linux and the Nvidia 5200. I've also seen elsewhere that it is helpful to edit the etc/X11/xorg.config file, but my file has NOTHING in it to be edited. Could anyone please tell me what - if anything - I could paste into the terminal in order to get some kind of workaround. The external monitor in question is a Samsung LCD television. It was previously connected to the same computer and worked fine (though slowly) with OS X. This is important as this computer is - or at least was - permanently connected to my television and used for streaming etc.

I was very excited about this whole open-source thing, but in all honesty, I'm at a complete loss and about to break down and purchase an entirely new Mac if I can't get this thing fixed...

---

### Post by linuxopjemac on 2011-08-14
[http://mac.linux.be/content/xorgconf-file-powerbook-g415-12-lucid-lynx](http://mac.linux.be/content/xorgconf-file-powerbook-g415-12-lucid-lynx)
You might need to add
```
Option "NoInt10" "true"
```
to the Device Section
If it does not work, replace
```
nouveau
```
by
```
nv
```

after downloading the file:
```
sudo mv name_of_file.txt /etc/X11/xorg.conf
```
reboot

good luck

---

### Post by BM_Bailey on 2011-08-14
Hi! Thanks for your help. I did everything you said but now, when I reboot (with the external monitor plugged in), it lights up white - though for a longer time than it did before - before saying no signal and going black, only now, the Powerbook's monitor also goes black.
When I did it the first time (with the unmodified txt), the computer went into low graphics mode. It gave me these errors:

(EE) Failed to load module "nouveau" (module does not exist, 0)
(EE) No drivers available.

If I substitute nv for nouveau it reboots regularly but does not detect the TV screen.
Thanks again for your help!

---

### Post by linuxopjemac on 2011-08-14
I am not sure whether nv is able to do TV.
Are you sure that the nouveau driver is installed ?
sudo apt-get install xserver-xorg-video-nouveau

---

### Post by BM_Bailey on 2011-08-14
Thanks for your help (again)!

I tried everything you said and it seemed to work best the first time, without modification. The screen on the Powerbook became scrambled as though it was trying to find the correct configuration with the monitor, but then ultimately failed. The computer did, however, detect the monitor! It just couldn't seem to sync up with it. I tried several different resolutions and refresh rates but none of them seemed to make any difference. The computer was previously working with the television with no problem, so there isn't some kind of bad hardware interaction; I just can't seem to get them to "resolve their differences."

Please let me know if there's anything else I should try. Otherwise, thank you very much for your assistance. I'm afraid Steve Jobs may have won this round... :(

---

### Post by linuxopjemac on 2011-08-15
you might need to add modelines, you can find out the specific modelines with cvt.
What kind of resolution are your going for and at which frequency? Do you know the specs of that TV ?

---

