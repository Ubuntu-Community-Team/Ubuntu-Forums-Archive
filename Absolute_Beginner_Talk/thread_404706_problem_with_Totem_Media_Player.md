---
title: "problem with Totem Media Player"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by cele on 2007-04-08
I'm getting error:
"A subtitle stream was detected, but no video stream."

I have installed:
gstreamer0.10-plugins-bad & gstreamer0.10-plugins-ugly
and still getting the same error!
It is a .avi file with XVID MPEG-4 video codec.

What to do?

---

### Post by Najand on 2007-04-08
probably you don't have the codecs installed on your computer. Try to install "w32codecs":
```

$ sudo apt-get install w32codecs

```

---

### Post by cele on 2007-04-08
And what are this 2 for:
gstreamer0.10-plugins-bad & gstreamer0.10-plugins-ugly ???

Should I install some other program for watching DVX? Something like "mplayer"?

---

### Post by Najand on 2007-04-08
"gstreamer0.10-plugins-bad/ugly" are for some codecs and realtime/quality image and audio plugins.
I think totem is enough. What sucks is the gstreamer, I recommend you to use totem-xine instead.

---

### Post by cele on 2007-04-08
have a  problem with that w32codecs installation

cele@cele-laptop:~$ sudo apt-get install w32codecs
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

what to do?

---

### Post by Najand on 2007-04-08
What architecture are you using?

---

### Post by cele on 2007-04-08
Ubuntu 6.10

---

### Post by Maestro23 on 2007-04-08
> **cele said:**
> have a  problem with that w32codecs installation

cele@cele-laptop:~$ sudo apt-get install w32codecs
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

what to do?

Try enabling all your resources: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Run your search again.

---

### Post by Najand on 2007-04-08
Let us do it the fast way:
    * Ensure the relevant repositories are enabled. Click System &#8594; Administration &#8594; Synaptic Package Manager &#8594; Settings &#8594; Repositories and then click Add. Check the Community maintained (Universe) and Non-free (Multiverse) boxes. When you close the window, click Reload.
    * Install the packages. While you could install packages individually using Synaptic, here is one case where any Ubuntu user can save a lot of time by using the command line. Quit out of Synaptic, then click Application &#8594; Accessories &#8594; Terminal and paste the following command:

```
sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui

```

---

### Post by cele on 2007-04-08
Great! Works just fine now.
In the mean time I tried to install mplayer. He works also but the sound with that player is distortide (like a low quality mp3)!? Any gues why?

One more thing, Should I do somethink with this...
...
The following packages were automatically installed and are no longer required:
  libgpgme11
Use 'apt-get autoremove' to remove them.
...
or not?

---

### Post by Najand on 2007-04-08
Sure... If apt says so, go ahead and remove it.

---

### Post by cele on 2007-04-08
Tnx a lot 1ce again!

---

### Post by Najand on 2007-04-08
No problemo...

---

### Post by Michaelt74 on 2007-04-08
From my experience with mplayer, it may be a solution if you're an advanced Linux user, but for beginners it's very difficult to compile; I spent hours with it and couldn't get it to work. Try vlc, it works great.

---

### Post by strabes on 2007-04-08
I recommend vlc or mplayer instead of totem, especially for the firefox plugin.

---

