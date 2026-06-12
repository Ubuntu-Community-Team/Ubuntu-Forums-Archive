---
title: "Why can't I convert avi to mp3 using Lame??"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by Niranjan81 on 2006-10-30
Am trying to convert avi files to mp3 using Lame. Just getting some shitty output.

---

### Post by Iarwain ben-adar on 2006-10-30
I may be wrong,
but isn't .avi audio AND video?

So if you convert to mp3,
you're actually converting a movie, so to speak.

Don't know how to do it correctly,
Sorry


Iarwain

---

### Post by derailed1 on 2008-05-27
In the old days with xp, I used to use winamp, output disk writer.  

I was actually looking around how to do it in ubuntu today.  And to answer your question, use ffmpeg in console.

type: 

ffmpeg -i <input> -vn <output>

the i means input and the vn means no video.

so,

ffmpeg -i tvshow.avi -vn tvshow.mp3

now you will have a mp3 rip of that avi file.  Hope this helps.

---

### Post by Bataille23 on 2008-05-27
For my "money", avidemux is where it's at.  You should be able to download it from one of the repositories.  It works a lot like the ffmpeg command, but it uses a GUI and gives you the ability to extract anywhere from less than a second of audio to three hours of audio (or however long the .avi is).  I use it all the time to get samples for my awesome music.

---

### Post by proalan on 2008-05-28
Could give VLC a try, you can output stream to a file much like winamp's write to disc feature.

---

