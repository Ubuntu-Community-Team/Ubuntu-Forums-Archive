---
title: "DVD drive plays CDs, but not DVDs - Feisty"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by Killtown on 2007-05-20
I have a Samsung SD-616T DVD-ROM drive.  It will play an audio CD, but gets an error message ("Could not read from resource.") when trying to play a DVD movie.  TotemMoviePlayer is what pops up first to try to play it.  I downloaded gxine, but that want play DVD's either.

Is it a driver problem?  Samsung website seemed to only have drivers for Windoz.

Is there a solution, or do I have to buy a new DVD-ROM?


PS - How do I change the defaults so when I put a CD/DVD in, I can get another program to automatically play them instead of the Feisty default players?

---

### Post by taurus on 2007-05-20
Maybe because you need to install libdvdcss2 first before you can play DVDs.

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by trent dillman on 2007-05-20
...

---

### Post by Killtown on 2007-05-20
> **taurus said:**
> Maybe because you need to install libdvdcss2 first before you can play DVDs.

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
It woooooooorked, it wooorked!


Now is there a way to change the DVD player default?

---

### Post by taurus on 2007-05-20
System -> Preference -> Removable Drives and Media -> Multimedia.

---

