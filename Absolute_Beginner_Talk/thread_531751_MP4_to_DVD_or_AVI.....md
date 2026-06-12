---
title: "MP4 to DVD or AVI...."
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by manifresh006 on 2007-08-21
Is there any program that can convert MP4 to DVD or AVI :confused::confused::confused:
or any burnable dvd file type

NOT AVI to MP4 :):lolflag:

---

### Post by jw5801 on 2007-08-21
Try dvd::rip. I've only had a quick look at it but it seems to have capabilities for lots of transcoding type stuff. I'm not sure if it's in the 32-bit repos (I know it's not in the 64-bit repos), but have a search around.

---

### Post by manifresh006 on 2007-08-21
Dang this thing is hard to find I saw it in another post....

Any others:(:confused:

---

### Post by jw5801 on 2007-08-21
The first link I get after typing dvd::rip into google is [this.](http://www.exit1.org/dvdrip/) :p

---

### Post by manifresh006 on 2007-08-22
WoW just got off of there.....:lolflag::lolflag::lolflag:
Don't  like google too much gives you too much other s***
Used ask, yahoo,dogpile and some otherones:lolflag::lolflag:

---

### Post by FakeOutdoorsman on 2007-08-22
Are you interested in doing this in a command-line or with a program that has a GUI?

ffmpeg is a great and flexible command-line program that can transcode just about anything, but it is often confusing for someone new to the program.

[DeVeDe]("http://www.rastersoft.com/programas/devede.html") is probably your best bet for a graphical program that can convert videos to DVD.  You may need to get Mplayer/Mencoder from Medibuntu before you install DeVeDe if you are using Feisty.  The default Feisty packages are broken according to the DeVeDe site.

1. Add Medibuntu repository to your sources.list. [Easy instructions]("http://medibuntu.sos-sts.com/repository.php").
2. sudo aptitude update
3. sudo aptitude install mplayer mencoder devede (or install via Synaptic and make sure Mplayer/Mencoder are the Medibuntu versions).

---

### Post by manifresh006 on 2007-08-22
Sounds like ffmpeg should get a chance....
How do Install it or what not:confused::confused:

---

### Post by manifresh006 on 2007-08-22
FakeOutdoorsman what do I do after I download the file and get a folder called devede-3.01.tar.bz2 with docs and stuff...:confused:

---

### Post by stmiller on 2007-08-22
VLC 'wizard' can convert all kinds of audio and video. It's basically a GUI for ffmpeg.

---

### Post by FakeOutdoorsman on 2007-08-22
You don't need to install DeVeDe from the source code.  I'm assuming you downloaded the source from the DeVeDe site.  You can install it with Synaptic if you have the "Multiverse" repository enabled.  To enable it:

System -> Administration -> Software Sources -> Check "Software restricted by copyright or legal issues (Multiverse)".

Then open up Synaptic and install the devede package there.  Once installed it should appear under Applications -> Sound & Video

---

### Post by manifresh006 on 2007-08-22
No luck what should the file be named as DeVeDe because all I see is dvdrip:(

---

### Post by FakeOutdoorsman on 2007-08-22
Try:

sudo aptitude update
sudo aptitude install devede

---

### Post by manifresh006 on 2007-08-22
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "devede"
The following packages have been kept back:
  acidrip amarok amarok-xine bzflag dvd+rw-tools flashplugin-nonfree gxine
  k3b libk3b2 liblircclient0 libtag1c2a libtagc0 libtheora0 readahead
  xmoto-data
0 packages upgraded, 0 newly installed, 0 to remove and 15 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

This is what I got.....:confused::confused:

---

### Post by FakeOutdoorsman on 2007-08-22
You can try to install it from [getdeb]("http://www.getdeb.net/comment.php?rel_id=1106").  Just download the .deb file to your desktop and open/install it.

---

### Post by manifresh006 on 2007-08-22
Sweet:guitar::guitar::guitar::guitar::guitar:
Thax Bro really really appreciate it man:popcorn::biggrin::biggrin::

---

