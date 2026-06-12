---
title: "vobcopy question"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by O-pos on 2007-05-28
Hello,

when vobcopy copies vob files from DVD on the hard drive, it maintains all languages, but doesn't copy subtitles. How is it possible that it could copy subtitles too? in Windows, DVD decrypter could copy subtitles too.

---

### Post by OzzyFrank on 2007-07-13
Hmm, I have used vobcopy once, but was EXTREMELY happy with it - especially compared to DVD Decrypter ([http://ubuntuforums.org/showthread.php?p=3016611#post3016611](http://ubuntuforums.org/showthread.php?p=3016611#post3016611)) - as it saved me many hours! As far as I could see, the subtitles were there, as I had to disable them. If you find the answer please post it in case others experience this. All I can add is my good results were achieved with this command:

**vobcopy -f -F 64 -l**

---

### Post by andrew.46 on 2007-08-06
Hi,

 Following your vobcopy queries:

> **O-pos said:**
> Hello,

when vobcopy copies vob files from DVD on the hard drive, it maintains all languages, but doesn't copy subtitles. How is it possible that it could copy subtitles too? in Windows, DVD decrypter could copy subtitles too.

There is an option in vobcopy to mirror the DVD:

```
       -m, --mirror
              mirrors  the  whole  dvd to harddisk. It will create a directory
              named after the dvd and copy the ifo, bup and vob  files  there.
              The title-vobs are decrypted during this.

```

This is the ay I normally use vobcopy, as I have a dual layer burner so the whole movie, subtitles, video quality etc is preserved.


                   Andrew

---

