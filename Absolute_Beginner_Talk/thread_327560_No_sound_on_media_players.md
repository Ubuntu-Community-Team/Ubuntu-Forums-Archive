---
title: "No sound on media players"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by tordan on 2006-12-29
All was working fine and dandy, then I installeled a couple of new media players to try them out and the sound stropped working on all of them. I think I want Amarok as my primary audio player.  Any ideas?

---

### Post by rajeev1204 on 2006-12-29
rightclick on volume icon on taskbar and go to open volume control

check if that is muted

---

### Post by tordan on 2006-12-29
I got sound when I uninstalled the unneeded media programs but the sound is low even w/ all visible levels up.

---

### Post by Arisna on 2006-12-29
Open a terminal and enter the command 'alsamixer`.  Use the arrow keys to navigate and adjust volume levels.  Pay special attention to the PCM channel.  Make sure it's turned up to 90 or so at least.

---

### Post by tordan on 2006-12-29
all levels are up @ terminal

---

### Post by rajeev1204 on 2006-12-29
hi

not sure if this is right solution but try this

go to sytem> preferences >sound 

try different audio devices , maybe it helps



regards

rajeev

---

### Post by tordan on 2006-12-29
Switched all sound events to the soundcard that I turned up in the terminal. Still the same.

Restart maybe?

---

### Post by rajeev1204 on 2006-12-29
MAYBE !!


GOOD LUCK

and go to first sticky thread in multimedia and video section , that should help

Also try this after all else fails 

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)


regards

rajeev

---

### Post by tordan on 2006-12-29
After some tweaking, I swiitched over to the on board sound card and got plenty of sound! 

You folks are awesome! Thanks for all the help!

---

