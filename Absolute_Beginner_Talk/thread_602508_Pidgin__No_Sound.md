---
title: "Pidgin:  No Sound?"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by kenwong on 2007-11-04
I clean installed Xubuntu 7.10 onto my machine a couple of days ago.

I have been using Pidgin but have failed to get sound from it.

I did some searches and found some people talking about "aplay %s", "bplay %s".  Don't know what these mean and how to use them.

Any help would be appreciated.

---

### Post by carlosfocker on 2007-11-04
Simple question.  Does the sound work at all?

---

### Post by kenwong on 2007-11-04
Yes, it works, for example, on web pages.

Thanks.

---

### Post by carlosfocker on 2007-11-04
couple things to try.

1. Go to Tools and make sure Mute Sounds is not checked,

2. Try going to Tools-->Preferences.  Then go to the Preferences tab.  Under method select alsa.  See if that works.

3. Go to System->Synaptic Package Manager. 
Select Edit-->Search and search for bplay.  It should be the first package displayed.  (Install by checking checkbox and selecting apply).  
Now go Try going to Tools-->Preferences.  Then go to the Preferences tab.  Under method select command and type in "bplay %s" without the quotes.

---

### Post by kenwong on 2007-11-04
Thanks, carlosfocker, it works now after I made changes you suggested.

However, one problem.

Every time immediately after it plays the tone, there is a piece of sound like "bid".  Why?

---

### Post by kenwong on 2007-11-04
... and one more issue:  The tones are played in very low volume.  But I have already push the volume of my laptop to the highest.

Thanks again.

---

### Post by carlosfocker on 2007-11-04
I'm not sure exactly what you mean by a sound like "bid".

What instruction worked for you?

As far as the tones being played at a low sound, is sound from other applications at an ok level? If not, you may want to download the gui version of the Alsa mixer.  You can do this by  going to **Add/Remove...** under the **Applications** menu, selecting Sound & Video.  Check the box for **Alas Mixer** and select **Apply Changes** to install.  This will place a menu item under Applications-->Sound & Video called Alas Mixer.  Open the app and find the PCM level and raise it to about 80%.  If you raise it to far it may distort your sound.

---

### Post by kenwong on 2007-11-05
Hi carlosfocker,

It was "bplay" that made my Pidgin sing.

The extra sound "bid".  For example, the tone is "do-re-me".  It plays "do-re-me---bid".  Every time the same.  I believe this is abnormal.

I checked alsamixer in Terminal.  PCM has already been set to 80.

---

### Post by kenwong on 2007-11-05
Any help?

---

### Post by nartooki on 2007-11-05
i wasnt able to get sound in pidgin either on a fresh install of xubuntu gutsy, and the bplay also gave me a small blip noise. using "aplay %s" without quotes works just fine though and doesn't have the extra blip.  you should already have aplay installed since it comes with alsa-utils

---

### Post by carlosfocker on 2007-11-05
It's funny i just realized my sound doesn't work either for pidgin.  Did nartooki suggestion work?

---

### Post by kenwong on 2007-11-06
Just changed it to "aplay %s".

Still, there are the small blips but they are lighter than previously when "bplay %s" was used.

And the tones are not played loudly.

Any other ideas?

---

### Post by Dylnuge on 2007-11-06
Go into alsamixer (for a GUI, double click your volume button. If you want to use the command line interface, just go into a shell and type "alsamixer" without the quotes).

Make sure PCM and Master volume are at 100%.

That should raise the volume. Most of the time your volume controls only master and not PCM, which is what causes the problem. If you need/want to link them together, just select them both by right clicking on the speaker icon and choosing prefrences.

---

### Post by kenwong on 2007-11-06
Thanks, Dylnuge.

I raised them to 90 and it is louder now.

So the remaining problem is the blips.

---

### Post by carlosfocker on 2007-11-07
There doesn't seem to be to much info on bplay besides whats in the readme with the install files.  The author states that bplay is beta and may have problems.  I would suggest submitting a bug either here or emailing the author of the program David Monro as he asks in his readme at the following:

[email]davidm@amberdata.demon.co.uk[/email]
[email]davidm@cs.usyd.edu.au[/email]

---

### Post by kenwong on 2007-11-08
But, carlosfocker, does aplay work for you?

---

### Post by superid on 2007-11-16
I'm running Ubuntu Gutsy (7.10) 64-bit, no sound in Pidgin (but audio is fine everywhere else, even in Pidgin's own Sound Test options).

I've tried both aplay and bplay to no avail.
Any ideas?

---

### Post by NomadTW on 2008-02-03
i had this problem... bplay didn't do anything at all, but aplay did

what i find odd is that it worked perfectly from the livecd but not once i actually installed... weird

---

### Post by loudestnoise on 2008-03-27
I have replicated the "blip" sound using bplay. It's fairly loud and annoying, and I'm pretty sure no sound is better than that. aplay does not work for me either. Unfortunate.

---

