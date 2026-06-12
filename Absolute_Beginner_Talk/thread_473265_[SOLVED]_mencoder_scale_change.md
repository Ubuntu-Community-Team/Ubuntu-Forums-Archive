---
title: "[SOLVED] mencoder scale change?"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2007-06-13
I need to convert an ogg file to avi or mp4. I know how to with mencoder, but I need to change the scale to 640:480. How can I add a scale change to this command: 
```
mencoder movie.ogg -o movie.avi -ovc lavc -oac lavc ?
```

Here's how to do it for reference
mencoder inputfilehere -oac mp3lame -ovc lavc -ofps 30 -vop scale=320:240 -o out.mpg

---

