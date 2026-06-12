---
title: "Playing Quicktime Online"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by tgdrums1990 on 2007-08-04
Last year i tried ubuntu and gave up because I couldnt figure it out, well im back giving it another go.  

I am having issues trying to stream quick time media online.  There are a few website I use that have quick time vid's I wanna watch but cant, because totem packages arnt installed, so I went and installed all the packages, but I still cant stream the quick time vids. So I tried installing Xine and there codecs and packages, but I cant figure out how to set it to be the default player for online material. 

I think the same goes for all my windows media, I cant stream that stuff either. 


Thanks in advance.

---

### Post by tprzepiorka on 2007-08-04
I suggest going to Add/Remove programs and search "Gstreamer" (make sure you change the drop-down box to "All Available Applications". Install all of the Gstreamer codecs. I can't say the videos work 100% of the time, but you should be able to stream most videos. 

Oh and I'm assuming your using 7.04(Fiesty Fawn), since if I can remember those codecs aren't available in Edgy Eft.

---

### Post by tgdrums1990 on 2007-08-04
> **tprzepiorka said:**
> I suggest going to Add/Remove programs and search "Gstreamer" (make sure you change the drop-down box to "All Available Applications". Install all of the Gstreamer codecs. I can't say the videos work 100% of the time, but you should be able to stream most videos. 

Oh and I'm assuming your using 7.04(Fiesty Fawn), since if I can remember those codecs aren't available in Edgy Eft.

No im using 6.1... 

And that still hasent fixed my issue. Thanks for the advice though.

---

### Post by Alexander2007 on 2007-08-04
> **tgdrums1990 said:**
> No im using 6.1... 

And that still hasent fixed my issue. Thanks for the advice though.

Open Synaptic and seach for "gstreamer0.10"

Install:
[B]gstreamer0.10-plugins-ffmpeg
gstreamer0.10-plugins-good
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
totem-gstreamer
totem-mozilla[/B]

If that doesn't work, use MPlayer. 
Open a terminal window and copy the following: 

```
echo "deb http://packages.medibuntu.org/ edgy free non-free" | sudo tee -a /etc/apt/sources.list
```
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Then type: ```
sudo apt-get install mozilla-mplayer w32codecs
```

---

### Post by Flashgordon20 on 2007-08-04
If you are using Firefox, this extension has worked well for me.

[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)   :)

---

