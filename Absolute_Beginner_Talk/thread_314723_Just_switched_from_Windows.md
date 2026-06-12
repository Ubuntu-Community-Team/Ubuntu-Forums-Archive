---
title: "Just switched from Windows"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by Tekovro on 2006-12-08
Hey guys, today i installed Ubuntu on my computer and its the first time ive ever seen another OS besides windows. i was just wondering. i'm trying to play an mp3 file and i decided to use Rhythmbox as my default audio player since i read some good things about it and i have an ipod. the thing is im not sure how to install it. i downloaded the zipped file and extracted it to my desktop and when i look in the folder i dont see any Setup.exe!! so how do i install this thing??

Thanks!

---

### Post by K.Mandla on 2006-12-08
You could install it through the Synaptic Package Manager, which is easy to use. If you want to start learning terminal commands, you can try this. ...

```
sudo aptitude install rhythmbox
```
By the way, welcome! :D

---

### Post by meng on 2006-12-08
Doesn't rhythmbox come default with ubuntu now? (It's one of the things that annoys me!)

---

### Post by K.Mandla on 2006-12-08
(I thought it did, but I couldn't remember ... it's been a while since I used straight Ubuntu. ;) )

---

### Post by tophatandy on 2006-12-08
first off welcome to the wonderfull world of linux.

now:

I had the same problem after making a complete migration from windows recently (as in within the month). I didn't even bother with rythmbox for my music collection.
For the following reason:
you need a codec to run .mp3's (which in linux is considered a propritary file extension) instead Downloaded vlc from the repository (you can acess this by going to applications-->add/remove..) then click two boxes towards the middle that say show unsupported and commercial to view all the programs.. then go to the "all" catagory and select vlc.

Now to answer your actualy question.
Plain and simply put:

linux doesnt run .exe's .


you should first note that my linux came with rythmbox already installed.

but if you really dont have it installed you can do the following:

1.)look for it in the repository and it will do an easy installation for you

-or-

2.)a.)open up the .zip file and extract to the desktop then open up the .deb or the .tar.gz or maybe just the .gz then it will put it into the gnome menu (application menu) automatically (similar to windows start menu) typically under the catagory of sound/video.

post here how it works out for you.

best of luck.
and once again..

welcome to linux.

:D

---

### Post by aysiu on 2006-12-08
Rhythmbox does indeed come with Ubuntu.

For software installation in general, read this:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

For MP3 playback, read this:
[http://help.ubuntu.com/community/RestrictedFormats](http://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Tekovro on 2006-12-08
lol wow you guys were right. it is on here already, it was just not set as default audio player. 

No mp3 support? i guess that explains why my songs weren't working lol

thanks so much for all the help guys, ubuntu's community is something different. i hate windows now!


i cant believe how incredible this is.. the add/remove thing is just amazing.

---

### Post by mdsmedia on 2006-12-08
While MP3 isn't supported by default, read the links aysiu posted above regarding restricted format support. It is possible (and quite simple) to get support for MP3 but they are a restricted (proprietary) format.

---

### Post by houstonbofh on 2006-12-08
> **Tekovro said:**
> lol wow you guys were right. it is on here already, it was just not set as default audio player. 

No mp3 support? i guess that explains why my songs weren't working lol

thanks so much for all the help guys, ubuntu's community is something different. i hate windows now!


i cant believe how incredible this is.. the add/remove thing is just amazing.
Every time I see posts like yours, I picture some poor guy with a new car posting "I want to listen to music in my car.  I hired a band, but can't fit them in the back seat..." :D No need to make it hard just because Windows does.  Makes you wonder how Windows got so popular while being so difficult.

---

### Post by K.Mandla on 2006-12-08
> **houstonbofh said:**
> "I want to listen to music in my car.  I hired a band, but can't fit them in the back seat..." 
LOL! :biggrin:

---

### Post by Usedpants on 2006-12-08
[http://pcmech.com/show/os/917/2/](http://pcmech.com/show/os/917/2/) is a good article for switching from windows to linux.

but this is what i did. i installed automatix2 from [http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38) and ran it from applications/system tools . Then i went into multimedia and installed every audio and video codec package. very fast and very simple. Good luck to you =). i just switched 2 days ago and its actually extremely easy to learn.

---

### Post by chris_n00b on 2006-12-08
> **Usedpants said:**
> [http://pcmech.com/show/os/917/2/](http://pcmech.com/show/os/917/2/) is a good article for switching from windows to linux.

but this is what i did. i installed automatix2 from [http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38) and ran it from applications/system tools . Then i went into multimedia and installed every audio and video codec package. very fast and very simple. Good luck to you =). i just switched 2 days ago and its actually extremely easy to learn.

Thats what I did as well. After a quick install of all the codecs, everything works now :D :cool:

---

### Post by Usedpants on 2006-12-08
that guide on migrating from windows to linux was kind of a help. but automatix is amazing!

---

### Post by quarkhirad on 2006-12-08
> **Tekovro said:**
> lol wow you guys were right. it is on here already, it was just not set as default audio player. 

No mp3 support? i guess that explains why my songs weren't working lol

thanks so much for all the help guys, ubuntu's community is something different. i hate windows now!


i cant believe how incredible this is.. the add/remove thing is just amazing.

well Tekovro welcome to the world of linux. Eveni have begun hating windows ever since about six months. 

As far as mp3 support is concerned you can use XMMS also. To install XMMS just go to synaptic pakage manager and search for XMMS . 

Cheers
:) :)

---

### Post by tophatandy on 2006-12-08
found another answer for you 

go to terminal (in accessories sub catagory in application menu)

and type 

```
sudo aptitude install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs
```


that should fix rythmbox so that you can use it to play mp3s

I got this from this page:

[https://help.ubuntu.com/community/RestrictedFormats#oneline](https://help.ubuntu.com/community/RestrictedFormats#oneline)

now no need to download vlc or anyother players...
unless you want to

:D

---

### Post by hyper_ch on 2006-12-08
Well, even if you are in ubuntu you could still test-drive Amarok... I tend to think this is THE best mp3 player :)

---

### Post by randytuggle on 2006-12-08
I play lots of mp3 files and I have been using Ubuntu for about a month. I prefer Beep Media Player for music. It works really nice. One of the coolest things about Ubuntu volume controls is how you can use a mouse with a scroll wheel to turn the volume up or down by placing your pointer over a volume control and rotating the wheel on the mouse. I never had windows offer that sort of control.

---

### Post by HokeyFry on 2006-12-08
pretty sure to play mp3s you just need the gstreamer ugly plugin, maybe the ugly multiverse one, too, i read that somewhere else on the forums, but i dont know the post. i know for gstreamer0.8 you just need to install the gstreamer mad plugin, but for 0.10 im not 100% sure.

---

### Post by xpod on 2006-12-08
> thanks so much for all the help guys, ubuntu's community is something different. i hate windows now!

Instant coffee:D 

I was an instant covert myself and this place was certainly half the battle.

The only "real" problem you might have is pulling yourself away from the thing..
Good luck to you ....and HAVE FUN!!!:mrgreen:

---

