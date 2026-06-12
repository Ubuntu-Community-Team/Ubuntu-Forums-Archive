---
title: "Sound Problems!!!!"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by Tommy2er on 2007-07-31
i was listening to some of my music on rhythm box and it was working fine.
then i stopped it to watch a video but then when i went to replay the music,
i got silence i tried other songs and they still didnt work and im still not getting sound.
i have a HDA Intel  and a  Realtek ALC880 sound system.

what can i do :confused:

---

### Post by FleetAdmiral74 on 2007-07-31
You are getting no sound at all? Cause I know that sometimes ubuntu has trouble playing from more then one source, so just clarify if you don't get anything at all now, or just for that one session.

Can always check the volume and mute options. Seems simple, but I have been caught unaware by changes in those settings in the past.

---

### Post by Tommy2er on 2007-08-01
hmm when i shut down my compuer and turned it back on the sound was fine, strange though

---

### Post by atomkarinca on 2007-08-01
when that happens again you can try typing in the terminal:

sudo killall alsa 
and
sudo killall osd

that works for me.

---

