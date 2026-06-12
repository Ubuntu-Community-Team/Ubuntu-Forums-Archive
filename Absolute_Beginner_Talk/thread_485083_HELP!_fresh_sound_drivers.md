---
title: "HELP! fresh sound drivers"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by anavar on 2007-06-26
I want to delete anything to do with my sound on ubuntu FF. Then reinstall all that I have deleted. I currently have no sound and have gone through all the pages and tips but can't get sound to work. The sound did work after I did a fresh install of ubuntu FF.

Please help me with this awful situation.

I don't know a whole lot about linux as well....

Anavar.

---

### Post by annda on 2007-06-26
your problem are probably not the drivers (unless you installed alsa manually) - alsa is by default installed as a kernel module, meaning an integral part of the system, not an extra driver. the trouble is caused most likely by configuration files. i don't know enough to tell you exactly what you need to change and where, so i suggest removing all the sound packages together with conf files. instructions are here:
[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#Getting_the_ALSA_drivers_from_a_.2Afresh.2A_kernel](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#Getting_the_ALSA_drivers_from_a_.2Afresh.2A_kernel)

please read it carefully and pay attention to what will be uninstalled together with alsa, especially gdm & co.

i hope it helps.

---

### Post by anavar on 2007-06-26
Thank you for the reply..... 

I am using realtek ac97 alc850 driver.... and I think there is some conflict or something not sure.

It might also be since I am using coax spdif on my onboard digitally hooked up to my speakers.

I will follow that post you sent and see what happens.

Thanks again.

If anyone else has any ideas it would be greatly appreciated. 

Anavar.

---

### Post by samuraiCat on 2007-06-26
> **anavar said:**
> I want to delete anything to do with my sound on ubuntu FF. Then reinstall all that I have deleted. I currently have no sound and have gone through all the pages and tips but can't get sound to work. The sound did work after I did a fresh install of ubuntu FF.

Please help me with this awful situation.

I don't know a whole lot about linux as well....

Anavar.

Too funny! I'm in the same boat. I posted on this a few hours ago. I was told to just save my bookmarks and PDFS and stuff from my /home directory on a USB memory stick, and then reformat/repartition. It will mean replacing all my programs, but since I screwed up all the ones that deal with audio recording, I would need to do that anyway. Besides, its not like install programs in Linux takes that long. The hard part (sort of) will be getting the video and printer drivers working properly again.

---

### Post by anavar on 2007-06-26
Yeah I just don't want to reinstall all of ubuntu and then load some programs and this whole thing happen to me again.

I just started using ubuntu FF with a dual boot windows xp home system.

So i don't really have much loaded on ubuntu just beryl and couple other prog's 

If you find a solution to the sound thing .....drop me a message please.

good luck with your troubles.

Anavar.

---

### Post by anavar on 2007-06-26
Annda your life saver. I tried that following link you sent and at first it didn't work but then I remembered someone saying you need to mute the iec958 playback and I did and sound started playing as soon as I did....


Thanks..... 


Anavar.

---

### Post by samuraiCat on 2007-06-26
> **anavar said:**
> Yeah I just don't want to reinstall all of ubuntu and then load some programs and this whole thing happen to me again.

I just started using ubuntu FF with a dual boot windows xp home system.

So i don't really have much loaded on ubuntu just beryl and couple other prog's 

If you find a solution to the sound thing .....drop me a message please.

good luck with your troubles.

Anavar.

Well, actually, reinstalling is the solution to my problems, seeing as how I uninstalled ALSA and intalled the linux-oss drivers for my card and messed everything up. By the way, the way Linux works, it's not going to be the programs that cause problems. That's just not possible, as I understand it. What can get screwed up, however, are the configuration and driver files. If you can't play any audio, then my guess is that your drivers or configuration are to blame.

Edited to add: BTW, I tried the link that worked for you, and those instructions still didn't do the trick for me. Good to hear that you're back up to speed.

---

### Post by stickx911 on 2007-07-02
> **annda said:**
> your problem are probably not the drivers (unless you installed alsa manually) - alsa is by default installed as a kernel module, meaning an integral part of the system, not an extra driver. the trouble is caused most likely by configuration files. i don't know enough to tell you exactly what you need to change and where, so i suggest removing all the sound packages together with conf files. instructions are here:
[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#Getting_the_ALSA_drivers_from_a_.2Afresh.2A_kernel](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#Getting_the_ALSA_drivers_from_a_.2Afresh.2A_kernel)

please read it carefully and pay attention to what will be uninstalled together with alsa, especially gdm & co.

i hope it helps.

This worked for me!  Thank you
:popcorn:

---

