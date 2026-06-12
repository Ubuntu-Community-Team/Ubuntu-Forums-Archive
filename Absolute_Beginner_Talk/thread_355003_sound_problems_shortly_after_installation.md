---
title: "sound problems shortly after installation"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by shadowboxer_k on 2007-02-06
hello!

i just installed ubuntu a couple of hours ago and it's great! i feel like a kid in a candy store :)

i installed skype and tested out the sound and everything was okay. a while after, i tried to stream some music (flash streams, i installed the plug-in) and the first 10 seconds of the song were fine, when some strange buzzing/crackling sounds started coming out of the computer and the sound stopped. i tried opening other files but no sound comes out at all. however, i can hear the silent static (for lack of a better word) when i play with the volume control - i can hear the (possibility of a) sound going up and down.

will anyone please help me get my sound back? :( 

thank you and sorry for sounding like the complete rookie that i am.

---

### Post by ComplexNumber on 2007-02-06
there are a few things to check.
do you have another sound card inserted as well as the inbuilt one?

also, install alsamixer because it will probably come in handy.

---

### Post by shadowboxer_k on 2007-02-06
nope, i got nothing else installed on my IBM ThinkPad T21. it's really strange, because the sound was going okay till it suddenly stopped.

i will go install what you recommended right away.

thank you!

---

### Post by ^rooker on 2007-02-06
Some webcams and headsets show up as additional soundcards in the system... 

In order to identify such ALSA-device-assignment problems, try running 
$ asoundconf list

This will output:
Names of available sound cards:
I82801CAICH3


You can then define your "default" card like this:
$ asoundconf set-default-card I82801CAICH3


When you run "alsamixer" you can usually get more information about "why silence?".


One more thing: Which application is producing the sound? The global sound settings in Linux don't always apply to all installed programs (e.g. XMMS, Kaffeine, ... have their own sound settings)

---

### Post by ComplexNumber on 2007-02-06
**shadowboxer_k**
i suspect that it may well be a loose connection. now you mention that there is only 1 sound card installed, i don't think its anything software related. i could be wrong, of course, but its just a haunch. i wuls suggest that you check your connections before you do anything.

---

### Post by shadowboxer_k on 2007-02-07
i figured out what was causing the problems!

everything had been going well until i plugged in my ipod. apparently it does recognize the ipod as a second soundcard and hence the conflict. i will play around with alsamixer today and see how that can be fixed. any advice?

thank you so much!

---

