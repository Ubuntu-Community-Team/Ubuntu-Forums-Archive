---
title: "Xserver crashes after Gutsy upgrade...:("
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by Brightbelt on 2007-06-20
OK,
Long Story - I got caught in between Feisty and Gibbons, so I went ahead with the upgrade. Lecture me if you will -  I'm not totally against just reinstalling Feisty.  I have my stuff backed up; the thing is I figure this is worth an effort or two before giving up....maybe. I'm on a Gateway M675x laptop, with an ATI RV350 video card and a 17" screen. It's a Pent 4, 3.2 gHz processor with 1.25 GB of ram. 

I'm booting to a blank screen after the Gutsy upgrade. So I went into recovery mode and ran this:  "dpkg-reconfigure xserver-xorg". 

I chose Vesa as my driver and ALL the defaults, and I'm STILL getting a blank screen on the reboot. I tried the 'nv' driver and that didn't work. For a moment, I highlighted the ATI driver and saw trouble already, so that was not an option.   

i just thought I'd post this IN CASE anyone had any other viable options.

---

### Post by Brightbelt on 2007-06-20
I appreciate any help anyone could offer. 

Many Thanks, Frank B.

---

### Post by NeoLithium on 2007-06-20
Well, I won't lecture you since you're probably aware this is one of the dangers of using the development version ;)  So there's a link that *********MIGHT*********** help out with the ATI driver, though that's not quite guaranteed either.  It's a feisty set of instructions though the xserver-xorg-video-fglrx might work for you on Gutsy.

---

### Post by Brightbelt on 2007-06-20
Thanks NeoLithium, I appreciate the understanding :D. I can't seem to locate the link you were offering to me, however. Am I missing something? 

Many Thanks, Frank B.

---

### Post by NeoLithium on 2007-06-20
ROFL! I suppose it would help if I included the thing in my post.  WOW I need coffee. [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

---

### Post by Brightbelt on 2007-06-20
Many Thanks, NeoLithium. I got it. 

As for the other option you mentioned - 
```
xserver-xorg-video-fglrx 
```

What would I do after running that command? How does that work?

Thanks, Frank B.

---

### Post by NeoLithium on 2007-06-20
If you followed the guide down to that point *crosses his fingers* you should be able to configure the ATI driver:
```
sudo aticonfig --initial
```
and then
```
sudo aticonfig --overlay-type=Xv
```

---

### Post by Brightbelt on 2007-06-20
The very first steps in the instructions guide don't work - I get a message that there is no gtk desplay.

I think we're backed up here further than you realize. I'm in recovery mode with no GUI to speak of. 

If I don't get a good idea pretty soon, I'm going to probably just reinstall Feisty.

Thanks anyways for helping,....Frank B.

---

