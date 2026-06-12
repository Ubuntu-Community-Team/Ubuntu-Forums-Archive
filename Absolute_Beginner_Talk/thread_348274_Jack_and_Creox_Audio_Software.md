---
title: "Jack and Creox Audio Software"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by flashbandit on 2007-01-28
I recently got Ubuntu on my comp and I'm very pleased, although I've run into some serious problems while trying to run the programs JACK, and creox. I play guitar, and so I thought the creox software would be fun to have, but I can't get it to work. While running jack, I run into a error saying there's a problem with ALSA. How do I install these programs, and get them to work? Thanks in advance!

---

### Post by flashbandit on 2007-01-30
Please Help!

---

### Post by Patrick K on 2007-01-30
I don't know much about all this as I have been trying for several weeks to get everything working but...

Have you been to the alsa web site? Click on the sound card link at the top and look up your sound card. Many, but not all, are supported. If it is listed, you can read about configuring ALSA for your hardware. Good luck, you'll probably need it. 

BTW, Creox looks rather interesting. I'll have to take a deeper look at it.

EDIT: forgot to include the link:
[http://www.alsa-project.org/](http://www.alsa-project.org/)

---

### Post by taurean on 2007-03-23
It depends on what the exact problem is.

I've got it running perfectly after a few things, but I think a bit of luck helped me. 

From the terminal/console I had problems, but found in the Ubuntu Dapper Synaptic repositories  (Im sure it would be the same for edgy or older versions of ubuntu) a GUI front end for it called qjackctl and that gives you a frontend that is so much easier than trying to run it manually.

If you've already done this, sorry for the redundant info.

Another thing that might be causing problems with the ASLA driver is I've heard some audio apps need the System Sounds to be disabled as they tie up the sound driver. From System/Preferences/Sound  which has helped me in the past, but it's my understanding that it doesnt affect Jack here. Not for me anyhoo.

If the error is something like [B]"15:54:22.205 Could not open ALSA sequencer as a client. MIDI patchbay will be not available.
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory"[/B] then Jack will still work, just not midi.

You just have to make sure that you load Jack before Creox so Jack knows how to connect the audio devices.

Basically, this is how I load them.

1: Ensure Jack is loaded (I use the GUI listed above). 
2: Make sure you Click Start in Jack to start the server.
3: Load Creox

Make sure you click the Start button in Creox if you want to check anything in Jack, or jack wont see it as a device it can talk to. If in Jack under Connect they are seeing each other and there are lines going to the proper places -  Alsa_pcm should be going to Creox, and vice versa - then it should work ok. 

You should be able to hear the guitar if you have the right 'source' from your Speaker settings set, ie; not Line Input if you're using the MIC. Which I do.

Also, depending on what style of Guitaring you play, if you fiddle a bit with the settings you can get some damn good sounds from it. Unfortunately I play both Heavy and Acoustic, and need the volume control open because Heavy is DAMN loud and if Im using a Jack Enabled multitracker to record, the acoustic is just overwhelmed by it.

Thats why I was searching for references to it, and came across your post.. Hopeing someone has a way to make it less loud.. 

 :guitar: :lolflag:

---

### Post by Sonicgoo on 2007-05-13
This worked for me, the effects are light but I can't really turn up in the Apartment. I need some good Earphones. 

I'm running on Feisty if any wants to know. 

Many thanks to taurean.

---

### Post by RichPicker on 2007-07-12
I finally got Jack and creox and Ardour working. But the guitar sound is very bad. Distorted even at extremely low volume.

I've found that using GNUSound to record gives by far the best sound. Sometimes I use Audacity for some file conversion.

I'm recprding an acoustic with a piezo, and mic with the acoustic, a strat, and a gibson with one P90. 

The jack applications really aren't sounding well for my system, Dell laptop, at all. The GNUSound recorded is superior.

Just my two pesos.

---

