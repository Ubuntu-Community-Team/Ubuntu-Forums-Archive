---
title: "Music file help"
date: 2005-12-13
forum: Absolute Beginner Talk
---

### Post by CanadaGradeEh on 2005-12-13
Well, anyone who's visited recently knows that I've posted a few newbish questions. Well, now that I'm actually in Linux now, I have a very urgent problem.

I burned the mp3 files I wanted from my other partition to a DVD disk because I don't know how to use the swap space yet. Apparently Totem doesn't like my files. 
I get this error report when I try to open any of my MP3's:
> 
Totem could not play 'file:///media/cdrom0/amon amarth - bleed for ancient gods.mp3'.

There were no decoders found to handle the stream,
you might need to install the corresponding plug-ins

I transferred the files over to my hard drive again from the disk too, and they won't work if accessed from my HDD either. Any help? I'm guessing I need to find this plug-in. Either that or Ubuntu doesn't support MP3?

---

### Post by teaker1s on 2005-12-13
look in wilki for restricted formats you have to install codecs as some areas they are illigal and ubuntu doesn't want to get sued or pay a royalty for every user
[https://wiki.ubuntu.com/RestrictedFormats?highlight=%28formats%29%7C%28restricted%29](https://wiki.ubuntu.com/RestrictedFormats?highlight=%28formats%29%7C%28restricted%29)

---

### Post by sonny on 2005-12-13
The mp3, wmv, wma, mov and the realplayer codecs are not "officially" supported on Linux, although you can get them to work, specially the mp3 one's. That is because as we are a free (as in freedom) community we don't like closed source codecs, and their creators don't care about anyone who doesn't pay them to use their codecs, and as Ubuntu won't pay a dime for them their not preinstall. There's some legal advise if you live in the USA, but as I live in Mexico I don't care about that, you can go to: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) to know how to install the codecs.

---

### Post by CanadaGradeEh on 2005-12-13
nvm

---

### Post by CanadaGradeEh on 2005-12-13
Hmm, I unpacked the universe and multiverse like it said, ran the code, downloaded the codecs, then ran that code, but it still says I need codecs.

---

### Post by sonny on 2005-12-13
I'm a very questioning man, and I've learn to doubt about almost everything, please do this for me:
copy the mp3 file to your hard drive, then change the name so it won't have any spaces in blank, then play it. I know it doesn't seem like it will help, but I've had very bad experiences with the spaces in the file's name.

---

### Post by CanadaGradeEh on 2005-12-13
Ok, but if it doesn't work I'll go to bed and come and complain tomorrow lol

---

### Post by sonny on 2005-12-13
Ok.. but if it does you stay with me, because I'm "studing" for my final test tomorrow, and I would like some company... hehehehehehehehe... ;)

---

### Post by CanadaGradeEh on 2005-12-13
fine, I'll stay up a bit longer :rolleyes: Ok, so that didn't work. 

This may piss you off, but maybe you could run me through what YOU did to enable MP3 access when you first installed? That is, if you remember :P It doesn't seem like the link provided wants to help me. Maybe I'm doing something wrong?

---

### Post by Evilchicken on 2005-12-13
Alright sonny heres a question to keep you company :D . I hear people say alot of stuff along the lines of "I burned the mp3 files I wanted from my other partition to a DVD disk because I don't know how to use the swap space yet." Why do they do that? Ubuntu recognized stuff on my other fat16 and fat32 partitions and I can open them all and what not. So should I be burning them still? Is this the key to MY not working plugins?

---

### Post by CanadaGradeEh on 2005-12-13
Well I'm an uber newb if you haven't noticed :P I realize that maybe I'm not even ready to be fooling around with Linux yet, but I'd like to get a taste of everything instead of just learn one thing at a time. I'll focus more on learning specific things at a time, yes, but I'd also like to have some knowledge in the areas they branch of into.

---

### Post by Evilchicken on 2005-12-13
Hey so am I. For 2 weeks now i've been trying to get mp3 playback. The hardest part is not having an internet connection. So I have to download something install it (well I think I install it can never tell) find out its dependencies go get them then repeat all this again. It kinda sucks. 3000 mp3's and cant figure it out.

Well I got to take shit exams today. So good luck **CanadaGradeEh** on getting that mp3 playback. Hopefully you'll figure it out so you can help me :cool:

---

### Post by sonny on 2005-12-13
Hey CanadaGradeEh what was the output when you run "sudo apt-get install gstreamer0.8-plugins gstreamer0.8-plugins-multiverse gstreamer0.8-ffmpeg"???

After running that please type: "gst-register-0.8" (without the quotes) in the same console

---

### Post by CanadaGradeEh on 2005-12-13
Well, considering I don't have much of an idea at all what I'm doing in Linux, and I'm pretty newb with how hard drive partitions work as well, I don't think I'll see it any sooner than you, because the solution I find will most likely be here lol.

Thank you for your effort Sonny, and sorry if I misinterpreted your post chicken. Good luck with your exams too. I'm dead freakin' tired lol. Anyway yea, good night, and consider this post a /addfriend or something. :)

---

### Post by CanadaGradeEh on 2005-12-13
Well I'm back if any of y'all got some ideas lol

---

### Post by Estariel on 2005-12-13
[QUOTE=sonny]Hey CanadaGradeEh what was the output when you run "sudo apt-get install gstreamer0.8-plugins gstreamer0.8-plugins-multiverse gstreamer0.8-ffmpeg"???

After running that please type: "gst-register-0.8" (without the quotes) in the same console[/QUOTE]

did you do this?

Open a Terminal (you can do this from the gnome menu) and enter the code as stated above (without the "")

---

### Post by CanadaGradeEh on 2005-12-13
CRAP! Why did I not see that post?

Ok, I'll boot into Ubuntu then tell you guys the output of the first code before I enter that second line of code.

---

### Post by CanadaGradeEh on 2005-12-13
Ok so I found out what I could do to listen to my music. I don't know if it was the proper installation of the codecs or the xine engine that Amarok uses, which has great media support. I was recommended Amarok by a friend, but also tried some different app-get installs at the same time. This is what I did in order:

> sudo apt-get install libdivx4linux

sudo apt-get install lame

sudo apt-get install sox

sudo apt-get install ffmpeg

sudo apt-get install mjpegtools

sudo apt-get install vorbis-tools

sudo apt-get install w32codecs

sudo apt-get install gstreamer0.8-plugins

sudo apt-get install gstreamer0.8-lame

sudo apt-get install gstreamer0.8-ffmpeg

gst-register-0.8

sudo apt-get install amarok amarok-engines amarok-xine 

Some the apps couldn't be retrieved, (libdivx4linux as an example for me), but I'm listening to music with no problem so there shouldn't be anything wrong if you skip those. Maybe they will work and just not me.

DIdn't think I'd actually be able to help on this forum lol. There ya go chicken!

---

