---
title: "how to install driver for laptop hardwares"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by clark0820 on 2006-12-30
Hi

       I'm beginner of ubuntu and I really don't know too much about computers. My window crash so I designed to switch to Ubuntu. Wonder if anyone can help me about installing hardware driver for laptop. I installed Ubuntu 6.06LTS.

       I have a NEC Versa P8000 laptop. I try to browse around different webpages but I still don't know a way to install driver for my wireless card(right now it has a signal bar show reception, but even though it show signal, I still can't get online, can only get online now with ethernet card) and my sound card(right now no sound at all).

      My laptop has a ATI IXP AC97 audio controller, and atheros AR5212 wireless card. Hope someone show me some steps or let me know which is the best webpage to see how to install drivers. Thank you very much.

Clark

---

### Post by Sef on 2006-12-30
> AC97 audio controller

Open the Terminal (Applications > Accessories > Terminal)

then type

```
gksudo gedit /etc/modprobe.d/alsa-base
```

Then you should see  something like this at the bottom:

> # Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 modprobe --ignore-install saa7134 $CMDLINE_OPTS && { modprobe -Qb saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2

Comment out the next to last line.  To comment out, just put a # in front of the line.  A # means don't read me.  Then change the end number in the last line from a 2 to a 0.

It should look like this now:

> # Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 modprobe --ignore-install saa7134 $CMDLINE_OPTS && { modprobe -Qb saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
# options snd-intel8x0m index=-2
options snd-via82xx-modem index=-0 

---

### Post by clark0820 on 2006-12-30
I tried and edit the alsa, but it still doesn't have sound (even after I restart my computer). Wonder if there re other methods. thanks.

---

### Post by clark0820 on 2006-12-30
wonder if anyone can solve the wireless problem??

yeah, the sound problem is still unresolved. Please help!!

Thanks a million!!!

---

### Post by macogw on 2006-12-30
[http://www.ubuntuforums.org/showthread.php?t=38972](http://www.ubuntuforums.org/showthread.php?t=38972)
That's a howto for your wireless card.

---

