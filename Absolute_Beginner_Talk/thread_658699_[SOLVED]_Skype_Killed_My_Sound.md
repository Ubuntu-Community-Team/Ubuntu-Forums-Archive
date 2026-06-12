---
title: "[SOLVED] Skype Killed My Sound"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by McNee on 2008-01-04
Ok, I needed to install Skype for a conference call, but I could not get my mic working... then after a reboot, it worked for the test call, but then it wouldn't connect with a friend of mine... then after restarting Skype to try again, I got no sound at all...

I've since uninstalled Skype via the repository, and ended up running it on my windows laptop...

Now, my sound works for most stuff, system sounds, MP3 playback, etc... but it is NOT working for DVD playback.

Other than when it wasn't working for skype, this is the only instance I'm noticing it not working...

Can anyone give me some suggestions on what to try?  

I'm running 7.1 if that makes a diff.

---

### Post by PmDematagoda on 2008-01-04
Are you running any other applications such as music players or video players that are using the sound system when trying to use Skype?

---

### Post by McNee on 2008-01-05
Mmm.... I might have had Rhythmbox up, but not playing anything while trying to get Skype working. But Skype is basically out of the picture now.

I need to figure out how to get sound back on my DVD playback now.

---

### Post by McNee on 2008-01-06
Ok, based on some thread I found, I switched my sound settings to ESD, and I am getting DVD playback again, but now I'm not getting sound from Firefox (just noticed when trying to watch a YouTube video).

if I try to select ALSA in sound preferences and do a test sound, I get

audiotestsrc wave=sine freq=512 !audioconvert ! adioresample ! gconfaudiosink: Resource busy or not available


Any one have a suggestion here?

---

### Post by McNee on 2008-01-07
Ok, haven't found a solution to the ALSA thing in particular, but found a link for installing a flash lib, and it seems to have worked, you can find it [here...]("http://ubuntuforums.org/showthread.php?p=4085258#post4085258")

---

