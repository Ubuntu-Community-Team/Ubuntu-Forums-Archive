---
title: "volume problem"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by band-aid on 2007-02-07
On my laptop the fn+f7 and fn+f8 adjust the volume level. Unfortunately in ubuntu it acts like its changing the volume (showing the little bar in the middle of the screen in everything) but it does not. How do I tell the audio manager to change the volume when I push the shortcuts. Thanks Band-aid

---

### Post by borris.morris on 2007-02-07
Go System -> Prefrences -> Keyboard Shortcuts. Then click on the Volume Up and press fn+f7 to turn it up. Do the same for vol down.

---

### Post by isecore on 2007-02-10
I've got the same problem. It started just earlier today.

Previously I had mapped my volume-keys on my multimedia keyboard to change the volume. Now, for some reason it doesn't work. It shows the small popup and acts as if it's changed the volume - but it hasn't! I've tried remapping the keys but to no avail.

This is very annoying. Now the only way to change the volume is through the volume control and it's slow and annoying. All the other multimedia keys work according to their mapping, but not the volume.

EDIT: I fixed it. The problem was that for some reason my onboard soundcard was claiming the first place in line. Changed /etc/modprobe.d/alsa-base so that the onboard sound got a higher slot than my Soundblaster Audigy2 ZS which is the one I want to use. You might ask why I even have my onboard enabled - I don't, but Ubuntu finds it none the less :)

Oh well, problem solved (for me).

---

### Post by borris.morris on 2007-02-10
hmm... you got me.

---

