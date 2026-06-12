---
title: "mozilla quicktime plugin"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by andshoesandsocks on 2007-01-05
i want to be able to play quicktime movies and if its not too much to ask windows media player files as well. i searched the forums and found something call Mplayer. I followed the isntructions and it didnt work.

i have a 1gig processor 128mb sd ram HP. someone please help me... thanks.

---

### Post by rajeev1204 on 2007-01-05
hi

Install mozilla-mplayer from the repositories . It will play quicktime and windows media video also . If u r using the 64 bit Ubuntu then wmv is tricky

Gxine plugin aalso plays quciktime well

---

### Post by andshoesandsocks on 2007-01-05
i figured it out! thanks a lot.

---

### Post by reabralop on 2007-01-14
So what do I do if mplayer is installed and it still doesn't play ANYTHING? 

The best I can do are youtube videos.

---

### Post by icefaerie on 2007-01-14
Are your universe and multiverse repositories enabled?  If so then you can install these programs to make just about any format play with mplayer (or any other media player like Totem, Xine, or VLC):

```
sudo aptitude install gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad-multiverse gstreamer0.10-ffmpeg w32codecs
```

For more info, see this page: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by reabralop on 2007-01-14
How do I enable them? If you are referring to the terminal, I have been trying that and every code I've tried putting in has failed, and I'm about to give up on this whole thing. I am having so many problems and can't seem to get anything to work right. The basic install is fine but not enough. I've spent the whole day on this and have only gotten the initial install done. 

I'm going to watch football!

---

