---
title: "Poll:Sound volume: Windows vs Ubuntu"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by sauravbhaumik on 2007-09-05
Does anyone notice that the sound volume in ubuntu is lower than that in Windows?
In any case, please tell us what comparative volume you get with windows and Ubuntu; and if possible, please let us know what your sound card is.

Thanks.
This poll is important.
Saurav
--------------
My vote: AC'97; sounds with 80% master, 80% PCM as it does with 10% master in windows XP. Latest alsa version.

---

### Post by Hobo Joe on 2007-09-05
I have noticed that, although it sounds like it's a little more drastic for you than it is for me.

Luckily for me, I have an awesome set of speakers that go louder than I could ever need.

---

### Post by marx2k on 2007-09-05
I have an Audigy 2, but I haven't booted into XP in a very long time.. the sound volume seems to be the same, but what I am sort of missing in the systemwide equalizing options that XP/Creative offered.

So are you talking about volume AFTER you messed with the volume settings in the configuration from cli? (alsamixer)

Also, your topic suggests there is an interactive poll to be taken, which there is not :(

---

### Post by stone on 2007-09-05
I noticed the same thing. This happened when I switched from Edgy to Feisty. I have to keep my volume cranked in order to hear it at a medium volume. "Rock out" volume is no longer available to me!

I'm just using whatever on-board sound card came with my motherboard.

---

### Post by mridkash on 2007-09-05
This problem was there in my Laptop (Compaq V3000, conexant device) when I freshly installed ubuntu.

But after recompiling the latest alsa driver (14 something), the sound is back and back with a bang. If i jack up the volume controls to full, the volume is more than what the speakers can handle peacefully. Also headphone volume is good. I keep the PCM 1 2 at around 80%.

---

### Post by caoinan on 2007-09-05
sound seems good to me  my sound card is a HT Omega Striker 7.1

---

### Post by univremonster on 2007-09-05
I've actually had the opposite experience, on my old Windows laptop my volume would change sporadically.  Not the kind you can adjust by grabbing the bar on the lower right hand toolbar, but the kind of volume you have to go into the control panel to adjust.  Even when it was on full, the speakers never put out anything louder than a mid-size airconditioner could cover up (though the speakers themselves and those which I plugged into the system were more than capable).  On Ubuntu I have never had any problems with that.

---

### Post by nowshining on 2007-09-05
half and half for me, some songs go tooo low and i have to crank it up and some well tooo loud - the computer sound goes thru my Stereo speakers thru AUX out... :P



edit: on windows - well they were Just okay..

---

### Post by SOULRiDER on 2007-09-05
I havnt used Windows in over a year, but ive never noticed any changes and I only have a crappy onboards sound card... I do however have like Hobo Joe big *** speakers so i can just put the volume up :P

---

### Post by aktiwers on 2007-09-05
```
alsamixer
```

---

### Post by sauravbhaumik on 2007-09-05
> **marx2k said:**
> I have an Audigy 2, but I haven't booted into XP in a very long time.. the sound volume seems to be the same, but what I am sort of missing in the systemwide equalizing options that XP/Creative offered.

So are you talking about volume AFTER you messed with the volume settings in the configuration from cli? (alsamixer)

Also, your topic suggests there is an interactive poll to be taken, which there is not :(

Of course, I meant an interactive poll :)
As to your question, the problems have been seen since I installed any copy of Ubuntu on my computer. I have both Edgy and Feisty installed right now; and  in both I see the problem. This happened on Feisty as well, where I didn't muddle up the sound control!

So, what's your comment?

---

### Post by sauravbhaumik on 2007-09-05
> **stone said:**
> I noticed the same thing. This happened when I switched from Edgy to Feisty. 
Well, did you notice the problem with Edgy?


> I'm just using whatever on-board sound card came with my motherboard.
Okay; but the stuff on the motherboard matters.

---

### Post by sauravbhaumik on 2007-09-05
> **mridkash said:**
> This problem was there in my Laptop (Compaq V3000, conexant device) when I freshly installed ubuntu.

But after recompiling the latest alsa driver (14 something), the sound is back and back with a bang. If i jack up the volume controls to full, the volume is more than what the speakers can handle peacefully. Also headphone volume is good. I keep the PCM 1 2 at around 80%.

Well, if I turn my master full, the sound is quite loud and one has to regulate the speaker volume to control it; but the problem is, I have to keep my master volume 80% or more in order that the sound may be quite observable. In Windows, the problem is not there - and with 20% volume, the sound is so loud as I can not ever obtain in Ubuntu.

I compiled the latest versions of alsa several times (months ago) in Edgy - but nothing better.

---

### Post by mridkash on 2007-09-06
I almost never touch master controls on the OS. 
Basically for listening music I use Amarok's volume control.

> Well, if I turn my master full, the sound is quite loud and one has to regulate the speaker volume to control it; but the problem is, I have to keep my master volume 80% or more in order that the sound may be quite observable. In Windows, the problem is not there - and with 20% volume, the sound is so loud as I can not ever obtain in Ubuntu.

I think the problem actually is non linear variation of volume, even I noticed it, just bring down the volume bar a little bit down and the volume drops drastically. Thats why I dont use it regularly.

And,
> half and half for me, some songs go tooo low and i have to crank it up and some well tooo loud - the computer sound goes thru my Stereo speakers thru AUX out... :P



edit: on windows - well they were Just okay..

Well I think this is a song problem not OS. songs can have different volume (gain). 
The reason why you dont notice it on Windows is maybe due to  auto volume leveling feature in media player and iTunes.
Solution: open the song that's too low volume in audacity and apply the gain to correct it.

---

### Post by n3tfury on 2007-09-06
> **nowshining said:**
> half and half for me, some songs go tooo low and i have to crank it up and some well tooo loud - the computer sound goes thru my Stereo speakers thru AUX out... :P



edit: on windows - well they were Just okay..

that's an issue with the source and how it was originally recorded.  compressing to a lossy format can make things much worse.

---

### Post by n3tfury on 2007-09-06
> **mridkash said:**
> 

Well I think this is a song problem not OS. songs can have different volume (gain). 
The reason why you dont notice it on Windows is maybe due to  auto volume leveling feature in media player and iTunes.
Solution: open the song that's too low volume in audacity and apply the gain to correct it.

unless you use [[COLOR="DarkOrange"]replay gain[/COLOR]]("http://replaygain.hydrogenaudio.org/index.html"), doing any sort of gain adjustment deteriorates the quality of said file.

---

