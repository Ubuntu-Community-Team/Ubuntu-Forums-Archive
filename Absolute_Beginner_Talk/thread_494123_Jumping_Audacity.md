---
title: "Jumping Audacity"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by RichPicker on 2007-07-06
I can record a mono or stereo track to audacity, no problem.
But when I add the second track, the sound jumps and jerks and pops.
Not knowing much about it, I've tried adjusting the sample rate, the kernel latency, and some other things like muting the software playthru.
But still it's not possible to record a second track - the sound jumps and starts and pops.

Any ideas?

R-

---

### Post by forrestcupp on 2007-07-07
I know this may not be an acceptable answer, but Ardour is really better for multi-track recording.  Audacity is better for recording one track or editing an audio file.

---

### Post by opossumjack on 2007-07-07
Hi RichPicker... do you have enough ram and audiocard memory?
It seems that the system couldn't manage more than 1 audio file...

Have you tried to reduce bitrate for the record file... This could be useful if your sistem could'nt manage big auio files.

---

### Post by opossumjack on 2007-07-07
I agree with forrestcupp.. 
There are lot of programs that give better multitrack support..

---

### Post by RichPicker on 2007-07-07
I can't use Ardour, because I don't understand how to connect/configure Jack, and Ardour needs Jack to run.

I can't say about not having enough RAM. Audacity works almost okay sometimes, and doesn't work well at all on other times. And sometimes it works better with ALSA input/output, and other times with OSS input/output.

I'd like to use Jack, and did have the Ubuntu Studio installed previously, but gave up when it came to configuring Jack. The instructions said it was a matter of trial and error to get it set-up. And there are too many factors I know nothing about in the MIDI - Jack world. I couldn't do it. I asked for help, but got none, so I gave up on it.

I would truly appreciate any and all advice/directions about Jack.

I just now loaded Ardour, but it wont run without Jack. I'll remove it. 

Or maybe another app is available?

Rich

---

### Post by forrestcupp on 2007-07-07
Well, I'll tell you how to get jack and how to try to get it started.  Hopefully it will just work.

First, you need to install jackd and jack's GUI control panel
```
sudo aptitude install jackd
sudo aptitude install qjackctl
```
You should be able to find qjackctl in your menus as "Jack Control".  That is the control panel.  If not just enter qjackctl in the terminal to load it.

Then when the control panel is up, just click the button that says "start."  Hopefully it will remain connected to jack.  If the word "started" in the black box is yellow, you're connected.

Keep this open and run Ardour.  It should work now.

If jack doesn't stay connected, you'll have to mess around with the configurations in the GUI.

---

### Post by RichPicker on 2007-07-07
WOw. It works. Thank you for the magic. 

I pulled my hair out when I had Ubuntu Studio installed, and did every imaginable thing to the jack control config.  but it wouldn't connect. But now it works.

Can you give me a few pointers about Ardour. I'll have to learn it. I clicked the Record, but it just flashes. 

But this is good news. Maybe I can use jack beat and others?

Rich

---

### Post by RichPicker on 2007-07-07
I get sound, and the meters are jumping. But the record button just blinks.

I need too much help. The documentation on the website is frustrating. It describes Ardour well, but no step-by-step instructions on how to use it.

---

### Post by RichPicker on 2007-07-07
Got it. Thanks very much. Now, if I could only play decent. Ha!

---

### Post by RichPicker on 2007-07-07
Well Yeah it works, but sounds horrible. Cracks and pops. I'll do what I can in the config. Otherwise, I'll just use GNOMEsound.

---

### Post by RichPicker on 2007-07-08
Tried Jackbeat, but it does nothing. No sound, nothing.
Disappointment again.

---

### Post by forrestcupp on 2007-07-08
I don't know what jack beat is.  If it happens to be an app for programming drums, you need to try Hydrogen.  It uses wav files for samples, and you mix it down to one wav, then import it into ardour.  If you install it, make sure you install the hydrogen drumkits too.

About your sound problems, do you think it might be too distorted?  If so, try turning down the volume in either alsamixer, or the GUI audio mixer.  If you're using your mic jack for guitar or an instrument, either switch to your line-in jack, or make sure the Mic Boost is turned off.

---

### Post by RichPicker on 2007-07-08
I'll re-install Hydrogen and try exporting to Ardour. Now that Jack is working, I need to start fresh and figure things out. I suspect JackBeat didn't work maybe because it needs to be connected? I don't know yet. I like Hydrogen.

Yes, it's the electric guitar that sounds crackly. It works okay in Audacity and GNUsound. I'll try running it through the guitar effects processor and see what happens. It's not distortion due to too much volume. It's more of a random crackling. I thought maybe the cord was shorting, but it works okay with the other two mixer/recorders. In Ardour, the distortion changes when I change the Latency.

With latency fo 32, I get no sound. At 64, it sounds the best. And at 128 and higher, the crackling sound is the worst.

---

### Post by RichPicker on 2007-07-08
I really should probably just give up.

How do I import a track? I click Edit, then "Import Audio (copy) ... as a new track"
And I get the Ardour Soundfile Selector. But I can not access home/
I can not access anything.
I double-click, and press enter, but I can not open any directories. It remains highligted blue after I click it, but it wiil not open or select anyting in home/

Or, does anyone know how to import a Hydrogen file into GNUsound?

---

