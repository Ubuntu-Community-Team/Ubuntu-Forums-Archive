---
title: "Sound lost on 10.10 after kernel upgrade"
date: 2012-02-11
forum: Asus Ubuntu Support (CLOSED)
---

### Post by grolain on 2012-02-11
Hello,

I have an Asus P50IJ, sound card is Intel 82801I.
I installed Ubuntu 10.10. The sound worked perfectly, until I upgraded the kernel in December 2011.
Since then, I have no sound. I searched on several forums, without success.

Here are some details : 

$ uname -a
Linux asus 2.6.35-32-generic #64-Ubuntu SMP Mon Jan 2 23:31:33 UTC 2012 i686 GNU/Linux

$ lspci -v | grep -A8 -i "audio"
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Santa Cruz Operation Device 1043
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at fe9f4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: oss_hdaudio
	Kernel modules: snd-hda-intel

$ cat /proc/asound
cat: /proc/asound: No such file or directory

$ aplay -l
aplay: device_list:235:  no soundcards found...

$ sudo apt-get install linux-restricted-modules-`uname -r` linux-generic
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
E: Impossible de trouver le paquet linux-restricted-modules-2.6.35-32-generic
E: Impossible de trouver de paquet correspondant à l'expression rationnelle «*linux-restricted-modules-2.6.35-32-generic*»

:confused:
I need some help !!
Thanks

---

### Post by grolain on 2012-02-12
Solved !!

I was quite easy :

$ sudo modprobe snd-hda-intel

and add a line with snd-hda-intel at the end of /etc/modules

Now it works !
:D

---

