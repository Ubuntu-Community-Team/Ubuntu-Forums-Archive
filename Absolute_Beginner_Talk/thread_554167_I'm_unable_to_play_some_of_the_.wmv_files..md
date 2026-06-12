---
title: "I'm unable to play some of the .wmv files."
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by sasikirandadi on 2007-09-18
The following error is being displayed when i'm playing some of the .wmv files.
This error is displayed only for some of the .wmv files. Many are being played as well.
Please help me i'm very new to unbuntu and linux.

**An error occured**

The playback of this movie requires the following decoders which are not installed:

video/x-asf-unknown decoder
audio/x-asf-unknown decoder

---

### Post by WebSiteGuru on 2007-09-18
Try these instruction, see if it's works for ya! And welcome to Ubuntu.

[http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)

[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

---

### Post by RomeReactor on 2007-09-18
Hi. You need the w32codecs to play those files. If you don't have the Medibuntu repositories, [look here]("http://ohioloco.ubuntuforums.org/showpost.php?p=3203196&postcount=11") for how to add them and get the codecs.

---

### Post by Gremlinzzz on 2007-09-18
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29)

---

### Post by angryfirelord on 2007-09-18
Here, I'll make it easy for you. :) Copy-Paste these commands into a terminal:

```
echo "deb http://packages.medibuntu.org/ feisty free non-free" | sudo tee -a /etc/apt/sources.list
```
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
```
sudo apt-get install w32codecs
```

If you still get an error, tell us what media player you're using.

---

### Post by kshane on 2007-09-18
> **sasikirandadi said:**
> The following error is being displayed when i'm playing some of the .wmv files.
This error is displayed only for some of the .wmv files. Many are being played as well.
Please help me i'm very new to unbuntu and linux.


WMV9 is a proprietary codec of Microshaft's.  plain WMVs should play with no problem, but newer WMVs (like what you might download off Amazon Unbox) are the newer proprieary form.

Unless someone has found a version that will work for Linux?  I understand that there is no codec for WMV9 for Linux/Ubuntu...

Kevin

---

### Post by kshane on 2007-09-18
> **angryfirelord said:**
> Here, I'll make it easy for you. :) Copy-Paste these commands into a terminal:

```
echo "deb http://packages.medibuntu.org/ feisty free non-free" | sudo tee -a /etc/apt/sources.list
```
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
```
sudo apt-get install w32codecs
```

If you still get an error, tell us what media player you're using.

As he said, some work, some don't...  WMV9 is most likely the culprit...  Therefore, installing or reinstalling w32codecs will not help.

Kevin

---

### Post by sasikirandadi on 2007-09-19
thanks a lot!
I think what kshane said is true its mostly the problem due to wmv9 files.
I think there is no other alternative for this other than just ignoring it.
Anyways Thanks a lot!

---

### Post by angryfirelord on 2007-09-19
Aww, you people give up too easily. Did you try playing your WMV files through mplayer or VLC with the w32codecs installed? Also, if you use Totem, you may want to change it to use the xine engine:
```
sudo apt-get install totem-xine libxine1-plugins
```

---

### Post by eidam655 on 2007-10-30
hi people :)

i just installed ubuntu 3 weeks ago and i like it :D

but that's not what i wanted to talk about.

i have been getting similar error message as sasiri...whatever. i used the copy-and-paste-commands posted above :) and they worked; however only with mplayer.

how can i play .wma files in audacious? in preferences->plugins the WMA 1.3.5 plugin is checked. however, when trying to play the file, audacious wants me to 1. check whether the file is accesible, 2. ensure that the plugin is installed.

what should i do? :( thank you for replies.

PS: how can i set audacious my default music player? thx.

---

### Post by homerj742 on 2007-11-20
I WAS able to play WMV's, but now I'm not able to. What's up with that? Just today, I did an update, but I can't imagine how that would affect MPlayer which was working fine before to stop working on WMV files (the same WMV files were playing fine a few days ago!)

---

