---
title: "record a windows media player video"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by helphope on 2007-05-05
Hi everybody.

I'd like to record and then burn a windos media player video such as ```
http://www.la7.it/news/videorubriche/dettaglio.asp?id=1226&tipo=22
``` but I haven't he faintest idea where to start from.

Is there any command from CLI?

Thanks

---

### Post by cvmostert on 2007-05-05
> **helphope said:**
> Hi everybody.

I'd like to record and then burn a windos media player video such as ```
http://www.la7.it/news/videorubriche/dettaglio.asp?id=1226&tipo=22
``` but I haven't he faintest idea where to start from.

Is there any command from CLI?

Thanks

first you have to get a plugin for firefox to download the flash video... or use this site

[http://javimoya.com/blog/youtube_en.php](http://javimoya.com/blog/youtube_en.php)

Then you will have to convert the file with ffmpeg2theora or ffmpeg to a better format... 

OR.. you can just leave the file as a .flv (flash) file, and burn it to disk using any burning program.

---

### Post by helphope on 2007-05-09
I've managed with this: from shell

> mplayer mms://la7.it/news/videorubriche/dettaglio.asp?id=1094&tipo=21 -dumpstream -dumpfile la8.wmv

maybe it may be useful to someone

I was wondering whether I can download a wmv file with wget.
Any hint?

Thanks:popcorn:

---

