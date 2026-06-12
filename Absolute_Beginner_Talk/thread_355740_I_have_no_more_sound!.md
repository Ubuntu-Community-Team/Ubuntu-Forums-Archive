---
title: "I have no more sound!"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by alex-desktop79 on 2007-02-07
This morning my sound was working great. I just came back and it no longer works.

Help.

---

### Post by muguwmp67 on 2007-02-07
Pardon me for this question, but have you muted it or turned it all the way down?

Has any new software been installed?  Does it work if you reboot?

---

### Post by thelocust on 2007-02-07
[B]
Are you using a soundcard or strait off the mb.


[/B]

---

### Post by alex-desktop79 on 2007-02-07
I checked, it is not muted or turned down, I plugged the jack to my iPod and sound works, so it's not my speakers.

Sound worked this morning when I left, no software has been installed but i changed a but of the audio settings in winecfg to try to get Half-Life 2 to work.

---

### Post by alex-desktop79 on 2007-02-07
I'm using a soundcard.

---

### Post by alex-desktop79 on 2007-02-07
Help? Is there a command I can run? Anything?

---

### Post by muguwmp67 on 2007-02-07
If in Ubuntu try going to system->sound.  This will open up a sound config app.  Try hitting the test button on 'sound playback' and 'music and movies'.  Do either of these work?

Also try double-clicking on the volume icon in the upper right.  Is PCM enabled?  If it isn't listed, go to edit->preferences and check off PCM.   Test the sound again in the sound  config app.  Any luck?

I don't know anything about Wine, but I can't imagine why a wine config file would affect your base sound setup, as it seems to me that it shouldn't affect anything until wine runs.  I would hope that it wouldn't make a modification to your base sound configuration after it runs, but I could be wrong.

---

### Post by alex-desktop79 on 2007-02-07
I get this error when I press test:

"audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Resource busy or not available."

I have no PCM Option.

---

### Post by muguwmp67 on 2007-02-07
> **muguwmp67 said:**
> I If it isn't listed, go to edit->preferences and check off PCM.   Test the sound again in the sound  config app.  Any luck?

You did not say whether you have rebooted or not, the error you received could indicate that Wine did not properly release the sound device after closing.

Are the options on the sound applet set to 'autodetect'?

---

### Post by alex-desktop79 on 2007-02-07
Yes they are, I did not reboot but I did a Ctrl+Alt+Backspace. I will reboot now.

---

### Post by alex-desktop79 on 2007-02-07
Rebooting does not work either.

---

### Post by alex-desktop79 on 2007-02-07
Sound does not work in Wine apps either. So it's not that.

I will go see if sound works in Windows.

I would appreciate not being left in this state, so anyone who can help...

---

### Post by alex-desktop79 on 2007-02-07
Sound works in Windows

---

### Post by thelocust on 2007-02-07
[B]
Do you get sound coming strait off the MB. If so it's your xorg.conf file.


[/B]

---

### Post by -Ghost9- on 2007-02-07
when I installed 6.10, i had no sound. I went to system, preferences, sound. Then on the Sounds tab at the bottom i had to switch the Default sound card from mb sound to Audigy 2 ZS(my sound card).

For some reason I don't have sound until after I log in though. Not sure why that is. I'm assuming because the user has to adjust the sound settings. I kinda miss the "bloop" at the login screen though.

---

### Post by alex-desktop79 on 2007-02-08
I used to get all that, now it plain doesn't work. It worked perfectly after a fresh install.

I will check if mb sound works in a minute.

---

### Post by alex-desktop79 on 2007-02-08
Sound does not work with mb either.

---

