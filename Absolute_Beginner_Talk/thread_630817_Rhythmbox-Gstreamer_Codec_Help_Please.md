---
title: "Rhythmbox-Gstreamer Codec Help Please"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by jordank on 2007-12-03
When I try to import a song to my rhythm box, it gives me an import error saying 
The gstreamer plugins to decode mp3 files can not be found

where can i get these/what can i type in the terminal to get these?
Also, i have m4a files aswell.

thanks.

---

### Post by 449 on 2007-12-03
Applications > Add Remove > Search 'MP3' a codec should come up that covers a variety of sound files.

---

### Post by jordank on 2007-12-03
no codecs, just mp3 playing programs.

---

### Post by thelatinist on 2007-12-03
You need to enable the universe and multiverse repositories under System | Administration | Software Sources.  Then go to synaptic and search for mp3 codecs (gstreamer).

---

### Post by jordank on 2007-12-03
they're both enabled, but still not seeing anything that says mp3 codecs.

---

### Post by thelatinist on 2007-12-03
For mp3's you want gstreamer0.10-plugins-ugly.  For some other formats, like AAC, you will want gstreamer0.10-plugins-bad.  Search for 'gstreamer.'

---

### Post by jordank on 2007-12-03
does anyone know what to type in the terminal to get the correct mp3/m4a codecs

---

### Post by qamelian on 2007-12-03
Go to Applications > Add/Remove...
Under show select  All Available Applications.
In the left frame, select the Other category.
In the right frame, scroll down until you find the package labelled Ubuntu restricted extras. Install this package and that should fix your problem.

---

### Post by thelatinist on 2007-12-03
> **jordank said:**
> does anyone know what to type in the terminal to get the correct mp3/m4a codecs

```
sudo apt-get install gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse
```

---

### Post by jordank on 2007-12-03
Installed ubuntu restricted extras, still cant add mp3 files to rythym box.  What's the problem here?
I think i still need the Gstreamer codecs.

---

### Post by qamelian on 2007-12-03
> **jordank said:**
> Installed ubuntu restricted extras, still cant add mp3 files to rythym box.  What's the problem here?
I think i still need the Gstreamer codecs.
Ubuntu restricted extras installs the GStreamer codecs that allow MP3 playback. It says so right in the description. If for some reason the codec didn't install, open the mp3 file in Totem Movie Player. Totem will tell you if the codecis not installed and will offer to install it for you.

---

### Post by thelatinist on 2007-12-03
Did you try installing the gstreamer codecs using the commands I put in above?

---

### Post by xinix111 on 2007-12-03
hi, it&#347; already explaned earlier in this post, you should just go to synaptic package manager and search for gstreamer, mark all 4 of them (for files you probably get to deal with later) and apply.

system>>administration>>synaptic

it'srealy not that difficult

---

### Post by veconom2 on 2007-12-04
Hi, I had the exact same problem. What I did to fix it was open the synaptic package manager and I clicked refresh. That allowed me to get all the gstreamer packages. I then went to the terminal and typed this:

sudo apt-get install gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse

which was posted here earlier. 

After doing all of this, I was able to play music. However, I've only played mp3's so far, I haven't tried other file types.

I hope this helps.

---

### Post by blinedale on 2007-12-08
Nevermind, though I had a similar problem but it turned out the files themselves were bad. Go figure.

---

### Post by Findeton on 2007-12-14
> **veconom2 said:**
> Hi, I had the exact same problem. What I did to fix it was open the synaptic package manager and I clicked refresh. That allowed me to get all the gstreamer packages. I then went to the terminal and typed this:

sudo apt-get install gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse

which was posted here earlier. 

After doing all of this, I was able to play music. However, I've only played mp3's so far, I haven't tried other file types.

I hope this helps.

I've got a problem: I've got already installed all those packets and rythmbox was working yesterday but now it doesn't play mp3 files: it says, for each mp3 file of my collection, that it was impossible to find the plugins for gstreamer for decoding MP3 files. I've got everything installed, and yesterday it was working but now... Now amarok freezes when i start it and rhythmbox is unable to play mp3 files, although i'm able to play mp3 files through vlc and xmms for example. But i want Amarok and Rhythmbox! :(

---

### Post by jordank on 2007-12-15
have you tried reinstalling the two?  What errors is it giving?

---

### Post by mackeno73 on 2007-12-15
> **veconom2 said:**
> Hi, I had the exact same problem. What I did to fix it was open the synaptic package manager and I clicked refresh. That allowed me to get all the gstreamer packages. I then went to the terminal and typed this:

sudo apt-get install gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse

which was posted here earlier. 

After doing all of this, I was able to play music. However, I've only played mp3's so far, I haven't tried other file types.

I hope this helps.

Hello,

Thanks all, I got same problem and do following instruction here then enjoy mp3

---

### Post by Findeton on 2007-12-19
> **Findeton said:**
> I've got a problem: I've got already installed all those packets and rythmbox was working yesterday but now it doesn't play mp3 files: it says, for each mp3 file of my collection, that it was impossible to find the plugins for gstreamer for decoding MP3 files. I've got everything installed, and yesterday it was working but now... Now amarok freezes when i start it and rhythmbox is unable to play mp3 files, although i'm able to play mp3 files through vlc and xmms for example. But i want Amarok and Rhythmbox! :(

Anyone got any idea?:confused:

---

### Post by jordank on 2007-12-20
did you try reinstalling?

---

