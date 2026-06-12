---
title: "A few issues."
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by Bushido989 on 2007-07-29
I just installed Ubuntu on my main box. When I installed it on my old box, I had no issues but this time around, things didn't go so well.

I have the realtek acl 880 chipset thing. Though my problem is just like the ones previously posted (Sound from speakers but not from headset) I seem to be unable to fix it. I was hoping for more detailed information on how some people got it working.


Thank you in advance.

---

### Post by FleetAdmiral74 on 2007-07-30
Can you link to these previously posted threads you mention?

So...does your headset just use the headphone male plug, like the one you would find on comp speakers or headphones? Or is it a USB one.

---

### Post by Bushido989 on 2007-07-30
Here are a couple I managed to find again :

[http://ubuntuforums.org/showthread.php?p=2921058&highlight=alc880#post2921058](http://ubuntuforums.org/showthread.php?p=2921058&highlight=alc880#post2921058)
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Yes, my headset is using male jacks. My two front jacks (mic and headphones). It seems as though they are just not installed. Well, at least, I can't get anything from them.
I can mess around with sound volume and the sound preferences but I just can't send or recieve sound through there.

---

### Post by Bushido989 on 2007-07-30
bump

---

### Post by asmoore82 on 2007-07-30
on many new sound chips front panel stuff gets its own channel in hardware, which in turn leads to a separate volume control in software

Double click on your panel volume control and play with everything in the alsamixer
you may have to 'Edit->Preferences' and give yourself even more sliders.

if you don't have the volume control on your panel you can run it from a terminal ...
```
~ $ gnome-volume-control
```

---

### Post by Bushido989 on 2007-07-30
I already had volume control. 

Devices in there are the HDA Intel (Alsa Mixer) and Realtek alc880 (OSS Mixer) I've toyed with both.

---

### Post by Bushido989 on 2007-07-30
bump.

---

### Post by ugm6hr on 2007-07-30
```
alsamixer
```
Use left/right/up/down arrow-keys to maximise all the controls.
Use "M" & left/right arrow-keys to unmute all the controls (mute=MM; unmute=OO).

Then try again.  The microphone might require an extra bit of tweaking.  If it doesn't work - post a screenshot of alsamixer.

---

### Post by asmoore82 on 2007-07-30
> **Bushido989 said:**
> I already had volume control. 

Devices in there are the HDA Intel (Alsa Mixer) and Realtek alc880 (OSS Mixer) I've toyed with both.

you only need to use the AlsaMixer ...

but did you 'Edit->Preferences' and turn on all the other sliders?

---

### Post by Bushido989 on 2007-07-30
> **ugm6hr said:**
> ```
alsamixer
```
Use left/right/up/down arrow-keys to maximise all the controls.
Use "M" & left/right arrow-keys to unmute all the controls (mute=MM; unmute=OO).

Then try again.  The microphone might require an extra bit of tweaking.  If it doesn't work - post a screenshot of alsamixer.

This might be the problem.

[IMG]http://img.photobucket.com/albums/v713/Bushido69/Screenshot-1.png[/IMG]
These last three inputs, I can change they're label. "Line" "mic" "front mic" stuff like that. I can't adjust their volume though. 

[IMG]http://img.photobucket.com/albums/v713/Bushido69/Screenshot.png[/IMG]
For the headphones, though unmuted, I can't seem to adjust the volume. The others work fine.

---

### Post by ugm6hr on 2007-07-30
Have you tried headphones with all volumes maximised / umuted?  My alsamixer headphone volume doesn't actually correspond to the headphones - yours might be the same.

The Input Source settings are for microphone / CD line-in etc - so don't affect internal file playback.

---

### Post by Bushido989 on 2007-07-30
> **asmoore82 said:**
> you only need to use the AlsaMixer ...

but did you 'Edit->Preferences' and turn on all the other sliders?

And yes all the sliders are on and maxed out. However, in the alsa mixer, some sliders I can't seem to adjust like the three inputs and headphones.

---

### Post by Bushido989 on 2007-07-30
bump-ahoy

---

### Post by Bushido989 on 2007-07-30
Another bump :(

---

### Post by Bushido989 on 2007-07-30
I take it nobody has an answer?

---

### Post by Bushido989 on 2007-07-30
*sigh* Thank god I dual boot.

---

### Post by ugm6hr on 2007-07-30
Are you sure the headphones work?

If it is important that you have headphones - just plug them into the speaker out socket.  That will definitely work (given the speakers work).

And another thought - how many sound cards do you have installed?

---

### Post by Bushido989 on 2007-07-30
> **ugm6hr said:**
> Are you sure the headphones work?

If it is important that you have headphones - just plug them into the speaker out socket.  That will definitely work (given the speakers work).

And another thought - how many sound cards do you have installed?

The headphones work when plugged into the speakers. 1 soundcard.

---

### Post by Acglaphotis on 2007-07-30
Have you tried installing a new version of alsa?

---

### Post by diatribe on 2007-07-30
> **Bushido989 said:**
> The headphones work when plugged into the speakers. 1 soundcard.

so...you need the speakers and headphones plugged in at once?  else I think you have your answer

---

### Post by Bushido989 on 2007-07-30
> **diatribe said:**
> so...you need the speakers and headphones plugged in at once?  else I think you have your answer

Well, switching from watching movies to playing Cs, it would be useful. 

And yes, I do have the latest Alsa.

---

### Post by ugm6hr on 2007-07-30
Are you certain the headphone socket works?  Have you tried it in another OS?  It seems very unusual that one output should work correctly, and the other does not...

---

### Post by Bushido989 on 2007-07-30
> **ugm6hr said:**
> Are you certain the headphone socket works?  Have you tried it in another OS?  It seems very unusual that one output should work correctly, and the other does not...

Yup, everything works fine on my xp side.

---

