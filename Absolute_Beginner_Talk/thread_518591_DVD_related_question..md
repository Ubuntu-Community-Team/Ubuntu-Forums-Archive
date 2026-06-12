---
title: "DVD related question."
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by SmokingGun on 2007-08-06
I have downloaded a dvd in the form of .VOB, .IFO, .BUP files.  

My question(s) is, how do i go about burning to DVD.  Is it as simple as just copying the AUDIO_TS and VIDEO_TS folders on to disc?  

Also, if i wanted to convert the DVD into a smaller mpg what is the best way to do it?  Can it be done?  

Finally, can the DVD files be played as is?  ie, just like putting the disc in the drive and having the menu, etc...?

---

### Post by Hallvor on 2007-08-06
Yes, just copy the audio and video folder to a blank dvd and burn it.

For conversion, I would recommend the open source XviD using an application like Acidrip or DVD::Rip. Acidrip is a little more straight forward, but may stress your dvd-rom as it reads directly from dvd-rom. It does not always hit the file size correctly. If you decide to have a 700 mb file, it might as well turn out as a 670 mb file. 

DVD::Rip is better for advanced users since it has more options, and does not stress the dvd-rom for hours. It can copy all the files to the hard drive before transcoding, and it hits whatever filesize you decide (at least when you copy to hard drive first).

> sudo aptitude install acidrip

[https://help.ubuntu.com/community/DVD::Rip](https://help.ubuntu.com/community/DVD::Rip)

---

