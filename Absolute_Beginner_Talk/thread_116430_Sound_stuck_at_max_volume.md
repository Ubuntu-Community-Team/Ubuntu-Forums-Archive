---
title: "Sound stuck at max volume"
date: 2006-01-12
forum: Absolute Beginner Talk
---

### Post by hen3rz on 2006-01-12
I cant change my volume level its stuck at max volume? I can move volume the slider up and down but it doesnt make a difference it still plays at max volume, it even plays at max volume when its turned all the way down?

What can i do to fix this?

---

### Post by kaamos on 2006-01-12
Make sure you are controlling the right mixer. You can choose one from "file->change device" in the volume control.

---

### Post by hen3rz on 2006-01-12
Thank you for your reply.

I Tried switching my device thing and it didnt seem to work.. so i started fiddling around with the "multimedia systems selector" and worked out that i was able to change volume levels using the "ESD - Enlightenment sound daemon" but unfortunateley when i go into XMMS I cannot control my volume. But when out of XMMS i can change the volume of the dekstop sounds and stuff.

Any ideas?

---

### Post by hen3rz on 2006-01-12
It appears XMMS is the only program that seems to be doing this... Totem movie player plays my soungs with total control of my volume...

**EDIT:**
**(A little of topic)**

Does anyone know how to fix a problem i have in Rythmbox Music player.

The error i get is this: "This file is an audio stream"

The file im trying to open is a .mp3

---

### Post by kaamos on 2006-01-12
Change xmms (and other apps as well) to use esd. You can choose this in xmms preferences.

Totem will use what is chosen in multimedia systems selector, and so does rhytmbox. For other apps, check the preferences.

---

### Post by hen3rz on 2006-01-12
Yay that worked! thank you!

oh and do you know anything about my error?
> The error i get is this: "This file is an audio stream"

The file im trying to open is a .mp3

---

### Post by kaamos on 2006-01-12
Have you enabled mp3 support? See [https://wiki.ubuntu.com/RestrictedFormats#head-7a73b076c82c7d7bb567bdac3322e53274f1d1f3](https://wiki.ubuntu.com/RestrictedFormats#head-7a73b076c82c7d7bb567bdac3322e53274f1d1f3)

---

### Post by hen3rz on 2006-01-12
I installed these a while ago cause I thought that it might be the problem.

> Reading package lists... Done
Building dependency tree... Done
gstreamer0.8-mad is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.


Ill try restart my computer. See if that helps.

---

### Post by kaamos on 2006-01-12
Should not be necessary. Try this command
```
gst-register-0.8
```

---

### Post by hen3rz on 2006-01-12
I still recieve the error after both a restart and "gst-register-0.8".

I'll just have to live with out the simple yet effective rythmbox music player.

---

### Post by kaamos on 2006-01-12
Now that is indeed strange. Try
```
sudo apt-get install gstreamer0.8-plugins-multiverse
gst-register-0.8
```

---

### Post by hen3rz on 2006-01-12
Hahahaha you did it!  It now works perfectly!

Thank you very much.

---

