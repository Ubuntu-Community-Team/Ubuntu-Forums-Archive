---
title: "Sound Problems"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by alakalaka99 on 2008-03-04
I have been unsuccessfully trying to solve my sound problems in 7.10 for an hour now, and I feel I have tried everything. At first, my volume was always loud, and my laptop volume controls did nothing to it. Then I realized that through the volume control I could adjust the volume from there, but couldnt use my buttons. I read through various forum posts, inputted some code and installed some things that were supposed to help. I rebooted, and now I can't get any sound at all. When I click the volume icon in the upper right hand of the screen a message saying "No volume control GStreamer plugins and/or devices found." So again I searched the forums, and installed some GStreamer things, which did nothing. My sound card is an Intel HDA card, and I have an HP dv5178 laptop. I have just recently installed Ubuntu, and am fairly new to Linux, but I know how to compile things, and imput code into the terminal, so any information will help, thanks.

---

### Post by spiderbatdad on 2008-03-05
maybe provide a link to the page containing the changes you made. Pretty hard to guess at what you might have done.:)

Also post the result of```
asoundconf list
```

If you want to work at it: this guide looks pretty good: [http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+soundmmon](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+soundmmon)

---

### Post by k33bz on 2008-03-05
Hey I had the same messages coming up when I did an update on my Kernel, I have fixed the majority of my sound issues, but it would seem you need to recompile your snd drivers again.
Follow this link to my thread and follow the instructions:
[http://ubuntuforums.org/showthread.php?p=4167431#post4167431]("http://ubuntuforums.org/showthread.php?p=4167431#post4167431")

also for other sound advice go here:
[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+soundmmon]("http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+soundmmon")

hope this helps

---

### Post by superprash2003 on 2008-03-05
try this [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by alakalaka99 on 2008-03-05
Ok, so I've tried every link you've given me so far the only one partially doing something is  the Comprehensive Sound Problem Guide.  I follow the instructions till #3, then I can't find the Alsa drivers it asks for. Also, the command "asoundconf list" returns back nothing, just a new line.

---

### Post by alakalaka99 on 2008-03-05
Ok, I followed the instructions more throroughly and I got sound back. Thanks a lot. 

Now my problem is controlling the volume with my laptop buttons. I have an HP dv5178 and the little volume up, down, and mute buttons dont work. I have checked the keyboard shortcuts, and the buttons are all registering as what they should be, they just aren't doing what they should be. Any ideas?

---

### Post by Mike1551 on 2008-03-06
Yeah, I've got the exact same problem, I was trying to get sound in my headphones only and not in both computer speakers and headphones, which failed miserably by the way, anyway, the result after some fiddling was that my sound buttons stops working. The mute button even turns to mute but nothing affects the actual sound. Oh, and I'm also using an HDA Intel soundcard. Quite the hazzle.

---

### Post by alakalaka99 on 2008-03-06
I too have the HDA card. I figured out my sound button issues by going into System > Preferences > Sound, and clicked PCM in the box near the bottom with a list like "Master, PCM, etc.". Works perfectly now.

---

