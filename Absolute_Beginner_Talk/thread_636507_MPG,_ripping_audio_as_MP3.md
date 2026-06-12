---
title: "MPG, ripping audio as MP3?"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by Cheese Roller on 2007-12-09
Can somebody tell me the name of a graphical program to rip audio as an MP3 (Ogg would be fine also) from a MPG file?

Thank you.

---

### Post by jordanmthomas on 2007-12-09
I don't know of one with a GUI, but mencoder will do this.
You can try looking for a frontend to mencoder if you don't want to use mencoder directly.

---

### Post by Dr Small on 2007-12-09
It's not graphical but it worked for me:
```
ffmpeg -i filename.mpg output.ogg
```

I don't have no mpg videos to test, but you could try it.

---

### Post by Cheese Roller on 2007-12-09
But then I can't pick the bitrate.

---

### Post by Dr Small on 2007-12-09
Try:
```
man ffmpeg
```

> -maxrate bitrate
           Set max video bitrate tolerance (in kbit/s).


---

### Post by jordanmthomas on 2007-12-09
ffmpeg has tons of options, including bitrate.
the -ab flag sets audio bitrate.

mencoder has similar options.

---

