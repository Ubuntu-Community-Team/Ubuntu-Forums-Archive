---
title: "audio playback is quiet...?"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by AggieTwist on 2007-12-06
can't seem to figure it out...helped get rid of background noise when i installed alsamixer but its still really quiet playback even through external speakers...i have a toshiba satellite laptop...if u need to know more just say so and i'll let u know.  also unsure how to get DVD's to play...thanks!

---

### Post by Shinbu-Otaku on 2007-12-07
for DVD's to play you will need the 'Ubuntu Restricted' package from the add/remove option. This will install codecs for all pay-only codecs such as WMA, WMV, DVD etc, most codecs that come as standard on Windows.

For the sound problem, open the sound menu (there should be an icon next to the clock to do this) and see if the master is on the highest setting. Sound always seems to be a bit quieter on ubuntu that it is on windows for me, but i just turn my speakers up a bit more :)

hope that helps

---

### Post by spupy on 2007-12-07
I got the same problem with my toshiba satellite after installing alsa. The strange thing is that in alsamixer, the Master Bar is not active at all. The PCM bar changes the volume. Also, after installing alsa, the device /dev/dsp appeared...

---

### Post by fearpi on 2007-12-08
> **spupy said:**
> The strange thing is that in alsamixer, the Master Bar is not active at all. The PCM bar changes the volume.

I also have had this happen since installing Gutsy. My sound is really quiet also, and it sounds like the actual volume is increasing exponentially (rather than linearly) with the volume meter, so anything below about 60% is inaudible, 100% sounds very distorted, and in between, the volume increases a lot with each small increase of the slider. I've considered trying alsa 1.0.15 (Feisty uses 1.0.14, I believe). Maybe I'll try that this weekend.

---

### Post by AggieTwist on 2007-12-08
> **spupy said:**
> I got the same problem with my toshiba satellite after installing alsa. The strange thing is that in alsamixer, the Master Bar is not active at all. The PCM bar changes the volume. Also, after installing alsa, the device /dev/dsp appeared...

yep, thats exactly the same deal with mine. as far as DVD playback, i already installed all the codecs but still nothing...

---

### Post by huckleberrymopo3 on 2007-12-08
I have the same laptop and the sound is super quite too. I have tried quite a few fixes from the forums with out any luck. Out of the 3 computers that I have installed Ubuntu on this is the only thing I have not been able to figure out how to get working.

---

### Post by lsmobrian on 2007-12-08
I had this happen too, i went through all my apps that use sound and maxed out their volume.  when i turned xmms volume up the system volume increased

---

### Post by TheShocker on 2007-12-08
I have this problem too. DVDs as well as music. Tried various programs. Odd thing is, it was not like this yesterday (it could play quite loud) but today it is very quiet.

---

### Post by TheShocker on 2007-12-08
Well I fixed my volume issue. I double-clicked the Volume Icon and up popped the volume control. For some reason PCM volume was way down. Now it's loud as all hell again. Duh. (As I said, I am a newb to Ubuntu).

But for some reason everything plays in only 2.1. I have a 5.1 set-up which works just fine in windows. I made a new thread for this issue here: [http://ubuntuforums.org/showthread.php?p=3918741](http://ubuntuforums.org/showthread.php?p=3918741)

---

### Post by salefish on 2007-12-09
My volume is also low and my alsa mixer is maxed out. 
I have gone into the registry editor by hitting alt+f2 and typing   gconf-editor opening the drop down menu apps, going to sound-juicer on the right hand side it says volume and the value is set at 1. does anyone happen to know if this would be the master volume control, or just exactly what it is?

---

### Post by jobyjoe on 2007-12-13
Changing the PCM level worked for me. Maybe try this

---

### Post by AggieTwist on 2007-12-13
right now i've sorta given up until I hear about something that seems to work for the Toshiba's...i just boot into Windows again when I want to listen to any media, you'd think that'd be a big enough kick in the face for Ubuntu that someone with more know-how would figure it out.  Although I really like using Ubuntu  its a complete pain to get everything compatible and working correctly so I still spend the majority of my time in Windows.  I would love to switch over but I don't have hours on end to spend troubleshooting audio and compatibility issues...

---

