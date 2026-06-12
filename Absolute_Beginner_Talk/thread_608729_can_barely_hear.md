---
title: "can barely hear"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by montaukestuff on 2007-11-10
i cranked up the sound on my notebook, on ubuntu and on the music player software fullblast and yet the volume is STILL very soft, i can barely hear it. how do i make it loud?! when i was running ubuntu off the cd only the sound at startup was loud so it obviously has the potential.

---

### Post by dixonstalbert on 2007-11-10
double click on volume icon on panel, or if you dont have one, open a terminal and type 

gnome-volume-control

move all sliders up and see if it makes a difference

---

### Post by mivo on 2007-11-10
Another thing to try: Type **alsamixer** in a terminal and see if everything turned up?

---

### Post by montaukestuff on 2007-11-10
sorry neither of those worked and ALL the volumes, both hardware and software, are turned up all the way.

---

### Post by dixonstalbert on 2007-11-10
hmmmmmmmmmm

try System> Preferences > Sound 

under Devices tab, what devices are listed in dropdown list under Sound Playback?

Can you get sound when you test them by clicking button?

---

### Post by montaukestuff on 2007-11-11
i already tried using both sound devices. the ubuntu one and the and sound card one, they both put out the same ammount of volume. i can get the sound to work HOWEVER it only works if i do it in a long lengthy way everytime. i have both vista and ubuntu on the same hard drive and if if i restart from from ubuntu and log on to ubuntu (opposed to logging on to vista) again the sound is soft, but if i just get done using vista or if i boot vista up wait till i get to the login screen then reboot b4 or after logging in (doesn't matter) then boot vista, the sound will work perfectly..

---

### Post by guga31bb on 2007-11-11
yeah, i've had the same problem ever since installing ubuntu. for some reason the sound is sufficiently loud when using headphones but when i plug in the speakers it gets super quiet. the same speakers work fine in xp though...

---

### Post by Supergoo on 2007-11-11
Does your laptop have a vol. comtrol on the laptop itself, I had a problem with something like this running 7.04 try turning it all the way down then back up it fixed the problem for me. Good luck .

---

### Post by montaukestuff on 2007-11-11
yeah tried that, sadly it doesn't work. i don't know y i have to start vista first then restart with ubuntu to get the volume to work. maybe a conflict in the 2 programs?

---

### Post by P4man on 2007-11-11
You said you have all the slider up, but did you enable all hidden sliders ? Go edit/preferences, select them all. Do the same for ALSA and OSS (file > change device).

 On my laptop, the volume is controlled with the "surround" slider, which is hidden by default, and also set to zero. (Booting vista first may set this slider to a normal value?)

---

### Post by montaukestuff on 2007-11-11
> **P4man said:**
> You said you have all the slider up, but did you enable all hidden sliders ? Go edit/preferences, select them all. Do the same for ALSA and OSS (file > change device).

 On my laptop, the volume is controlled with the "surround" slider, which is hidden by default, and also set to zero. (Booting vista first may set this slider to a normal value?)

thanks for the suggestion, but that didn't work either :( they're all active and turned up, except for the mic of course

---

### Post by P4man on 2007-11-11
Hmm.. one last thing you could try: open a terminal and type "alsamixer". This will give you a good old DOS style app. press TAB 3 times so view is set to ALL;. Then use up and down keys to adjust the levels, left right to switch items, and M on some of them to mute/unmute. Experiment while playing an MP3 or something

---

### Post by montaukestuff on 2007-11-11
> **P4man said:**
> Hmm.. one last thing you could try: open a terminal and type "alsamixer". This will give you a good old DOS style app. press TAB 3 times so view is set to ALL;. Then use up and down keys to adjust the levels, left right to switch items, and M on some of them to mute/unmute. Experiment while playing an MP3 or something

sadly this did not work either. it's ok. thanks for the help everyone. i decided to save the frustrated and switched over to a different linux and the sound works great!

---

