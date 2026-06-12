---
title: "Updates cause problems. Why?"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-03-29
When I do the initial updates (about 113 files) my ATI Radeon 9200SE has fits. I'm sorry, at this time I can't afford an Nvidia card. So, please, don't go there. However, you can send me yours. lol \\:D/ 

To continue: The normal screen crashes and a new screen tells me that my video resolution is set to high. I have to reboot and start in safe mode (?) and retype into terminal the instructions to re-install my video driver. Sometimes it works and sometimes it doesn't.

What is there in the updates that could be causing this problem? I realize, from what I've read,  that when a new kernel is installed that I have to re-install my video driver. I do that, but I still get the screen crashes. I tried installing Envy to see if that would help. However, I can't get Envy to install. I noticed that some other people have had difficulty installing Envy. I prefer line command but that doesn't seem to solve my problem with the updates. Does anyone know if it is ok to leave the updates uninstalled? If I need them, what ones can I leave out that may be messing up my video driver?

BTW, does the video resolution and refresh rate have anthing to do with video problems?

Thanks for your assistance. I have been working on this problem for over a month. I get it to working and then one of those crazy updates messes my video up again. [COLOR=Blue]Me no likum updates![/COLOR] For the first time in twenty-three years of computing, I got so mad yesterday with this problem that I did a slam dunk on my keyboard. Not the thing to do. Now I need to update my keyboard. [-X lol

---

### Post by justin whitaker on 2007-03-29
Yeah, updates to Xorg tend to break, well, Xorg. :) 

You can reinstall the drivers via aptitude and apt...I forget the commands, but they are here in the forums. 

Yes, the resolution problems are related to the video.

As for leaving updates...you can leave them, even deselect them...you never actually have to update unless there is a security patch, and then you should patch it. The updates are really more like suggestions.

---

### Post by kittyhawk63 on 2007-03-29
> **justin whitaker said:**
> Yeah, updates to Xorg tend to break, well, Xorg. :) 
You can reinstall the drivers via aptitude and apt...I forget the commands, but they are here in the forums. 
Yes, the resolution problems are related to the video.
As for leaving updates...you can leave them, even deselect them...you never actually have to update unless there is a security patch, and then you should patch it. The updates are really more like suggestions.

Thanks for this information. When I first started using Linux back in early February, I was told that I needed to install all the updates. I am glad to hear that I don't. I have charter.com and they have been really good about protecting me from attacks.
 Thanks again.
kh

---

