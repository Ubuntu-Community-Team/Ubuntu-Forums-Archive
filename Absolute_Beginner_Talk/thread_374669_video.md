---
title: "video"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by applehead on 2007-03-02
Hi everyone 
I can't believe I've finally got Ubuntu to work!  Feels good!!!!!!!!!

I've looked through all the documentation about playing video and installing plugins, I installed gstreamer.  but when I try to play video from this site: [http://icliverpool.icnetwork.co.uk/liverpoolecho/]("http://icliverpool.icnetwork.co.uk/liverpoolecho/")
I get audio but no video. Also when I try to wach video from sky news, it tells me to install a plugin wich it then isn't able to do.

Do I need another plugin?
Is there a load of plugins that I'm going to need for other things on other sites?
Do I have to type comand lines to instal things?

Any help would really be apprieciated.

---

### Post by taurus on 2007-03-02
Have you seen this guide?

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by applehead on 2007-03-02
yes. I'll read it again though

---

### Post by applehead on 2007-03-02
I think I'm right in saying that I need w32 codecs.
the best I can find is this site:
[http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/]("http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/")
but I haven't got a clue what it's telling me to do. any chance of a better explanation?

---

### Post by taurus on 2007-03-02
w32codecs:

[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs)

libdvdcss2:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by applehead on 2007-03-02
I'm just going round in circles, non of this makes any sense to me, I can only put so much time into this and then it's back to windows or get a mac 

[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs]("https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs")
this page seems to give a link to a non existant page. the best I can do is here:[http://www.debian-multimedia.org/]("http://www.debian-multimedia.org/")
and that seems to have links to non existant pages.

please help!

---

### Post by taurus on 2007-03-02
I don't know what more I can explain because I thought the first link about w32codecs explains it very well.  It says that you can download the w32codecs_20061022-0.0_i386.deb and install it from a terminal with

Applications -> Accessories -> Terminal
```

wget -c http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb
sudo dpkg -i w32codecs_20061022-0.0_i386.deb

```

---

### Post by applehead on 2007-03-03
I've pasted that text into the terminal and it dowloaded something. I restarted but it's still not working. I've tried installing mplayer but that says it doesn't have the codecs.
any ideas?

---

### Post by Perfect Storm on 2007-03-03
Have you installed mplayer mozilla plugin?

---

### Post by applehead on 2007-03-03
Yes I have.  I either get just audio (in the case of sky news) or nothing at all.

---

### Post by applehead on 2007-03-03
I've read through lots of other posts and documentation and tried lots of different things, still no joy. There must be a fairly simple way to view embeded video. 
 could someone go to sky news and see if they can play video.  is it just me?

---

### Post by Maestro23 on 2007-03-03
I'm running Xbubuntu 32-Edgy 6.10 w/FF 2.0.0.2 and I can play video from that site.  The mplayer-plugin picks up the embedded video for me.

---

### Post by applehead on 2007-03-03
I think I'm running ubuntu 6.06 LTS.
What is w/FF 2.0.0.2?
I have just got version 6.10 through the post, do you think I should try that instead?

---

### Post by Maestro23 on 2007-03-03
If you are switching to Edgy 6.10, definately get FireFox 2.0.0.2 from the Repositories.  Then as I'm sure you know, get your codecs: Restricted Formats.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Good luck.

---

### Post by applehead on 2007-03-03
Well, I've tried everything suggested, still just audio, no video.

This is my last attempt. I've spent about  hours on this so far. If this is what using linux is going to be like then I'm off.

This is my final plea... PLEASE HELP ME!!!!!!!!!!

---

### Post by Perfect Storm on 2007-03-03
Try this:
First uninstall mplayer mozilla plugin, eventually totem mozilla plugin (it will interfere sometimes).

then:
```
sudo aptitude install gxine libxine1 libxine-extracodecs libxine-main1 gxineplugin
```

This require that you have both universe and multiverse enable first.

---

