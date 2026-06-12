---
title: "&quot;Sound Recorder&quot; requests &quot;Multimedia Settings&quot; adjustment."
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by suomalainen on 2008-01-23
Hello Ubunteros,

I'm trying to use "SOUND RECORDER" Found in Linux Ubuntu 7.10 under Applications--> Sound & Video.

When I start this program and click "new" I get the following message:

**Your audio capture settings are invalid. Please correct them in the Multimedia settings.**

Can someone tell me where the MULTIMEDIA SETTINGS are found?

Thank you!

---

### Post by b0rka7a on 2008-01-23
I'm not sure, but try that:
Go to the Volume Control (gnome-volume-control) > Edit > Preferences > check the Capture box > Close. Next go to the Recording tab and set Capture to max (and unmute it if it's muted)
Tell me if this works. ;)

---

### Post by suomalainen on 2008-01-23
I'm using 7.10 So I went to System-->Preferences-->Sound.

Under Audio conferencing I did a test of the "Sound capture" with ALSA setting and got the following Error Msg. 

"Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'"

Was this the place you wanted me to go?

Thanks for your help and advice.

---

### Post by fiprojects on 2008-01-30
Has this been resolved? I've tried to start Sound Recorder too and get the same message...

---

### Post by tgs1952 on 2008-02-15
I'm in the same boat: my error message in Preferences>Sound is:

gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open resource for writing.

---

### Post by bullfrog2 on 2008-02-15
in sound recorder i changed capture to mix and it worked fine for me didnt change any thing else hope this helps bullfrog2

---

### Post by Be Dave on 2008-02-15
Switching to "mix" did the trick for me also.

---

### Post by tgs1952 on 2008-02-15
'mix' is not an option in my preferences>sound. So, the problem remains.

---

