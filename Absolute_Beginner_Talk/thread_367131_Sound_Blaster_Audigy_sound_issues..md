---
title: "Sound Blaster Audigy sound issues."
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by caintona on 2007-02-21
I am having a hard time getting my sound to work.  Does anyone have a guide on how to reinstall sound drivers? 

Thanks,

Greg

---

### Post by NewOldTimer on 2007-02-21
caintona,    what kind of problems are you experiencing? there may be other options other than just reinstalling drivers, I'm a n00b here but will offer what I can, and there are a lot more "experienced" in this forum who would be more than willing to assist if you could be more specific about the problem at hand.

---

### Post by caintona on 2007-02-21
It just isn't working and I don't know where the sound card is configured.  The only place i can find anything on changing anything about sound is in the System -> Preferences -> Sound.

Perhaps I just need to be pointed in the right direction.  what is the file that controls the sound?

I found something a while ago about how to fix this but can't seem to find the fix anymore.

---

### Post by NewOldTimer on 2007-02-21
right click on your volume icon and open volume control, theres a few more options there, by the way do you have any sound at all like when you boot-up or shut-down?

---

### Post by caintona on 2007-02-21
No sound on boot-up.  I had this set up before but can't remember what I did.  I just installed Vista on a dual boot and F'd this up.  I'm in the midst of a transition to Ubuntu as my main OS.  Every thing is working fine at work but not here at home.

I'm feeling like a n00b myself, but I have no idea how sound works in Linux. period. Nor what to do when it is broken.  It seems like every time i try to set linux up sound is one of the biggest problems.  same with old redhat and suse years ago.

---

### Post by NewOldTimer on 2007-02-21
check this out, hope it helps

[http://linux.iuplog.com/default.asp?item=94639](http://linux.iuplog.com/default.asp?item=94639)

---

### Post by NewOldTimer on 2007-02-21
maybe this is what you were looking for?
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_configure_sound_to_work_properly_in_GNOME](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_configure_sound_to_work_properly_in_GNOME)

also this?    [http://www.tldp.org/HOWTO/Soundblaster-AWE.html](http://www.tldp.org/HOWTO/Soundblaster-AWE.html)

---

### Post by maruchan on 2007-02-21
Before you reinstall sound drivers and stuff like that, install alsamixergui and use it to make sure that everything that should be unmuted and turned up, is. 

I have an Ubuntu system with an Audigy, and the last time sound didn't work, it was because I had a switch (some sort of Digital I/O or something) turned on in the mixer. One click and my sound was back.

One clue is, when you play a sound in e.g. XMMS, does the sound scope work, indicating that it is playing? That would tell me it's just a mixer setting as opposed to the sound card driver being broken.

---

### Post by caintona on 2007-02-23
I think my problem had something to do with an ATI HDTV Tuner card I had installed.  As everyone knows the old ATI driver install isn't the easiest always and I think its screwed up the sound config as well with the audio capture from the tv tuner.

I ended up reinstalling ubuntu becuase my vid drivers were just plain hosed and I wanted to start over.

Thanks for the help guys.

G

---

