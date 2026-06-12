---
title: "Need help installing nVIDIA card"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by ricardisimo on 2006-10-10
I just purchased an nVIDIA 64M GeForce MX4000 T64/T32 AGP VGA card, and I was hoping against hope that i would be able to simply pop it in and watch the magic happen. 'Twas not to be. Instead I get a failure to start the X Server. I have no idea where to begin with this, and any help or pity would be appreciated. TIA.

---

### Post by blendmaster on 2006-10-10
Well, though this isn't the "real" way of doing it, you can install automatix, and it will probably give you the drivers you need without having to do anything. 

Go here: [http://getautomatix.com/wiki/index.php?title=Installation](http://getautomatix.com/wiki/index.php?title=Installation) , 

and it will give you the instructions needed to get automatix.

Hope that helped!

---

### Post by halfvolle melk on 2006-10-10
Or run this:
```
sudo dpkg-reconfigure xserver-xorg
```
to fix the X server, and
```
sudo apt-get install nvidia-glx nvidia-kernel-common
```
to install the 3D driver.

---

### Post by Medieval_Creations on 2006-10-10
I would use automatix2... I had all kinds of problems with getting the nvidia driver to work, I was eventually able to do it, but on my last load I broke down and tried automatix2 & it saved me a ton of time... The only config change I had to make was edit my resolution into the xorg.conf.  Other than that it worked perfect.

Link to Automatix site - [http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38)

---

### Post by bodhi.zazen on 2006-10-10
[How to install the Nvidia driver](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

I prefer method 2.

---

### Post by halfvolle melk on 2006-10-10
1) I don't think Ricardisimo has X running. "I get a failure to start the X Server". Does Automatix2 run without X? (I don't know, but I don't think so).
2) Installing the latest driver is pointless for such an old card and will break at the next kernel update.

---

### Post by blendmaster on 2006-10-10
Yeah, I meant automatix2.

Sorry about that!

(Just look for the section saying how to install automatix2 for (X/K)Ubuntu).

---

### Post by RanDinCarolina on 2006-10-10
Dude doesn't have "X". He'll have to use the terminal to get started, i.e; log into a terminal, reconfig X to use the "nv" driver, start X, and go from there. 

See the nVidia threads in here. I've used those more time than I will admit to anyone unless it's Halle Berry......:D

---

### Post by bodhi.zazen on 2006-10-10
> **halfvolle melk said:**
> 1) I don't think Ricardisimo has X running. "I get a failure to start the X Server". Does Automatix2 run without X? (I don't know, but I don't think so).
2) Installing the latest driver is pointless for such an old card and will break at the next kernel update.

Why so hostile?

The link I posted covers the newest nvidia driver as well as legacy cards. I am not familiar with her card but I did not see it listed as a legacy card.

What makes you think > Installing the latest driver is pointless for such an old card and will break at the next kernel update.
The nvidia drivers, in my experience, do not break with kernel upgrades. Lord knows I've done my share of kernel upgrades and have never had a problem with the nvidia drivers.

---

### Post by halfvolle melk on 2006-10-10
I'm sorry bodhi.zazen, I didn't mean to sound hostile at all! Just wanted to point some technical info. No offence intended! AFAIK using nvidia-bla.run will need to be redone after a kernel update.

---

### Post by bodhi.zazen on 2006-10-10
> **halfvolle melk said:**
> I'm sorry bodhi.zazen, I didn't mean to sound hostile at all! Just wanted to point some technical info. No offence intended! AFAIK using nvidia-bla.run will need to be redone after a kernel update.

LOL :lol:

No worries then, perhaps I'm oversensitive today. :(

I installed the nvidia drivers because the open source drives did not work for me. I have not had a problem with kernel updates.

---

### Post by bobpur on 2006-10-10
Let's not be knocking stuff just because it's got some age on it:) I have a 6 or 7 year old Compaq with a PNY Verto MX2 / MX 400 videocard that still turns out a respectable picture or video. Along with a Soundblaster 5.1 X-gamer sound card for music and games. Dual booting Ubuntu and whatever.

---

### Post by Nunana on 2006-10-11
Dear People,

The first solutions Halfvolle melk gave me solved my NVidia problem (I only had 640x480 60Hz while my xorg.conf had a lot different tastes) on a Compaq Presario6000 with Compaq TFT5015M. Thank you very much!
Now I have 1280x960 60Hz

---

### Post by ricardisimo on 2006-10-11
> **halfvolle melk said:**
> Or run this:
```
sudo dpkg-reconfigure xserver-xorg
```
to fix the X server, and
```
sudo apt-get install nvidia-glx nvidia-kernel-common
```
to install the 3D driver.

More problems. I get as far as "Video Card's BUS Identifier" which it has as ```
PCI:1:0:0
``` which I suspect is wrong, especially if "PCI" refers to a slot... the card I'm putting in is AGP. If this is the problem, how do I find out which slot the card is in?

Immediately after this, I get "xserver is now disabled. Restart GDM when it is configured properly." Then I get my regular prompt. Obviously, I'm not getting any graphics.

I'm checking out some of the nVIDIA threads right now, but if anyone knows what's up, I'd greatly appreciate it. Thanks.

---

### Post by bodhi.zazen on 2006-10-11
To identify your PCI try this:```
lspci -X | grep VGA
```

and this:```
sudo dpkg -reconfigure -phigh xserver-xorg
```

The second command is simpler in that it chooses the defaults for everything but resolution.

---

### Post by ricardisimo on 2006-10-12
> **bodhi.zazen said:**
> To identify your PCI try this:```
lspci -X | grep VGA
```

and this:```
sudo dpkg -reconfigure -phigh xserver-xorg
```

The second command is simpler in that it chooses the defaults for everything but resolution.

Correct me if I'm wrong, but you're giving me two separate pieces of info: the first is how to ID my card's AGP slot, and the second is an alternative reconfig to the one's which I've been given up to this point. Is this correct? Thanks.

---

### Post by ricardisimo on 2006-10-12
```
lspci -X | grep VGA
```

One more thing: What's the vertical line in this first command? Is that a line break, or is this part of one single line of code? If it's part of a single command, is this the character that shares the \ (backslash) key? Thanks.

---

### Post by bodhi.zazen on 2006-10-12
LOL :lol: Sorry 'bout that.

Yes to your first two questions.

sudo dpkg -reconfigure -phigh xserver-xorg

Selects the default setting for everything but screen resolution.

sudo dpkg -reconfigure xserver-xorg

is the full tamale.

The | is the very same as on the \ key, on the Right just above <Shift>.

This is a "pipe". It directs the output from the first command (ls) to the second (grep).

Grep is a filter for the output.

Try it:```
cd
ls
ls | grep Desk
```
Difference ?

Do you know how to "man".

In a terminal type```
man grep
```
To exit just type q.

:lol: No, do not worry if you do not understand the man pages on day 1, but they will become a valuable source of information.

At any rate, how's you monitor?

---

### Post by ricardisimo on 2006-10-13
> **bodhi.zazen said:**
> At any rate, how's you monitor?

The good news is that I have the new card installed and running. The bad news is that it seems to be behaving itself very modestly better than the SiS that was already here. I wanted to test the frames per second, so: ```
glxgears printfps
```
But the response I get is this:
```
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual
```
Evidently nVIDIA doesn't work with all of the same commands, or is there something else?
How do I fine-tune the card, now that it's running? Thanks.

---

### Post by bodhi.zazen on 2006-10-15
sorry, I do not know the answer to this one. Start a new thread, this is too far off the original question to be drawing a response.

---

