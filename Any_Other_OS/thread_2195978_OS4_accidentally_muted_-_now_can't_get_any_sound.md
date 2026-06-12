---
title: "OS4 accidentally muted - now can't get any sound"
date: 2013-12-27
forum: Any Other OS
---

### Post by classacted on 2013-12-27
Hello,

I accidentally muted the sound (I can't recall exactly how, but I think I just pulled the slider down) and then slid the slider back up for sound and now I can't get the sound back.  I know it's not the speakers because if I boot to xp or windows7 I get sound.

I have a screenshot here that shows a window in the upper right corner.  there is an x between the speaker and the volume bar.  I am 99% certain that the problem is getting rid of that x.  I never paid it much mind before, but I don't think the x is there when there is sound.

[http://imageshack.com/a/img838/4479/r8ag.png](http://imageshack.com/a/img838/4479/r8ag.png)

there's bad news.  I tried to fix the problem by following some tutorials and entering commands in the terminal.  I don't know how badly I messed things up.  that's why I am here.
at this time, I am not sure if I have pulse or alsa.  neither work anyway.
I am getting ready to wipe the partition and install new, but I thought I would come here and ask for help first.
I might also learn something about configuring and diagnosing sound problems while I am at it.  I am pretty good with the terminal and editors.

thanks.


edit:  I am running OS4 (not mac) linux as it says in the title.  either 12.04 or 12.10.  I can't seem to find where it says.

---

### Post by oldos2er on 2013-12-27
Moved to Other OS/Distro Support.

---

### Post by mips on 2013-12-27
check alsa mixer.

---

### Post by classacted on 2013-12-27
I actually couldn't believe it was alsamixer, but it was.  I have sound.

to start with, all I had (as you see in the picture) was master.
I added everything I could, and everything on the bottom that had a red X, I removed the X by clicking on it.  by the time I removed the last X the sound was playing.

it turns out that I need all of these in the alsamixer and that none are muted:

1. master
2. headphone
3. front
4. surround
5. center
6. LFE

thanks mips.  you were right  :)
I'll mark this thread as SOLVED if I can figure out how.

---

