---
title: "Audio and Visual Trouble"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by Net_Trekker on 2007-06-16
Dear Reader,

Hello, I'm very much a beginner and this is my third day with Ubuntu on a T40 laptop.  Everything was running very smoothly until my attempts to use either the Rythmbox Music Player and the Movie Player with MP3s and OGGs have resulted in both programs continually thinking, until, while exiting said programs, I'm told that they are "not responding".  I had previously been able to run both aps with success.  I would like to request advice as to how to better diagnose the problem?  Could you please help?

Many, many thanks.

---

### Post by matthewboh on 2007-06-16
My guess would be that you added some drivers along the way.  Is it not working for any type of file or not working for the same type of file?

I found that after I added the gstreamer0.10-plugins-bad everything stopped working, so I removed it from the Package Manager and then everything worked again.

---

