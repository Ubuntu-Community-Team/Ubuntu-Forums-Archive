---
title: "[SOLVED] no sound for one user"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-12-12
I enabled the mouse over mp3 preview by following the instructions here witch may have something to do with this problem [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_get_Mouse_over_preview_of_MP3_files_working](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_get_Mouse_over_preview_of_MP3_files_working)
I did a "sudo addgroup kristina audio" witch returned an output that she had been added to the pulse audio group logged out then in. No luck. I went to system>preferences>sound and hit test and got this error
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open resource for writing.
Any help would be appreciated

---

### Post by swoll1980 on 2007-12-12
Problem solved this command "sudo chmod a+rwx /dev/dsp" allowed the sound card to be used by all users. They should add this to the tutorial

---

