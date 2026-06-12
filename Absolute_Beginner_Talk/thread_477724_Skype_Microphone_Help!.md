---
title: "Skype Microphone Help!"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by alecwh on 2007-06-18
I have a logitech headset, and I also have Skype on Ubuntu.

When I call the Test Call, I can't hera myself, it doesn't pick up my mic. 

Can someone help?

EDIT: I can BARELY hear myself. BARELY. I don't know how to fix this.

---

### Post by aktiwers on 2007-06-18
Try Clicking on the sound icon in your top panel. Can you turn up your Mic there?

---

### Post by alecwh on 2007-06-18
now all I hear (in the skype test call) is static. :(

---

### Post by alecwh on 2007-06-18
I made the mic work, so Ubuntu can hear it (I've tested it.) It's a problem with skype, but I don't know what.

---

### Post by alecwh on 2007-06-18
Ok, here's what's happening: I've turned my mic all the way up, and I've made it output to my headphones, so I can hear myself when I talk inside the mic.

When I go into skype, and call the skype test ing service, I have to YELL into my mic for me to BARELY hear myself.

I have no idea what's wrong, can someone help?:

---

### Post by aktiwers on 2007-06-18
Have you looked in the skype settings? Maybe there is something you can turn on in there?

Or go back to the sound Icon and click it (the one in the panel) and pick:
Edit => Preferrences

Now look if something is missing. Maybe it will help you if you turn on the Mic Boost (+20dB).

Its just a guess.. but worth trying.

---

### Post by johnfarrow on 2007-08-03
Have you found a solution.  I have  the same problem exactly

---

### Post by sailor2001 on 2007-08-03
right click on your sound icon...open volume con trol... edit prferences....tic mic select...tic mic 2 if you are plugged into front of tower

---

### Post by startherepodcast on 2007-08-03
Try Running 

```
alsamixer -cX
```

Replace X with a number probably 1, 2 or 3 until you find the correct device.

Push the tab key and you will see capture is selected then just turn up the volume.

Hope this helps

Adsized

EDIT: The Method Above Should Work To.

---

### Post by scawa on 2007-10-31
I am having the same problem.

I can't get ANY sound through the microphone.

I am using KBUNTU 7.10.
Using Skype and also my Logitech Quick Cam with Kubuntu/Ubuntu are the two things that are keeping me from ditching WIndows and using Kubuntu full time.   But I need those two pieces of hardware for work.

What I see is lots of suggestions all over the place, but none that ever were successful in getting either to work.   Shouldn't be this hard.

Stephen McConnell

---

### Post by samuliri on 2007-11-01
Have you check this:

[http://ubuntuforums.org/showthread.php?t=143512](http://ubuntuforums.org/showthread.php?t=143512)

---

### Post by jaredssix on 2008-02-04
This worked for me:

open volume via the speaker icon (right click icon at upper right of monitor)

Edit >> Preferences

Check Mic Boost (+20dB)

Close the window, and select the "Switches" tab in the volume control window

Check Mic Boost (+20dB)

---

### Post by meteozguz on 2008-04-27
I fixed my mic problem but now
the output sound comes from at the headset and the speakers at the same time...
I tried to specify sound output it didnt work
any help? thanks


Volume Control: HDA Intel (Alsa mixer)
Switches tab -> headphone checked
Options -> Input source Front Mic/Mic

Prefenrences ->

checked -> Master/Headphone/PCM/FRONT/FRONT LINE/FRONT MIC/MICROPHONE/MIC BOOST /INPUT SOURCE

---

### Post by trippinnik on 2008-04-29
How did you fix the mic input? I've got a similar onboard intel sound with mic and headphone jac in the front and outputs in the back, but use the front for headphone and mic but can't get mic to pick anything up.  I've turned up the volume on every input/mic volume setting I could find.

---

### Post by aktiwers on 2008-04-29
> **trippinnik said:**
> How did you fix the mic input? I've got a similar onboard intel sound with mic and headphone jac in the front and outputs in the back, but use the front for headphone and mic but can't get mic to pick anything up.  I've turned up the volume on every input/mic volume setting I could find.


Double-click on the sound icon in your top panel.
Go to preferences and add "mic select".
In the new tab select "mic 2".

It should work, I have same setup

---

### Post by trippinnik on 2008-04-30
> **aktiwers said:**
> Double-click on the sound icon in your top panel.
Go to preferences and add "mic select".
In the new tab select "mic 2".

It should work, I have same setup

I don't have any option to "add 'mic select'"
I've already checked all the boxes so that it displays all the possible volume sliders, Line in / Mic / front mic and a ton of output ones.  I've turned up the volume on everything.

I can even here my voice coming out of the speakers but Skype doesn't record it.  I've tried changing the input device used by Skype but all but the default/intel HDA(hw,0) report an error.

---

