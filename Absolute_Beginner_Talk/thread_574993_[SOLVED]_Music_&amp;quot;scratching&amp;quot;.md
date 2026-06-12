---
title: "[SOLVED] Music &amp;quot;scratching&amp;quot;"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by iamthemicrowave on 2007-10-13
After upgrading to 7.10, much of my music plays with scratches when there is a large amount of bass in the song.  The problem is not in my speakers.  I am using Rhythmbox to play music, is there a way to edit equalization problems?  I can not find one.

---

### Post by RomeReactor on 2007-10-13
Hi. This may help: in Rhythmbox, go to "Edit->Preferences->Playback tab" and enable "Use crossfading backend".

---

### Post by iamthemicrowave on 2007-10-13
Wow that fixed my problem.  Thank you so much.  What did this option enable, by the way?

---

### Post by Kingsley on 2007-10-13
Use Amarok.

---

### Post by RomeReactor on 2007-10-13
> **iamthemicrowave said:**
> Wow that fixed my problem.  Thank you so much.  What did this option enable, by the way?

It essentially enables Rhythmbox to fade out a song that's ending and overlap it with a beginning song that fades in. You can determine the duration of the fade and the overlap with the **Crossfade Duration (Seconds)** slider. If set at zero, there is no crossfade or overlap. It's a new feature for Rhythmbox.

---

