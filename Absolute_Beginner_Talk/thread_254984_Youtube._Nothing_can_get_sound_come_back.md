---
title: "Youtube. Nothing can get sound come back"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by viniciuscarvalho on 2006-09-10
Hello there! I know this is a very know BUG, but I've tried everything and I still get problems with youtube and ubuntu. What is really p****** me off is that sometimes I get sound sometimes not.

I tried download the alsa-oss and edit the firefoxrc to point the FIREFOX_DSP="aoss". Tried to download libflash-mozplugin and nothing. Is there any other thing I should to to get it working?

Regards

---

### Post by Sabrage on 2006-09-10
hello viniciuscarvalho

i'm sure you'll get an answer from an expert soon, but sometimes i lose sound on flash and it comes back after i restart the browser. if that doesn't work then i log out and log in again from ubuntu. it usuallu works. other than that i don't know sorry. i usually lose sound on flash after i have used a mediplayer for sound.

good luck

---

### Post by indigoshift on 2006-09-10
That happens to me from time to time, too.

I just click the volume down a notch or two, then back up again, and the sound works great.

---

### Post by H.E. Pennypacker on 2006-09-10
When watching YouTube videos, I can hear sound.  Just to eliminate any possible causes, make sure nothing else is using the sound card.  To see what the cause could be, first close ALL windows.  Then open up Epiphany and play a YouTube video.  Can you hear sound?

Do you have ALSA enabled?  Go to Volume Preferences, and select ALSA.  

Currently, there are too many audio problems.  The biggest problems seem to be no audio with flash movies and multiple applications not being able to use the soundcard at the same time (regardless of what tricks you have up your sleeve).  

Hopefully, all this will be sorted out with future versions of Ubuntu using ALSA and only ALSA, and OSS will become extinct.  Let's hope so.

---

### Post by cwaldbieser on 2006-09-11
Not really a fix, but you can download the videos using the "VideoDownloader" extension for Firefox and play the .flv files with ffplay (from the ffmpeg package).  Or, you can use ffmpeg to turn it into a .mpeg file and watch it with whatever movie player you want.

---

### Post by codejunkie on 2006-09-11
***YOUR MILEAGE MAY VARY meaning this may or may not work for you, but i'm hoping it will.***

this will disable the startup sound when ubuntu loads, but after doing this i haven't had any problems with sound in flash not working.

Click on **System/Preferences/Sound** Uncheck Both *Play system sounds & Enable software sound mixing (ESD)*

Now right click on the Volume Applet and choose Preferences click the Drop Down Box now select the (OSS Mixer) listed for your sound card instead of the (Alsa mixer) and restart, hopefully you won't have any more problems with sound in flash.

---

### Post by junglepeanut on 2006-09-11
Try Firefox 2.0, no more intermittent issues for me, especially nice that it even works when multiple sound files are on. 

Running (X/K)(F)(XGL)Ubuntu

Gateway 8510gz (stock)

I suspected this when I used other browsers I tended to not have issues, when 2.0 was beta I had to see if it was fixed, so far no issues, and videodowloader, mediaconnectivity, etc extensions all continued to work (better in fact). Only extension I lost was (tabPlus) of course lol.

Hope this fix works for you.

---

### Post by ramcosca on 2006-09-11
Right now I'm running Firefox 2 Beta 2 and I don't get sound, either. I'll try what codejunkie said, though. It'll be sad losing the startup sound since I like it so much... but sacrifices will have to be made. Perhaps I can sudo cp the .wav file to the desktop and open it whenever I log on....lol

I'll update when I reboot... in a couple of hours.

BTW, question. Can I not lose the startup sound and still have the OSS thing to work? :confused:

---

### Post by heinlein on 2006-09-13
Not sure if this will help you, but try and run this line in the terminal:
```
sudo ln -s /tmp/.esd-1000 /tmp/.esd
```

Then restart Firefox.

I know that's what I do to get it work in Opera (which I prefers), and since Firefox won't recognize Flash, I can't test if it works there.

---

