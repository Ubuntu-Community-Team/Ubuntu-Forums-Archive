---
title: "Changing default sound card NVIDIA to Soundblaster Live"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by Karnex420 on 2006-10-13
Must be a switch somewhere I'm forgetting or I don't understand what is being said.  
Could someone tell me how to do this?  I've done what is written in many posts for other people.
I have Dapper and am new to linux.

---

### Post by PriceChild on 2006-10-13
System>preferences>sound

Sounds tab, choose it at the bottom.

---

### Post by Karnex420 on 2006-10-13
Thanks Pricechild, but it wont stick.  When I close the sound preference window it reverts to nvidia.

---

### Post by Gokudan on 2006-10-13
Hi!

First you need to disable the on board sound on the mobo BIOS, then u can expect linux/windows not to detect the onboard sound.

Att.
Gokudan.

---

### Post by Karnex420 on 2006-10-13
Hi Gokudan, 
I can't see my sound card on bios.  Is mobu different than the normal bios display or am I not recognising a code that represents soundcards on my computer?  You don't mean to disable the video card on bios do you?

---

### Post by Karnex420 on 2006-10-14
So I see from somewhere else they said this.  I will post it here for others to see though I haven't figured this out yet so back up your system before you apply this, and I quote:

""""""""""FloSynergy
March 23rd, 2006, 10:21 PM
hi there,

i've got the same issue...running audigy 2 zs pcmcia soundcard on kubuntu, on an asus a2 notebook.

kmixer recognises the sound card, but i'm not sure how to get it to ignore the onboard card (fried!) and route to the pcmcia...

the onboard sound card doesn't show up in the bios.....can't disable it there.

any ideas?

flo
FarEast
March 27th, 2006, 04:58 PM
Hi;) ,

If you have 2 sound cards or more and want to define one of them as primary...

1. Execute 'lsmod | grep snd' to know the modules which drive them.

2. Edit(or create) /etc/modprobe.d/sound, for example, as follows:

options snd-emu10k1 index=0
options snd-ymfpci index=1

3. Execute 'sudo update-modules' and 'sudo /etc/init.d/alsa-utils restart'.

I hope this helps."""""""""    End Quote



This site I googled might help me too.
[http://whp-java.extweb.hp.com/ewfrf/wc/document?docname=bph07154&lc=en&cc=us&dlc=&product=59963](http://whp-java.extweb.hp.com/ewfrf/wc/document?docname=bph07154&lc=en&cc=us&dlc=&product=59963)

HP and Compaq Desktop PCs - Resolving Sound Problems
Files and settings for your sound card may have changed and could be ... Press the F5 key, select Yes, and then press F10 to save the default BIOS settings. ...
h10025.www1.hp.com/ewfrf/wc/document?lc=en&cc=us&dlc=&product=92985&docname=bph07154 - Similar pages

    HP and Compaq Desktop PCs - Resolving Sound Problems
    Figure 5: Sound connectors on sound card. If the PC has sound connectors in both locations the on-board sound setting should be Disabled. To enter the BIOS, ...
    h10025.www1.hp.com/ewfrf/wc/famiDocument?lc=en&cc=lamerica_nsc_carib&dlc=en&product=12455&amp... - Similar pages
    [ More results from h10025.www1.hp.com ]


Sorry for the confusing quotes but I want to leave a trail.

---

### Post by Gokudan on 2006-10-14
> **Karnex420 said:**
> Hi Gokudan, 
I can't see my sound card on bios.  Is mobu different than the normal bios display or am I not recognising a code that represents soundcards on my computer?  You don't mean to disable the video card on bios do you?

Hi there Karnex420!

    Sorry to confuse you a little, mobo it's a term most of the IT techy's (like me :D) use for mother board.

     If your motherboard has an on board audio chip it should be displayed on the BIOS, try to look on a menu called Integrated Peripherals, it should be there.

     About the linux stuff you posted, i'm sorry i can't help you, i'm a linux newbie too, i just installed ubuntu 6.06 2 days ago since i've heard it's a very good distro for beginners and also i got tired of trying to install Gentoo 2006.1 x64 from scratch :(

Cya!
Att.
Gokudan

---

### Post by Karnex420 on 2006-10-15
Thanks Gokudan.  Finally found it, but maybe I should let everyone look at my sound.  I pulled this up from the directions given above; 
1. Execute 'lsmod | grep snd' to know the modules which drive them.

This is what I have now:

rick@rick-desktop:~$     lsmod | grep snd

snd_emu10k1x             19364    0
snd_rawmidi              25504    1 snd_emu10k1x
snd_seq_device            8716    1 snd_rawmidi
snd_intel8x0             33692    1
snd_ac97_codec           93216    2 snd_emu10k1x,snd_intel8x0
snd_ac97_bus              2304    1 snd_ac97_codec
snd_pcm_oss              53664    0
snd_mixer_oss            18688    1 snd_pcm_oss
snd_pcm                  89864    4 snd_emu10k1x,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer                25220    1 snd_pcm
snd                      55268    11 snd_emu10k1x,snd_rawmidi,snd_seq_device,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore                10208    1 snd
snd_page_alloc           10632    3 snd_emu10k1x,snd_intel8x0,snd_pcm
rick@rick-desktop:~$

My sound is still not coming from my soundblaster and I have no micrphone or line-in on either card.
When I turn off my default soundcard in my bios my boot up stalls on the brown ubuntu dapper screen but I hear two clicks of sound from my soundblaster soundcard engaging before it stalls.

---

