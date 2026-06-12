---
title: "Microphone Problems"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by Khashai on 2006-12-14
I am having problems with my microphone recording.. I am a Linux newbie, and this is what I have figured out so far...

with ALSA, I am using driver CA0106 (Audigy SE)

I finially figured out to change my Shared/Mic In to Mic In (which should have been obvious to me) in the Volume Control.

However, what I am experiencing is this.. My microphone randomly cuts out. Usually this happens when I am in Skype, which to say the least, is extremely inconvenient.

Is there a way to correct this... and can you please explain it to me, like I am a 3-year-old?

I had thought that upgrading to the latest ALSA might help, but I know absolutely nothing about configuring the tar file. A friend on Skype (chat, since the mic only works sometimes) suggested that it may be an issue with the microphone process, but a Google search only made me more confused.

Obligatory PLZ HELP! goes here :-D

---

### Post by xyz on 2006-12-14
> **Khashai said:**
> I am having problems with my microphone recording.. I am a Linux newbie, and this is what I have figured out so far...

with ALSA, I am using driver CA0106 (Audigy SE)

I finially figured out to change my Shared/Mic In to Mic In (which should have been obvious to me) in the Volume Control.

However, what I am experiencing is this.. My microphone randomly cuts out. Usually this happens when I am in Skype, which to say the least, is extremely inconvenient.

Is there a way to correct this... and can you please explain it to me, like I am a 3-year-old?

I had thought that upgrading to the latest ALSA might help, but I know absolutely nothing about configuring the tar file. A friend on Skype (chat, since the mic only works sometimes) suggested that it may be an issue with the microphone process, but a Google search only made me more confused.

Obligatory PLZ HELP! goes here :-D

Have you tried this:
In a console, try and run 
```
alsamixer
```
and then do unmute all the outputs by hitting “m”

Then have a hit on "tab" to go the capture settings
Click and highlight the “Mic” setting using the arrow keys.
Hit space to enable the microphone.

Click to highlight the “Capture” setting using the arrow keys.
Hit space to enable capture (note that just because you have volume bar
And finally "esc"

See if it helps

---

### Post by Khashai on 2006-12-14
> **xyz said:**
> Have you tried this:
In a console, try and run 
```
alsamixer
```
and then do unmute all the outputs by hitting “m”

Then have a hit on "tab" to go the capture settings
Click and highlight the “Mic” setting using the arrow keys.
Hit space to enable the microphone.

Click to highlight the “Capture” setting using the arrow keys.
Hit space to enable capture (note that just because you have volume bar
And finally "esc"

See if it helps

Ive been in the alsamixer already, but thank you for the run down of the key controls!

The problem I have in alsamixer is that under the Capture settings, I have no "capture" volume bar listed, only a "Mic" bar. When I tab to All (and only then), does the Capture volume bar show up, and at that point, hitting space visually does absolutely nothing.

---

### Post by Khashai on 2006-12-14
Now my sound just died entirely, ALSA claims that I have no device installed... 

My head just exploded.](*,)

---

### Post by xyz on 2006-12-15
In a terminal, type:
```
sudo aptitude install alsa-oss
```
BTW, are you on Dapper or Edgy?

---

### Post by zazen666 on 2006-12-27
Hey that fixed a problem I was having! Thanks

---

### Post by SAGEv4.5 on 2006-12-27
Thanks for the thread. It has solved my microphone/Audacity problems!!

---

### Post by zazen666 on 2006-12-28
Actaully, now since I followed XYZ's advice, I am not getting sound when I play games. any thoughts?

---

