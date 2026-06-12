---
title: "two many errors to mention"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by 888mafia on 2008-03-17
Im tryin to put  Internet DJ Console on my system it calls for these packages to be in stalled  i dont think i have them .
On start up i get this error OAFID : Desk-bar applet.
When in my broswer i have no exit ecept in file cant use bookmark 
im just tryin to get this radio station up



Python  	                                Required
Jack Audio Connection Kit 	     Required
PyGTK                                   	Required
vorbis-tools 	                              Required
libsndfile 	                                 Required
libsamplerate 	                            Required
libshout 	                               Required
LAME 	                                      Recommended - for streaming/recording in the mp3 format
eyeD3 	                                     Recommended - for metadata tagging and mp3 support
faad2 	                                     Recommended - provides support for m4a files
libmad                                  	Recommended - provides support for mp3 files
ffmpeg                             	Recommended - provides support for wma files
FLAC 	                                Recommended - provides support for flac files

where can i find these ?
i am a new born 2 days old with ubuntu and linx

---

### Post by Xiong Chiamiov on 2008-03-17
Try (just guessing, don't blame me if it has any errors):
```

sudo apt-get install python pygtk vorbis-tools libsndfile libsamplerate libshout lame eyed3 faad2 libmad ffmpeg

```

Essentially, if you need those things installed, then go ahead and install them.  Are you familiar with how to use the package manager?

---

### Post by 888mafia on 2008-03-17
no i dont

---

### Post by dmitrijledkov on 2008-03-17
Go to **System -> Administration -> Synaptic Package Manager**

Enter admin password.

Then press **Reload**. Then **Search**.

Type the thing you need/want/wish. Browse through results. Mark what you want in the boxes. Then press **Apply**. This will then download and install selected packages.

---

### Post by 888mafia on 2008-03-17
ill try nnow ty

---

### Post by 888mafia on 2008-03-17
this may sound stupid but besides what i listed what do i need or should i have to make this run right

---

### Post by dmitrijledkov on 2008-03-17
> **888mafia said:**
> this may sound stupid but besides what i listed what do i need or should i have to make this run right

Well, does it run? And if it does what do you not like about it to make it right?

---

### Post by 888mafia on 2008-03-17
[LIST=1]
[*]I have to force exit
[*]packages i try to find can not be found
[*]OAFIID  errors on start up
[*]cant minamize panels
[*]help file wont load
[*]when scrolling  down bookmarks it disapears
[/LIST]
thats just the beggining

---

### Post by jan quark on 2008-03-17
> packages i try to find can not be found
enable the software sources in system > administration >software sources

---

### Post by dmitrijledkov on 2008-03-17
Instead of Downloading and compiling source code from the website I would recommend to delete whatever wherever you did and do following

Open Synaptic, Press search.

Enter **idjc**, mark for installation click apply.

This will automatically install and configure Internet DJ console. Next time search in synaptic first any software you want to install and only if you don't find it there proceed further.
Synaptic automatically installs all necessary dependencies, libraries, etc.

Instability issues will be solved as well, since version on the website is "alpha" - unstable. But in repository previous from 6.X series but stable (and better).

To install additional codecs for all those different restricted formats (and many other good stuff you will need) install ubuntu-restricted-extras from synaptic again (if you are using ubuntu).

Both of these operations you can do in command line
```
sudo apt-get install idjc ubuntu-restricted-extras
```

---

