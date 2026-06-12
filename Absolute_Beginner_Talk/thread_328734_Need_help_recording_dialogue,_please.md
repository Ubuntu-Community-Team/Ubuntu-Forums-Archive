---
title: "Need help recording dialogue, please"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by L Campbell on 2006-12-31
I have a headset which works well with Gizmo and Skype.

It also works well with the little movies from Metacafe.

I have found that I can record my voice in a .wav file.

My question is, what do I need to do in order to record about 5 mins. of dialogue from a Metacafe movie, in a .wav file?

Thanks.

---

### Post by logos34 on 2006-12-31
The easiest way would probably be to use Gnome Sound Recorder (or its KDE counterpart).

Gsr is connected to Sound Juicer, so you have to set your preferences there, but in the case of a .wav file not much to set.  

You'll have to set gsr input as 'mix'.  Just make sure your Capture isn't muted in alsamixer.  
These are Flash videos, so I think you'll have to record it as it comes through your soundcard.  Maybe someone else knows how to rip flash audio streams.

---

### Post by L Campbell on 2006-12-31
> **logos34 said:**
> The easiest way would probably be to use Gnome Sound Recorder (or its KDE counterpart).

Gsr is connected to Sound Juicer, so you have to set your preferences there, but in the case of a .wav file not much to set.  

You'll have to set gsr input as 'mix'.  Just make sure your Capture isn't muted in alsamixer.  
These are Flash videos, so I think you'll have to record it as it comes through your soundcard.  Maybe someone else knows how to rip flash audio streams.

Thanks, I can see how to set gsr for .wav files but cannot find the term 'mix' anywhere.

Also, by looking at the manual, I can't see any reference to anything other than using the CD ROM drive.

What am I missing here?

---

### Post by logos34 on 2006-12-31
you're looking in the  'record from input' dropdown menu?

---

### Post by logos34 on 2006-12-31
what version of gsr are you using? Mine's 2.16.1.

---

### Post by L Campbell on 2006-12-31
> **logos34 said:**
> you're looking in the  'record from input' dropdown menu?

Thanks again.

I did:-  Applications -> Sound & Video -> Sound juicer CD Extractor

The Sound juicer window opens and I see:- Disc,  Edit,  Help

Under Edit I go to Preferences, where I set Format to Voice Lossless (WAV audio) but I do not see the option you suggested.

Am I in the wrong screen?

---

### Post by logos34 on 2006-12-31
No, you should be in gsr.  

In gnome sound recorder: right above the 'record as' dropdown box where you chose 'Voice, lossless WAV audio) there's the 'record from input' box and inside at the bottom is the 'mix' and 'mix mono' selection.  If not, then maybe you're still running the older gnome desktop with a slightly diff gsr.

---

### Post by L Campbell on 2006-12-31
> **logos34 said:**
> what version of gsr are you using? Mine's 2.16.1.

Ahh!

Mine is 2.14.4

---

### Post by deadgobby on 2006-12-31
You can use Audacity too to make a wave file. If you mess up, you can edit a word out and record at that punch out.
GObby

---

### Post by logos34 on 2006-12-31
what about under 'File' at top left?  No preferences or settings where you can choose your input source?

---

### Post by L Campbell on 2006-12-31
> **logos34 said:**
> what about under 'File' at top left?  No preferences or settings where you can choose your input source?

It doesn't have a 'File' menu on the sound juicer page.

Maybe I can get the updated version that you have from EasyUbuntu ?

---

### Post by L Campbell on 2006-12-31
> **L Campbell said:**
> It doesn't have a 'File' menu on the sound juicer page.

Maybe I can get the updated version that you have from EasyUbuntu ?


OK, I've got the newer version on my destop and will try to install it.

---

### Post by logos34 on 2006-12-31
before you do that just start some video or audio and hit the record button.  Then try to play it back.  If it works you can use it to record the audio from flash video.

---

### Post by L Campbell on 2006-12-31
> **logos34 said:**
> before you do that just start some video or audio and hit the record button.  Then try to play it back.  If it works you can use it to record the audio from flash video.


The problem with that is that I have NO video or audio disks.  I just haven't developed an interest in any of that stuff yet.   :-)

---

### Post by logos34 on 2006-12-31
just start a video playing from metacafe.  Hit the record button,  Does it work?

---

### Post by L Campbell on 2006-12-31
> **logos34 said:**
> just start a video playing from metacafe.  Hit the record button,  Does it work?

When I'm actually in 'Sound juicer', I do not see any option to record.

When I go to Apps -> Sound & video -> Sound Recorder,  there is the 'Record' button but clicking this when the Metacafe video is playnig, doesn't record anything.

---

### Post by logos34 on 2006-12-31
your volume is probably muted (does it to me all the time).

Try again, but first (in gsr) click File>open volume control or go to the speaker icon/master volume and right click on it and choose 'open vol contrl' .  In the vol control window that pops up look for the Capture tab and make sure there's no red 'X' at the bottom and the sliders are all the way up.  If you dont see a capture tab, click edit>preferences and check the box for 'capture'. 
 
hopefully that will work.

Whew, this is getting involved!

---

### Post by L Campbell on 2006-12-31
> **logos34 said:**
> your volume is probably muted (does it to me all the time).

Try again, but first (in gsr) click File>open volume control or go to the speaker icon/master volume and right click on it and choose 'open vol contrl' .  In the vol control window that pops up look for the Capture tab and make sure there's no red 'X' at the bottom and the sliders are all the way up.  If you dont see a capture tab, click edit>preferences and check the box for 'capture'. 
 
hopefully that will work.

Whew, this is getting involved!

Thanks, all these instructions are applied but I still can't get a recording.

If I try to install the latest Sound juicer (v 2.16.2) what code should I use?

This has not worked for me:-

qwer@qwer-desktop:~/Desktop$ sudo apt-get install sound-juicer-2.16.2
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sound-juicer-2.16.2

It definitely IS on my desktop.   :-)

---

### Post by logos34 on 2006-12-31
Forget Sound Juicer, close it...just focus on Gnome Sound Recorder/gsr...Follow what I said above and tell me if it works.  your recording vol/capture is probably muted.  Just go to your master volume/speaker icon on your desktop panel (next to clock) and right click and select 'open volume control'.
And then click on the capture tab or click on edit>preferences and check the box for "capture"

---

### Post by L Campbell on 2006-12-31
> **logos34 said:**
> Forget Sound Juicer, close it...just focus on Gnome Sound Recorder/gsr...Follow what I said above and tell me if it works.  your recording vol/capture is probably muted.  Just go to your master volume/speaker icon on your desktop panel (next to clock) and right click and select 'open volume control'.
And then click on the capture tab or click on edit>preferences and check the box for "capture"

Thanks,I know this must be frustrating for you and I do appreciate your efforts.

Using Sound Recorder (not juicer) and with the Volume control not muted, I still get nothing.

I do notice that, when I close and then re-open, Volume controll, the microphone and CD (under 'Capture tab) do become muted again.  So when I was trying to record, I did keep the Volume control window open.

Its probably time for me to give this a rest, till tomorrow.

Kind regards.

---

### Post by logos34 on 2006-12-31
Ok, thanks!.  You're close though to getting this working,  It usually ends up being a volume setting somewhere.

Happy New Year!

---

