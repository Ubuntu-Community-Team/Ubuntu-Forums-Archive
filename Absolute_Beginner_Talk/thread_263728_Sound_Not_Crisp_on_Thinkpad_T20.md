---
title: "Sound Not Crisp on Thinkpad T20"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by ishift on 2006-09-23
hi,

i have sound on my thinkpad t20, but as the volume increases, the crispness of the sound gets more and more crappy.

for some songs, the sound quality is good. for the majority, however, it's bad. i mean, i can't put it up loud. the problem only arises when i'm playing mp3s.

i tried using vlc, amarok, xmms, and rhythmbox. it's the same. what could be the problem?

thanks!

---

### Post by iluminate on 2006-09-23
Hi,

Are you using external speakers or listening with the built in speaker in Thinkpad?

---

### Post by ishift on 2006-09-23
built-in speakers

---

### Post by iluminate on 2006-09-23
As far I know, the built in speakers have never been famous for beeing a audiophiles first choice of speakers. :D 
No matter what OS you install on your thinkpad, the sound will still be )(¤#)=%#)/!
Use external with a descent amp!

---

### Post by nts on 2006-09-23
does this ocurr with all file types? or just certain ones?

---

### Post by ishift on 2006-09-23
> **nts said:**
> does this ocurr with all file types? or just certain ones?

from what i understand, only mp3s.

---

### Post by nts on 2006-09-23
I would check what bit-rate they were captured at...

---

### Post by ishift on 2006-09-23
> **iluminate said:**
> As far I know, the built in speakers have never been famous for beeing a audiophiles first choice of speakers. :D 
No matter what OS you install on your thinkpad, the sound will still be )(¤#)=%#)/!
Use external with a descent amp!

the thing is, they worked well when i had windows. i was expecting similar sound performance.

> **nts said:**
> I would check what bit-rate they were captured at...

hmm, good point. they range from 160-221 kbps. it's not a specific bit-rate that sounds bad. i think it's a range. i'll provide a more detailed answer later, but i think this suffices for now.

---

### Post by nts on 2006-09-23
have you tried different media players?

---

### Post by ishift on 2006-09-23
> **nts said:**
> have you tried different media players?

yea..

> **ishift said:**
> 
i tried using vlc, amarok, xmms, and rhythmbox.

---

### Post by nts on 2006-09-23
> **ishift said:**
> yea..

sorry, my bad.

---

### Post by nts on 2006-09-23
have you checked that you have the latest drivers installedfor the sound card? or maybe if you need an older version of the sound card driver...

---

### Post by ishift on 2006-09-23
lol...it's all good.

i still don't understand why it's not as crisp as it should be. the same files play fine in other computers.

and, yea, i think i do have the latest drivers installed. the card and driver are:

Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion]

---

### Post by nts on 2006-09-23
> **ishift said:**
> lol...it's all good.

i still don't understand why it's not as crisp as it should be. the same files play fine in other computers.

and, yea, i think i do have the latest drivers installed. the card and driver are:

Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion]

so you have checked with older/newer versions of the driver?

---

### Post by ishift on 2006-09-23
i'm not entirely sure. i just got that info from the device manager.

---

### Post by insane_alien on 2006-09-23
ahh i know this problem. its easy to fix.

go to the terminal and type "alsamixer" without the quotes obviously

then using the arrow keys, shimmy over to "PCM" and then use the down arrow to take it down to around 77 (lower if it still sounds distorted)

it should be fixed then. you may need to do it again for various reasons that i haven't quite sussed out yet

---

### Post by nts on 2006-09-23
Back of the net!

[http://talisman.mv.com/laptop.html](http://talisman.mv.com/laptop.html)

I quote:

The sound chip is a CrystalClear SoundFusion Audio Accelerator (CS4614/22/24). This does not seem to be support by the OSS modules in RedHat, however the ALSA Project does have support for this chip. Download the ALSA drivers, uncompress them, change to the ALSA directory and run "./configure --with-cards=cs461x", then a "make", and "make install". From there the module(s) can be inserted using insmod or modprobe. It seems that this sound card can't handle the PCI Bus Power Management feature, so in order to get this working properly you'll need to disable that. From the ThinkPad setup (F1 after turning it on), choose 'config' and then 'power', scroll to the bottom and disable the 'PCI Bus Power Management' feature. I can now play mp3 etc... without any trouble, here's the /etc/conf.modules portion for Alsa:

alias char-major-116 snd
alias char-major-14 soundcore
alias snd-card-0 snd-card-cs461x
alias sound-slot-0 snd-card-0
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-12 snd-pcm-oss

---

### Post by ishift on 2006-09-24
whoa. i leave for one night and, bam, i get two solutions! w00t.

i'll try them out as soon as i can. i'll let you know what happens.

thanks a lot, guys!

---

### Post by happy-and-lost on 2006-09-24
I had that problem with my laptop's sound card.

Then I found Banshee media player :D

---

