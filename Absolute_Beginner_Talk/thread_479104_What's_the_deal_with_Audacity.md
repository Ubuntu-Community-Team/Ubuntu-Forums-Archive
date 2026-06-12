---
title: "What's the deal with Audacity ??"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2007-06-20
I just installed a triple-boot with Edgy as the newest, with corresponding Fiesty and XP, but still, 
none of the input sources will record !! , I have a SBLive 5.1 card and it will record steams, but 
evidently not in Ubuntu !  The input souces in Edgy are: Vol,Line,Mic,CD,Line1,Phone In,Phone Out,
and Video, none ot which are available in Fiesty , why can't I get Audacity to record what's playing on the computer ???  Thanks for listening to my rant,lol ;)

---

### Post by ramjet_1953 on 2007-06-20
Make sure that you have[COLOR="Red"] alsa-oss[/COLOR] installed from the repositories.

Start Audacity with the command [COLOR="Red"]aoss audacity[/COLOR].

Regards,
Roger :cool:

---

### Post by sultanoswing on 2007-06-20
I had the same / similar problem earlier this week - no selectable input sources for me using Feisty, Audacity 1.26 (from the Repo's) and an SBLive! 5.1. Hance, unable to record "what you hear" as I can using (*shudder*) the windows build.

Problem resolved by using Audacity 1.3 beta (or CVS compile in my case). Apparently ALSA integration is a work in progress, hence the advice above. The recording level is a bit low, but acceptable - apparently this is a known problem with SB Live cards and the current Audacity ALSA implementation.

---

### Post by Drakkor on 2007-06-20
Yeah,  alsa-oss is installed, I don't even get an input source in Fiesty ! :(

---

### Post by sultanoswing on 2007-06-20
> **Drakkor said:**
> Yeah,  alsa-oss is installed, I don't even get an input source in Fiesty ! :(


Simultaneous posting :) - see above!

...and using the aoss command, don't forget to set Audacity to use **OSS: /dev/dsp** under 'Preferences'

---

### Post by Drakkor on 2007-06-20
Thanks,sultanowing,  I have done some research, and did find that I could compile the source code,for the 1.3 beta somehow,
but , I,being a noob to linux, actually would have no idea how to actually implement it ,lol  :(

---

### Post by ramjet_1953 on 2007-06-20
What options do you get when you click on[COLOR="Blue"] Edit>Preference[/COLOR]s in Audacity?

Is it anything like the attached screenshot?

Regards,
Roger :cool:

---

### Post by Drakkor on 2007-06-20
Here it is:

---

### Post by ramjet_1953 on 2007-06-20
OK, next step:

1. Right-click on the [COLOR="Blue"]speaker icon[/COLOR] in the top bar and choose "[COLOR="Blue"]Open Volume Control"[/COLOR]

2. When the window opens, click on the [COLOR="Blue"]Edit tab[/COLOR] and choose [COLOR="Blue"]Preferences[/COLOR]..

3. Make sure that the following are selected:

[COLOR="Blue"]Master, Headphone, PCM, Line-In, CD, CD Capture, Microphone, Microphone Capture, Mic Boost, Capture, Mix.[/COLOR]

4. Close that and now clock on the [COLOR="Blue"]Recording tab[/COLOR] and make sure that the sliders are at maximum and that there are no X's on the icons at the bottom of the sliders.

5. Now click on the [COLOR="Blue"]switches tab[/COLOR] and select the [COLOR="Blue"]capture source[/COLOR]. ie microphne, line-in, etc.

Hope that this gets you going.

Regards,
Roger :cool:

---

### Post by Drakkor on 2007-06-20
Yeah,thanks, ramjet,  I was finally able to record, with the "Vol" input source, but anytime I raiise the PCM level,
the sound turns into an irratating whining pitch ! Other wise the sound is very muddy, I have played with the 
levels quite abit, and can't seem to correct it.  I think I'm gonna have a go at trying to compile the 1.3 beta.

---

### Post by sultanoswing on 2007-06-21
> **Drakkor said:**
> I think I'm gonna have a go at trying to compile the 1.3 beta.

Good one. You'll learn a *LOT* of useful 'how-tos' along the way, and it SHOULD work!

---

### Post by Keisad on 2007-06-21
I had the same problem...

Alsa-oss had no use for me. I could only use the OSS drivers, and they don't record AND play at the same time. You'll have to compile the beta with portaudio to be able to use alsa.

---

### Post by Patrick K on 2007-06-21
Just do what I do, reboot to windows. I've given up completely on Linux for any recording work. I have tried Edgy (which works the best), Feisty, and Ubuntu Studio. None work as well as Win 98 (which is what I have, XP might even be better). I have a M-Audio card, which is one of the best supported cards in Linux, but Windows is still much better for recording. BTW, recording live music is the main use for my computer. I have several studio mics and an outboard 16 channel mixer. 

BTW, Audacity will work with ALSA drivers, I've done it. But it still doesn't work as well as under windows.

---

### Post by Drakkor on 2007-06-21
Besides recording streams, I'd eventually like to record my Yamaha midi keyboard multi-track preferably through ZynAddSubFX, which has a lot of cool sound effects, but I also haven't found a proper software muliti-track recording solutiion yet,lol ! :D

---

### Post by Patrick K on 2007-06-21
Ardour is probably the best multi-track solution for Linux (it's in the repos). I've had better luck with it than Audacity in Linux. It's much more complicated than Audacity. Ardour requires Jack so you'll have to install and configure it.

---

