---
title: "audacity high pitch squeel?"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by darkeale on 2007-02-23
when i record in audacity i get a high pitch tone in the background. cant figure out whats doing it and it never used too. anyone got any thoughts?

---

### Post by darkeale on 2007-02-23
all other sound is fine except i only get it in one app.

---

### Post by BobSongs on 2007-02-25
What "source" are you trying to record from? Microphone?

What version of Ubuntu are you using?

Have you installed anything before this noise began?

Is it resolved by now?

---

### Post by chaplanger on 2007-02-25
What you may be experiencing is feedback from your speakers into the mic.  When you are recording turn the speakers off to see if this alleviates the problem.  

Also I have noted that the mic is always on so that it adds a hum to speakers when playing music so when not using the mic, I ensure it is muted.

---

### Post by mcduck on 2007-02-25
If you are recording using anything connected to your computer with a cable make sure that the cable isn't close to any CRT display, TV or such device or if possible turn such devices off when you are recording.

---

### Post by darkeale on 2007-02-25
hi. just got a new sound card and this appears to have stopped the problem. now i can get sound when using more than one application but only for certain things. audacity and gtick still need to be run on there own. anyone know how to sort this?

thanks

---

### Post by mcduck on 2007-02-26
I think Audacity only supports OSS sound, and that only allows sound from one app at a time. I have no idea about gtick, probably the same thing..

---

### Post by gabrielsaldana on 2007-03-19
I have the same problem with Audacity and my microphone. I've tested with Sound Recorder and the sound is nice and clean. 

On Audacity I get this high pitch tone on the right channel only and all sound recorded sounds like a crappy radio or phone call.

Anyone has a clue on how to fix this?

---

### Post by chocolatemintmocha on 2007-03-28
I had a similar issue. When I tried to record in audacity it would have crappy quality and a hiss. It took me forever to figure it out, but I eventually found a link on the audacity site which explained it. My understanding is that audacity uses OSS sound driver by default and ubuntu uses ALSA by default. Assuming this is the problem, all that you have to do is go to synaptic and search "aoss", without quotes. Then download alsa-oss.
Then go to your terminal and type "aoss audacity". Then double click on the volume control, which is on the top bar of the screen by default. then click on the capture tab, and make sure the recording volume is up. Then test out recording in Audacity!

---

### Post by OneSeventeen on 2007-06-02
thanks, this worked great for me!

For some reason audacity worked just fine until a recent update, but I'm not complaining since it is working again!

The only thing I did extra was went into system>preferences>main menu to change the command to "aoss audacity"

works great!

For other readers who are curious:[list][*][Wav file of before the fix](http://bin.woventhorns.com/bad_audacity.wav)
[*][Wav file of after the fix](http://bin.woventhorns.com/good_audacity.wav)[/list]

---

### Post by ramjet_1953 on 2007-06-02
Thaks for the tip chocolatemintmocha!

Worked great for me.

Regards,
Roger :cool:

---

### Post by Adam590 on 2007-06-14
Mine also worked fine (after much tweaking and most of chocolatemintmocha's tips above). I could record beautifully from either the microphone or the "mix" (soundcard?) - no more screech or robot voice.

Unfortunately, after a recent update and the addition of LiVES video editing software, I'm now back to the square one with Audacity. I'm still using the aoss command for audacity, and here are some relevant screenshots of some of my settings - hope that helps with a diagnosis:
[URL="http://i17.tinypic.com/4xo7ytv.png"]
my Audacity settings[/URL]

[my Alsa settings]("http://i7.tinypic.com/53hzek0.png")

I swear I've tried every combination of them that I tried before to make them work, but I'm still getting the buzzing Mr. Roboto, and Audacity gives me the warning message if I try to record/play in anything other than OSS. 

Any ideas?

---

### Post by ramjet_1953 on 2007-06-14
The curent version of Audacity that is in the repos for Feisty is basically an OSS application.

The high pitched squeel that you hear is because you are trying to contol it with ALSA.

To fix this, first make sure that you have downloaded the package [COLOR="Blue"]alsa-oss[/COLOR] , which is an OSS wrapper for ALSA. This can be downloaded, using Synaptic.

Next, make sure that you start Audacity with the command:

[COLOR="Red"]aoss audacity[/COLOR]

This should prevent the above problem and recordings should now be clear, without any background noise.

You can modify the startup command in the menu system by editing it in [COLOR="Blue"]System>Preferences>Main Menu.[/COLOR]

Regards,
Roger :cool:

---

### Post by Adam590 on 2007-06-15
Thanks, I think I'm starting to understand all that wrapper business :) 
I'd heard that it meant that you could control Audacity with Alsa, but I thought that meant you also had to _select_ Alsa (in Audacity).

So, to recap:

1. get the alsa-oss wrapper from the Synaptic Package Manager

2. change the Main Menu entry command to [COLOR="Red"]aoss audacity[/COLOR]
(by going to System->Preferences -> Main Menu -> Sound and Video -> right-click Audacity, choose Properties -> change command to [COLOR="Red"]aoss audacity
[/COLOR]
3. make sure that Audacity is set to use OSS for both input and output
(in Audacity, Edit -> Preferences -> Audio I/O)

4. Under your own (Alsa) volume control choose Edit -> Preferences, and make sure everything is selected

5. While in the Alsa volume control window, click the Switches tab, then either Microphone Capture (for recording with a mic), or Mix (for recording from the sound card). Also, on Alsa's _Recording tab_, make sure the little microphone is toggled "on" (no red X) and that the volume is adjusted sufficiently. 


Did I leave anything out?
Works fine for me now like this, thanks!

---

### Post by Keisad on 2007-06-19
Ahhhhh....

Above post = My saviour

:D

---

### Post by chickendude on 2007-12-24
I'm also getting the high pitched sound again (i came across it before and had downloaded the alsa-oss package and it fixed everything right up) but now when i run it through the terminal it doesn't give me the option of selecting OSS in the preferences menu for input or output... And I can't record in Sound Recorder without the high pitched noise either (I CAN record sound, it just has that dreadful tone over top of it), any suggestions? (To clarify, I'm able to follow each step except for the third step, as there is no OSS option in the drop-down menu.)
Thanks :)

---

