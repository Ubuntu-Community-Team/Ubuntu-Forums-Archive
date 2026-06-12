---
title: "Audigy 2 ZS Notebook and ALSA/ESD"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by colsandurz on 2007-05-07
I have three sources of audio on my notebook, the speakers, the integrated soundcard, and my audigy 2 zs and no natter how I set it in preferences>sound and volume control I can't get any response from my Audigy.  The speakers and integrated card work fine.  Currently, my audigy is set to use the ALSA mixer along with my speakers, but the integrated card is set to use OSS.  

How can I get my Audigy card to work?  I had it set up before using ESD, but I don't remember how I did it.  I think I used an terminal command that was something like

```
sudo set audigy
```

but I think there was more to it.

Thanks for any help.

---

### Post by tbg58 on 2007-05-07
Here's someone who had a very similar problem.  After some back and forth on the forums here, they got the problem solved.  Have a look here:
[http://ubuntuforums.org/showthread.php?t=407661](http://ubuntuforums.org/showthread.php?t=407661)

Hope this helps!
Good luck!

Rob in TN

---

### Post by colsandurz on 2007-05-08
Well I think what's going on is that my integrated card is given priority over my audigy.  I think this because whenever I unplug my 1/8th jack from my integrated card sound goes directly to my laptop speakers.  Note that, to Linux at least, that my laptop speakers and integrated sound are two separate sound devices.  So I think I can solve my problem by disabling my integrated sound device... the only problem I don't really know how to do that....

---

### Post by colsandurz on 2007-05-08
I think I found it... can I disable my integrated card by edited my 

/etc/default/alsa

```
# Configuration file for alsa-base

# List, separated by spaces, the names of modules that should be
# unloaded, if present, before the machine is suspended. Use the
# special name "all" if you would like all ALSA sound modules to be
# removed. The modules that are removed will be loaded again after
# resume.  Currently this only has an effect if you are using apmd.
# Examples:
#     Value         Action at suspend time
#     ""            Do nothing
#     "snd-cs46xx"  Stop sound processes and remove the snd-cs46xx module
#     "all"         Stop sound processes and remove all ALSA modules
force_unload_modules_before_suspend=""

```

Edit:
I just realized this wouldn't work because I'm trying to disable a card that uses an OSS mixer.

---

### Post by anachreon_ on 2007-05-13
In order to load the PCMCIA card first, try creating a file called "sound" in /etc/modprobe.d/, with the following two lines in it

```

options snd-emu10k1 index=0
options snd-intel8x0 index=1
```

where the index=0 card is the card you want to load first, and the index=1 card is your onboard sound (for me, the intel8x0).  snd-emu10k1 should load the sound blaster driver.   Let me know if that does / doesn't work.

---

### Post by TekNullOG on 2007-06-08
I look forward to trying this when i get home. I will post if it works for me and if it solves any other sound problems.

---

### Post by TekNullOG on 2007-06-14
> **eightinches said:**
> I look forward to trying this when i get home. I will post if it works for me and if it solves any other sound problems.

No it didn't fix the fact that firefox uses the wrong sound card for website sounds.

Ohh well...

---

