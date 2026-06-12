---
title: "[SOLVED] Change Aspect Ratio In Mencoder?"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2007-06-06
I am trying to figure out how to change the aspect ratio of a video I have. Right now, to convert my video, I am using this command.
```
mencoder -ovc xvid -oac mp3lame -xvidencopts bitrate=687 -o <output.avi> <input.avi> 

```
What can I add to that to change my ratio to 4:3?

I figured it out...```
mencoder out.ogg -oac mp3lame -ovc lavc -ofps 30 -vop scale=320:240 -o out.mpg

```

---

### Post by izi on 2007-06-30
Try using 
```
mencoder [...] -force-avi-aspect 1.33 [....] 
```

The parameter in the case is X:1 (so for 4:3 = 1.33:1 use this value)

I usually use this when I just need to fix the aspect ratio of a movie since it also works with "-ovc copy" (so no need to re-encode the entire move just for changing the aspect ratio...)

---

