---
title: "Blue movies"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by auldcat on 2007-11-16
:popcorn: Hello everyone,
I am new to linux and ubutu, and this is my first post in the forum.
Perhaps someone has encountered this problem before. 
Video played with movie player are blue. I have installed all the available codecs, but they remain blue.
VLC, however displays the color correctly; but VLC jumps back and forth erratically.
Win xp plays them properly, so it is not the videos themselves.
Interestingly, thumbnails are displayed with proper color. 
Video driver perhaps? The card is a radeon x1950pro. Searching has not turned up anything similar with this card though.
Any suggestions will be appreciated.
TIA,
Auldcat

---

### Post by derby007 on 2007-11-17
Nice Title, sounds interesting :) :)
[COLOR="Blue"](PS> Sorry I can't help).[/COLOR]

---

### Post by KIAaze on 2007-11-17
What video format are they in?
You can use G-spot in windows to find out. Under GNU/Linux I don't know what equivalent there is.

Also, have you tried other players like Kaffeine and mplayer?

---

### Post by genbuntu on 2007-11-17
lol :D
the title caught my attention .  First, 'blue movies' and then 'g-spot'. lol, ( wicked mind :evil:) . 
:biggrin:

As already suggested, you may try a couple of other video players to rule out problem with VLC alone.

---

### Post by auldcat on 2007-11-17
Hello everyone,
A little more information.
The movie format is xvid or divx. I haven't tried any of the mpeg flavors or windows media. If ubuntu can't  handle these avi formats with my install hardware..., well it's a deal buster. 
Interestingly, searching blue movies results in similar questions but no solutions as of last night.
I believe mplayer and movie player are the same front end.
Thanks for looking,
Auldcat

---

### Post by daimaru on 2007-11-17
did you install the w32codecs from medibuntu.org? if not just follow the steps there. and it should work

---

### Post by auldcat on 2007-11-17
Hello everyone,
Thanks for your reply daimaru.
Yes I installed the w32codecs.
Here is where I am at the moment:
Totem persist in playing movies blue.
Mplayer after additional downloads using synaptic of anything that looked useful, works!
VLC plays in the same herky-jerky fashion.
Kaffeine does not read NTFS partitions apparently and is of no use to me.
One out of four is better than nothing.
Auldcat

---

### Post by KIAaze on 2007-11-17
Strange that it's because it's on the NTFS partition.
Have you tried copying it to your Ubuntu partition and reading it with Kaffeine there?

---

### Post by auldcat on 2007-11-20
Hello everyone,
I took the time to survey the functions and performance of the four video clients I have installed with hope that someone will be able to help me resove this mess. I know from looking around these forums that these issues are not unique to me.
Let me begin with the frequently recommended VLC. VLC will browse to an NTFS partition, imparative for dual windows/linux box; but video playback is jerky and unwatchable, however audio is uneffected. This true for both avi and dvd sources. Color rendition is good, not blue.
Totem will browse to an NTFS partition, but the color rendition is blueish. Totem will not play dvds without jerking.
Mplayer will not browse to NTFS, does not play dvds, but will play avi media just fine if I find it through file browser on my NTFS.
Kaffeine does not browse to NTFS and does not open dvds.
All of this media works fine under windows, so I can only conclude that fault lies with ubuntu and/or the various video clients.
I have as I have mentioned earlier installed all the requisit codecs, as the survey would seem to demonstrate.
Frankly, I'm disappointed. Where is the killer video playback ap? There is some very good freeware available under windows. It seems to me that video  is something that needs to work well right out of the box if linux is going to challenge windows on the desktop, as I sincerely hope it will. I know windows can't claim as much but I was hoping for a higher standard from ubuntu.
Thanks for looking,
Auldcat

---

### Post by MegaJim on 2007-11-20
To answer the op: yes you can watch blue movies on ubuntu!

---

### Post by NIT006.5 on 2007-11-20
I have experienced this before on Feisty, and in my case the problem was being caused by desktop effects (specifically beryl). Are you running any effects? I no longer have this problem since I upgraded to gutsy and compiz-fusion, but it's possible it could be a similar issue?

Maybe try changing the window manager temporarily and testing, just in case that's causing a problem.

At terminal: 
metacity --replace

Then try playing vids again.

---

### Post by Firlian on 2007-11-20
I've got the exact same issue.
I remember having had this issue before and fixing it, think it had something to do with gstreamer.

---

### Post by por100pre1 on 2007-11-20
Are you using Desktop Effects? If so disable them, that should work. :-k

---

### Post by Firlian on 2007-11-20
I'm not using any desktop effects atm...
I'm pretty confident its a gstreamer setting- still googling for the answer... I know the truth is out there :)

---

### Post by Firlian on 2007-11-20
Solution here! :popcorn:

> launch gstreamer-properties from terminal
change the video output plugin to custom
change the video output pipeline to:

ffmpegcolorspace ! video/x-raw-yuv,format=(fourcc)YV12 ! xvimagesink

source: [https://answers.launchpad.net/ubuntu/+source/totem/+question/7373](https://answers.launchpad.net/ubuntu/+source/totem/+question/7373)

---

### Post by genbuntu on 2007-11-20
You may also try real-player for linux (though I think it is not as powerful as its windows version, but it may work for you ).
Try searching in synaptic or forums for installation help; for e.g. [http://ubuntuforums.org/showthread.php?t=550028&highlight=install+realplayer](http://ubuntuforums.org/showthread.php?t=550028&highlight=install+realplayer)

Of course the best would be if you can get totem to work. Its a neat and light player :)

---

### Post by Angus77 on 2008-02-09
What Firlian posted above works for me!

---

