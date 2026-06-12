---
title: "Emac G4 - Sound Card wont work in Edgy"
date: 2006-11-12
forum: Apple PPC Users
---

### Post by Note360 on 2006-11-12
I just updated from dapper to edgy and now my sound card doesnt work. I get a mute all the time. It works in OSX and Dapper but not in Edgy. HELP!

---

### Post by br00tal on 2007-01-14
I have the same problem.  Although, I did attempt to install from the desktop (the standard) install disk, and I did hear the log on drum sound when it finally booted up.  I ended up doing the alternative install of Edgy because of the classic eMac display problem that everyone has.  Can someone tell me how to get my soundcard working?

It's a 1st gen eMac (the 700MHz one wth NVidia stuffs).

---

### Post by Linuxbro on 2007-01-20
I have the identical problem on a 1Ghz Emac. Installed Edgy with regular boot disk and got the drums sound, but install did not complete. Completed install with alternate disk, but no sound. What kind of sound card/chipset in the Emac? I can't find a description anywhere!

---

### Post by runcivalle on 2007-01-22
[The same exact thing happened on my 1 Ghz eMac (combo drive). After various tries at following these instructions [https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting")
I managed to get some sound, although quality is bad. I used the sole Apple driver (which seems to be a powerbook G4 driver) on the ALSA website (see instructions in link). It's called 'powermac'. Then I ran 'modprobe snd-powermac', and I got a message on the desktop (!!)  telling me to set up sound. After this, in the Sound preference panel, I could hear an annoying beep when testing 'Auto-detect'. I made sure that snd-powermac was loaded at launch (see link again), and now sound is there.
Problem is, it's not very good quality. Actually, the 'drums'  sound really tinny compared to the ones you hear on the Live cd launch screen, and everything else comes out distorted. So I have wondered whether I had to change some settings in the mixer, or if there is a better sound module. Running System Profiler under Mac OS X, I've found out the sound circuit is called TAS3004, and is from Texas Instruments. I haven't found anything  for the brand on the ALSA website, but googling gives some Linux sites, one at least [http://www.gelato.unsw.edu.au/lxr/source/sound/oss/dmasound/tas3004.c]("http://www.gelato.unsw.edu.au/lxr/source/sound/oss/dmasound/tas3004.c") even seems to have drivers and says the device is also known as 'snapper' (weird!).  It's a very techy site, and I don't understand half of what they're saying. The easiest thing would for someone who still runs Dapper to tell us what it loads at launch, but I don't know if that's going to happen. Otherwise I could continue messing around and see if things get better, but I'm starting to get a bit tired of this issue :-\"

---

### Post by runcivalle on 2007-01-22
Hello, I just made a rapid check. Again this is the most useful: [https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting")
General sound problem: Hopefully no need to go further: just get ubuntu to load snd-powermac (type 'sudo modprobe snd-powermac'). Type alsamixer and check which channels are muted (there's an m underneath). If necessary, unmute something with spacebar. Open Sound preference panel, try the test. If If it works, then type sudo nano /etc/modules and edit the file to add snd-powermac in the list of modules to be loaded. Reboot. You should hear sound from now on.

Sound quality: Try playing a cd. If it sound horrible, type alsamixer in the console and use the the arrows on keyboard to change the little columns (spacebar mutes/unmutes), try everything until the sound is good. Also try setting Sound preferences from auto-detect to ALSA.

Hope this helps.

---

### Post by fcapria on 2007-02-27
> **runcivalle said:**
> Also try setting Sound preferences from auto-detect to ALSA.

Hope this helps.

Thanks. This is what did it for me - g4/733. It seems auto-detect doesn't work in this build.

---

