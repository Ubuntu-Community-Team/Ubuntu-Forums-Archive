---
title: "New install issues...noob needs help!"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by haw338 on 2007-03-02
Hey there all...

Here's my story: I am trying to install ANY ubuntu on my system.  I have tried both the 6.06 and the 6.10 versions.  Both failed miserably.  I can not even get the live cd portion to work.  It goes into the ubuntu selection screen, I make the selection of starting the live install, it shows the progress bar, then flashes the cursor in the upper left, and then the best part is it will go into a blank black screen, and my system will give me about a second long beep (the internal kind that you never want to hear...).  I have tried the different boot methods, but I believe I am doing that wrong.  I tried the noapic, nolapic, pci=noacpi, all doing exactly nothing for me.  I'm a noob when it comes to programming and linux, but I teach the hardware end of PC's for a living (hmmmm...maybe I should switch careers!)  So I am thoroughly stumped, frustrated, and disgusted by my linux experience, or the lack of it so far.  Here are the specs of my PC followed by all the versions that I have tried up to this point.  Hope one of you ubuntu geeks are laughing at me right now and saying that it is a simple fix!  Please enlighten me!!!!!

PC Specs:

AGP8X Mobo
AMD athlon 64 3000+ 2.01 GHz
1.5 GB RAM
XpSP2
3 HDD's (1 seagate, 2 WD's; 40 GB, 200GB, 300GB)
ATI9600 video

Versions I have tried:
ubuntu-6.06.1-desktop-amd64
ubuntu-6.10-dvd-amd64
 
I am also currently downloading the alternative 6.06 version...but my guess is it won't work.  Thanks for all your help!!!!

---

### Post by confused57 on 2007-03-02
You're right, it's probably your video card, maybe this thread can help:
[http://www.ubuntuforums.org/showthread.php?t=354041&highlight=blank+screen](http://www.ubuntuforums.org/showthread.php?t=354041&highlight=blank+screen)

---

### Post by Kateikyoushi on 2007-03-02
Indeed most likely your video card, the alternate cd should work but you could try this as well with the live cd. [LINK]("http://www.ubuntuforums.org/showpost.php?p=2193083&postcount=3")

---

### Post by haw338 on 2007-03-02
Just got done trying all the suggestions...here's what's happening!  I found the file, changed it to radeon, then finished loading, blank screen with long sustained beep.  Then went through the process again, changed file to vesa, and got to the screen that says ubuntu with a pretty box around it, and then it froze.  (Version 6.06 only, version 6.10 still crashed hard).  I appreciate the help thus far...is there anything else I could try?  I've scoured the forums here for the past few days, and I haven't seen anything like that.  could it possibly be just a bad vid card?  Please help!!!

---

### Post by Kateikyoushi on 2007-03-03
I doubt the card is bad, give the alternate cd a try, I have no better idea.

---

### Post by petegreenhorn on 2007-03-03
Hi , i had a similar prob with first attempts at loading Ubuntu 6.10 . the only way to load i could load it was to disable the drive containing the windows os . soon as i did that it went smooth as you like . but hey don't ask me why . I'm new to computers altogether. Good luck , and it's worth the effort in the end .

---

### Post by haw338 on 2007-03-05
Interesting...I'll give it a try.  Thanks 

> Hi , i had a similar prob with first attempts at loading Ubuntu 6.10 . the only way to load i could load it was to disable the drive containing the windows os . soon as i did that it went smooth as you like . but hey don't ask me why . I'm new to computers altogether. Good luck , and it's worth the effort in the end .

---

