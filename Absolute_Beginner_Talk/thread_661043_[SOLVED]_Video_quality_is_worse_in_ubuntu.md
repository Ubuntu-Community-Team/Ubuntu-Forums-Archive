---
title: "[SOLVED] Video quality is worse in ubuntu?"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by Skivache on 2008-01-07
Today I downloaded a .m4v file to watch in Ubuntu and noticed that the quality seemed worse than when I watched a similar video in windows.  I booted windows and I was right, the same video in Ubuntu is much more pixelated than it is in windows. I have attached 2 screenshots to show you just how bad it is. I have used totem and vlc but both produce the same quality.  Can anyone tell me why this is and how it can be fix it

---

### Post by kellemes on 2008-01-07
Did you install the best driver there is for your graphics-card?

---

### Post by philinux on 2008-01-07
Personally I prefer mplayer with its optional smplayer gui front end.

---

### Post by Skivache on 2008-01-07
Yes, I have the latest Nvidia drivers for my card, I am going to try playing the same video on another computer running linux to see if it has the same problem.

---

### Post by Skivache on 2008-01-07
> **philinux said:**
> Personally I prefer mplayer with its optional smplayer gui front end.

Does that have any effect on the video quality?

---

### Post by philinux on 2008-01-07
I've always thought it better than totem.

These apps are all free from synaptic. Try them out, you've absolutely nothing to loose.

---

### Post by Skivache on 2008-01-07
Mplayer doesn't seem to play .m4v video files.  I am going to play the same video on an Intel and another Nvidia card to see if it is better quality.

---

### Post by philinux on 2008-01-07
Just looked at the msnbc site and most videos are flash really good quality.

How are you getting the .m4v files. I could have a look how they run on my system.

---

### Post by Steveway on 2008-01-07
Oh yes, I see it. Your Windows seems to add an ugly blur to your Videos.
That's not good.
(Just kidding, try to change the video-output of VLC to something different, afaik OpenGL gives good results.)

---

### Post by LowSky on 2008-01-07
Personally the two look almost the same, the pixilation could be from grabbing a peice of the video that was moving, or changing color. I would love to see another sample of something from the middle of the show.

The best you can do is check your diplay settings, make sure your using the newest driver, that you using the correct refresh rate for the monitor and correct suggested resolutions.

m4v is an apple quicktime format of mp4 if my memory is correct. The should run fine if you have all the codecs installed. Unless its DRMed videos that have been converted, then their will be some quality loss

---

### Post by Skivache on 2008-01-07
The same video plays fine in gxine on another linux distro (comp with nvidia card).  There must be something weird with my drivers or codecs. I will grab some new drivers for my card and post another screenshot for you guys.  The video comes from [here]("http://www.msnbc.msn.com/id/8132577/").

---

### Post by philinux on 2008-01-07
In mplayer both m4v and wmv look fine to me. Very acceptable. As long as you dont look full screen.

---

### Post by Skivache on 2008-01-07
I think I have solved my problem, Ubuntu seemed to be using the wrong driver for my card. The quality is much better now in totem and vlc. 
PS - I posted some new screen shots from the middle of the show for LowSky.

---

