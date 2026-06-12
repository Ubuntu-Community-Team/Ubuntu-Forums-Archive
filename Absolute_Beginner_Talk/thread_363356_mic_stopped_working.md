---
title: "mic stopped working"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by shadowboxer_k on 2007-02-16
hey,

i installed ubuntu edgy a week ago and all worked fine until two days ago when i downloaded alsamixer. i don't know if there's a connection at all, but that's about when my microphone stopped working. 

when i opened alsamixer the mic was muted, so i unchecked that box and it seemed to work, from the sounds it was making. but then i tried to use it on skype and it didn't work. :(

what could have gone wrong?

any advice gratefully accepted.

---

### Post by PurplePenguin on 2007-02-16
Don't forget that alsamixer has a section for playback and capture.  You'll want to mute your mic in the playback part, but make sure it's set to capture.  There are a ton of posts about this on these forums with more detailed steps to take.

I'm not the best guy to talk to about this, because I still don't know exactly what to do to get the mic working perfectly.  I just sort of randomly fiddle with the settings until things start to work. :D

The good thing is that it *will* work with the right settings. :)

EDIT: Just checked... searching this forum for these words: alsamixer mic capture
will give you a bunch of helpful threads.  Read through a couple of them and I'm sure you'll be up and running in no time!

---

### Post by Quintin Riis on 2007-02-16
What version of skype are you using?  What is your soundcard?  What is mic plugged into?  

'alsamixer' in a terminal, and then <tab> to adjust capture settings.  Make sure it is not muted.  You can also double-click the sound icon and click the 'capture' tab.

---

### Post by Yumi on 2007-03-07
Has this issue been resolved? I seem to have the same problem. Skype worked well until I think a update some weeks ago. Now mic not working.

I followed all the threads. But in the gnome window for alsamixer the capture tap is missing and in the alsamixer settings from the terminal the capture section is incomplete. Does not show a vertical bar under the mic section.

Michael

---

