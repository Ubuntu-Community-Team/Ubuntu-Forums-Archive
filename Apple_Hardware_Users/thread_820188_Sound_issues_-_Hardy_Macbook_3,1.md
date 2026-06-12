---
title: "Sound issues - Hardy Macbook 3,1"
date: 2008-06-06
forum: Apple Hardware Users
---

### Post by EJ_48 on 2008-06-06
My sound was working fine before, but after I did a suggested update (update manager popped up on my toolbar) the sound has crapped out on me. I don't know what the problem is. I've made sure the volume controls are turned all the way up in alsamixer, but that didn't seem to fix the problem. I'm pretty much a noob, so be gentle.

---

### Post by cyberdork33 on 2008-06-06
Can you double check this:
[https://help.ubuntu.com/community/MacBook_Santa_Rosa#head-6a2f3399bd41e87c39ff69ff7a48a1953db51cdd](https://help.ubuntu.com/community/MacBook_Santa_Rosa#head-6a2f3399bd41e87c39ff69ff7a48a1953db51cdd)

---

### Post by trouble1313 on 2008-06-06
I have the same situation. Some update killed off sound. Used to work fine in Fiesty, Edgy and even Hardy. Everything is enabled and I even went as far as making sure pulseaudio was in charge just as I had on my htpc also with hda_intel just yesterday. Also doesn't work either (Pulse is just pointing at the alsa sink anyway). Device is seen, sliders up, speakers selected, just no output. This is also a mbp 3,1.

-Trouble

---

### Post by avtolle on 2008-06-06
I don't have a computer as either of you. The updates were to the kernel, however, including one today (I don't know if it's shown up, yet on yours) to a .19 kernel. Thus, you may need to check the modules again if you've not done so, and do the modprobe thing over. Just a thought.

---

### Post by EJ_48 on 2008-06-07
> **cyberdork33 said:**
> Can you double check this:
[https://help.ubuntu.com/community/MacBook_Santa_Rosa#head-6a2f3399bd41e87c39ff69ff7a48a1953db51cdd](https://help.ubuntu.com/community/MacBook_Santa_Rosa#head-6a2f3399bd41e87c39ff69ff7a48a1953db51cdd)

I've done that and the sound was working great before the latest update. Now, there's nothing.

---

### Post by cyberdork33 on 2008-06-07
> **EJ_48 said:**
> I've done that and the sound was working great before the latest update. Now, there's nothing.
Yes, but I am saying to check and make sure it is still there.

---

### Post by EJ_48 on 2008-06-07
> **cyberdork33 said:**
> Yes, but I am saying to check and make sure it is still there.

Oh, sorry. Yes, it's still there.

---

### Post by EJ_48 on 2008-06-08
I've turned up all the volume levels in alsamixer and that doesn't seem to do anything either. I'm still not getting any sound. I'm at a complete loss. It was working fine a week ago, but now I get no sound.

---

### Post by EJ_48 on 2008-06-08
> **cyberdork33 said:**
> Can you double check this:
[https://help.ubuntu.com/community/MacBook_Santa_Rosa#head-6a2f3399bd41e87c39ff69ff7a48a1953db51cdd](https://help.ubuntu.com/community/MacBook_Santa_Rosa#head-6a2f3399bd41e87c39ff69ff7a48a1953db51cdd)

One more thing. I try to follow the directions in the link provided in the wiki for what you need to do in Hardy after you change the options file under modprobe, but for some reason I don't have a "switches" tab under "Volume Control".

---

### Post by cyberdork33 on 2008-06-09
> **EJ_48 said:**
> One more thing. I try to follow the directions in the link provided in the wiki for what you need to do in Hardy after you change the options file under modprobe, but for some reason I don't have a "switches" tab under "Volume Control".
They are likely not added in your mixer. You can add more items in the preferences for the gnome-mixer applet.

If you truly want to make sure you see ALL the channels, just run 'alsamixer' in the terminal. This will show EVERYTHING. use arrows to move, 'm' to mute/unmute (or flip the switches)

---

### Post by EJ_48 on 2008-06-09
> **cyberdork33 said:**
> They are likely not added in your mixer. You can add more items in the preferences for the gnome-mixer applet.

If you truly want to make sure you see ALL the channels, just run 'alsamixer' in the terminal. This will show EVERYTHING. use arrows to move, 'm' to mute/unmute (or flip the switches)

Yeah, that's usually how I use aslamixer, by using it in terminal. All the channels are unmuted and turned up. Still nothing.

---

### Post by theverant on 2008-06-11
Nevermind - Had to unmute "front" sound channel through Alsamixer!  :oops:

---

### Post by EJ_48 on 2008-06-12
I've redone the modprobe, I've made sure that all channels are turned all the way up and unmuted in alsamixer, but still nothing. This is really frustrating. I've been using my Mac OSX side more than I'd like to in the past week.

---

### Post by cyberdork33 on 2008-06-12
> **EJ_48 said:**
> I've redone the modprobe, I've made sure that all channels are turned all the way up and unmuted in alsamixer, but still nothing. This is really frustrating. I've been using my Mac OSX side more than I'd like to in the past week.IDK what to say, especially since it doesn't seem that anyone else exhibits this problem. Have you tried reinstalling?

---

