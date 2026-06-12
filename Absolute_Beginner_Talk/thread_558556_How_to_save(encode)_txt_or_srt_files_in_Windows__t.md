---
title: "How to save(encode) txt or srt files in Windows  to be read correctly in ubuntu"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by offline on 2007-09-24
When I move srt or txt files written in greek from my windows machine to my ubuntu pc, I can not read them. Neither vlc or smplayer or gxine or... can do it. Some even won't start playing the relevant clip when this subtitle file is chosen.   :(

---

### Post by hyper_ch on 2007-09-24
Windows does not use UTF-8 by default as character encoding. So you'd have to set your media player to use ISO-xxxxxx-x to be able to properly display them.
Or you could completely change your system to ISO-xxxxxx-xx

---

