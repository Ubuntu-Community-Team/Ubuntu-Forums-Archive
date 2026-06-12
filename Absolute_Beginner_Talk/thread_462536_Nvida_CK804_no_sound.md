---
title: "Nvida CK804 no sound"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by newway on 2007-06-02
ASUS A8N SLI Deluxe motherboard. onboard Audio (nVidia CK804 AC97).
after Installing Ubuntu 7.04 there is no sound whatsoever. 
I've made sure that Volumn control is pushed up and plugged in 
my speaker/headphone in "Front" connector.


lspci output as follow:

 lspci | grep audio
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)

when trying to play Amarok, it is seems everything is working, just no sound whatsoever coming out...

I tried boot from Ubuntu 7.04 and Ubuntu 6.06 live CD also there is no sound...

Is there anything I am missing? Thank you in advance

---

### Post by vwr0527 on 2007-07-20
hey i have the same sound card, same problem.
help please.

EDIT: I had an improperly seated ram chip on my motherboard. Somebody told me this could have damaged the sound chip functionality. Anyone know if thats true?

---

### Post by paganatron on 2007-10-26
Got the same board and exactly the same problem. I installed Kubuntu 7.10 with the same result. No sound! 
Anybody got any ideas??

---

### Post by MunchySnacks on 2007-12-15
bump

same problem no sound on onboard A8N-SLI Deluxe

---

### Post by rollOver on 2007-12-16
Same problem MSI K8N Neo3 motherboard, got as far as determining that I need  alsa intel8x0, is that right? I install this but can't seem to switch ubuntu from NVidia CK804 (the PCI bridge chipset) as the "sound card" how do I blacklist the NVidia? Is that what I need to do? The Intel8x0 is installed but doesn't show in System/Preferences/Sound as an option, just Nvidia CK804 and Realtek neither of which produces sound.

And yes, I have made ceertain that nothing is muted in alsamixer.

---

### Post by tor528 on 2008-01-11
*bump* Same problem, nf4k8ab-rs motherboard.  nForce4 chipset, CK804 audio.

---

### Post by tor528 on 2008-01-11
See the following post:

[http://fedoraforum.org/forum/showthread.php?t=171686](http://fedoraforum.org/forum/showthread.php?t=171686)

> once the front panel connector is removed pins 5 6 and 9 10 must have jumper caps installed otherwise the back audio panel will be disabled

Even though I am using a different motherboard than that user, this piece of advice [SOLVED] my problem.

---

### Post by rollOver on 2008-01-27
> **tor528 said:**
> See the following post:

[http://fedoraforum.org/forum/showthread.php?t=171686](http://fedoraforum.org/forum/showthread.php?t=171686)



Even though I am using a different motherboard than that user, this piece of advice [SOLVED] my problem.

Thanks for this, my motherboard (MSI K8N Neo3) is the same. Explains everything as the last case I had it in had front panel connectors, new one does not. Thanks a million--my last hardware prob solved!

---

### Post by dominik_ap on 2008-01-31
Hey i have the same problem, is somebody reading this post?  Can anyone help us? please...

I dont know what to post here to help you, thanks

---

### Post by rollOver on 2008-01-31
> **dominik_ap said:**
> Hey i have the same problem, is somebody reading this post?  Can anyone help us? please...

I dont know what to post here to help you, thanks

What motherboard are you using?

The jumpers mentioned above solved my problem, sound is working perfectly now without config changes to Ubuntu. (Hardy Heron alpha 3)

---

### Post by dominik_ap on 2008-01-31
Hi i am using DFI NF4-U-SLI, Chipset nVidia nForce 4, and what thing with jumpers can solve it? I had sound before 1 month and when i am using Windows, there is also sound, so it must be in some driver or something what i made bad in ubuntu :)

---

### Post by rollOver on 2008-02-01
> **dominik_ap said:**
> Hi i am using DFI NF4-U-SLI, Chipset nVidia nForce 4, and what thing with jumpers can solve it? I had sound before 1 month and when i am using Windows, there is also sound, so it must be in some driver or something what i made bad in ubuntu :)

You've made NO changes to your hardware config since it was working in Windows? 

In my case I moved the motherboard into a new case, etc. Went from using a sound card to not, when you do this and do not plug into the "front" panel sound connections you must jumper two sets of pins on the MB to route sound to the connectors on the rear of the MB. This is quite counter-intuitive IMHO so I would not have thought to check my MB manual for this "feature."

Once I jumpered these pins my sound worked flawlessly with a "stock" ubuntu install, no changes made to configuration files, etc. I am using an MSI MB (nForce3) and Hardy alpha 3 though so YMMV.
It may be worth checking your MB manual, I haven't heard of DFI and a Google search turned up nothing so I am not sure how to help without more info.:popcorn:

---

### Post by dominik_ap on 2008-02-02
Ok thanks, i am still looking on the google for some help, but nothing, just some people had the same problem like me - there was a sound and once it dissappear and stopped working.

BTW: I dont think it is problem in hardware (so i wont change the jumpers), but thanks for your advice.

---

