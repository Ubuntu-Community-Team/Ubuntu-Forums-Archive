---
title: "Self installing and sound question"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by iiieckiii on 2007-10-05
Hello all, resident noob here with another question. This time I need a little help with sound and self installing tar.bz2 files. I've been doing some research to help me get my sound working on Ubuntu and went straight to the Creative site and it stated that most Linux distros provide drivers for Creative SB products. However, my sound is not working so I'm guessing Ubuntu  doesn't support it? (can someone clear this up?). Anyways I got directed to to alsaproject and there I downloaded the 1.014 (latest stable version) hoping to get some sound. But then I forgot I don't know how to self install it, can anyone help me install this or have another sure fire way of getting sound using another method? My sound card is a Soundblaster Audigy MP3+ by the way. Thanks for the help guys and gals.

---

### Post by Crenfinkle on 2007-10-07
Before you do anything else, go to the terminal and input **alsamixer**. Unmute any of the sliders that have MM underneath them. If that doesn't work, move on to the next steps. 

alsa should be installed by default, but you can install the newer stable version using the following:

first, input

**sudo apt-get install build-essential**

now, cd to the directory where you downloaded the various alsa-modules (make sure you have alsa-driver at least)

now, input 

**tar xjf alsa-driver1.0.14**  (or whatever the tar.bz2 file is titled)
enter the uncompressed folder
**./configure** (you will see lots of cryptic stuff now)
**make** (more cryptic stuff)
**make install** (more cryptic stuff)

now you're done. Reboot and *hopefully* you hear the drums when the login screen comes up.

---

### Post by iiieckiii on 2007-10-08
> **Crenfinkle said:**
> Before you do anything else, go to the terminal and input **alsamixer**. Unmute any of the sliders that have MM underneath them. If that doesn't work, move on to the next steps. 

alsa should be installed by default, but you can install the newer stable version using the following:

first, input

**sudo apt-get install build-essential**

now, cd to the directory where you downloaded the various alsa-modules (make sure you have alsa-driver at least)

now, input 

**tar xjf alsa-driver1.0.14**  (or whatever the tar.bz2 file is titled)
enter the uncompressed folderbz2
**./configure** (you will see lots of cryptic stuff now)
**make** (more cryptic stuff)
**make install** (more cryptic stuff)

now you're done. Reboot and *hopefully* you hear the drums when the login screen comes up.

Ok so I've done the apt-get when i first installed Ubuntu so that is checked off. Also I'm not sure about the first step on the tar xjf. This is what I did:
tar xjf alsa-driver-1.0.14.tar.bz2
then a slew of errors came out. I'm not sure what it all meant but I do know I still have no sound and can't move onto the next step on ./configure and all that. So if you explain it again what the command line should be. Thanks. Also I did go into the alsamixer and unmuted everything, still no sound, just to make sure I got that out of the way too.

---

### Post by Crenfinkle on 2007-10-09
ok, try extracting the contents in nautilus. Find where you downloaded the file, right click and select  **Extract Here**. Then proceed to the terminal and attempt the installation using the folder that was created when you ran the extraction graphically.

---

### Post by strabes on 2007-10-09
You could try some of the solutions mentioned on this page: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

