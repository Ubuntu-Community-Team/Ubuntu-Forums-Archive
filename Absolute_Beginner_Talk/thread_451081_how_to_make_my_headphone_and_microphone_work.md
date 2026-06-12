---
title: "how to make my headphone and microphone work ?"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by HunkieChan on 2007-05-21
it doesnt work.. i followed a site's instruction and installed alsa lib,utils,driver but it doesnt do any good .. can anyone please hellp me ?

---

### Post by gradedcheese on 2007-05-22
One approach is to right-click the volume level icon in the upper right hand corner and choose 'open volume control'.  In there, go to Edit-Preferences and enable very meter, switch, option that your card provides.

Now look for checkboxes that have to do with headphone jack sensing, input source (mic vs. analog vs. line-in), and headphones in general... basically experiment.  To test things, I like to do this from a Terminal:

```

arecord > aplay

```

(control-c to kill it any time).  This records and plays back in a loop, so you can have that open in a shell as you play with soundcard options...

---

### Post by HunkieChan on 2007-05-22
ok i have all checked.. so are you saying it has to be a combination and i have to find out which one is and check em out ? is that what you're saying ?

---

### Post by gradedcheese on 2007-05-22
First you enable all of them in Preferences, then you close that window and play with all the sliders, on/offs, etc.  Basically turn on the microphone 'volume', unmute it, make sure the input source is mic, and play around.  Each card is a little bit different.

---

### Post by HunkieChan on 2007-05-22
ok i have like 7 "stuffs" in the preferences which one do i check ? all of em ?

---

### Post by HunkieChan on 2007-05-22
> **gradedcheese said:**
> First you enable all of them in Preferences, then you close that window and play with all the sliders, on/offs, etc.  Basically turn on the microphone 'volume', unmute it, make sure the input source is mic, and play around.  Each card is a little bit different.

okay i try that.. but i have this problem .. when i put in my headphone jack.. i can hear it thru my headphones but at the same time it plays on the speaker .. how can i fix that ?

---

### Post by gradedcheese on 2007-05-22
Ah.  Some soundcards have headphone jack sense, which turns off the speakers, and some don't.  Some let you choose the sound output as 'speaker' or 'jack' (those are all possible checkboxes somewhere)

---

### Post by HunkieChan on 2007-05-22
see i have two tab in the volume controler one of em is playback and other is switches.. playback as 4 option masters, pcm, ext mic, int mic and under switches linein, iec958, intmic... and i tried all combination .. neither my headphone or mic works :(

---

