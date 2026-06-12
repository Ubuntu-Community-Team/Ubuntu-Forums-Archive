---
title: "Newbury needs instructions for MP3 playing"
date: 2005-11-29
forum: Absolute Beginner Talk
---

### Post by leorob on 2005-11-29
I am totally new to Linux.
My system is up and running but mp3s won't play due to a missing codec.
I have downloaded all updates and tried to fix things in "repositories" to no avail.
Please give me STEP by STEP instructions on how to fix this. Please assume I know nothing so keep it simple.
I am close to expert in Windows if that means anything.
Thanks
Sorry that my spelling program corrected "Newbie" to Newbury.

---

### Post by aysiu on 2005-11-29
To get the right repositories, look at my sig.

Then, open up a terminal and copy and paste these commands in ```
sudo apt-get update
sudo apt-get install gstreamer0.8-mad libmad0 gstreamer0.8-lame lame liblame0
gst-register-0.8
``` P.S. Terminal is in Applications > Accessories > Terminal

---

### Post by leorob on 2005-11-29
I opened terminal, copied and pasted your text.
Text scrolled as things were happening.
When done I clicked on an mp3 and got the same eror message.
Still need help.
thanks

---

### Post by akiro.yamamoto on 2005-11-29
if you want mp3 right now, use Synaptic and install xmms (mp3 playback built in) until I can track down the required files for mp3 playback with gstreamer.

Regards

---

### Post by aysiu on 2005-11-29
[QUOTE=leorob]
When done I clicked on an mp3 and got the same eror message.[/QUOTE] What's the error message?

---

### Post by akiro.yamamoto on 2005-11-29
I think this will do the job:
CODE:
sudo apt-get install gstreamer0.8-plugins gstreamer0.8-plugins-multiverse gstreamer0.8-ffmpeg 

That should get the plugins that you need, not only for mp3 but for others
as well.

Hope this helps
Regards.

---

### Post by leorob on 2005-11-29
OK, I'll try to answer all of you. (Nothing worked).

the error message from Totem is: Totem could not play "the file"
There wer no decoders found to handle the stream. you might need to install the corresponding plugin

When trying the other command suggested i get this message:
ldn't find package gstreamer0.8-plugins-multiverse
use Synaptic and install xmms (mp3 playback built in) until I can track down the required files for mp3 playback with gstreamer.
and my third answer: When you tell me to "use Synaptic and install xmms" That means nothing to me as a newcomer. What is synapic? how do I install xmms and what is it. i'm sorry but you have forgotten what it is to really be a beginner.

---

### Post by aysiu on 2005-11-29
Did you enable extra repositories as per the instructions in my signature?
If so, you should have the gstreamer multiverse plugins.
Instructions on Synaptic are in the second link in my sig.

By the way, if you're typing stuff into a terminal, copy and paste everything (input, output) so we can see what's going on. There may be errors you're not seeing as errors. And if there are errors, we need ton know what they are; otherwise, we can't help you fix them.

For example ```
sudo apt-get install gstreamer0.8-lame
Reading package lists... Done
Building dependency tree... Done
gstreamer0.8-lame is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by akiro.yamamoto on 2005-11-29
Click:
System >> Administration >> Synaptic Package Manager.
This will bring up Synaptic....
You should ensure that you have the repositories enabled...
Click:
Settings >> Repositories 
Then:
Add Official, Restricted, Community, Multiverse for binary..
It will then ask if you want to update 
Say YES....
When it's done do a search for xmms and the files listed earlier in this post.
Mark then for installation.
Then Click apply when done...
It should then install the packages you requested.....
Now when it's finished applying the changes.. check for mp3 playback ...
BTW xmms should be now in 
Applications >> Sound and Video 

I found this guide to be of great assistance when I firsty started out 5 days ago...[http://ubuntuguide.org/](http://ubuntuguide.org/)
:smile:
Post back any and all errors reported....
Or let us know if the problem was solved.

---

### Post by akiro.yamamoto on 2005-11-29
The Ubuntu wiki also has some invaluable info for getting up to speed....
[https://wiki.ubuntu.com/UserDocumentation](https://wiki.ubuntu.com/UserDocumentation)
:smile:
Hope this helps.
Regards

---

### Post by aysiu on 2005-11-29
[QUOTE=akiro.yamamoto]
I found this guide to be of great assistance when I firsty started out 5 days ago...[http://ubuntuguide.org/](http://ubuntuguide.org/)[/QUOTE] I did, too, but it's a bit outdated now. I would follow the instructions in the first link in my sig, which enables the universe repositories, and then follow the instructions in [http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs)

A few codecs will not be available (w32codecs, divx4linux, and maybe one or two others), but after you do that, you should be good. It may not hurt to install totem-xine, if you're insistent on playing MP3s with Totem.

If you're unsure about this whole installing software stuff, please read this:
[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

It explains all the different ways to install software in Ubuntu.

Once you're sure you have the correct repositories (please, please, please--just follow the instructions in the first link in my sig--that's what the link is there for), copy and paste this into a terminal: ```
sudo apt-get install gstreamer0.8-plugins gstreamer0.8-plugins-multiverse gstreamer0.8-ffmpeg
``` and post the exact output of that command.

For example, when I copied and pasted it into my terminal, this is what happened: ```
sudo apt-get install gstreamer0.8-plugins gstreamer0.8-plugins-multiverse gstreamer0.8-ffmpeg
Reading package lists... Done
Building dependency tree... Done
gstreamer0.8-plugins is already the newest version.
gstreamer0.8-ffmpeg is already the newest version.
The following extra packages will be installed:
  gstreamer0.8-dirac gstreamer0.8-faac gstreamer0.8-faad gstreamer0.8-wavpack
  gstreamer0.8-xvid libdirac0 libfaac0 libmp4v2-0 libwavpack0
The following NEW packages will be installed:
  gstreamer0.8-dirac gstreamer0.8-faac gstreamer0.8-faad
  gstreamer0.8-plugins-multiverse gstreamer0.8-wavpack gstreamer0.8-xvid
  libdirac0 libfaac0 libmp4v2-0 libwavpack0
0 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 812kB of archives.
After unpacking 2507kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com breezy/universe libdirac0 0.5.2-0ubuntu1 [318kB]Get:2 http://archive.ubuntu.com breezy/multiverse gstreamer0.8-dirac 0.8.11-0ubuntu1 [24.7kB]
Get:3 http://archive.ubuntu.com breezy/multiverse libmp4v2-0 2.0.0+cvs20040908+mp4v2+bmp-0ubuntu2 [214kB]
Get:4 http://archive.ubuntu.com breezy/multiverse libfaac0 1.24clean-0ubuntu3 [55.1kB]
Get:5 http://archive.ubuntu.com breezy/multiverse gstreamer0.8-faac 0.8.11-0ubuntu1 [27.4kB]
Get:6 http://archive.ubuntu.com breezy/multiverse gstreamer0.8-faad 0.8.11-0ubuntu1 [27.2kB]
Get:7 http://archive.ubuntu.com breezy/universe libwavpack0 4.2-0ubuntu1 [69.0kB]
Get:8 http://archive.ubuntu.com breezy/multiverse gstreamer0.8-wavpack 0.8.11-0ubuntu1 [28.3kB]
Get:9 http://archive.ubuntu.com breezy/multiverse gstreamer0.8-xvid 0.8.11-0ubuntu1 [29.3kB]
Get:10 http://archive.ubuntu.com breezy/multiverse gstreamer0.8-plugins-multiverse 0.8.11-0ubuntu1 [19.2kB]
Fetched 812kB in 6s (131kB/s)

Preconfiguring packages ...
Selecting previously deselected package libdirac0.
(Reading database ... 114370 files and directories currently installed.)
Unpacking libdirac0 (from .../libdirac0_0.5.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package gstreamer0.8-dirac.
Unpacking gstreamer0.8-dirac (from .../gstreamer0.8-dirac_0.8.11-0ubuntu1_i386.deb) ...
Selecting previously deselected package libmp4v2-0.
Unpacking libmp4v2-0 (from .../libmp4v2-0_2.0.0+cvs20040908+mp4v2+bmp-0ubuntu2_i386.deb) ...
Selecting previously deselected package libfaac0.
Unpacking libfaac0 (from .../libfaac0_1.24clean-0ubuntu3_i386.deb) ...
Selecting previously deselected package gstreamer0.8-faac.
Unpacking gstreamer0.8-faac (from .../gstreamer0.8-faac_0.8.11-0ubuntu1_i386.deb) ...
Selecting previously deselected package gstreamer0.8-faad.
Unpacking gstreamer0.8-faad (from .../gstreamer0.8-faad_0.8.11-0ubuntu1_i386.deb) ...
Selecting previously deselected package libwavpack0.
Unpacking libwavpack0 (from .../libwavpack0_4.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package gstreamer0.8-wavpack.
Unpacking gstreamer0.8-wavpack (from .../gstreamer0.8-wavpack_0.8.11-0ubuntu1_i386.deb) ...
Selecting previously deselected package gstreamer0.8-xvid.
Unpacking gstreamer0.8-xvid (from .../gstreamer0.8-xvid_0.8.11-0ubuntu1_i386.deb) ...
Selecting previously deselected package gstreamer0.8-plugins-multiverse.
Unpacking gstreamer0.8-plugins-multiverse (from .../gstreamer0.8-plugins-multiverse_0.8.11-0ubuntu1_all.deb) ...
Setting up libdirac0 (0.5.2-0ubuntu1) ...

Setting up gstreamer0.8-dirac (0.8.11-0ubuntu1) ...

Setting up libmp4v2-0 (2.0.0+cvs20040908+mp4v2+bmp-0ubuntu2) ...

Setting up libfaac0 (1.24clean-0ubuntu3) ...

Setting up gstreamer0.8-faac (0.8.11-0ubuntu1) ...

Setting up gstreamer0.8-faad (0.8.11-0ubuntu1) ...

Setting up libwavpack0 (4.2-0ubuntu1) ...

Setting up gstreamer0.8-wavpack (0.8.11-0ubuntu1) ...

Setting up gstreamer0.8-xvid (0.8.11-0ubuntu1) ...

Setting up gstreamer0.8-plugins-multiverse (0.8.11-0ubuntu1) ...
```

---

