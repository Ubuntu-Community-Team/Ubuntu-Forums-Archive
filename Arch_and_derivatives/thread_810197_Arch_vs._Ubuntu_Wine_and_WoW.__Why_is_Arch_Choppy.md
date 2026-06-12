---
title: "Arch vs. Ubuntu: Wine and WoW.  Why is Arch Choppy?"
date: 2008-05-28
forum: Arch and derivatives
---

### Post by NerdyShinobi on 2008-05-28
Ok, I'm taking the plunge into Arch, and going through install after install to get the flow of things.  I've got a basic Openbox desktop, Wine, and World of Warcraft installed in Arch.  WoW is actually on my home partition and is shared among Ubuntu and Arch.

Here's the rub:  Ubuntu gives a smooth WoW experience compared to Arch.  Arch has a stutter in graphics timed with a big disk read every 5-10 seconds.  I have absolutely no clue how to fix this.  What is diferent between Wine/WoW in Ubuntu and Wine/WoW in Arch?  If I can just nail this down, I think I could go Arch full time!

---

### Post by chucky chuckaluck on 2008-05-28
seen this yet? - [http://wiki.archlinux.org/index.php/Wow](http://wiki.archlinux.org/index.php/Wow)

---

### Post by chachawpi on 2008-05-28
It isn't choppy for me.  I'd say performance in Arch is around 5% better than it is in Ubuntu.  There must be something that you have running on your system.  Are other games choppy?

---

### Post by Dr Small on 2008-05-28
Maybe the wrong video driver?

---

### Post by czarr on 2008-06-04
It seems like your xorg may not be configured corectly, what did you use to create it? If your using nvidia drivers then you should use the nvidia tool to create it. Make sure acceleration is on also. 
[http://wiki.archlinux.org/index.php/NVIDIA](http://wiki.archlinux.org/index.php/NVIDIA)

---

### Post by NerdyShinobi on 2008-06-04
Ok, just an update:  Low frame rate and choppiness were 2 seperate issues:

Choppiness was caused by the CFS scheduler.  There's a pacage in the AUR that's a kernel patch for just this issue.  I would LIKE to install the Zen kernel and it's matching nvidia-beta driver, but that's not working yet for me...but the patched vanilla kernel works fine.  CFS = Choppy WoW.

Low frame rate was a problem shared in both Ubuntu and Arch, and was a straight up Wine issue.  Downgraded to 0.9.61, and framerates skyrocketed!  For Ubuntu, I just grabbed the proper .deb directly from WineHQ and installed with dpkg -i.  In Arch, I used yaourt to install wine (yaourt -Sy wine)...I got totally lucky that it installed an earlier version. :)

Hope this helps others....certainly pushed me one step closer to Arch.  Now, to get some kind of ipod-convenience action going....

---

### Post by handy on 2008-06-04
I can't play Guild Wars in Arch, & when I play a DVD it is somewhat choppy, for lack of a better word.  I consider these two problems to be due to the poor ATi GPU drivers that I have to use, as the same hardware running OS X does a fantastic job in both of those areas.

Is it possible to configure these problems away?

I'll look at the WoW link given in this thread & see if it has info' that can help me.

I'll post results.

---

### Post by handy on 2008-06-04
Both links were completely useless to me with regard to improving my display quality, during both games & movie playback.

---

### Post by NerdyShinobi on 2008-06-04
@handy  Is it liek a pause or stutter exactly every 15 seconds?  That was the "choppy" problem I had, and the CFS scheduler fix worked to fix it.

---

### Post by handy on 2008-06-04
> **NerdyShinobi said:**
> @handy  Is it liek a pause or stutter exactly every 15 seconds?  That was the "choppy" problem I had, and the CFS scheduler fix worked to fix it.

No, in DVD's I get a horizontal banding when the stress is on display wise, which of course interferes with my viewing pleasure.  I usually choose to boot into OS X to watch a movie because of this problem.

As far as gaming is concerned, I can not play Guild Wars with either Cedega or CrossOver Games (which is the better one these days) as the graphic interpretation is so poor.

As previously stated (I think) I think that these problems are due to poor ATi drivers for Linux & the GPU in my iMac.

I may be wrong, I would love to find a solution instead of waiting for AMD to get it right.  Not that I have any problems with AMD, if it was not for them, intel chips would be slower & vastly more expensive.

---

