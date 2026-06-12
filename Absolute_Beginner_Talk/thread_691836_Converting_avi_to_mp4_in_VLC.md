---
title: "Converting avi to mp4 in VLC"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by phoenix23 on 2008-02-09
Trying to convert an avi to mp4 ipod

:sout=#transcode{width=320,canvas-height=240,vcodec=mp4v,vb=1024,scale=1,acodec=mp4a,ab=128,channels=2}

The video is fine, but there is no audio. Am I using the right codec? mp4a? That's what all the tutorials say I should be using. Also tried mpga... no sound also.

Thanks

---

### Post by fiddledd on 2008-02-09
You could try Avidemux, it's a GUI and converts almost all containers with a few clicks. I think it's in the repositories. If it's not the latest version in repos you can get .deb from here:

[http://www.getdeb.net/app/Avidemux](http://www.getdeb.net/app/Avidemux)

---

### Post by nothingspecial on 2008-02-09
Or try Winff.

---

### Post by mc4man on 2008-02-09
A fairly new app that shows promise
[http://teknoraver.campuslife.it/software/mp4tools/#ubuntu](http://teknoraver.campuslife.it/software/mp4tools/#ubuntu)
More advanced
[http://h264enc.sourceforge.net/faq.html](http://h264enc.sourceforge.net/faq.html)

---

### Post by phoenix23 on 2008-02-09
So in avidemux you use mp4 format, x264 video and faac audio?

How do you resize the video to 320x240 so it'll play on the psp?

---

### Post by justsomedude on 2008-02-09
^^No, you have to use XVid instead of x264 in Avidemux.

The iPod is capable of playing x264, but only up to AVC level 1.3. Avidemux doesn't give you acces to AVC levels, so you have to use XVid instead.

faac works fine (make sure you downmix to stereo).

You can find various resizers if you click Filters.

Also, make sure you completely disable b-frames in XVid, the iPod does not understand b-frames.

---

### Post by phoenix23 on 2008-02-09
Is xvid4 the same as xvid? Cause I don't see a plain old xvid

And do you know if this will still play on the psp?

---

### Post by justsomedude on 2008-02-09
> **phoenix23 said:**
> Is xvid4 the same as xvid? Cause I don't see a plain old xvid

Yes.

> And do you know if this will still play on the psp?

No idea, I don't have a PSP. However, Avidemux has a PSP Autowizard (Auto --> PSP).

---

