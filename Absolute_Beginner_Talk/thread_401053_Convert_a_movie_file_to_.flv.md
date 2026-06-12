---
title: "Convert a movie file to .flv?"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by miggols99 on 2007-04-04
I want to convert a movie file (.mov) to a flash file (.flv). Can I do this? The one built into flash doesn't  work.

---

### Post by eljalill on 2007-04-04
ffmpeg should be able to fo this. It's in the repositories, but apparently you have to do a special build for that task.
Here: [http://flowplayer.sourceforge.net/encoding.html](http://flowplayer.sourceforge.net/encoding.html) is more information.

But I am not sure, whether you'll be wanting to compile yourself...

---

### Post by miggols99 on 2007-04-04
Can you explain what you put into them? Does it go like this?
```
ffmpeg -i name_of_movie_to_convert.[avi] -s (size of movie)>> 320x240 -ar 44100 -r 12 name_of_movie_to_convert_to.flv
```

---

