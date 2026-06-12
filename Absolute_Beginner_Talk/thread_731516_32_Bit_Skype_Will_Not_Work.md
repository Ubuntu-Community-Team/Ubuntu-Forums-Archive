---
title: "32 Bit Skype Will Not Work"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by jordank on 2008-03-21
I have skype installed, but It won't allow me to use audio or video.  What version is required to get this working with my webcam?  Do i need a certain java version?

What steps should I take to get this working?

---

### Post by herbster on 2008-03-22
In the Options > Audio what do you have selected?

---

### Post by jordank on 2008-03-22
There's no actual audio section, but there is a "sound devices section"

I got skype working for the most part, in which people can see me, I can see people, i can hear people, but they can't hear me.

I'm using the microphone on my webcam to talk to people, but it doesn't seem to work.

In the "sound devices" section, it says:

sound in: default device
sound out: default device
ringing: default device

I don't know which one is microphone, Sound in or sound out.

And I don't know why people can't hear me.  Any ideas?

---

### Post by herbster on 2008-03-22
Open gnome-volume-control and check your mic volume level and ensure it's not muted. Turn the levels up all the way and try again.

If still no go, try Audacity.

```
sudo apt-get install audacity
```
(if it's already installed, great!)

Run Audacity, hit Edit > Preferences and not which device is being used for Recording. Hit Ok and then the red circle for record, say a word, stop and playback. You hear yourself?

---

