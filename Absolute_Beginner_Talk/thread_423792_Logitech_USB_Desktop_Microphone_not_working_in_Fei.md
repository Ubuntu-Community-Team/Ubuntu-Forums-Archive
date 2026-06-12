---
title: "Logitech USB Desktop Microphone not working in Feisty/Skype"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by Emerpus on 2007-04-26
Gentlemen,

I have just installed Ubuntu Feisty and Skype but my microphone doesn't work (at least not with Skype). Is there an easy way to fix this? 
Searching the forums I can see that I am not the only one with this particular problem but the suggested fixes seem a bit complicated for a noob and relate to previous versions of Ubuntu and Skype so I was hoping things might be easier now. Otherwise I understand that I probably need to copy/paste some code into a file called ~/.asoundrc to make it work. If this is the case I hope that someone would be kind enough to tell me where this file is located an walk me through it. Thanks :-)

---

### Post by AmyRose on 2007-04-26
Unfortunately, there is no easy way to do it. Skype is hardwired to use the same card for audio input and output, and the only way to fix that is to use the Skype DSP Hijacker. This worked for me, but please note that it is a bit tricky for new users. [http://195.38.3.142:6502/skype/](http://195.38.3.142:6502/skype/)

Upset? Blame the Skype developers for not releasing the source.

---

### Post by Emerpus on 2007-04-26
Thanks Amy (and I am sorry for calling you a gentleman if that term is somewhat inappropriate in your case - I meant it the nicest way possible!).

I just need to understand why this is necessary when it seems possible to specify different sound devices for Audio in and Audio out in Skype->Tools->Preferences->Sound Devices? Does this have to do with something else? Btw. do you have the exact same microphone as I do or could it be that my problem is different?

Great to find female friendliness in here anyhow. ):P

---

### Post by murmelhunter on 2007-06-26
Can you please let me know how does your Mike shows up in the device manager?

In case if your Microphone is called AK 5370 please try this:

Ensure if your microphone is switched on green LED of the switch is illuminated,
if not press the switch once normally the green led with turn on.

Go first to Applications => Sound & Video => Soundrecorder

Click on file and open the Volume control

Now click on file and change device into AK 5370, once it done move the volume bar of the microphone nearly to the max.

Now start Skype and open the option menu select here the sound devices

ensure that following sound device for sound in is selected: AK5370     (plughw;default,0)

Make a test call and normally you can here you voice now and can call now perfectly.

---

### Post by carloslosgrande on 2007-06-26
Hi, if you put this in the terminal;
> vumeter -r &
you'll get a little meter showing on your screen showing if the mic is picking up anything. Sometimes with skype the mic works fine but not in skype. I've had ongoing trouble.

---

### Post by nburles on 2007-07-03
> **murmelhunter said:**
> Go first to Applications => Sound & Video => Soundrecorder

Click on file and open the Volume control

Now click on file and change device into AK 5370, once it done move the volume bar of the microphone nearly to the max.

Now start Skype and open the option menu select here the sound devices

ensure that following sound device for sound in is selected: AK5370     (plughw;default,0)

Make a test call and normally you can here you voice now and can call now perfectly.

Works perfectly having done this, and very easy!  Thanks :)

---

### Post by ry4n on 2007-07-03
> **murmelhunter said:**
> Can you please let me know how does your Mike shows up in the device manager?

In case if your Microphone is called AK 5370 please try this:

Ensure if your microphone is switched on green LED of the switch is illuminated,
if not press the switch once normally the green led with turn on.

Go first to Applications => Sound & Video => Soundrecorder

Click on file and open the Volume control

Now click on file and change device into AK 5370, once it done move the volume bar of the microphone nearly to the max.

Now start Skype and open the option menu select here the sound devices

ensure that following sound device for sound in is selected: AK5370     (plughw;default,0)

Make a test call and normally you can here you voice now and can call now perfectly.

I have done this and i still can't record???help me 
:(

---

### Post by djaquay on 2007-08-11
Thanks, murmelhunter.  That did the trick.  Would be nice if it wasn't such an obscure thing, (i.e. if it showed up in alsamixer, which is what I was used to using).  Anyway, thanks again.

Dave

---

