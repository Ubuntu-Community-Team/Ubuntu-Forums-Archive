---
title: "Creative webcam and Ubuntu 6.06"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by bcoop on 2007-05-19
Hi,
I am running Ubuntu 6.06 2.6.15-28 kernel. I have been trying to get a webcam up and running so I can converse with my kids easier. I have a Creative Notebook cam VF0250. I have obtained compiled and modprobed both spca5xx and gspcav1. spca5xx doesn't do a thing, I suspect due to the kernel being below 2.6.11. modprobe loads gspca fine, the cam light comes on and /dev/video0 exists. But still no picture through vlc, xawtv or camorama (latter freezes).  I have redownloaded the module gspca and compiled it but still with no luck seeing video. I hate to return the cam as it works well with my Mac.

Any help would be great.

Coop.

---

### Post by the.dark.lord on 2007-05-19
Exactly which webcam? And why aren't you using Ubuntu 7.04?

---

### Post by bcoop on 2007-05-25
I am using a Logitech notebook cam (046d:08d8). Using macam on my mac the Logitech also works well.

I returned the Creative as it wouldn't install properly on a Win box either (black screen).

When the cam is plugged in it calls gspca (only) creates the /dev/video then nothing appears in any software even though it is conf for /dev/video or video0.

Module assistant doesn't list gspca as an option even though I am using 2.6.15-28?

I haven't upgraded to 7.04 as I am in the middle of some work that I can't mess up. An upgrade might destabilize what I am doing - happened in the past. After 31 May the possibility exists.

Thanks much for your thoughts
Coop.

---

### Post by Inxsible on 2007-05-25
You might wanna give [https://help.ubuntu.com/community/EasyCam](https://help.ubuntu.com/community/EasyCam) a try !
 
I think in the background it also uses Camorama, and since you said that Camorama freezes for you, I don't know if this would work, but no harm trying, I guess

---

