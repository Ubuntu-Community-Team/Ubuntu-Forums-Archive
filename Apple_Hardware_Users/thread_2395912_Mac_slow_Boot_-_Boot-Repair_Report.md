---
title: "Mac slow Boot - Boot-Repair Report"
date: 2018-07-08
forum: Apple Hardware Users
---

### Post by f.stoneman on 2018-07-08
Hello. Any help would be appreciated. I am newer to the ubuntu/linux community but am working hard to learn my way around. I installed Ubuntu 18.04 LTS with Minimal Installation via USB on an old MacBook (black) with SSD from OWC. Ubuntu completely boots up and I can run programs and access the web. My startup is taking roughly 6minute 30 seconds and shut down I get some code to show up before I have to manual hold the power button to shutdown. First I tried re-downloading and reinstalling Ubuntu from a new USB, no change. Then I ran Boot Repair and followed the prompts. Maybe my startup time is normal for an older computer, I simply do not know enough. Again any thoughts or help would be appreciated while I continue to read through the forums. My paste bin and coding on shut down are to follow. 


My paste bin is [http://paste.ubuntu.com/p/vQRTvt627d/](http://paste.ubuntu.com/p/vQRTvt627d/)
Shut Down Coding:
[    622.816230] [drm:drm_atomic_helper_wait_for_flip_done [drm_kms_helper]] *ERROR* [CRTC:41:pipe B] flip_done timed out
[    633.056103] [drm:drm_atomic_helper_wait_for_dependencies [drm_kms_helper]] *ERROR* [CRTC:41:pipe B] flip_done timed out
[    643.296137] [drm:drm_atomic_helper_wait_for_dependencies [drm_kms_helper]] *ERROR* [PLANE:35:plane B] flip_done timed out

---

### Post by TheFu on 2018-07-08
No desktop/laptop should need more than 45sec to boot.  Most should boot in under 20s.   If they are taking longer, there is a problem.   Could be configuration, could be hardware, often is it network setup stuff so things have to time out over and over and over before boot can finish.  Sometimes it is a missing disk that was available during installation, but has since been removed or powered down.

First thing to know is that Macs are a little different, so you'll want to always post in the Apple sub-group and provide sufficient information for those good folks to know what hardware you actually have.  I don't know anything about Apple hardware, but people usually say something like "2015 MBP", which I guess provides sufficient information. "old" is subjective.  Old means 1993 to me. Is that what you intended?  2000 is "new" and 2010 is "brand new."  Facts are best.

Always include "apple" in the problem title here.  That will get more eyes with those skills to look.
"Apple MB slow boot on 18.04 Gnome3" is the title I'd use.  If you know the year for the MB, add that.

Many questions aren't apple specific, but booting is hardware-centric, so it is very relevant.

And welcome to the forums.

---

### Post by oldfred on 2018-07-08
Moved to Apple sub-forum.

I also do not know Mac, but not seeing anything in report that looks ab-normal. Maybe others knowing Mac will or know of issues.

---

### Post by f.stoneman on 2018-07-08
I appreciate the the input TheFu and thank you for the transfer oldfred. Old is very subjective, sorry about that. It is a MacBook 4,1 2008.

---

