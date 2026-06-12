---
title: "Another &quot;I can't record in Audacity&quot; thread"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by maoglone on 2007-07-19
First off, I'm using a Compaq C500T series, feisty fawn, and just downloaded Audacity.  I use it to record a podcast, and use the microphone jack/line in to plug a mixer in.  Wasn't a problem in XP or Vista, but I'm getting nothing but an error message that says "Error while opening sound device.  Please check the input device settingsl and the project sample rate."  

I've installed  alsa-oss, turned on everything in the Volume Control but still can't record.  How do I set my devices so that this'll work and I'll be able to get the podcast up and running again?  Got a show to do tomorrow evening and I can't miss it.  

I opened audacity through the terminal and came up with this, too:  
> 
Expression 'SetApproximateSampleRate( pcm, hwParams, sr )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1108
Expression 'PaAlsaStreamComponent_InitialConfigure( &self->capture, inParams, self->primeBuffers, hwParamsCapture, &realSr )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1659
Expression 'PaAlsaStream_Configure( stream, inputParameters, outputParameters, sampleRate, framesPerBuffer, &inputLatency, &outputLatency, &hostBufferSizeMode )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1783
Expression 'SetApproximateSampleRate( pcm, hwParams, sr )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1108
Expression 'PaAlsaStreamComponent_InitialConfigure( &self->capture, inParams, self->primeBuffers, hwParamsCapture, &realSr )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1659
Expression 'PaAlsaStream_Configure( stream, inputParameters, outputParameters, sampleRate, framesPerBuffer, &inputLatency, &outputLatency, &hostBufferSizeMode )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1783

So, what should I do?  I'm very new to Ubuntu, and until yesterday wasn't really comfortable with the whole "Terminal" thing... so if you don't mind, please be gentle...

thanks!

---

### Post by maoglone on 2007-07-19
Partially a bump, but mostly I'm posting again to give a little more info and maybe ask another question.  

I'm thinking that the hardware devices might be mapped out in a funky/wrong way, as I can't record ANYTHING in ANY recording software, so it might be useful to look at how those are configured.  Anyone know how to do this, and also to move them around so that I can make sense of this apparent mess?  

Also, does anyone have any suggestions on recording applications that might be a little easier to set up?  I've been wrestling with Audacity for 2 days now and am starting to tire of it.  Might be the n00b in me talking, but you know...

Anything you've got will help.

---

### Post by ramjet_1953 on 2007-07-19
Have you done this?

[COLOR="Red"]sudo apt-get install alsa-oss[/COLOR]

This is an ALSA wrapper for Audacity, which is an OSS application.

start-up Audacity with the command [COLOR="Red"]aoss audacity[/COLOR]

If this works OK you can modify the startup command for Audacity in  System>Preferences>Main Menu

Also in the volume control click on Edit>Preferences and make sure that all of the capture options are clicked.

Hope that this helps.

Regards,
Roger :cool:

---

### Post by expatCM on 2007-07-20
Just wondering if you have had a thorough look round alsamixer, especially the Record sliders.

---

### Post by maoglone on 2007-07-20
I have done all of those things, and still nothing.  Are there other alsa things I should install?

---

### Post by maoglone on 2007-07-20
Any other suggestions?  

How do I map my inputs properly?  What other alsa software components do I need to have?  At this point, it might be more time-efficient to download/install the right software than it would be to just reinstall Windows.  As time goes on, though, I'm becoming progressively less sure of that.

---

