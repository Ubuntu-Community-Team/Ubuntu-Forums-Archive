---
title: "Had sound now lost it"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by mastergunner on 2008-03-22
Guys I have had sound for a while and now I dont. Can somebody give me a hand? I am running Kubuntu 7.10 on my desktop.

---

### Post by aerisismine on 2008-03-22
had the same problem, haven't fixed it yet.

Go to a terminal and type alsamixer, paste results.

---

### Post by erginemr on 2008-03-22
And paste the following ones as well:
```
aplay -l
```
```
cat /proc/asound/cards
```
```
lspci | grep -i audio
```

---

### Post by mastergunner on 2008-03-22
This is alsamixer:

 Card: NVidia CK804                                                           &#9474;
&#9474; Chip: Realtek ALC850 rev 0                                                   &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master [dB gain=0.00, 0.00]  

All of the volumes are maxed.

---

### Post by mastergunner on 2008-03-22
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by mastergunner on 2008-03-22
cat /proc/asound/cards
 0 [CK804          ]: NFORCE - NVidia CK804
                      NVidia CK804 with ALC850 at irq 22
 1 [UART           ]: MPU-401 UART - MPU-401 UART
                      MPU-401 UART at 0x330, irq 10

---

### Post by mastergunner on 2008-03-22
lspci | grep -i audio
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)

---

### Post by erginemr on 2008-03-23
Unfortunately it will be a second-hand suggestion, as I didn't have such a problem myself in my box, so I can only suggest you to follow this ongoing thread:
[http://ubuntuforums.org/showthread.php?t=732197](http://ubuntuforums.org/showthread.php?t=732197)

especially the external links given therein (in post #3, 7 & 8)  by me and oedha to seek for a solution for your problem. Good luck...

---

### Post by mastergunner on 2008-03-23
erginemr are you saying you do not know what is wrong or you do know? Could you tell me?

---

### Post by erginemr on 2008-03-23
What I am saying is that I didn't experience any sound issue as my sound card chip is completely different than yours. But I have been following the Ubuntu forums for quite sime time and know that your card (which may be considered as falling into the HDA gr&#305;oup) is a source of trouble for many, many Ubunteros, and the links I have suggested contain success stories for the owners of those cards.

So, long story short, since no one else seems to have noticed your postings here, I have decided to take the initiative and did my best to point you to the right direction.

---

### Post by erginemr on 2008-03-23
Another path is to recompile ALSA for your kernel following this howto:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

but its is way more advanced and more complicated than the links I gave above, so should be considered as a last resort.

---

### Post by erginemr on 2008-03-24
Please refer to here for screenshots on respective sections of Synaptic to enable backports, and for very easy scripts by a fellow Ubuntero to recompile ALSA to the latest version:
[http://ubuntuforums.org/showpost.php?p=4574654&postcount=10](http://ubuntuforums.org/showpost.php?p=4574654&postcount=10)

---

