---
title: "Either I'm deaf or sound isnt working"
date: 2005-07-27
forum: Absolute Beginner Talk
---

### Post by ubuntuvirgin on 2005-07-27
Hi folks , 

Looks like I have a problem a few others are having . I just dont understand how to fix it  :???: 

Heres my results :

snd_intel8x0           29984  1
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  0
snd_mixer_oss          16768  1 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  1 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm


No idea what any of that lot means or even if it will help. The chipset is an onboard sis on a PcChips M848 A Mobo

In volume preferences i have a choice of SIS S17012 (Alsa Mixer) or a C-Media CMI9761 (OS MIxer) , selecting either does nothing. 

When i insert a CD , music player starts and displays the name of the track but clicking on play does nothing . (No error messages)


Any ideas plz folks ? 


thanks 

 ](*,)

---

### Post by Shiven on 2005-07-27
could be that your mixer devices are muted, try this:

sudo alsamixer

at the top it will give you some information whether the specified channel is muted.

does rhythmbox (music player) actually play the file (the bar to the top right moving)?...

because that could be something else.

---

### Post by ubuntuvirgin on 2005-07-27
Hi , 
all are max'ed out volume wise. 

When entering a CD the player recognises the CD as it tells methe CD title in the box , but clicking on play does nothing. The player doesnt crash and responds as it should when i close it down.

Hope that helps 

thanx for you input

---

