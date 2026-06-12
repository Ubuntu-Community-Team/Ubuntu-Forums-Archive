---
title: "Sound problems."
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by geokok1981 on 2006-07-05
I am having the following problem with sound:

1. In Ekiga sound quality is nit very good (I connect to voipbuster through it which in windows has better quality) and after a while the other person can not hear me at all (seems that my part that takes the sound sort of crashes).
If I run the wizard at the audio setup part I can choose HDA Intel or default. The test fails with HDA Intel and I have to restart Ekiga to run it again.It seems fine with "default" but then I had the problem described here.

2. Using the the default sound recorder in the start menu I managed to record my voice through my headset the first time I used it but after that it never captured any sound again!!!I tried tweaking with the sound settings but did not work and now I can't even remember what the original settings were.

Any suggestions to resolve this problems with sound? System is a laptop clevo m400 and I have the device set to HDA Intel (I tried the Realtek option as well made no difference).

---

### Post by LordRaiden on 2006-07-05
Have a look at my guide in my signature. Go through and post back if you hit a roadblock.

---

### Post by geokok1981 on 2006-07-05
Seems like a well put guide but I am not quite sure what I should use from it for my problem. I mean I got sound fine. It's just with the specific apps that require input of sound that things go wrong.....
Can u be a bit more clear on what I should do?

---

### Post by LordRaiden on 2006-07-05
Sorry, I got confused ready your post. Not too familiar with Ekiga but what other sound settings are there? The kind of output (alsa, oss, esd, ). Try not using the wizard, to get a few more settings if possible.

---

### Post by geokok1981 on 2006-07-05
I am afraid it is not Ekiga's fault but a more general one since i am having problem with voice recording as well. Perhaps alsa gets messed up when I use the mic from my headset??
The weird is as I said it worked the first time and then silenced for ever.....

Using Windows so many years I'd know what to do there.....but I don't want to give up Ubuntu. 
I really want to reach a level where both operating systems will be as easy to use for me....
Maybe when I give up the laptop and start using a desktop Ubuntu will work better....
Perhaps I should use a tool inherited from the windows world....format.......

---

### Post by LordRaiden on 2006-07-05
You'll have to look at a sliders in alsamixer (making sure microphone and capture are both not muted - maybe +20db switched on)

I also don't know your specific soundcard that might lead me somewhere.

---

### Post by geokok1981 on 2006-07-05
Well from windows control panel I get:
Realetec High Definition Audio 

The machine is a clevo m400 laptop. Perhaps you can dig more specs from that..

I believe I have tried all the sliders but without much luck. I had the microphone and the line in and pretty much everything not muted. 
By default capture 2 was activated but I tried capture and capture 1 as well..no luck...

---

### Post by LordRaiden on 2006-07-05
do ```
aplay -l
``` in a console. That will give me exactly what I want. Should've asked sooner so sorryabout that.

---

### Post by geokok1981 on 2006-07-05
here u go my friend:

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC880 Digital [ALC880 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by geokok1981 on 2006-07-05
Ok good news!!! Further tweaking with the sliders and the options restored voice recording in sound recorder!!!Seems a noob is always a noob...
 
However since u got all my hardware details and u say I shouldn't use the wizard can u help me setting up the sound in Ekiga, cause like I said I had problems there (see above).  I remind u that I connect through voipbuster with Ekiga if that makes a difference. 

By the way, thanks for all the guidance u gave me so far!!!
Seems that Ubuntu really has a warm and welcoming community!!!:D

---

### Post by LordRaiden on 2006-07-06
Read the Audio problems section here- try using the wizard once again [http://www.gnomemeeting.org/index.php?rub=3&pos=0&faqpage=x201.html#AEN241]("http://www.gnomemeeting.org/index.php?rub=3&pos=0&faqpage=x201.html#AEN241")

---

### Post by geokok1981 on 2006-07-06
Don't know really....skype works great though....
Maybe I ll try openWengo as well.

---

### Post by cvmostert on 2006-11-13
geokok1981, i usually did not have problems with ekiga, but after reinstalling and upgrading to ubuntu efty, i also have a problem with ekiga.

Skype recording and phoning works well, and other sound apps recording works well.

just ekiga... i can not even hear the other side when i call using voipbuster... it worked ok in dapper. probably just some setting... 
not a hardware problem. we will figure it out. I am on a desktop..

dont think the laptop is your problem

edit: I found my problem... after reading on the ekiga site...

it was with the nat settings...

i ran the config druid again and deliberately made it look for the nat, and enabled stun again...

i believe i did it before, but... after doing it again... it works!

it does not have the same sound as normal recording... but then again, it is not normal recording its phoning.

hope this helps
take care.

---

### Post by geokok1981 on 2006-11-20
I am on edgy as well now but my problem is not sound anymore 'cause Ekiga
can not be set up at all now. I am on a different machine and using a dsl connection with a modem router.
No matter what ports I open or run the script they provide at the website of Ekiga it keeps saying " Symmetric NAT detected"....

So.....so much for Ekiga I guess....

---

### Post by cvmostert on 2006-11-24
Has the ekiga website given you any information on the NAT problem?

I still have the same problem, all sound works, just Phoning in ekiga does not work. Skype works just fine.

---

