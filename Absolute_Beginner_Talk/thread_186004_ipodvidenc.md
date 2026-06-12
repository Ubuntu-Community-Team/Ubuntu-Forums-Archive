---
title: "ipodvidenc"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by drobvice on 2006-06-01
I followed this post to convert videos to ipod video format on my dapper install:

[http://www.ubuntuforums.org/showthread.php?t=114946&highlight=ipodvidenc]("http://www.ubuntuforums.org/showthread.php?t=114946&highlight=ipodvidenc")

It will convert videos from avi but they appear to be slideshows and not smooth at all.  When I followed the guide, I installed all software and everything appeared to install with no errors.  Then, I tried my first video and got the previously mentioned result.  At the bottom of the guide I saw an automated install for the whole process which resulted in a gui'ed ipodvidenc but still have the same results.  I also tried vive but am having trouble with it as there are no presets when installed and I have to rename the videos to remove spaces.  Any help appreciated.

---

### Post by gommle on 2006-06-01
Did you try to view it on the ipod?

Try to download a video from Google Video in iPod format and see if you get the same result.

I have the same problem, but the files work fine when i view them on my iPod.

---

### Post by drobvice on 2006-06-02
I just tried converting another video and it came out and played great on the computer.  Haven't tried transferring to ipod yet.

---

### Post by drobvice on 2006-06-02
Anyone know about 16:9 output with ipodvidenc?  Mine came out 4:3

---

### Post by %hMa@?b&lt;C on 2006-06-02
i use the FFMPEG script, works flawlessly, it is at the bottom of the page that you linked to in your first post in this thread.  Also, if you have the 60 gb ipod i think you have to do something, it is also at the bottom of that thread.

---

### Post by drobvice on 2006-06-02
I reinstalled Vive from source last night and this time it had profiles (the .deb didn't).  I just created a profile for widescreen, et voila, magique! Now my only problem with vive is that videos with spaces in the names will not work.  I have to rename everything and take them out to convert them.  When I used ipodvidenc (both the self-made script and the gui) there was no problem with this.  Can this be avoided with Vive?

---

