---
title: "QuickTime For Ubuntu"
date: 2006-04-06
forum: Absolute Beginner Talk
---

### Post by etherealbeats on 2006-04-06
I really need some kind of plugin to be able to watch QuickTime movies (.mov etc) on Ubuntu. Also is there anything that will allow it to work with Firefox for the Apple movie trailers? Anyone know of anything which will allow me to do this?

Thanks,
jem

---

### Post by pbaehr on 2006-04-06
I think [this]("http://www.ubuntuguide.org/#mplayer") will do what you want. It sets up mplayer for use within firefox and I'm pretty sure this will handle quicktime. I think you'll have to install the codecs from mplayers site to handle quicktime, though. Not positive.

---

### Post by etherealbeats on 2006-04-06
Installed MPlayer and the plugin. Firefox still wont play the quicktime files, like movie trailers. I am running Firefox 1.5 and not the older one that ships with Ubuntu. I followed the instructions in the Ubuntu wiki for this.

---

### Post by pbaehr on 2006-04-06
Do you have the codecs from mplayer downloaded and properly installed? It's a bit of a pain but it will enable mplayer to play virtually every video file in existence. I will see if I can find you a guide for grabbing those.

---

### Post by pbaehr on 2006-04-06
Okay. If you haven't already, go to: [http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html) and download the "Essential Codecs" package.

Then you need to unpack it to /usr/local/lib/win32/ (you may need to create it yourself)

For what it's worth, I'm basing all this on [this]("http://fuxoft.blogspot.com/2006/01/taming-ubuntu-mplayer-and-simple-smtp.html") page. Check that out for more information. It also suggests that you may need to call the directory "codecs" instead of "win32" so you can try that too, I suppose.

---

### Post by etherealbeats on 2006-04-06
Ok, thanks for sourcing this, greatly appreciated. I am a newbie to Linux and I have come from a Mac so I need a bit of help. I have created the win32 directory and downloaded to codecs. What is the command to extract it to the win32 directory as I keep going wrong?

Thanks

---

### Post by pbaehr on 2006-04-06
Okay, I'm not at my ubuntu box right now so the instructions will be a touch on the vague side.

First you want to go ahead an create the directory.
```
sudo mkdir /usr/local/lib/win32
```

Next, you should be able to double click the file you downloaded to open the compressed folder. Find the extract option (maybe someone else can give you more details here) and tell it to extract to the directory you just made. That should do it.

There is also a command line way to do this and it would probably be easier if I just told you what to type in but I use it infrequently and I don't want to type the wrong thing. Again, maybe someone else can jump in and provide it?

Good luck.

EDIT: Okay, the command to simply unpack the file would be:
```
tar -xvvzf [filename]
```
I think it unpacks it to the current directory (but I could be very very wrong) so you could theoretically navigate to /usr/local/lib/win32 and run it from there. Not certain about that, though.

---

### Post by kaveraj on 2006-04-08
Try FF plugin Media Player Connectivity ([home page]("http://membres.lycos.fr/sethnakht/")).  It allows you to choose from a list of players installed to play any embedded media. I was able to watch the apple trailers. But on this same DSL line I have watched it in Apple's quicktime plugin without any pauses and jitters. May be some option should be enabled for caching and smooth playback over internet.

---

