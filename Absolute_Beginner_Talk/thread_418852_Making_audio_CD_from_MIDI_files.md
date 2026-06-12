---
title: "Making audio CD from MIDI files"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by paker on 2007-04-22
I have several MIDI files (.mid) downloaded to Desktop. I want to burn an audio CD from them. Can someone explain to me how it can be done? I can play the files with timidity. That's as far as I can go. Audacity does not open it. Neither does Rosegarden. Ararok and KMid cannot play the file. I even installed the linux kelnel of low latency (because Rosegarden complained about timing resolution being not good enough). 
Thanks.

Someone suggested to run timidity from terminal: timidity *myfilename.mid* -ow  This didn't work. -ow is not identified.

FYI: Ubuntu Feisty 32bit version

---

### Post by paker on 2007-04-22
I have a question for those who are familiar with Windows. How difficult is it in Windows to convert midi files to wav or something suitable for audio CD burning? So far, I haven't been successful to do that in Ubuntu and wonder if Windows provides easier means? Thanks.

---

### Post by Jonam on 2007-04-23
Timidity should work. You might want to try using the capital 'O' in front of 'w' instead of lowercase 'o' which has a different meaning. If that doesn't work, post back and I will try it out. 

The method of converting midi files to sound files is either through using the hardware midi synth in the soundcard and recording this or having all the midi wavetables as part of the software and either output these wavetables to the soundcard or direct to file (as Timidity does).

Jonam

---

### Post by paker on 2007-04-23
Thanks for the correction. I will do that this evening at home, and post back.

Let me ask you another, related question. I tried to play a midi file in another program called MIDInight Express under Windows. But the file is missing PRG info accordingn to the error message. Is this a common variation of midi files?
Thanks.

---

### Post by paker on 2007-04-23
Thank you, so much. "timidity myfile.mid -Ow" did it. I am a happy camper now. Thanks again.

---

### Post by Jonam on 2007-04-24
No problem - happy to help.

Jonam

---

### Post by thommango on 2007-04-29
Wow, I'm glad I read this post.  I'm new to linux, but in the windows world I've found few programs can actually do this.  In sonar, you have to play the midi files and record them to another track at the same time.  Sibelius does it, but that's a pricey program.

Glad I read this thread.

thom

---

### Post by Jonam on 2007-04-30
Typing:

timidity --help

will give you all the options this program provides.

Jonam

---

