---
title: "convert mpg to swf"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by r3bol on 2008-03-05
Is there any software I can use with ubuntu to convert a mpg video file to a flash swf?
Thanks.

---

### Post by Cypher on 2008-03-05
[FFMPEG]("http://ffmpeg.mplayerhq.hu/") will convert the MPG to FLV (the SWF is just the player that will play the FLV).

The version that's in the repository, however, doesn't have MP3 support so your converted files will have no audio. So follow [these instructions]("https://wiki.ubuntu.com/ffmpeg") on fixing that.

---

### Post by billgoldberg on 2008-03-05
Or the keep things easy:

use winff 

[http://biggmatt.com/winff/downloads/](http://biggmatt.com/winff/downloads/)

download the .deb

---

### Post by Cypher on 2008-03-05
The WinFF GUI is great, but still need the FFMPEG fixed up first..

---

### Post by billgoldberg on 2008-03-05
Yes, I forgot to mention that.

There is a .deb file of the full FFMPEG you can download here:

[http://skulboxx.com/Ubuntu/sbx/](http://skulboxx.com/Ubuntu/sbx/)

(you install a .deb file by double clicking it after downloading it)

---

