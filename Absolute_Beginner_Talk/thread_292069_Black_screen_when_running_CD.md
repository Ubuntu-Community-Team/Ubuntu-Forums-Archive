---
title: "Black screen when running CD"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by jworld2 on 2006-11-03
I am new to ubuntu and I just want to run the CD without changing my computer. So I burned the CD and put it in and restarted the computer. The Ubuntu start screen pops up and I select "Start or Install Ubuntu" it then proceeds to load for a couple minutes. Then the creen goes black and I cannot do anything but restart my computer. How can I fix this and is this even the right way to just run the live CD?

---

### Post by compmodder26 on 2006-11-03
Sounds like it had a hard time configuring your graphics settings.  Try running it with the second option of "Safe Graphics Mode".

---

### Post by jworld2 on 2006-11-03
I've already tried that option and I get the same results.

---

### Post by Bachstelze on 2006-11-03
Maybe have a try at a Dapper CD instead. It's said to be more stable than Edgy.

---

### Post by jworld2 on 2006-11-03
I will give that a try and report back if it works or not. It might be a couple of hours depending on how long it takes to download and burn.

---

### Post by GIFRATE on 2006-11-03
I had the same problem, I had to install nvidia drivers. Basically, It goes blank when X is loading. Try Ctrl-Alt-F1 after your screen goes blank and your hard drive stop loading stuff. If you get to a terminal, you could probably load the right drivers for your video card using apt-get.

---

### Post by jworld2 on 2006-11-03
Downloaded and burned dapper and started loading it. The first time I did it it did practically the same thing as it did with edgy but then I tried to load it again with safe graphics mode. After a while of loading a screen popped up with a message saying something to the effect of that the X drivers had failed to load or were turned off. I couldn't get out of this screen and I had to restart again.

---

### Post by funrider on 2006-11-03
i had the same problem before on my laptop. i then set a lower resolution from the keyboard short cut and it worked fine. if you are running it on your desktop, i guess you can tune your monitor in a similar way.

---

### Post by bdawgg on 2006-11-03
At the first screen where you choose to install, there  should be function key options.
Choose f4 (I believe) this will allow you to change from vga (default) to 800 x 600 or whatever.
Works, as I had the same problem.

---

### Post by jworld2 on 2006-12-07
sorry it's been awhile. I stoppped trying to get it to work for a while but now i have started again. I have burned dapper onto a disc and when I try to do safe graphics mode it starts to load things as usual but then it goes to this weird screen where it says something about not being able to start xserver. I looked on the internet and found that the way to reconfigure the xserver is to type "$ sudo dpkg-reconfigure xserver".

the only problem is that I'm not sure where or when to type this in. Could anybody tell me or perhaps give me another way to get this going? 

(I've also tried knoppix and that works fine and I've tried gentoo but that gives the same problem about the xserver)

---

