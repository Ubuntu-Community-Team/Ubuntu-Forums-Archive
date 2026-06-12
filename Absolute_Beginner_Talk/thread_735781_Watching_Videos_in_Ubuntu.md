---
title: "Watching Videos in Ubuntu"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by iSplicer on 2008-03-26
Hey Guys

Im about to switch to Ubuntu completely, although one thing is pissing me off so much. Watching videos. Im talking about the xvid tv shows that you download off torrents (I cant watch them on TV, I dont have time =( ). They come in .avi

I have tried so many players, installed heaps of codecs recommended by people (I might have missed some). But how much I try, every single video I play is VERY slightly choppy, if you concentrate hard you can see little glitches here and there. With VLC and Xine.

I also need something to get the subtitles working (.sub, .idx). On windows, I would simply install CCCP, and it would work simply like that.

please help get one person completely switched to Ubuntu!

Thanks

---

### Post by whitecore on 2008-03-26
I am not sure on codecs but to watch videos i use gstreamer ugly which show nicley except for some .mkv videos.the chopyness in the video could be your system is not fast enough or the right drivers are not installed.

---

### Post by iSplicer on 2008-03-26
> **whitecore said:**
> I am not sure on codecs but to watch videos i use gstreamer ugly which show nicley except for some .mkv videos.the chopyness in the video could be your system is not fast enough or the right drivers are not installed.

So after i install gstreamer ugly, my mplayer, vlc and xine, etc all will start using it?

---

### Post by Tom--d on 2008-03-26
VLC usually just has all the codecs built in it. 

You've played it through VLC player,right?

---

### Post by Zatzum on 2008-03-29
I have the same kind of problem, .avi files won't work with any media player I've tried. The videos are in video/x-msvideo format. VLC player shows them, but they sound awful and there's small green boxes here and there. Should I install some codecs or could it be possible that is is because of my hardware? The computer is quite old (my first week with Ubuntu, and I'm very happy with my decision!), does it have any effect on this?

---

### Post by rajaram_s on 2008-03-29
As you open the totem player, it says some codecs are to be downloaded. Just click on download them now and you should be able to vie the videos. P.S For this  your computer is directly connected to the internet. Even otherwise, players like VLC are always capable of playing any video, excluding a very fw formats such as .rm.

---

### Post by Tews on 2008-03-29
Sounds like a codec problem ... Checkout this thread ... [http://ubuntuforums.org/showthread.php?t=613462]("http://ubuntuforums.org/showthread.php?t=613462")

---

### Post by zeronothing on 2008-03-29
you could try installing the codecs from the [Medibuntu]("http://www.medibuntu.org/") website. This site has a bunch of stuff gear towards media. Their is also good documentation on had to get the repositories into your apt sources.list file. I would like to point out this site also has other things beside codecs. give it a look

---

### Post by Zatzum on 2008-03-29
Thank you very much, I'm going to try these out. I'll let you know about the results :)

---

### Post by zeronothing on 2008-03-29
also I forgot to mention the Medibuntu website only supports ubuntu up to 7.10. they haven't added 8.04 for support yet. this could be a problem for you. if that is the case just execute this command in terminal with ubuntu:

sudo apt-get install ubuntu-restricted-extras

this will install all the things you need

---

### Post by TeoBigusGeekus on 2008-03-29
About the subtitles issue:
Open VLC and go to File->Open File
Open File tab, choose your divx and tick the 
Use a Subtitles File box.
Choose your subtitle file and press ok...

---

### Post by Zatzum on 2008-03-29
Well, the restricted extras did the job. Never thought of it, but great to have friendly people here! I saw it in add/remove list but didn't read description (the fonts made me ignore it...) Great, everything is perfect! :D Thank you all who helped me!

---

### Post by kayel_justice on 2008-03-31
Hey guys please check out the thread "all video players crash", it's a little different, I could use your help

---

### Post by stchman on 2008-03-31
> **iSplicer said:**
> Hey Guys

Im about to switch to Ubuntu completely, although one thing is pissing me off so much. Watching videos. Im talking about the xvid tv shows that you download off torrents (I cant watch them on TV, I dont have time =( ). They come in .avi

I have tried so many players, installed heaps of codecs recommended by people (I might have missed some). But how much I try, every single video I play is VERY slightly choppy, if you concentrate hard you can see little glitches here and there. With VLC and Xine.

I also need something to get the subtitles working (.sub, .idx). On windows, I would simply install CCCP, and it would work simply like that.

please help get one person completely switched to Ubuntu!

Thanks

I can play .avi files all day long.

Try installing all the proprietary CODECs.

[http://www.stchman.com/codecs.html](http://www.stchman.com/codecs.html)

---

