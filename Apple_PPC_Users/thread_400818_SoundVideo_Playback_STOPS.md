---
title: "Sound/Video Playback STOPS"
date: 2007-04-03
forum: Apple PPC Users
---

### Post by didjital1984 on 2007-04-03
First, my setup: Dual 867 PPC G4, 768 MB of RAM, running the SMP kernel and Feisty beta (but my problem occurred with Edgy as well)

When I am playing music (in Quod Libet, Rhythmbox, etc) or watching a movie in VLC (or any other media player, regardless of file format) sound playback will stop completely after a while if my system load gets too high, even briefly -- for instance, if I am playing music in Quod Libet and try to start up Synaptic, my system load jumps up and sound playback stops. Quod Libet is still responsive to a point -- menus work, I can tell it to "quit", or I can pick another song to play (it won't start playing) -- but as soon as I do any of those things it freezes up and I have to kill it from the terminal. During the whole procedure, I have plenty of free memory, so I don't think that is the issue.

Also important to note is that if I am playing a movie in VLC, only the sound stops -- the video will keep going, but without sound. If I close VLC and open the file again, sound is still broken. I have to manually kill both processes before sound will work in VLC again.

Any suggestions would be GREATLY appreciated.

---

### Post by quizno50 on 2007-04-04
I can't say too much, cuz I've never had that problem myself; but it sounds like a bug with your sound drivers since it's in more than one program... I'd try re-installing, and making sure you have all the updates for your release... Which apple system are you using? Sounds like one of the later model PowerMacs released just before the G5... If you've got one sitting around, try hooking up a USB Audio Device and see if you have the same problem with that...

---

