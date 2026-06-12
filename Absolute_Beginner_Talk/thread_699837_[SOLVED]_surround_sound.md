---
title: "[SOLVED] surround sound"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by masque7 on 2008-02-17
hi all,

firstly i'd like to say that yes i have tried the search feature and picking bits out of posts to help my problem, but i'm having no luck

i'm using 5.1 surround sound with sound card. only getting sound out of the two "front" speakers. the two "rear" and the sub-bass thing are silent. in Windows you had to enable this via the sound card settings, so it's understandable that Ubuntu can't by default do the same

i've tried double click the volume setting, and adding things in there. i just can't figure out how to get the other speakers working, or to enable surround sound at all..

i have the creative sound blaster audigy card, hope that helps too as it was mentioned in another thread

a little help, if possible, would be appreciated... sorry for asking such a stupid question

---

### Post by shad0w_walker on 2008-02-17
Most of the time Ubuntu will have recognised you have 5.1 sound but it is upto applications to use it. What are you trying to play that is 5.1? I'm assuming a DVD or similar, whatever you are trying to play, let us know and tells us what you are playing it in. It normally just requires a quick selection in the options to get it running properly.

---

### Post by masque7 on 2008-02-18
actually I was trying to listen to mp3s in amarok, i checked playback in amarok and i didn't see any option for it

---

### Post by masque7 on 2008-02-18
[QUOTE=Craga_89
]Hey guys, just in case you still haven't figured it out heres how to get surround sound working. I'm running a Realtec sound card.

Open up your gnome sound control using:
gnome-volume-manager
Go to the Edit menu and choose Preferences... to open up slider choices.

Scroll down the list checking these off as you go (if they're not already):

Surround
Duplicate Front

Unmute the Surround slider if it's muted and turn it up to a reasonable level, around the same as your PCM or Master volume. Then navigate to the Switches tab and check Duplicate Front.

Alternative:
Open up alsamixer in gnome-terminal:
alsamixer
Use your arrow keys to scroll to and turn up Surround, then scroll to Duplicate Front and press the m key to unmute ([00] Symbol).

Command-line junkies
For all you who love the command line, heres one command (or rather 2-in-1) to do it all for you ;).
amixer sset Surround 90%; amixer sset 'Duplicate Front' toggle

Congratulations! You should now have surround sound in all of your applications ;).[/QUOTE]
I'm going to give the above a try. Just posting this here in case anyone else comes across my thread

---

### Post by masque7 on 2008-02-19
okay sadly still no luck, but however i've been trying to use [this thread](http://ubuntuforums.org/showthread.php?t=184814), can anyone help an *absolute beginner* how to make the script and the .asoundrc file?

i'm assuming i create both in /home/masque7? just not sure how, especially the script part

again, i'm trying to get amarok to play mp3s in 5.1... or duplicate the sound into the other speakers so they're all playing

thanks in advanced
masque7

---

### Post by masque7 on 2008-02-20
hi again guys,

sorry to bump the thread, i'd just really like to 'duplicate' the sound into the other speakerss via that script (if possible).. just really not sure how i go about it and creating the .asoundrc file.. and where i put them

any help would be appreciate, i know mp3s aren't necessarily 5.1 surround, i'd just like to get sound from all of my speakers.. in this case, i'd like to get the 'rear' and 'sub/bass' working 

again, you had to enable this option in windows via the Creative EUX settings. '3d surround sound for mp3s/music files'.. something like that. I'm sure there's a way to do it, but i know it's not going to be simple

Any help would be appreciate
Thanks in advanced

---

### Post by shad0w_walker on 2008-02-20
On my desktop you can double click on the volume control (In the system tray/notification area) and it will pop up the volume control program. When you get into the program have a look in Edit -> Preferences. There will probably be a big list of tick boxes, I would tick them all so you have full access to all your sliders, switches, etc. Hopefully there will be a new tab appear that says 'Switches' and in there an option to tick that will duplicate the front audio to the rear speakers.

---

### Post by masque7 on 2008-02-21
> **shad0w_walker said:**
> On my desktop you can double click on the volume control (In the system tray/notification area) and it will pop up the volume control program. When you get into the program have a look in Edit -> Preferences. There will probably be a big list of tick boxes, I would tick them all so you have full access to all your sliders, switches, etc. Hopefully there will be a new tab appear that says 'Switches' and in there an option to tick that will duplicate the front audio to the rear speakers.
Yeah, I've tried what you said before I started this thread.

Eventually you do get a box for 'duplicate sound', just doesn't do anything. Thanks anyway though.

I think that aforementioned script is the only way to get it working. Only thread I've read where someone's had success anyway. Just a shame I don't undestand what I'm doing with it. :(

---

### Post by Afkpuz on 2008-02-25
Here are the simple commands.  I'll explain them too.  Ready to take some notes?

Open a terminal Applications>Accessories>Terminal



Paste in
```
sudo gedit ~/.asoundrc

```


This command will open up a text editor (gedit) and edit the file listed after it.  "~" is short for your home folder.  If this text editor finds that the file you're calling for doesn't exist, it will create it for you and give you a blank doc. 

Then paste into the file:
```
pcm.!default {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    route_policy duplicate
}
```

To get 5.1 in DVDs (I've only tried it in VLC), Paste this into the same file a few lines below the other stuff.

```
pcm.analog {
    type plug
    slave analog_slave;
}

pcm_slave.analog_slave {
        pcm surround51;
        format S32_LE;
}

```

Click save.  close that window and log-out and then back in. (CRTL+ALT+Backspace)


That should configure duplication in your speakers.  If you want to watch movies with 5.1 surround in VLC, open VLC and goto Settings>Preferences.  Click the Audio arrow, then the Output modules arrow.  Make sure that is set to "ALSA", then click on the "ALSA" section (under output module arrow) on the left.  Make sure you have your sound card selected here.  Save and return to the main  screen.  Start your movie and select 5.1 in the dvd's audio menu.  then once the dvd is playing (it doesn't work until your out of the menu and into the movie itself, Click on Audio>Audio Device>5.1

That should do it for you.  Hope it works.

---

### Post by masque7 on 2008-02-26
> **Afkpuz said:**
> Here are the simple commands.  I'll explain them too.  Ready to take some notes?

Open a terminal Applications>Accessories>Terminal



Paste in
```
sudo gedit ~/.asoundrc

```


This command will open up a text editor (gedit) and edit the file listed after it.  "~" is short for your home folder.  If this text editor finds that the file you're calling for doesn't exist, it will create it for you and give you a blank doc. 

Then paste into the file:
```
pcm.!default {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    route_policy duplicate
}
```

To get 5.1 in DVDs (I've only tried it in VLC), Paste this into the same file a few lines below the other stuff.

```
pcm.analog {
    type plug
    slave analog_slave;
}

pcm_slave.analog_slave {
        pcm surround51;
        format S32_LE;
}

```

Click save.  close that window and log-out and then back in. (CRTL+ALT+Backspace)


That should configure duplication in your speakers.  If you want to watch movies with 5.1 surround in VLC, open VLC and goto Settings>Preferences.  Click the Audio arrow, then the Output modules arrow.  Make sure that is set to "ALSA", then click on the "ALSA" section (under output module arrow) on the left.  Make sure you have your sound card selected here.  Save and return to the main  screen.  Start your movie and select 5.1 in the dvd's audio menu.  then once the dvd is playing (it doesn't work until your out of the menu and into the movie itself, Click on Audio>Audio Device>5.1

That should do it for you.  Hope it works.
I really can't thank you enough! :)

i changed the Amarok engine to alsa 5.1. I then used GNOME ALSA MIXER, and turned a few of the options up, and I now have mp3s coming from all speakers! :D

---

### Post by masque7 on 2008-02-29
so it lasted 2 days... I now have no sound at all. None. Not from any audio, or video. Were some 'volume' updates, I didn't do them. Did them anyway since sound wasn't working at all.

Any ideas?

*EDIT*: after a couple reboots it's back again. strange...

---

