---
title: "Rosegarden no sound"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by Mick8882003 on 2008-02-25
complains about the res on the midi not being hight enough, it runs and the audio bars light up.
the main sound is fine.

---

### Post by marufaberlin on 2008-02-25
I have the same problem. What does it for me is reinstalling JACK, running timidity -ia, connecting the midi output from rosegarden to the timidity alsa mixer interface. But that can't be the solution can it?

---

### Post by marufaberlin on 2008-02-25
Oh I forgot, I just ignore the message about the system timer. You have some annoying pauses, but it doesn't matter that much. Also, you can install the linux*-rt kernel. This one has realtime scheduling and that should work.

---

