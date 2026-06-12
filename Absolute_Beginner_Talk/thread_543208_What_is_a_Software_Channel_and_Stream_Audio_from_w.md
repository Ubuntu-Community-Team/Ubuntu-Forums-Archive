---
title: "What is a Software Channel and Stream Audio from website"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by sluggo1234 on 2007-09-04
I tried to download a sound recorder and editor using the Ubuntu download manager. I found one and tried to download it. This is the message that popped up:

A later version is available in a software channel. You are strongly advised to install the version from the software channel, since it is usually better supported.

I haven't a clue as to what and where a software channel might be found to download an audio editor and recorder 

I have a series of tapes produced by a friend who is a public speaker. He has a website where he wants to place them. The host does provide for streaming audio. So I need to record the tapes to my computer, (Which is no problem once I get the Audio recorder) edit them (this may be a problem unless there a manual to download) and them upload the to the hosting site with my ftp.  I did that once a long time ago with both Real and Windows media decoder. I had to produce an audio html, a txt document and then upload the audio.  I had a Real Production Guide and Real Producer Plus. I did not care for Real as they nag the listener to death. I went to Windows Media Encoder 6.0 (no longer available) and the same information for free from Windows stating all the details in stream audio as well as embedding a audio player on the site and telling them where to go to get Windows Media Player or other player that would play wave files.. I know MP3 is probably better but as I have done this using Real and WME but then it may be as simple as telling the recorder to save the Wave files as MP3 files. But will all the listeners have MP3 Players? It might be better to use Wave files. I have no knowledge concerning this, so I am looking to all the knowledgeable people here for help. 

Now I am attempting to do the same thing using Linux.  I have no idea which audio recorders are best used in Linux and how to get the files to stream.

So you see I need advice and pointers on where to go. Careful now I do not want to go THERE.:)

Hopefully someone can start me on the first step.
sluggo1234

---

### Post by carloslosgrande on 2007-09-04
[FONT="Comic Sans MS"]Hi, have you tried[COLOR="Red"] 'system>administration>synaptic package manager'[/COLOR] ?
or alternatively[COLOR="#ff0000"] 'applications>add/remove' [/COLOR]?
Also you may want to allow access to software channels which you can do in[COLOR="#ff0000"] 'add/remove' [/COLOR]by selecting the box in the top right corner, that probably says[COLOR="#ff0000"] 'supported ubuntu applications'[/COLOR] and change it to[COLOR="#ff0000"] 'all available applications'[/COLOR]. This is what I have.[/FONT]

---

### Post by sluggo1234 on 2007-09-05
> **carloslosgrande said:**
> [FONT="Comic Sans MS"]Hi, have you tried[COLOR="Red"] 'system>administration>synaptic package manager'[/COLOR] ?
or alternatively[COLOR="#ff0000"] 'applications>add/remove' [/COLOR]?
Also you may want to allow access to software channels which you can do in[COLOR="#ff0000"] 'add/remove' [/COLOR]by selecting the box in the top right corner, that probably says[COLOR="#ff0000"] 'supported ubuntu applications'[/COLOR] and change it to[COLOR="#ff0000"] 'all available applications'[/COLOR]. This is what I have.[/FONT]

Well, I am a beginner to Linux, I had no idea where to start. Thanks, not sure what I did but using Synaptic Package Manager somehow, not sure exactly how but I did get Audacity downloaded.  Now I have advanced from the "what is a software channel to lets stream some audio.  

Well, Need to back up some. I have Audacity downloaded, but not  working. When using Windows ME I have no big problems with Audacity, it records and plays back. So far I cannot get a peep out it in Ubuntu Linux.  Doing some research now, but a fast pointer or two would be helpful here.  :confused:
sluggo.

---

### Post by carloslosgrande on 2007-09-05
[FONT="Comic Sans MS"]You most likely need to get your Audio and Video codecs. Synaptic has this stuff. 
Search for gstreamer.
You may also need w32codecs. have a look here> ;[http://www.newlinuxuser.com/w32codecs-and-mplayerplug-in/](http://www.newlinuxuser.com/w32codecs-and-mplayerplug-in/)
and here;> [http://swik.net/w32codecs](http://swik.net/w32codecs)
I'm sure there are other places to get this stuff too.
Have a look in the documentation which is VERY useful for lots of stuff; > [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)
Good luck.
Check this out too;>  [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/) which has a lot of clear explanation.[/FONT]

---

### Post by sluggo1234 on 2007-09-05
I found the page and when I tried to add this info I was told "The file "/etc/apt/sources.list" is read-only." and "you do not have the permissions necessary to save the file" which was source.list with this added on: 

## Medibuntu - Ubuntu 6.10 “feisty eft”
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

So how do I get to the permissions to change them or is there something else I need to do?
sluggo

---

### Post by sluggo1234 on 2007-09-05
> **carloslosgrande said:**
> [FONT="Comic Sans MS"]You most likely need to get your Audio and Video codecs. Synaptic has this stuff. 
Search for gstreamer.
You may also need w32codecs. have a look here
and here;
I'm sure there are other places to get this stuff too.
Have a look in the documentation which is VERY useful for lots of stuff; 
Good luck.
Check this out too; which has a lot of clear explanation.[/FONT]

It is easy to see that I will not get this solved in one day, week, or month. So perhaps for now we could say this thread is solved while I read and practice with what you have given me. I will return to Windows to try to get these messages streamed.  

By the way where and how do I get to the daily videos for the month of September?
sluggo

---

### Post by carloslosgrande on 2007-09-05
Hi, [COLOR="Red"]sudo[/COLOR] will give you permission to make root changes (root = admin in windows)
sudo = super user do
In the case of altering files you can use [COLOR="#ff0000"]gksudo gedit /etc/apt/sources.list[/COLOR]
you will be prompted for your password and then you'll be in, and able to change stuff.

[COLOR="#ff0000"]*_But be careful!_*[/COLOR]You are changing system files!

Its a good idea to copy the file first like this; > sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup

I copied this Howto from the 'ubuntu documentation' site, ...I think;
> Feisty Fawn for beginners. If your a new user, copy and paste commands into the terminal, should be relatively easy from that point forward. 

For mp3, etc. 
Open up Add/Remove programs from your Application bar. 
Go to Sound&Video and Find and Check all of the packages below (easily done by searching for gstreamer)
"GStreamer ffmpeg video plugin"
"GStreamer extra plugins"
"GStreamer plugins for aac, xvid, mpeg2, faad"
"GStreamer plugins for mms, wavpack, quicktime, musepack"

Then go to Other subsection of Add/Remove and find
"Ubuntu restricted extras"
For Flash support
While under the "Other" section enable
"Macromedia Flash plugin"
For DVD Playback and Win32 Codecs 

Edit the file /etc/apt/sources.list using either of the following commands in a terminal:
Code:
$gksudo gedit /etc/apt/sources.list
to open it in the GUI text editor

or
Code:
$sudo vim /etc/apt/sources.list
to open it in the Vim command line text editor

Add the following lines to add the Medibuntu repository to the file:
Quote:
## Medibuntu - Ubuntu 6.10 &#8220;edgy eft&#8221;
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free non-free 
Import the gpg key for the Medibuntu repository to ensure that the packages are installed without warnings/errors regarding trust:
To do this, run the following command from the terminal:
Code:
wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -
Now update the local list of packages to get the list of packages from the newly added Medibuntu repository:

In a terminal execute the following command:
Code:
sudo apt-get update
Now you can install libdvdcss2 and w32codecs using the following command:
Code:
sudo apt-get install libdvdcss2 w32codecs

Certainly patience is helpful but I don't think it needs take too long for the initial setup.
Audio streaming requires plugins which is, I think, covered in the links I gave you.

---

