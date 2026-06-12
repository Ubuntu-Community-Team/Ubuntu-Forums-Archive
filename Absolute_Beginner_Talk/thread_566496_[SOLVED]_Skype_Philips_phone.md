---
title: "[SOLVED] Skype Philips phone"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by Dai Bando on 2007-10-03
I have just been given a Philips VOIP080 phone for my birthday. When I plug it in I get nothing to show it is working. If I press the Skype test call I can hear all the introductory shpiel on the handset but there is no sound recorded from me. Anyone any ideas.
By the way this is my 78th birthday not my 87th as I mentioned last week, just a touch of old age.

---

### Post by Dai Bando on 2007-10-04
Is no one going to answer please?

---

### Post by Onyros on 2007-10-05
Hi there, Dai ;)

To start off, happy birthday!

It may seem complicated first, but dealing with sound in Ubuntu (and any other Linux flavour) is quite straightforward... IF the hardware is detected automatically.

Make sure you have your Skype settings for Audio Device setup correctly, meaning, in Skype's options, click on the "Sound Devices" tab, and select as device for both the "Sound In" and "Sound Out" options whichever options is stated as VOIP phone.

If there are none, chances are the phone hasn't been properly detected, and troubleshooting that may be a little more difficult.

If there is such an option and even after you've chosen the VOIP phone for Sound In/Out you can't hear your own voice on the test call, you may have to set the volume for the phone mic: you'll have to right click on your sound volume icon (under GNOME it's on the top right, to the left of the date/time), an then click on "File" and choose the VOIP phone.

After that, try tampering with the sound volumes on whichever option there are for Microphone (they'll probably be under recording, because for playback it'll make you hear your own voice - which is something you better avoid, because of the feedback.

I'm trying to be as generic as I can, because I don't have a similar phone of my own to test out and help you more directly, but with these few instructions you'll probably get there ;)

Take care!

---

### Post by Dai Bando on 2007-10-06
Thanks for the information Onyros, I shall try that; and thank you for the birthday wishes, much appreciated.

---

### Post by Dai Bando on 2007-10-06
Thanks Onyros that fixed it.

---

### Post by Virkoff on 2007-11-21
Dai Bando, can you tell me how you get this phone configurated? I have problems with the PCm volume in alsa and i can't "demute" the device...

---

### Post by Dai Bando on 2007-11-30
Hi Virkoff; I am sorry for not replying to you before. I am afraid I can't help you with your Query because I just plugged in the handset went to options and clicked on the Philips lines in the Sound devices and it all worked.

---

