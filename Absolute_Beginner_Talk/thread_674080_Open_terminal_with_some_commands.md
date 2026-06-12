---
title: "Open terminal with some commands"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by Mramius on 2008-01-21
I would like to open a terminal with an echo command saying a certain line of text depending upon which terminal is opened.  I would also like that terminal to play a sound.

Is this possible?

---

### Post by brennydoogles on 2008-01-21
I know it is possible to echo certain text when a terminal opens... I am not sure about the sound though. Here is what my terminal looks like when I open it.....

---

### Post by ikex on 2008-01-21
> **Mramius said:**
> I would like to open a terminal with an echo command saying a certain line of text depending upon which terminal is opened.  I would also like that terminal to play a sound.

Is this possible?
if your using gnome the following worked for me
first i made a script test.sh
```

#!/bin/sh
echo "some text here?"
aplay -q test.wav
bash

```then ran 
```

gnome-terminal --command="sh test.sh"

```hope that helps

ohh aplay is ALSA specific, so you might want to look also into 'play'

---

### Post by Mramius on 2008-01-21
Works like a charm ikex!  Thanks!

---

### Post by Mramius on 2008-01-21
> **brennydoogles said:**
> I know it is possible to echo certain text when a terminal opens... I am not sure about the sound though. Here is what my terminal looks like when I open it.....

How do you get it to echo an ascii image?  I added one to my script but it fails to launch.

---

### Post by Mramius on 2008-01-23
Anyone?

---

