---
title: "audio problem"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by deivys20 on 2006-04-15
This is my first time trying linux and so far I like it a lot. However, I am having such a awful time trying to get the audio to work. I have a sound blaster live value card with a pair of boston accoustic that uses digital analog. I have read every thread I could find on the subject but I didnt understand half of tutorials for it and the other half didnt work. Can someone help me this? Also can you bear in mind i am a noob so I need my step by step instructions. ](*,)

---

### Post by graigsmith on 2006-04-17
i just posted a how to on this, but it hasn't appeared yet. this should fix all your problems.

in the console type alsamixer to get to the alsa mixer program.
First hit f5.  Then turn up the volume on EVERYTHING. You use the cursors for doing this, press up, and then press right and turn everything up.

If you are having problems, like getting no sound at all.  pay special attention to all the bars to the right of "ac97"  one of the emu10k1 settings in particular needs to be set at 0 otherwise you will get no sound at all.  and some should be enabled.  its best to just disable all of them, and start turning them up till you can hear sound.  if the sound turns off when you start turning the volume on them up, then that is probably one of the ones that needs to be set at zero.

Now. find the "Line" channel, make sure its not muted. hit the spacebar, to enable recording on it.  Scroll over to the caputre channel,  and hit spacebar.  you should now be able to use line in to record in audacity.  yay

Now, Here is the part that took the longest time to figure out.  Find the "Tone" setting, unmute it with m.  Your bass and treble settings should now work.  If turning up bass sounds like a broken speaker with lots of distortion.  just go to the "wave" and set it to 50% or just enuf so that you don't have anymore distortion in the bass.  

mute the microphone channel as well, you get far less noise during playback that way. 

Hope this helps let me know if you run into any problems.

---

### Post by deivys20 on 2006-04-17
I will try that and see if I can get this audio working. Thanks.

---

