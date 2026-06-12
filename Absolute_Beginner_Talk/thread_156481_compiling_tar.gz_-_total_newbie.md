---
title: "compiling tar.gz - total newbie"
date: 2006-04-07
forum: Absolute Beginner Talk
---

### Post by Rubberhead on 2006-04-07
I am trying to get a driver to work, but I cannot find any .deb packages of the install. Only a tar.gz.

Whenever I try to find a howto, I get stuff with kernel upgrades, linux headers, makefile commands...  :confused:  too abstract for my brain atm.
I've had major networking problems for the last 4 months, and the tought of troubleshooting alone is really making me feel tired. I don't have much commandline experience either.

Would someone mind helping this noob out? I'dd really like to give Linux a go :mrgreen:
P4 PC btw...

---

### Post by meborc on 2006-04-07
there's a video of how to install stuff on ubuntu [http://video.google.com/videoplay?docid=5253052326994067125&q=ubuntu&pl=true](http://video.google.com/videoplay?docid=5253052326994067125&q=ubuntu&pl=true)
the first part is about synaptic, but most of the end of the video is about compiling from source..

what driver and what for is it btw?

---

### Post by Sef on 2006-04-07
Also to compile in Ubuntu, you need to download build-essential.

sudo apt-get update

sudo apt-get install build-essential

---

### Post by Rubberhead on 2006-04-07
[QUOTE=meborc]there's a video of how to install stuff on ubuntu [http://video.google.com/videoplay?docid=5253052326994067125&q=ubuntu&pl=true](http://video.google.com/videoplay?docid=5253052326994067125&q=ubuntu&pl=true)
the first part is about synaptic, but most of the end of the video is about compiling from source..

what driver and what for is it btw?[/QUOTE]

Serialmonkey r2500 driver... :-\" 
default setting won't work, ndiswrapper won't work, looks like my best bet...

I tried editing the interfaces manually, but a newbish as I am i'm probably doing something wrong.
It detects, it won't connect. WPA doesn't work, WEP is the devil... I see the drivers as the most logical way out.

PS: Video sound gets AWFULLY stuttery after a while, I can't even hear what they're saying :-|

---

