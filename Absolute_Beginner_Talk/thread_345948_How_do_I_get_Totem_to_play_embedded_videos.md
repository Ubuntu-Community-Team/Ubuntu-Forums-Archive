---
title: "How do I get Totem to play embedded videos?"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by TheAlmightyNilz on 2007-01-25
Hey guys, I have an issue with Totem.
I don't really like it as a media player, but it's set as the default program to access if I click on a video on a website to watch. My first solution was to just get rid of it to have another media player be used for this purpose, but if I removed it, it was going to remove some important system files (this is what my brother told me). :confused: 

So, I just want to know how to get it to work.
Right now, when I click on an embedded video I get this message:

Totem could not play 'fd://0'.
You do not have a decoder installed to handle this file. You might need to install the necessary plugins.

So, being a total newb to Linux, I wanted to know what the steps I need to take are in order to install these "necessary plugins" and get it working. The answer might be incredibly simple, and if it is, I apologize for wasting your time. :( 

OR, can someone explain to me how to set another media player as the default player, and I won't have to worry about it. I'd rather actually do both, but either is fine. :)

-Nilz

---

### Post by ashmew2 on 2007-01-25
Hi , have u installed all of the ugly/bad/good plugins ? 
Although im not pretty sure that it has sumtin to do with embedded videos in the browser , i think u shud take a look here : [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)
Then make sure you have enabled all the repositories , if u dunno how take a look at :
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

And in the terminal (Applications>Accessories>Terminal if you are using Ubuntu with Gnome Desktop) type : 
```
sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui
```

It shud install all the plugins u need to play almost any of the file types of videos and audio.
And as far as changing video players is concerned , Ubuntu can run a variety of Video Players including Kaffeine. TO install it you need to type in terminal :
```
sudo aptitude install kaffeine kaffeine-mozilla
``` 
After Kaffeine is installed , right click the type of files u want Kaffeine to play(For example .mp3) , and click Open With and select Kaffeine instead of Movie player.I think it is a pretty good player.Please let me know if this fixed your problem.

---

### Post by TheAlmightyNilz on 2007-01-25
Thanks man, that first line you provided is what got it working. Thanks a bunch! :D

---

### Post by ashmew2 on 2007-01-26
Welcome to the Ubuntu Forums :D

---

