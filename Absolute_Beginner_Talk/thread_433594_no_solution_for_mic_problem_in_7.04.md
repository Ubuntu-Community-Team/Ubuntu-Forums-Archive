---
title: "no solution for mic problem in 7.04 ?"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by lumarh on 2007-05-05
I use ubuntu 7.04

i have trawled the web trying every solution i found - is it just not possible to get my mic working in feisty? I as of recently have a sound blaster live, but had the same problem with onboard sound. 

I have tried all the volume controls, preferences, mic is activated etc, volume is up, mucked around in alsamixer, in kmix, 

i can hear myself through speakers - so the problem essentialy is no mic ***record*** function.

anyone have a similar experience and/or solution? thanks 
stressing me out --- i want to yell at ubuntu dev's i mean come on....its a mic. i should be able to plug and use

---

### Post by mikewhatever on 2007-05-05
I can hear myself in the speakers, when the 'micpypass' is not muted (see the screen shot). The little window in the center comes from Edit>Properties and gives more options. Try checking them.
What is kmix? Aren't you using Ubuntu, or is it Kubuntu after all?

---

### Post by RichPicker on 2007-05-05
Lumarh:

Yup. Same problem here. And I've tried everything suggested. None of the developers respond to this problem. I agree with you - it's a mic - a simple device. The developers are only concerned about the servers? It is frustrating, and definitely NOT a viable replacement for windows.

---

### Post by Najand on 2007-05-05
Try to unmute "capture" under some mixers like alsamixer.

---

### Post by RichPicker on 2007-05-05
Capture is not muted in alsamixer. Still no mic.

---

### Post by RichPicker on 2007-05-05
I didn't originate this thread, and hope I'm not butting in. Attached is a jpg of my Alsamixer GUI.

---

### Post by Najand on 2007-05-05
> **RichPicker said:**
> I didn't originate this thread, and hope I'm not butting in. Attached is a jpg of my Alsamixer GUI.

The input source is muted. Try to change all to MAX.

---

### Post by RichPicker on 2007-05-05
In alsamixer, from the terminal, I can select Mic or Line. But there is no mute or volume level available. In the Volume Control, Capture and is at max. Those are the only adjustments available that I know.

---

### Post by RichPicker on 2007-05-05
And from the Alsamixer GUI, I can not adjust the Input level.

---

### Post by RichPicker on 2007-05-05
Here is a screen shot of my Alsamixer.

---

### Post by lumarh on 2007-05-05
everything in alsa is on full, and nothing is muted. my capture is set to mic.

and yeah kmix is the KDE equivalent but i downloaded it to see how it go's

---

### Post by lumarh on 2007-05-05
heres my settings

[IMG]http://i95.photobucket.com/albums/l159/lumarh/Screenshot.png[/IMG]

---

### Post by ccw127 on 2007-05-05
I have a slightly related problem (I think) with my 7.04 install. I am using the onboard HDA sound that is on my nforce 680i mobo. I was able to get the mic to 'slightly' work, at least to the point that ventrilo (A voip program used for video games... aka Wow) will take the input so I can talk, but when I try to use 'Sound Recorder' it acts like I have no input device; weird to say the least. Sorry this post doesn't provide a solution, but it may give people an idea of things to check. I haven't really bothered working with the problem too much because at this point, what I NEED to work, works.

Chris

---

### Post by RichPicker on 2007-05-06
Very strange. Others have the same problem also. Your settings look good to me, for what that's worth. There is no Slider on your Mic in alsamixer?

---

### Post by lumarh on 2007-05-06
not in alsa, no. in the volume controls there is one for mic (speaker output)... as well as a seperate one for capture. 

do you think uninstalling and reinstalling alsamixer might help? and where can i found a how-to on that? thanks

---

### Post by RichPicker on 2007-05-06
I've been reading messages on other sites about having to stand on your head to get the microphone to work with other linux flavors, like RedHat. It's looking to me like linux, regardless of flavor, is not the right system for laptops. Maybe it's great for servers, but it's lousy for laptops, for people who use skype, messenger, and such. I doubt there is anything wrong with your settings or applications - it's linux that's at fault. Or more accurately, it's linux that falls short.

A) Because so many PC users are desperate to find an alternative to windows, the ubuntu (and other) developers have over-sold linux. 

B) Because those of us who use laptops are in the minority, the developers don't have the time (or are not willing?) to build ubuntu (and other flavors) in a way that will work for us.

---

### Post by fca_neo on 2007-05-06
I have the same problem on my desktop and on a laptop. I looked around but there is no solution. as many have said before: this is freaking frustrating, I would love Ubuntu to be an alternative for commercial OS but that will never happen if a very simple and universal device as a mic doesn't work flawlessly.

By the way, my systems are like 7 years old so it is not a problem of the hardware being to new to get linux support.

---

### Post by lumarh on 2007-05-06
it smells to me like some easily fixed kernal problem (easily fixed by kernal hackers - ie. not me). i got my mic working pretty easily in 6.10, but 7.04 is just not doing it. i dual boot anyway but its a pain.
thanks for the help nevertheless guys

---

### Post by RichPicker on 2007-05-06
I heard from one of the developers today. They ARE working on it. They do have to prioritize, and the mic problem is understandably not the most urgent. If we can be patient a little longer they will release a fix. They are doing the best they can, they appreciate us reporting the bugs, and they appreciate it when we are patient. (I'm probably one of the most impatient.)

Peace, 
R-

---

### Post by ubnewbie2 on 2007-05-06
> **RichPicker said:**
> I heard from one of the developers today. They ARE working on it. They do have to prioritize, and the mic problem is understandably not the most urgent. If we can be patient a little longer they will release a fix. They are doing the best they can, they appreciate us reporting the bugs, and they appreciate it when we are patient. (I'm probably one of the most impatient.)

Peace, 
R-

Having been on both sides of this fence, (developing/using),  I appreciate what the devs are saying, and also, communication, both ways, such as you have provided here, is key, so thanks for letting us know.

---

### Post by ccw127 on 2007-05-08
My two cents....
I would like to reiterate that I don't think this is a kernel/driver level problem (at least not totally). I have many of the same symptoms of posters on this and other threads, and yet I have found that the mike will work in some certain situations. Try other pieces of software, you may find the combination that works.
I am using the alsa libs through wine to get my mic working for Ventrilo and it works flawless; yet I can't get anything else mic related working.

Just things to keep in mind,
Chris

---

### Post by RichPicker on 2007-05-10
Could you give some instructions on alsa.lib and wine that I might try it.

---

### Post by ccw127 on 2007-05-10
If you already have Wine installed, make sure it is at the latest version. Then go into the configuration program 'winecfg' from the cli and one of the tabs is named audio. I changed from the OSS driver to the ALSA driver and my mic works fine in windows apps under wine now. of courser this doesn't solve any problems for Linux native apps, as I haven't figured out what the stumbling block is yet.

---

