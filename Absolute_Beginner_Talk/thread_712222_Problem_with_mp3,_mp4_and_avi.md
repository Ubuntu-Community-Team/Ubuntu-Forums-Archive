---
title: "Problem with mp3, mp4 and avi"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by poscomp on 2008-03-01
No matter what I do I can't load codec or codecs drivers to run these file extensions. The avi file from my digital camera does run but I can't play an mp3 audio or mpg video or mp4 video or avi video. I really love ubuntu but for these few problems. Can someone please help me?
Lew Blackman

---

### Post by Tom--d on 2008-03-01
Use VLC player to play videos. It has all the codec's built in!

---

### Post by w0ng on 2008-03-01
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Add the repo, then install w32codecs

---

### Post by LuisGMarine on 2008-03-01
This might help you for mp3's I know it did for me.  

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by songstruck on 2008-03-04
I could not play avi's with VLC (Ubuntu 7.1). On opening the file, I would see a brief green screen, then VLC would shut down. 

I fixed the problem by changing the VLC video output module preferences to X11. Other options may work as well, don't know. 

Here's how:
1) Open VLC
2) Choose "Preferences" from the "Settings" menu
3) Make sure the "Advanced options" box is checked at the lower right.
4) Expand the "Video" option in the list on the left
5) Click on "Output modules"
6) Change the Video output module to "X11 video output"

This fixed problems with some other file types as well.

songstruck

---

### Post by stchman on 2008-03-04
> **poscomp said:**
> No matter what I do I can't load codec or codecs drivers to run these file extensions. The avi file from my digital camera does run but I can't play an mp3 audio or mpg video or mp4 video or avi video. I really love ubuntu but for these few problems. Can someone please help me?
Lew Blackman

To install proprietary codecs do the following in a terminal:

```

sudo apt-get -y install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
```

You should be able to play those files after that.

---

### Post by slughappy1 on 2008-03-04
You could try and install ```
sudo apt-get install ubuntu-restricted-extras  
```
This allowed me to play every format that I have or have dealt with.

It could also be a Compiz problem if you are running it. My video card is black listed by Compiz. What type of video card do you have?

---

### Post by Tom--d on 2008-03-04
> **songstruck said:**
> I could not play avi's with VLC (Ubuntu 7.1). On opening the file, I would see a brief green screen, then VLC would shut down. 

I fixed the problem by changing the VLC video output module preferences to X11. Other options may work as well, don't know. 

Here's how:
1) Open VLC
2) Choose "Preferences" from the "Settings" menu
3) Make sure the "Advanced options" box is checked at the lower right.
4) Expand the "Video" option in the list on the left
5) Click on "Output modules"
6) Change the Video output module to "X11 video output"

This fixed problems with some other file types as well.

songstruck


YAY!!!
Thanks!! 
Why? 

I have the Intel 965 chip set. I taken it off the blacklist and vlc player never works while having effects on. 
VLC player (while playing videos)now works with my graphics card unblocked! 

Thank you, thank you!

:KS

---

