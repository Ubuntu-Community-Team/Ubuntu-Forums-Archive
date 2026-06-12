---
title: "[SOLVED] lost in tv tuner hell... please help"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by questio verum on 2007-11-16
My problem is, I can't seem to get my tv tuner configured to run under linux.

The aggravating factors are two-fold... 1.) I'm a linux n00b, and 2.) My tuner seems to be out of favor under linux.

 I have an ATI All-in-Wonder 9250 (works fine under Windows).  I'm running Ubuntu 7.10  (Gutsy Gibbon) on a Tyan 1854 mobo w/ a 1Ghz P3 and 768 MB ram.  It's old and creaky, but it does what I need it to for the most part.

I live in the US, so I'm trying to capture NTSC format.  I have the coax output from a cable box feeding into the coax input on the ATI All-in-Wonder 9250.  I installed mythtv.  Then I learned it doesn't support my tuner so I removed it.  I installed bttv 0.9.14 and xawtv.  That didn't work out and I've since removed xawtv and installed TVtime and Zapping.  They each tell me they are unable to open /dev/video0.  Zapping tells me the file or directory doesn't exist.  I'm not sure what to do about that.  

I spent time searching the web until I wound up at  [http://www.freeos.com/articles/3007/]("http://www.freeos.com/articles/3007/").  This site more than any other seemed to offer something substantial.  I've tried to follow the procedure outlined, but when I get to the part about installing, configuring and compiling video4linux, my eyes glaze over and I fall over limp onto my keyboard.  The instructions just aren't 100% n00b-friendly.  For one thing they ask me to "check for availability of videodev.o in the /lib/modules/linux/misc directory."  I can't find such a directory on my HDD.  They also ask me to "go into kernel configuration."  Not sure what that is, but it sounds risky.  Further, they ask me to "compile support for video4linux as a module."  I don't really even know what that means, -yet.  I would like to learn though.

I've got a new system build in the works, and will try to use more linux-friendly parts, but for the time being I'm stuck with what I've got.  Is there any way to make this work?

Any help would be appreciated, even if it's just telling me my card won't work.  

THX


qv

---

### Post by uclalinux on 2007-11-17
Did you set  up both the Myth TV front and back end? its a two part process. Also DID you check to see if your TV Tuner card is capable with Linux/Ubuntu?

---

### Post by derby007 on 2007-11-17
Quoted from another forum: hope this helps> 
"DO NOT get an All-in-Wonder card as these will not not work with MythTV. I would highly suggest a PVR-250/150 or you could even go with the PVR-350 but thats for advanced users and another topic. There is also the PVR-500 which is a dual-tuner card if you happen to have the right cable or satellite equipment. Any one of those you will be happy with."

---

### Post by questio verum on 2007-11-17
Yes, I did install both frontend & backend for mythtv.  I was able to open the program up, but... no broadcast signal.  After looking around on the web I found out that my tuner clearly isn't supported by mythtv.  I removed mythtv.  I've been trying to find out if the A-i-W is useable at all under linux, but have yet to find a definitive yes or no; just anecdotal responses.  

I've been looking at Hauppage tuner cards as a solution.  The PVR-500 would probably satisfy my needs for this box.  For my next rig I'd prefer something digital _and_ analog in a PCIe flavor.  Do you know if the WinTV-HVR-1800 is supported in kernel 2.6.22?


qv

---

### Post by newlinux on 2007-11-19
[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1800](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1800)

Implies it won't be in kernel until some version after 2.6.24

---

### Post by reckless2k2 on 2007-11-19
all-in-wonder does not work in linux. i know because i tried countless times. get a hauppauge card. they work.

---

### Post by Bigbird999 on 2007-11-19
Just for your info, the difference between the ATI all in wonder cards and the Hauppauge cards is that the AIWs are software encoding cards.  This means that the analog TV signal is converted to digital files by using a software program and your computer CPU to do the encoding (usually to Mpeg2).  The Hauppauge cards are hardware encoding cards, meaning that the encoding is done by a chip on the card and the digital file is written to the hard drive without consuming any CPU cycles or software.  

BB

---

### Post by questio verum on 2007-11-22
...  I have suspected as much.  I guess now I can stop wasting my time and move on.  Thanks.

qv

---

