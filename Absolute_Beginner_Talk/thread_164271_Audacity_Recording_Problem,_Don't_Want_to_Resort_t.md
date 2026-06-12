---
title: "Audacity Recording Problem, Don't Want to Resort to WINXP"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by gigi1234 on 2006-04-22
I am trying to use Audacity to record audio input from the line-in on my Thinkpad laptop.

I am new to audio recording but I have managed to make the recordings in Windows but I would much rather stick with Ubuntu if possible since I hardly use my Windows partition anymore.

In Ubuntu my soundcard works, the drivers are there, and I have no trouble with other audio-related tasks.

In Audacity it seems like the line-in input is not being recognized. When I go into preferences and try to set the I/O settings, there are no choices for playback or capture except /dev/dsp. So I am at a loss at how to set my input and output settings. Or maybe it is something else. But the program is recognizing any input sound. 

Other programs I have tried (gramofile, sound recorder) don't seem to work either.

Please someone save me from having to reboot my Windows partition!

---

### Post by jazzmuzik on 2006-04-22
I've had a lot of problems setting audio in Audacity as well. But try double clicking on the speaker icon at bottom right. Look at the Capture tab. Maybe something needs to be enabled there (click the speaker or mic icons), but I never quite figured it out completely.

---

### Post by gigi1234 on 2006-04-22
Yeah. I have also tried a simple command-line recording tool called gramofile and I have the same problem: no audio is being recognized from line-in.

Anyone else have any ideas?

---

### Post by BoyOfDestiny on 2006-04-22
[QUOTE=gigi1234]Yeah. I have also tried a simple command-line recording tool called gramofile and I have the same problem: no audio is being recognized from line-in.

Anyone else have any ideas?[/QUOTE]

Are you sure the sound the isn't muted? Double click the speaker icon (in gnome it should be on top right), check the volume on line-in.

the other option, in a terminal try 
sudo killall esd

See if that fixes it...

---

### Post by Dr Von Bon Bon on 2006-04-22
Yeah something like this happened to me:

Before opening Audacity go to the command line and type:

killall esd

(add the sudo at the beginning if you need it)

There is also a problem with recording mono tracks over one another and to recitify this change the recording to stereo.

I hope that works.

---

### Post by gigi1234 on 2006-04-22
Wow this is really frustrating.

I am ABSOLUTELY sure it is not the volume levels.  I have set line-in 
And I can hear the input audio too.

I tried the killall esd, no luck.

Not sure what else to try.

But thanks all for suggestions.

---

### Post by gigi1234 on 2006-04-23
Okay, could this be the problem?

I opened the sound mixer and just started clicking on choices. When I select "ADC" the input starts to register.

What is this???

---

