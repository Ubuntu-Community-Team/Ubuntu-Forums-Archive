---
title: "microphone no longer works"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by ginestre on 2008-02-05
Before going away for a week last week. my mike worked well. I often used it with skype and with audacity.
Now I have come back, accepted the security upgrades that the system (feisty) offered, and the mike no longer works.

In the volume control panel, mic and line input are checked, unmuted and have a volume set - these are the same values that existed before the security upgrade. Everything is correctly set to my ALSA on the Soundblaster audigy card I have.

In the System > Preferences > Sound, likewise everything looks good to go- and hasn't been changed since before the update.  But the sound capture test doesn't capture any sound- because the mic has stopped working.

 It's things like this that get my goat. The boss keeps telling me I'm a fool for not using windows- because if I double boot into XP on the same PC, it 'just works'. 

Anyone any ideas?

---

### Post by avanrens on 2008-02-05
To boost your Mic Input (I had to do this to get Skype to work)
Right click on the sound icon.
Open volume control.
<Edit><Preferences>
Scroll down and check Mic Boost.
Use the slider on the Mic Boost to set the require input boost.

---

### Post by ginestre on 2008-02-05
> **avanrens said:**
> To boost your Mic Input (I had to do this to get Skype to work)
Right click on the sound icon.
Open volume control.
<Edit><Preferences>
Scroll down and check Mic Boost.
Use the slider on the Mic Boost to set the require input boost.

Thanks for the reply: but sadly this was already checked, so that's not the problem.

---

### Post by avanrens on 2008-02-09
I installed Ultimate Ubuntu 1.7 and the mic won't work in Skype. I installed ALSA Mixer and now it works fine.

---

### Post by david_kt on 2008-02-09
> **ginestre said:**
> Thanks for the reply: but sadly this was already checked, so that's not the problem.

May be you could check your bios setting and change the mic options. It just happen to my pc (dual boot with windows), headphone and mic work perfectly in Gutsy, but did not work in windows (yes, did not work in windows but worked in Gutsy).

First I thought it was due to windows problem or driver problem. Reinstalled both windows and sound driver still did not solve it. After I change the setting in the bios, it works now.

DK

---

