---
title: "Mic won't work"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by fermeul on 2007-03-02
Hi, 

i'm doing some tests on ekiga for research. But i can't get any sound captured from my micro. i've tried everything from reinstalling my sound card (realtek alc880) to changing all kinds of settings in alsamixer. Output is working fine and i can play music. It's just de mic that doesn't work. Not even with gnome-sound-recorder. 
Does anybody have some advise?

thx

---

### Post by in_flu_ence on 2007-03-02
Have you checked the input channel being switched on from the volume control?

I think I had that problem and my system had the input (mic) to be off by default.

---

### Post by F43RY on 2007-03-10
Hi in_flu_ence, I've your same problem!!!
I found this link:
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=ATI&card=ATI-IXP+southbridge+AC97+audio.&chip=IXP+SB150%2C+IXP+SB200%2C+IXP+SB250%2C+IXP+SB300%2C+IXP+SB400&module=atiixp]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=ATI&card=ATI-IXP+southbridge+AC97+audio.&chip=IXP+SB150%2C+IXP+SB200%2C+IXP+SB250%2C+IXP+SB300%2C+IXP+SB400&module=atiixp")

My integrated soundcard (ALC880) seems to be the model: IXP SB400 built on an ATI chipset.

In my case the solution above didn't fix completely the problem but something changed.
From the above procedure I followed the quick installation loading modules on kernel and not ricompiling it.

The main problem I found with mic is on skype. Micro becomes mute after a few time I speak. The only action which restore the correct situation is rebooting the system.](*,) 
After following the procedure, calls hold up longer but still the micro becomes mute and the system needs to be rebooted.
I tried unsuccesfully any possible kind of setting on mixer (setting on/off switches and rebooting system everytime).


Any suggestion is appreciate


FYI my system has:
O.S. Ubuntu edgy 6.10
Mobo: Sapphire  PC-A9RD480Adv with latest BIOS
Video card: Sapphire X800 XT

---

### Post by in_flu_ence on 2007-03-10
For my case, I simply have to set the thing at the volume control. I have a creative audigy soundcard if you need some of my hardware info.

However, when i tried to use Linux in the earlier year, i think there are conflicts on the soundcard if you have two applications that try to take control of it. Not sure if it is the same case here. So try to see if you stop any media player and just use skype. do a few test and see if it works.

If that is really the case, then maybe there should be a fix from the ubuntu team (MAYBE). or we might even need to submit a bug report if there does not have a solution.

But hope it works

---

### Post by in_flu_ence on 2007-03-10
For my case, I simply have to set the thing at the volume control. I have a creative audigy soundcard if you need some of my hardware info.

However, when i tried to use Linux in the earlier year, i think there are conflicts on the soundcard if you have two applications that try to take control of it. Not sure if it is the same case here. So try to see if you stop any media player and just use skype. do a few test and see if it works.

If that is really the case, then maybe there should be a fix from the ubuntu team (MAYBE). or we might even need to submit a bug report if there does not have a solution.

But hope it works

---

