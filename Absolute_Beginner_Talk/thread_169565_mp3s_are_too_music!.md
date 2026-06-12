---
title: "mp3s are too music!"
date: 2006-05-02
forum: Absolute Beginner Talk
---

### Post by ZelasMetallium on 2006-05-02
Every time I try to put an mp3 file into my Rhythmbox library it says it's not an audio stream.  What gives?

---

### Post by trent dillman on 2006-05-02
You may need the proper mp3 plugin, as Ubuntu cannot ship with a decoder by default.

You should search the forums for w32codecs or install all the gstreamer plugins...

---

### Post by halitech on 2006-05-02
I may be off center but when I think of audio stream, I think of something being sent across the net. How are you trying to get the file into Rhythmbox?

---

### Post by ZelasMetallium on 2006-05-02
[QUOTE=trent dillman]You may need the proper mp3 plugin, as Ubuntu cannot ship with a decoder by default.

You should search the forums for w32codecs or install all the gstreamer plugins...[/QUOTE]
How would I go about installing those plugins?

[QUOTE=halitech]I may be off center but when I think of audio stream, I think of something being sent across the net. How are you trying to get the file into Rhythmbox?[/QUOTE]

The files are in my home folder and I'm using the File => Import Folder command.

---

### Post by aysiu on 2006-05-02
[QUOTE=ZelasMetallium]How would I go about installing those plugins?[/quote] Follow [these instructions](https://wiki.ubuntu.com/RestrictedFormats#head-a57167a3ce442dc52d9b05e46a14503330d4e970)

---

### Post by ZelasMetallium on 2006-05-02
Kay, did all that but it still doesn't work.

---

### Post by DooX on 2006-05-02
I followed also steps in Ubuntu Wiki and not working for me also.I dont get error anymore,just dont hear music.Yes,i checked is volume on it is.

---

### Post by ZelasMetallium on 2006-05-03
Any new ideas anyone?

---

### Post by mostwanted on 2006-05-03
[QUOTE=ZelasMetallium]Any new ideas anyone?[/QUOTE]

Follow the link Aisyu gave you, there's no other way. You must have done something wrong.

---

### Post by zba78 on 2006-05-03
for mp3 playback I found that installing libxine-extracodecs worked fine.

get it from [http://packages.ubuntu.com/dapper/libs/libxine-extracodecs](http://packages.ubuntu.com/dapper/libs/libxine-extracodecs) although that is for Dapper (which is what i run) I don't know if it'll work on earlier versions

---

### Post by trent dillman on 2006-05-08
...

---

### Post by wilem on 2006-06-03
This worked for me! Thanks!

---

