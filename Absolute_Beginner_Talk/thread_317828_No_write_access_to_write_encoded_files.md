---
title: "No write access to write encoded files"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by Buck2348 on 2006-12-13
A Google search turned up only one other instance of this, and there was no help there.  When I rip a CD track into mp3 with grip, and with the path to the destination directory set on a mounted network (Windows) share, grip rips and encodes it, then in a little box headed Warning (grip), it says "No write access to write encoded file."  I can write other files (including mp3s) there, and grip can write files in my /home directory.  I'd really like some help on this--can't stand the thought of going back to MusicMatch Jukebox.

Thanks,
Buck

---

### Post by YoHell on 2008-03-05
This happened to me too and it was all my fault. For each encode grip flung up a popup that grabbed focus, saying "no write access to write encoded file.". The reason was that after a reinstall / keep old home dir, the target dirs no longer existed. I remembered to fix the rip dir, but forgot the encode dir.

I fixed this by going to: Config tab -> Encode tab -> Options tab, and actually supplying a valid path in the in the "Encode file format" field (duh). 

Suggestion to developers: It may be helpful to echo the path that you can't write to in the popup so that people can see what they did wrong.

---

