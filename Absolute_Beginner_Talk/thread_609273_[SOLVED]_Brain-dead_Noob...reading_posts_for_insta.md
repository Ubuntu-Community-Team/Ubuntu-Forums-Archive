---
title: "[SOLVED] Brain-dead Noob...reading posts for installing music player...Help!"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by Vesper007 on 2007-11-10
Hi to all the dedicated post(ers) and community 411s.
This is my first post at Ubuntu Forums. I've been reading and searching posts for getting a music player installed on 7.10 but i just don't get it (sorry).

First; i'd like to say that this forum is absolutely wonderful and contains lots of wisdom (amen to all you Linux 'Geeks' - read: compliment!).

Secondly: Agggghhh!

I'm not missing my M$ OS...and i like the fact that Linux puts noobz into the fray of getting to know the insides of the workings of our computers. The M$ OS i was using was keeping me in the dark. But now that Linux is part of my life (hopefully for a long time:)), the light seems a little dim. Here's what I don't know:

_       - everything Linux _- ](*,)

1. I have about 2700 music files (mp3, lots of wma, and acc   - - - I spent the morning copying all  my audio files to my /home/music directory

2. Then went to import the folder into an application 'rhythmbox' (is that a good player?)

3. every one of the files came up with import errors - not recognized.

4. Put a regular CDA into CDROM and still nothing happened. 

5. Read post 'absolute beginners...' about going to 'add/remove' and installing 'synaptic mangaer'  - but it was not there (do I need this addon?) - why isn't it there? Is my list of 'add/remove' up to date? If not, how do i get it to list ALL available plugins for Ununtu disro?

Well, that's about it. This is my primary concern at this time - though m sure there will be others.

:arrow:**Can someone walk me through*** HowTo ULTRA 101***. I'm good at following instructions but it's all seems quite cryptic to me. 

Thank you in advance for any and all contribution to my audio woes.

---

### Post by Paul820 on 2007-11-10
It sounds like you don't have the codecs installed to play the files. Do you have the multiverse repositories enabled in System->Administration->Software Sources ?

---

### Post by Vesper007 on 2007-11-11
> **Paul820 said:**
> It sounds like you don't have the codecs installed to play the files. Do you have the multiverse repositories enabled in System->Administration->Software Sources ?

Thanks for the speedy reply (these forums always amaze me at the help that's available 8) )

- i went to System>Admin>Software Sources as suggested. There was a box ticked that read:

 "**CD ROM with Ubuntu 7.10 Gutsy Gibon - officially supported restricted copyright**"

 - and i noticed that the "Download From" box had 'Canada'  so selected Main Server>update: Some 48 programs/plugins (??) downloaded but there is no list showing what is available. 

Does the **Bold **(see above - this reply)mean that i am to install my Distro and have Ubuntu 'look' for what is needed?

Gee; i'm really not too bright at this. How about step 1, step2, step 3, etc... (i'm taking lots of notes!)

---

### Post by Presto123 on 2007-11-11
I'll give you this info:

For Codecs, I have: GStreamer ffmpeg video plugin, Gstreamer extra plugins, Xine extra plugins. 

In order to get these go to: "Applications" then "Add/Remove" and type in: "Codecs" in the search bar, making sure that the "Show" dropdown list to the immediate right of the "Search" has "All Available Applications" selected.

Hope that helps.

*Edit* As with all of my information I post, I, too, am fairly new. I may give you needless additions to a degree, but my computer works fine with these codecs. This includes audio/video with the exception of Flash"

---

### Post by Vesper007 on 2007-11-11
> **Presto123 said:**
> I'll give you this info:

For Codecs, I have: GStreamer ffmpeg video plugin, Gstreamer extra plugins, Xine extra plugins. 

In order to get these go to: "Applications" then "Add/Remove" and type in: "Codecs" in the search bar, making sure that the "Show" dropdown list to the immediate right of the "Search" has "All Available Applications" selected.

Hope that helps.

*Edit* As with all of my information I post, I, too, am fairly new. I may give you needless additions to a degree, but my computer works fine with these codecs. This includes audio/video with the exception of Flash"

Presto123: I was able to find only xine extra plugin with warning that wouldn't function on my i386...did some more searching and found a list of libxine1 (plugins, ffmpeg, gnome) - - found them on SPM (***sans*** libxine1-gnome)

....anyway, here goes; I'm going to try to load my songs into 'rhythmbox' again - just a few - because i reinstalled 7.10 thinking i had done something wrong. If it works, i'd consider this prob solved. If not, i'll just keep on it. 

Cheers mon ami

Went online and downladed gst-ffmpeg.tar.gz @ [http://gstreamer.freedesktop.org/src/gst-ffmpeg/?C=M;O=D](http://gstreamer.freedesktop.org/src/gst-ffmpeg/?C=M;O=D)
 (i think it's the correct file that you listed above) where do i extract it to so that it is in the selections of SPM?

---

### Post by forestpixie on 2007-11-11
you'll need to enable the repos in software sources - then have another look for the codecs

---

### Post by Frak on 2007-11-11
1. Rythmbox is a bad player IMHO, use [banshee]("apt:banshee") or [amarok]("apt:amarok").
2. You need [Ubuntu-Restricted-Extras]("apt:ubuntu-restricted-extras") package to play audio. You could install these seperately, but why not just get the bundle. This package will automatically enable the needed repos.

---

### Post by theharshone on 2007-11-11
I agree, amarok seems to be a more user friendly player. And as was said before, you should install ffmpeg, lame, and w32-codecs(not sure if this is in the repos).

---

### Post by HermanAB on 2007-11-11
Uhm, if you look at the top of the Absolute Beginner forum (this one), then you'll see a sticky post called 'Complete guide to installation in Ubuntu'.

Cheers,

Herman

---

### Post by forestpixie on 2007-11-11
Amarok +1 , never used banshee - but my son prefers it to amarok - neither of us like rhythmbox though

might need libxine1-ffmpeg installing with it

just read first post again - you should have synaptic installed - it's in system >admin

---

### Post by Vesper007 on 2007-11-11
> **HermanAB said:**
> Uhm, if you look at the top of the Absolute Beginner forum (this one), then you'll see a sticky post called 'Complete guide to installation in Ubuntu'.

Cheers,

Herman

It's the first thing i read before installing. Like i said before...things are quite cryptic with all of this (for me anyway). I'm not finding this easy, but i am learning ever so slowly. 

I'm going to get amarok. 
Do i need to uninstall anything that i've installed to 'try' to get rhythmbox working? (maybe leave it alone and just go to different player?) 

thanks again for the 411s

---

### Post by Frak on 2007-11-11
Leave it and go for amarok.

---

### Post by Vesper007 on 2007-11-11
AMAROK worked first time out of the 'box'....thank u, thank u, thank u!

:guitar:It's playing my mp3s (will check the other formats tomorrow :) )

Building my library back to what it was and oh, btw; THANK YOU

---

### Post by LizardKing73 on 2007-11-11
Glad everythings working but if I may offer another player suggestion give VLC a try, it plays all file types including wma and mp3.
To get it log into terminal and enter

sudo apt-get update

then

sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc

If Amarok is working good 4 ya then nevermind but thought I would just offer the suggestion.

Take care

---

