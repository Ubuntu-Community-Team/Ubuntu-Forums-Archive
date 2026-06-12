---
title: "Video Conversion"
date: 2010-10-06
forum: Apple Hardware Users
---

### Post by trj021782 on 2010-10-06
I need to find some good software to convert MKV's to AVI's or anything else that will work on my PS3. 

so far I have tried the following with no success

AviDemux - never got it to start
Transmageddon - never actually converts
Arista - never converts
TheMonoSpot - never converts

I would also be willing to hear suggestions on how to get AviDemux to work because I have heard good things about this program

any suggestions?

---

### Post by e79 on 2010-10-06
Give a try to 'PMS' (stand for PS3 Media Streamer), it can convert on the fly. Though I only tried a couple .mkv so far, it worked pretty well.

[http://code.google.com/p/ps3mediaserver/downloads/list](http://code.google.com/p/ps3mediaserver/downloads/list)

Hope this helps

---

### Post by trj021782 on 2010-10-06
> **e79 said:**
> Give a try to 'PMS' (stand for PS3 Media Streamer), it can convert on the fly. Though I only tried a couple .mkv so far, it worked pretty well.

[http://code.google.com/p/ps3mediaserver/downloads/list](http://code.google.com/p/ps3mediaserver/downloads/list)

Hope this helps

Although I appreciate the attempt, this advice is counter productive. I am already using PS3 Media Server and although it does let me stream media I do not want my media streamed, I want my movies available on the PS3 via my 2TB external HDD

---

### Post by e79 on 2010-10-06
I'm sorry if I misread the question and I'm afraid I can't help you on this case. I hope someone else will have the answer.

Regards

---

### Post by Jahid65 on 2010-10-06
you can use winff for conversion.
```
sudo apt-get install winff
```
you can find some handy presets [http://winff.org/html_new/downloads.html](http://winff.org/html_new/downloads.html) you should have install the necessary codec before converting video of that type of codec.

---

### Post by SeijiSensei on 2010-10-06
Use mencoder:

```
mencoder -o output.avi -oac mp3lame -lameopts vbr=3 -ovc xvid -xvidencopts=pass=1  input.mkv
```

This does one-pass encoding.  For better quality, you can use the two-pass technique:

```

mencoder -o /dev/null  -ovc xvid -xvidencopts pass=1 input.mkv
mencoder -o output.avi -ovc xvid -xvidencopts pass=2:bitrate=1000 -oac mp3lame -lameopts vbr=3 input.mkv

```

The first pass writes a file that the second pass uses to optimize the output AVI.

You'll need to have ubuntu-restricted-extras enabled to produce MP3 output, or build mencoder manually from the source code at [http://www.mplayerhq.hu/](http://www.mplayerhq.hu/).

---

