---
title: "Audacity"
date: 2006-01-05
forum: Absolute Beginner Talk
---

### Post by Dr Von Bon Bon on 2006-01-05
Okay, I have got over the problem of using the microphone with the useful killall esd command but now I have another problem...


Whenever I try and record a second track on audacity (this is on the same project) the quality of it is horrific. This isn't a buzzing throughout the track but whenever any audio is played it is just a crackly fuzzy mess.


This isn'T due to the levels as I have checked those out perfectly and changed it from deadly quiet up and through to deathly loud. I have tried changing the input volume and I have tried messing about with the quality settings.

Now, I also know that this isn't to do with the mic or the computer as I had it running perfectly on Windows.

Also, this isn't because of the sound coming out of the speakers as I put headphones in.


Has anyone got any ideas because I really, really need this software?

Thank you very much

---

### Post by Dr Von Bon Bon on 2006-01-09
Does anybody have any ideas please?

---

### Post by hen3rz on 2006-01-09
Im having trouble with audacity too. I cant record or listen to stuff with it...
[B]
Error Initializing Audio[/B]
There was an error Initializing the audio i/o layer.
You will not be able to play or record Audio.

Error. Host Error.

Any ideas???

---

### Post by Dr Von Bon Bon on 2006-01-12
Yeah I know about this one.


These means that your sound isn't configured properly but I have no idea how to fix this.


So you can use audacity go to terminal and type in:


```
killall esd
```

Then open audacity and you will be able to record and stuff on there and for some reason I find that realplayer works but the rest of the audio players won't work.


This is all fine and dandy as when you have finished using audacity just go into terminal and type:

```
esd
```

and you should be able to play all your stuff again.

Rock And Roll

---

### Post by green_lifesaver on 2006-01-16
unfortunately dr von bon bon, I am having the exact same problem as you. Whenever I try to record, it comes out with a slight distortion and the more tracks I record on top of that the worse it gets, the secondary tracks even change there frequency it gets that bad. So I suppose no one has a cure for this than?

---

### Post by Dr Von Bon Bon on 2006-01-17
Someone really must have had this problem and solved it.

Please someone help

---

### Post by mbrubeck on 2006-01-20
Audacity has problems recording in mono on some Linux systems:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=249388](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=249388)

You can work around this by recording in stereo instead:
[http://audacity.sourceforge.net/help/faq?s=recording&i=stereo](http://audacity.sourceforge.net/help/faq?s=recording&i=stereo)

---

### Post by pjbgravely on 2006-01-30
See this thread. [http://ubuntuforums.org/showthread.php?t=117600](http://ubuntuforums.org/showthread.php?t=117600) for a work around to the host error.

---

### Post by Dr Von Bon Bon on 2006-01-30
Thanks loads, that is so much better now.


Again, thanks loads.

---

### Post by thojoh on 2006-02-03
Thanks for this tip, pjbgravely!

I applied the changes from the Hoary Unofficial Guide. Now audicity does work again. 

Only I still do not know how to make good recordings.

For example: I am trying to record the sound from a video recording that I made myself. The sound is stored in an .mpg file on my computer.
I can play it in Totem Movie Player with good sound quality, but when I try to record that sound with Audacity so that I can create a soundfile, the sound turns quite bad (a lot of 'static' (chchhhccchc - if you know what I a mean :rolleyes: ) when I play the recording back. 

What I tried is changing the input: it only works at all when I put it on 'Volume' or (strange enough) on 'Phone out' - with similar effects: bad sound.

Changing to stereo doesn't help either
 
I am not a crack yet in working with audacity so maybe I am doing something  wrong that is very simple. 
But Dr von Bon Bon, you sound like your problem is solved... How come? Did you also simply apply the Hoary changes, or did you do something that I overlooked?

 :neutral:
Any advice?

---

### Post by pjbgravely on 2006-02-03
I just tried recording with a cheap mic using Audacity. I found it helps when you plug it into the correct port:-D The sound quality wasn't choppy but it was distorted. I checked the preferences and found that under Quality/ default sample format was set to 32 bit. I changed it to 16 bit to match my card and all was fine. 

  I then tried to capture from a mpg like you did. I wasn't able to record until I changed to the OSS mixer and deselected all of the input devices. I could not get anything to work with the ALSA mixer so Audacity must use OSS and we know the cause of the problems. To make the recording sound good I adjusted gain to 1/3 then set the recording level with the  PCM level. I you cannot find all the devices in the mixer then select edit/ preferences to add them.

  One thing, the video I played was in Mplayer, and I know I had to set it to ALSA to stop choppy playback, so you are still having problems make sure that the player is using ALSA

---

