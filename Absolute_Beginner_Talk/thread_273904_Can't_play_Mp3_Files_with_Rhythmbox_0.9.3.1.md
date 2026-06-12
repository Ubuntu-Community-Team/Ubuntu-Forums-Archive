---
title: "Can't play Mp3 Files with Rhythmbox 0.9.3.1"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by hermeez on 2006-10-09
The files I am trying to listen too are on my slave drive that is NTFS.

I have changed to Ubuntu to get the MS monkey off my back.

This is a bit of a learning curve here for me, just installing software can be a task for me! WOH

Anyway I copied the mp3 to my desktop on the linux box and stil didn't play from there.

I don't know where to start troubleshooting

---

### Post by foxmulder881 on 2006-10-09
You have install the gstreamer codecs. For troubleshooting, go to [http://www.ubuntu.com/support](http://www.ubuntu.com/support)

That's a good place to start.

Also, you can go to System>Help>System Documentation and search for gstreamer. This will give you more information regarding install process etc.

---

### Post by ghostshadow189 on 2006-10-09
i think can try to use xmms , it good for mp3s

---

### Post by LinuxSon on 2006-10-09
Hi!! :mrgreen: 

I am also a Ubuntu-newby, and being such a big, HUGE!! music fan, I just had to have my mp3s up and running before I did anything else...
Unfortunately, no mp3-support for me....

So I downloaded VLC Player!!:rolleyes: 

Listening to my mp3s now at this moment...

PS: Ubuntu uses either .deb or .tgz packages...
    Instructions on installation are usually a readme file somewhere in the
    zipped file...

Enjoy!!! 8)

---

### Post by Ben Sprinkle on 2006-10-09
Get libmp3-mad and libmp3-ugly.

---

### Post by Lord_Dicranius on 2006-11-10
I just wanted to post with my experience in getting .mp3's to play.  No longer than 10 mins ago, I started listening to my first .mp3 on Linux (with the help of Noven from irc.binrev.net#binrev).

I installed mplayer using Synaptic.  Then Noven gave me a command to install libxvidcore4.  It said it was already installed, but I'm not sure if it was installed by default, or if it was installed because another install I did was dependent on it.  Anyways, I opened mplayer, clicked on the window to open my audio file, and it worked!

I hope this helps others as it has helped me!

---

### Post by rlozano on 2006-11-10
> **hermeez said:**
> The files I am trying to listen too are on my slave drive that is NTFS.

I have changed to Ubuntu to get the MS monkey off my back.

This is a bit of a learning curve here for me, just installing software can be a task for me! WOH

Anyway I copied the mp3 to my desktop on the linux box and stil didn't play from there.

I don't know where to start troubleshooting

try installing automatix2.... as noob, it will help you alot get those codec neede to play your mp3's and other multimedia stuff...

hope this helps...

---

### Post by Harmshi on 2006-11-10
I agree. Automatix 2 is a great and easy way to install all the multimedia stuff you need in one go!

---

### Post by shane2peru on 2006-11-10
Lets finish this thread.  Automatix2 for whatever reason does not work on my dapper system.  I installed it via apt, and it just exits for no reason.  I would like to know what I package I'm missing to have Rhythm box play MP3 with out Automatix2.  Any ideas??  Thanks.

Shane

---

### Post by Busch on 2006-11-21
just download this file and there you go :)

[click here yo]("http://archive.ubuntu.com/ubuntu/pool/universe/g/gst-fluendo-mp3/gstreamer0.10-fluendo-mp3_0.10.2.debian-1_i386.deb")

Worked for me,  oh yea to install it just use the gdebi package installer.. so basically double click on the file :).

---

