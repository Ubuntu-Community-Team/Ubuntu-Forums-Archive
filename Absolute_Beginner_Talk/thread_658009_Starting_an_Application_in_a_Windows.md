---
title: "Starting an Application in a Windows"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by chewit on 2008-01-04
Hi,

I want to be able to start an Application in a window. I have a few games which makes the screen go blank, due to the screen resoultion been set too high. Is there a way to be able to start the application in a window. using the terminal???

---

### Post by spydon on 2008-01-04
Many games have parameters that set them to windowed, you can write this to see which parameters that is available for the game:
```
gamename --help
```
Then look for windowed mode or something like that....

For example the game xmoto you write this to get it windowed:
```
xmoto -win
``` or ```
xmoto --windowed
```

---

