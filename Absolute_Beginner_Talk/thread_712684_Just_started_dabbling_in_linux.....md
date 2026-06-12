---
title: "Just started dabbling in linux...."
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by offbeat on 2008-03-02
hello. I am a freshman in college who recently has switched his preferred major to Computer Information Systems. Whereas I am pretty competent with Windows, I feel as though its my best interest to dabble in getting a basic understanding in Linux because I have a feeling it's an operating system I will encounter alot in the courses I will be taking! I'm also kind of personally fed up with some of the unfortunate nuisances I encounter through Windows Vista, and would like to go for a change in pace.

I downloaded the Boot CD and ran the active environment, however I encountered a few issues that I assumed could be addressed here. I'm sure they are relatively simple fixes, but as I said, I'm a total neophyte to this thing, so my apologies for my ignorance.

(My computer is a Dell Latitude D830, fyi, I don't know if that would matter)

My first big problem is that I cannot connect to the internet using the active environment, which makes me reluctant to fully install Linux until I can get on the internet and address my problems through Linux instead of having to log back onto Windows to do so. My sound card also isnt syncing up with Linux, and I couldn't unmute my computer because I was missing some driver. Is there some kind of package of drivers I need to install in order to make it compatible with my computer?

again, sorry for being so ignorant to this entire concept, but this is totally fresh ground for me. Thanks alot for any help you can provide!

---

### Post by aysiu on 2008-03-02
This might help you out:
[https://wiki.ubuntu.com/LaptopTestingTeam/DellLatitudeD830](https://wiki.ubuntu.com/LaptopTestingTeam/DellLatitudeD830)

---

### Post by jlambeth1 on 2008-03-02
I have a Dell Latitude D630 so the specs for the sound card are probably the same.  To get the sound working, open a terminal and type
sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa.

This got my sound working.  As for your internet problem, maybe someone else has a solution as my wireless connection has always worked great for me.

---

