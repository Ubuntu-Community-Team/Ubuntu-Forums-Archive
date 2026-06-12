---
title: "ManDVD produces dvdauthor error. Please help"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by SPQQKY on 2007-07-27
I've got ManDVD and all the dependancies. I get down to the last part to generate the DVD, in the GUI it shows a warning that says mpeg files cannot be transcoded (not sure why, I have everything I was supposed to get). But I tried to generate the video anyway and I get a dvdauthor error:
```
STAT: Processing /home/my-name/ManDVD-2.4/New Folder 1//genmenu.mpg...

INFO: Video pts = 0.178 .. 0.211
INFO: Audio[8] pts = 0.178 .. 0.178
INFO: Audio[32] pts = 0.178 .. 0.178
STAT: VOBU 1 at 0MB, 1 PGCS

INFO: Generating VTSM with the following video attributes:
INFO: MPEG version: mpeg2
INFO: TV standard: ntsc
INFO: Aspect ratio: 4:3
INFO: Resolution: 720x480
INFO: Audio ch 0 format: mp2/2ch, 48khz 20bps

STAT: Processing /home/my-name/ManDVD-2.4/New Folder 1//gibvideo0.mpg...
ERR:  Error opening /home/my-name/ManDVD-2.4/New Folder 1//gibvideo0.mpg: No such file or directory
```
So what's I think it's telling me is it cannot handle mpeg audio [audio for source is MP3](which I don't understand, I have all codecs)

Any help is appreciated. I tried the multimedia and video section but no one has a clue, only suggestions of other apps.

Thanks.

---

### Post by SPQQKY on 2007-07-27
Well, I guess I give up. Ubuntu (Linux in general) is obviously not for me. Two days on this forum with litteraly 4000 people here and I can't get this to run. 
No wonder we have to pay Bill Gates for his OS and all the others for software on Windows......it actually works.

---

### Post by bferd on 2008-05-10
I know this is an old post but it may help someone to know there can't be any spaces (or punctuation?) in the file path


eg. /home/my-name/ManDVD-2.4/**New Folder 1**//gibvideo0.mpg

should be:

/home/my-name/ManDVD-2.4/**NewFolder1**//gibvideo0.mpg

Ubuntu, Windows they both frustrate me most of the time

---

### Post by dash86no on 2008-05-20
> **bferd said:**
> I know this is an old post but it may help someone to know there can't be any spaces (or punctuation?) in the file path


eg. /home/my-name/ManDVD-2.4/**New Folder 1**//gibvideo0.mpg

should be:

/home/my-name/ManDVD-2.4/**NewFolder1**//gibvideo0.mpg

Ubuntu, Windows they both frustrate me most of the time

Thanks for this post, it certainly helped me as I was having a problem due to having spaces in my filenames.

---

