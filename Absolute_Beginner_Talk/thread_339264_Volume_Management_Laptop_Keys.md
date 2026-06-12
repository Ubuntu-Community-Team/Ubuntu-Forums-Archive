---
title: "Volume Management Laptop Keys"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by mlissner on 2007-01-15
Hello all,

I'm having a problem with my volume. I have an Asus A96F laptop with three Fn key combos for volume. When I press the volume up, down or mute buttons, the volume pop up shows up in the center of my screen (as it should) and shows that it is making those changes. Unforunately though, that volume display thing is not changing the actual volume of my computer. It's changing the PCM-2 volume instead, which as far as I can tell means nothing.

So here's the quesions:
1. What's PCM-2?
2. How do I get the key combos to adjust the volume, not the PCM-2?

Thanks.

---

### Post by kairu0 on 2007-01-15
PCM-2 sounds like one of those alternative names for the main speaker controller. It's common with laptop sound cards. For example, my volume is actually called "Front".

If you right-click on the volume control in the tray, and choose Preferences, is it set to PCM-2? If not, set it, then try again.

---

### Post by mlissner on 2007-01-15
Hmmm...I'm a little confused. I have ALSA and OSS to choose from in both the "Volume Control" box and the "Volume Control Preferences" box. I don't know which is better for what reason, but I've pretty much tried all of the combinations possible between these two boxes.

So far, nothing has worked. My impression is that the "Volume Control" controls how all sound is output/input, and that the "preferences" thing is how the function buttons are controlled. If that was the case, this would be simple, but no logical combination seems to be working.

More suggestions?

---

### Post by kairu0 on 2007-01-20
It sounds like this volume control is built-in and so you haven't had to install anything for it to pop up on the screen. Is that right? It seems funny that a BIOS-level function like that would control a different volume level in one OS than in another.

It might be easiest to map a different key combo to control the volume, if you are happy with that. Preferences Menu -> Key Combinations to find places to set Volume Up and Volume Down with a favorite keystroke.

By the way, ALSA is a better choice than OSS. However, this has nothing to do with your problem.

---

### Post by mlissner on 2007-01-20
No, it's not a bios level funtion that I seem to be controlling here. It's a very gnome looking thing. See, that's the strange thing. When I do a volume up or down combo, the gnome thing pops up on my screen, and the bar goes up, down or mutes depending on the combo I do. However, whatever volume that's controlling never seems to be the one that actually changes the sound coming out of my computer.

I just went and rigged another three key combos to do volume control. I had the same results. The gnome thing pops up in the middle of my screen, the volume appears to change, yet what I hear does not.

What IS going on here!

---

### Post by CyberCod on 2007-02-04
I'm having the exact same symptoms on my desktop after a power failure re-enabled my onboard sound.

been looking for a way to tell what is controlling that little popup in hopes of finding a conf file for it, but no luck yet.

---

### Post by mlissner on 2007-02-04
Yes...it's pretty annoying and seems to be unfixable for some reason. Out of curiousity, what chipset do you have? 

I have the Intel 945abg I think...dual core intel?

---

### Post by soulwater on 2008-06-15
Hi, i'm also a new Ubuntu user and ive just managed to get my fn volume/mute keys on my (shitty) Packard Bell to control my master fader.

1. I assigned my keyboard shortcuts(System>Preferences>Keyboard Shortcuts...volume up, down and mute). This seemed to do nothing!

2.Set default mixer tracks to 'playback' instead of ALSA mixer(default) in System>Preferences>Sound.

See Screen shot below.

And now it works, hope it works for you guys too.

Oh, and thanks to everyone who developed Ubuntu...im amazed by how seemless the switch from XP has been!

---

### Post by mlissner on 2008-06-15
That's good to hear, and thanks for the thoughts. I managed to get mine fixed. I think the solution was to wait for the next version of Ubuntu. You'll see that my original post was from early 2007...

---

