---
title: "Low sound in Mplayer"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by U5tabil on 2007-03-18
My sound is realy low i think in mplayer, and others for that mather.
My reciver is on -20 the sound is good when playing music in amarok but a litle low here to, but when watching a movie in Mplayer i need to set the reciver to -0 before it is the same as -20 when playing music. iv set the sound master to 80% and the Mplayer to 80% the same in amarok. Is it my soundcard that is just crap since its integraded?

Anyone know what is wrong?

---

### Post by gilgongo on 2007-03-18
I don't know if this is your problem, but what worked for me is this:

1. Open a terminal
2. Type "alsamixer" 
3. You will see an application that looks like it came out of the 1980s.
4. Use the arrow keys to navigate to the PCM volume and turn it up, or unmute it (using the "m" key) if necessary. You may have to mute other things too.
5. Hit Esc to save and see if you now have better sound.

---

### Post by U5tabil on 2007-03-18
> **gilgongo said:**
> I don't know if this is your problem, but what worked for me is this:

1. Open a terminal
2. Type "alsamixer" 
3. You will see an application that looks like it came out of the 1980s.
4. Use the arrow keys to navigate to the PCM volume and turn it up, or unmute it (using the "m" key) if necessary. You may have to mute other things too.
5. Hit Esc to save and see if you now have better sound.


Hey thanks that helped ALOT!! and yeah that realy looked like it came out in the 1980`s :lolflag: 

But i think that to get even better sound i need to get a better card, any sugestion about what sort that should be?

---

### Post by gilgongo on 2007-03-18
Glad that did it - lots of people seem to have that problem, so I suppose it's sound card related. I have a Dell Dimension 5100 with a built-in sound card (can't remember what), but then I don't have much need to good quality sound, just sound. 

Perhaps there are some audio gurus out there who can reccomend a good card?

---

### Post by U5tabil on 2007-03-18
I Have a Dell to but a Dimension 4600. I have the PC connected to my 37" LCD TV. So i use the computer alot to watch movies, and listen to music alot. So good quality is needed. And since my soround set is quit expencive a 5.1 set with a 7x150watt reciver and so on i migth get a good soundcard to weigth up for the other setup. Do i seem to be in a "dead" zone at the time and a big lack og money after a big 1600$ dollar speed ticket....

---

### Post by DougieFresh4U on 2007-03-18
Just to add my 2 cents worth. I found an old Sansui Stereo Receiver (has the tubes in it) and I have routed my music from computer through it,  and a nice set of speakers and WOW!! what killer sound comes out!!  :guitar:  Also when I have to use headphones (I live with grandpa) I plug them into that old receiver and sound is great. **BTW:** I should mention that the computer I am using for all this is a Dell OPTIPLEX  GX50 with an old Intel motherboard.

---

### Post by U5tabil on 2007-03-19
I think i should look for a card that has S/PDIF since my Reciver have this. I dont know much about S/PDIF but after what i have heard that i suposed to give more cleaner sound?

---

### Post by nick1 on 2007-05-20
Greetings,

I too am experiencing low sound when using MPlayer to play a DVD.

_System Specs:_
-Dell Latitude D820
-Intel Core 2 Duo
-sound card: HDA Intel
-sound chip: SigmaTel STAC9200
-Ubuntu 6.06 LTS Dapper Drake
-Kernel version 2.6.15-28-686
-MPlayer version 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8

_I have tried the following:_
1.) running alsamixer at the console shows that all levels are at maximum.
2.) double-clicking the Volume Contol in Gnome shows that all levels are at maximum.
-all columns are checked.
-active device (File > Change Device) is set to HDA Intel (Alsa mixer)
-leves for SigmaTel STAC 9200 are also set to maximum
3.) volume slider in MPlayer is set to maximum (far right)

I'm really stumped on how to resolve this problem.  I know for a fact that the volume of this DVD should be louder then it currently is while playing in MPlayer.

Thank you for your time,

---

