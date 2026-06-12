---
title: "Choppy video"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by jackichad on 2007-05-09
Hello all,

Just installed Ubuntu 7.04 on my IBM Thinkpad T23.  So far I am loving everything except it seems like the video is very choppy.  One example I can give is when I'm choosing a screensaver some of the more intensive graphic screensavers appear very choppy and almost bring the system to a crawl.  I also notice this on some games I play.  If I launch the game Chromium it just completely brings the system to its knees.  Normally I would just think that it is because of the lame little video card on this laptop, which I believe is a S3 Savage (no idea how much on board ram) but I had Ubuntu 6.06 installed on this system for awhile and the screensavers had no problem.  

Is there some sort of package I need to install to optimize my system's video performance or a tweak I need to make somewhere?

Any help would be greatly appreciated.  I'm loving everything else about the new OS so far.

Thanks!
-Chad

---

### Post by Stickymaddness on 2007-05-09
Do you have your video drivers installed?

---

### Post by jackichad on 2007-05-10
Do you know where I could locate the files?  I have done some googling trying to track them down but have not had any luck.  

Thanks in advance for you help!

---

### Post by IainT on 2007-05-10
Bring up the terminal and type *glxinfo*

Tell us what these two lines say:

direct rendering:
server glx vendor string:

Also - when you say video do you mean .avi files and the like too?

---

### Post by jackichad on 2007-05-11
Here is the info you requested:

direct rendering: No
server glx vendor string: SGI

To be honest, I don't notice it so much on .avi files and youtube and that type of thing as much as I do the slowdown on screensavers and games like Chromium

Thanks for your help!!!

---

### Post by RomeReactor on 2007-05-11
> direct rendering: No

Hi. The problem is you don't have 3d acceleration on your card right now; [this link]("http://ubuntuforums.org/showthread.php?t=75393") explains methods to go about doing that. Sorry I can't be of more help, as I don't have a Savage card and know very little about them.

---

### Post by jackichad on 2007-05-13
Followed the steps in RomeReactor's link but unfortunately I am still getting the "direct rendering: no" field.

Any help is appreicated.

Thanks!

---

### Post by goodmayonnaise on 2007-08-18
direct rendering: No
server glx vendor string: SGI

Sorry, I don't have any help. I'm new to linux and Ubuntu and I'm looking for answers.  I also share your problem. I'm running Ubuntu 7.04 on a T23 and I'm having the same glitches. 

Video playback is ok really, It's just 3D rendering I think. 

I guess I just want to know if anyone has resolved this issue.

---

