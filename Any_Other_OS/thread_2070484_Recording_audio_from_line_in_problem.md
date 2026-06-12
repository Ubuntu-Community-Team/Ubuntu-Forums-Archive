---
title: "Recording audio from line in problem"
date: 2012-10-12
forum: Any Other OS
---

### Post by rmcellig on 2012-10-12
I'm not sure if this post is in the right forum but here goes.

I have Linux Mint 13 XFCE installed on my Dell 3000 Desktop. Works fine except that I am having problem recording my radio shows from a radio that is hooked up to my machine. I can hear the radio coming through my external speakers but am unable to record audio from the radio.

This is the code I am using and I know it works because I use it when I boot into Puppy Linux. No problems at all.

arecord -t wav -f cd -d 40 /home/randy/Desktop/Test.wav

The Test.wav file appears on my desktop and when I hover over it I can see that it is recording based on the Last Modified time. So that part is working. When I open the file in Audacity and normalize it, there is no sound.

All I have hooked into this computer is a pair of standard computer speakers so how should Im set up my Alsamixer as well as the sound settings when I click on the Sound Settings icon in the lower panel.

---

### Post by Habitual on 2012-10-13
This may help:

[Record what comes out of your speakers]("http://www.bournetoraiseshell.com/article.php/20101116231547304?query=sox")

---

### Post by rmcellig on 2012-10-13
I just solved my problem. I had to go to the Pulse Volume Control and make sure the Line settings were correct.

---

