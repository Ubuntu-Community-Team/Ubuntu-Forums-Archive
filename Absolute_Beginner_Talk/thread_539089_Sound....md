---
title: "Sound..."
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by bittiez on 2007-08-30
Mine is a bit of a unusual problem compared to those that i have read, I have went through many topics and Google searches before deciding to post here, so anyway, the first day I had Linux installed the drivers for my sound automatically installed, and my sound worked fine. Day two,  only my right ear has sound, so i assume its because somewhere something was set to left ear mute and right ear sound, well also on day two i noticed, when i do fn arrow up(for automatic sound adjustment) It raises the microphone volume instead of the actual sound volume so this is frustrating too.. Please help in any way you can thanks

---

### Post by bvmou on 2007-08-30
See what happens if you open a terminal window and type "alsamixer" <Enter>.   You may find that there are options for directly handling the different parts of your sound equipment.  In my case there is a bug (or actually a sort of alpha driver that I patched in) that makes many uses of the volume wheel quirky, so I can correct its settings in the alsamixer window with regular keyboard arrows.

---

### Post by bittiez on 2007-08-31
alsamixer: function snd_mixer_load failed: Invalid argument

---

