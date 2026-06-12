---
title: "problem with sound output in audacity...searched, no luck"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by JonnyMaycunich on 2007-10-24
so  when i open audacity i get an error message before it opens saying "there was an error initializing the audio i/o layer. You will not be able to play or record audio. Error: host error. i have no idea what the problem is and when i go to preferences for the audio i/o there is nothing in the playback or record boxes.....ive searched but cant find anything.....and when audacity worked perfectly when i had it along time ago when dapper came out...but i just got it again and it does not work...

---

### Post by Martje_001 on 2007-10-24
Try ALSA/OSS as output managers for audio.

---

### Post by JonnyMaycunich on 2007-10-24
how exactly do you do that? i think i might have done something like that but not so sure..

---

### Post by Martje_001 on 2007-10-24
In preferences of audacity I think. Or try the speaker (by the clock).

---

### Post by erginemr on 2007-10-24
I too had the identical error in Audacity before, but this was when I tried to use another program that uses sound (say another music player) . Does this happen when the only running program that uses sound is Audacity?

---

### Post by JonnyMaycunich on 2007-10-24
no im not running any other programs at all...my computer has sound and everything, just not in audacity.. i typed gstreamer-properties in terminal and messed around with that for a while and it worked for a little bit but after restarting...it doesnt work again...
and in the preferences section under audio i/o there arent any playback or recording devices....not quite sure what the problem could be..

---

### Post by erginemr on 2007-10-25
Well, apart from gstreamer-properties above, there is a second dialog in the Gnome menu (via Preferences -> Sound), that lets you play with the sound input / output settings. Could you please also play with its settings to see if it helps any better?

---

