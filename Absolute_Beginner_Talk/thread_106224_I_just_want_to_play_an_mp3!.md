---
title: "I just want to play an mp3!"
date: 2005-12-20
forum: Absolute Beginner Talk
---

### Post by charliedee on 2005-12-20
Just when I thought I knew computers, up comes Linux.

I'm not a new user to computers. Far from it. I'd consider myself as an advanced user, not an expert, because I can do everything I want and need to on Windows machines. I bought an Apple Mac a few months ago because I wanted a refreshing change. I liked the change from the slow and unpredictable Windows operating system so much that I thought, why not try Linux? So I installed Ubuntu Breezy Badger on an old PC with very few problems but now I'm here:

I want to play an mp3 but I can't. When trying to load an mp3 in the program 'Music Player', I simply get the message;

"Error: This file is not an audio stream"

and if I simply double click on an mp3 file, 'Totem Movie Player' says;

"Totem could not play 'mymp3.mp3' - There were no decoders found to handle the stream, you might want to install the corresponding plugins."

Fair enough, I say, but how? I don't have a direct internet connection to the PC because the network card doesn't work (everything in this PC is made from old parts) but when I look the problem up in this forum, other people with the same problem seem to be able to get it fixed. Problem is, all it takes is one new word to throw me off and I'm lost. Someone says, "run Synaptic..." :confused: Synaptic? I'm Down on the first hurdle.

So in summary, PLEASE could someone help me play an mp3? I'm sure I'll find other things I want to do very soon indeed but until I deal with this one, I can't be bothered to try out this new operating system. Understand that I'm not trying to be a complete idiot, but if you start shooting command line phrases at me and I come across a problem, no matter how small it may seem to the typical user of Linux, I'm not likely to try and find another way around it. What I need is someone to speak to me like I'm a four-year-old.

Thanks for reading and any help that you'll offer in advance.:D

charliedee

---

### Post by Gurgeh on 2005-12-20
Basically, Get XMMS of the synaptics package manager, its a lot like Winamp and u can install loadsa of enhancements (Visual, quality etc) wicked little piece of software. If you can work out a way of getting ubuntu to associate MP3 with XMMS then give us a shout, atm I have to drag and drop...

Alternatively u can use Automatix (yuck) to obtain all the codecs and ass fist ur machine into obedience.

---

### Post by 23meg on 2005-12-20
Do this: [http://help.ubuntu.com/starterguide/C/faqguide-all.html#codecs](http://help.ubuntu.com/starterguide/C/faqguide-all.html#codecs)

If you don't have internet access you may download the gstreamer-mad package [here]("http://packages.ubuntu.com/breezy/libs/gstreamer0.8-mad"), transfer it to your Ubuntu installation and install it with ```
 sudo dpkg -i /path/to/file
```but you may have dependency problems.

---

### Post by Knomefan on 2005-12-20
Hi, I think the start guide should help you out here (It also explains what synaptic is and how to use it):
[http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-music-and-movies](http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-music-and-movies)

Of course, feel free to ask further questions

Opps, just saw you don't have internet access. You should really try to get it to work, as it will make life with breezy a lot easier.

Anyway, you need to install the following packages to get mp3 playback:
[http://ftp.cs.umn.edu/pub/ubuntu/pool/universe/g/gst-plugins0.8/gstreamer0.8-mad_0.8.11-0ubuntu5_i386.deb](http://ftp.cs.umn.edu/pub/ubuntu/pool/universe/g/gst-plugins0.8/gstreamer0.8-mad_0.8.11-0ubuntu5_i386.deb)

Download it to your home directory, then open up a terminal (Gnome menu -> Accecoirs (or something, I'm not on an English system) -> Terminal)

Then install it with ```
sudo dpkg -i gstreamer0.8-mad_0.8.11-0ubuntu5_i386.deb

```
Just type this in the terminal, it will ask you for your password, enter your users password, hit enter and that should be it.

---

### Post by charliedee on 2005-12-20
Ok, Gurgeh. Thanks for replying. I have ABSOLUTELY no idea where the hell the synaptics package manager is found :D but I'm pretty sure from my previous experience with other operating systems that if you right click the mp3 file and click properties, you'll be along the right lines. Click the 'open with' tab at the top of the window and then click 'Add' and select 'XMMS' from the list, that'll work. Select XMMS with the 'radio buttons' to make it the default program for the plaback of mp3 files. Someone may prove me wrong on that one.

---

### Post by charliedee on 2005-12-20
Knomefan and 23meg, thanks very much for your quick replies. I'll check out your advice later. Knomefan, I do have internet access, just not on my Linux machine. I'll post back when I have some news.

Thanks again.

---

### Post by Gurgeh on 2005-12-20
Oh yeah ur totally right but that doesn't seem to work for me. U'll find Synaptics package manager in the Systems > Administration/Preferences I think its something like that, get XMMS from multimedia section, make sure u've got the CD in the drive and hopefully it should take it from there.

PS: I really wouldn't bother with Totem, u'd be better of trying to read the raw MP3 data and then sing the song to urself lol.

---

### Post by Alpha_toxic on 2005-12-20
First of all you should realy get this network card working. This will realy make your life much easier.

Now I see you are not using Ubuntu but Kubuntu, so there is no Synaptic there...
In Kubuntu there is Adept, which basicaly does the same thing. Obveously everyone else that has been answering you is using Ubuntu (and 23meg has Drapper), so don't be surprised you can't find what they are telling you to...

Now back to those MP3's:
As you perhaps know mp3 is a proprietary format, so if it was in the default distro, you would have to pay for it.

If you have no Internet connection on the Kubuntu box, you should download XMMS (looks and feels just like Winamp 2) from somewhere else. I think [this]("http://packages.debian.org/unstable/sound/xmms.html") will do the trick. At the bottom of the page there is a table. "i386" is probably what you need. You should also consider those dependances listed above. After downloading just right click on the file and find the "install" or sth (I'm not exactly sure what the line was, I'm not on my Kubuntu box right now...).

You will allmost for sure run in some dependances trouble, wich if using Synaptyc/Adept, would get automaticaly solved, but you need network conection for that. 

Than, as 23meg said, you should install  "[gstreamer0.8-mad]("http://packages.ubuntu.com/breezy/libs/gstreamer0.8-mad")". This is actualy the library that plays those mp3's.

Final words:
Man you should realy get that network working. Ubuntu/Kubuntu is so much internet directed distro, that I just don't know what are you going to use for if it's not connected. Except that it is so much easier to install apps using Synaptic/Adept. With only 2-3 clicks you get the newest version of whatever app you want and with all dependances solved!! No trouble, no headaches...

Bye, and I hope I helped :)

---

### Post by charliedee on 2005-12-20
Whoops! I'm almost 100% certain that I'm using Ubuntu. I was in a hurry to set up my profile so I accidentally clicked Kubuntu instead. Very sorry for the confusion I may have caused. Thanks for your help everyone. Once again, I'll check it later on and I'll try and get a network card up and running.

---

### Post by charliedee on 2005-12-20
Thanks very much guys for all your advice and support, but I've not actually found anything that works so far. I'm not sure why I haven't, but I've downloaded LOADS of files, tried the 'sudo dpkg -i' command on nearly all of them, resulting in every single case with some kind of error. These are most of the files that I've managed to download (in no particular order):

gst-plugins0.8_0.8.11-0ubuntu5.diff
xmms_1.2.10+cvs20050809-4_i386.deb
madplay_0.15.2b.orig.tar
gstreamer0.8_0.8.11.orig.tar
gst-plugins0.8_0.8.11-0ubuntu5.diff.gz
gst-plugins0.8_0.8.11-0ubuntu5.dsc
gst-plugins0.8_0.8.11.orig.tar.gz

Knomefan, your link for [http://ftp.cs.umn.edu/pub/ubuntu/pool/universe/g/gst-plugins0.8/gstreamer0.8-mad_0.8.11-0ubuntu5_i386.deb](http://ftp.cs.umn.edu/pub/ubuntu/pool/universe/g/gst-plugins0.8/gstreamer0.8-mad_0.8.11-0ubuntu5_i386.deb) returned a 404 not found error. Sounded like the right kind of file.

Alpha_toxic I downloaded the "i836" .deb file, just like you said, but when I right clicked on it, I got something like 'open with archive manager' but no install option. Opening it with the archive manager resulted in an error like, "this isn't an archive."

I started up the Synaptic Package Manager (thanks for helping me find it by the way, Gurgeh) and it came up with an error message that was basically telling me that it couldn't connect to the internet. Fortunately, I could just skip right past that but I couldn't find XMMS in the Multimedia section, even with the Ubuntu disc in the drive. So I've done pretty much everything I've been told to do but install a new media player.

PLEASE! Someone, help me here. Everyone must've faced this problem at some point in their Linuxing time. What did you do? If it means connecting to the Internet, then I believe I have now collected enough hardware and configured enough settings to go online.

Keep me updated! :confused:

---

### Post by Knomefan on 2005-12-20
[QUOTE=charliedee]
Knomefan, your link for [http://ftp.cs.umn.edu/pub/ubuntu/pool/universe/g/gst-plugins0.8/gstreamer0.8-mad_0.8.11-0ubuntu5_i386.deb](http://ftp.cs.umn.edu/pub/ubuntu/pool/universe/g/gst-plugins0.8/gstreamer0.8-mad_0.8.11-0ubuntu5_i386.deb) returned a 404 not found error. Sounded like the right kind of file.
[/quote]
Try right clicking on it and then save as...
I just tried it and this worked for me.

Just in case [some]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fg%2Fgst-plugins0.8%2Fgstreamer0.8-mad_0.8.11-0ubuntu5_i386.deb&md5sum=0a50e63b835caf8036a81ebaafc3f363&arch=i386&type=main") mirrors.

---

### Post by Rackerz on 2005-12-20
I can't belive no one has mentioned this; 

Go here and edit your sources.list according to this, [http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php) (Make sure to choose the sources.list for 'Breezy' Not Hoary.

Then go to this page in the wiki [https://wiki.ubuntu.com/RestrictedFormats?highlight=%28Restricted%29](https://wiki.ubuntu.com/RestrictedFormats?highlight=%28Restricted%29) to read up on why you can't pla the Mp3.

To install the codecs you need to play your mp3s type this in console; 

> sudo apt-get install gstreamer0.8-plugins gstreamer0.8-plugins-multiverse gstreamer0.8-ffmpeg

---

### Post by charliedee on 2005-12-21
Ladies and gents, the winning answer was submitted by Rackerz. I connected the machine up to the internet and, sure enough, the process ran like clockwork, apart from when I typed the command;

sudo apt-get install gstreamer0.8-plugins gstreamer0.8-plugins-multiverse gstreamer0.8-ffmpeg

I kept getting the message;

Setting up gstreamer0.8- [insert extra part of file name here]
OIL: ERROR liboiltest.c 247: (): illegal instruction in idct8x8_s16_mmx

All the same, I can now play mp3s on Linux, so I'm not really bothered if it seemed accept that last command like sandpaper down the throat. :D

Thanks to everyone that contributed to this thread. You all made me feel most welcome to the world of Linux and I certainly won't be putting 98SE back on this machine.

---

### Post by Rackerz on 2005-12-21
> **charliedee]Ladies and gents, the winning answer was submitted by Rackerz. I connected the machine up to the internet and, sure enough, the process ran like clockwork, apart from when I typed the command said:**
> 
OIL: ERROR liboiltest.c 247: (): illegal instruction in idct8x8_s16_mmx

All the same, I can now play mp3s on Linux, so I'm not really bothered if it seemed accept that last command like sandpaper down the throat. :D

Thanks to everyone that contributed to this thread. You all made me feel most welcome to the world of Linux and I certainly won't be putting 98SE back on this machine.
No problem ;). This is a particular subject i wont forget about, it was the first thing i noticed that didn't work.

---

