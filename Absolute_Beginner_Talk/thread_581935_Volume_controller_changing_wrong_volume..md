---
title: "Volume controller changing wrong volume."
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by Gdobbs on 2007-10-19
I recently installed Gutsy, and I've certainly had less problems with it than I did with Feisty. The only problem I have now is the volume control changes "IEC958 C". I went into alsa mixer and "IEC958 C" moves up and down as I move the volume slider, but what acually controls the volume is "Analog F". How can I make the volume slider on my desktop change "Analog F" instead of "IEC958 C"?

---

### Post by argie on 2007-10-20
I'm not sure about Gutsy, but it's probably similar to Feisty here. Just Right Click on the Volume Control panel applet and select Preferences (*Don't Open the Volume Control dialog and then go to preferences*).

---

### Post by Gdobbs on 2007-10-20
All the options still only control the first bar in alsamixer (which doesnt seem to control the sound)

[img]http://img88.imageshack.us/img88/5169/screenshotmw8.png[/img]

I want the volume control to change "Analog F", as thats what acually changes the sound. Changing my preferances did nothing.

---

### Post by Gdobbs on 2007-10-20
Anybody?

---

### Post by argie on 2007-10-21
Hmm, changing the default in the Preferences dialog doesn't help? Do you have more than one sound card?

---

### Post by rico2k_uk on 2007-10-21
i have the same issue - i only have 1 soundcard also. it jsut the keyboard is altering the wrong volume control. however manually changine the speaker icon on the top bar does work.

---

### Post by argie on 2007-10-21
Oh, does System » Preferences » Sound help then?

---

### Post by rico2k_uk on 2007-10-21
nope.

---

### Post by drmatty on 2007-10-21
I've been having the same problem with my laptop.

---

### Post by shad0w_walker on 2007-10-21
Using the Preferences > Sound dialog should work. Try finding all the sliders that control your volume (I have about 4 because i have 5.1) and ctrl + click to select each of the ones you need, this will make the keyboard volume button change all those volumes at once.

BTW
Have you tried checking the PCM volume slider? That generally changes the volume level for everything.

---

### Post by Gdobbs on 2007-10-25
I have tried every slider, I can find for volume and can only get it to change by going into also mixer and changing it.

---

### Post by ashughes on 2007-10-30
I was having the same problem.  Not just with my laptop either, with the onboard sound for my desktop as well.

This is what worked for me:
1. Click on System>Preferences>Sound
2. On the Devices tab, under the Default Mixer Tracks section, make sure your sound device is selected - mine was HDA Intel (Alsa Mixer)
3. Make sure PCM is the only track selected

Hope this helps.

Cheers.

---

### Post by drmatty on 2007-11-03
> **ashughes said:**
> 

This is what worked for me:
1. Click on System>Preferences>Sound
2. On the Devices tab, under the Default Mixer Tracks section, make sure your sound device is selected - mine was HDA Intel (Alsa Mixer)
3. Make sure PCM is the only track selected

Hope this helps.

Cheers.

Thanks! This solved the problem for me!

---

