---
title: "Can you all playback BBC News videos?"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by staib on 2007-04-13
Hi
Am running 6.10 with Firefox and nvidia video drivers courtesy of Automatix.
But cannot get the videos on the [BBC news pages]("http://news.bbc.co.uk/") to playback...    Is there an easy fix here?
Thanks

---

### Post by Gif on 2007-04-13
Hi,

I've got same problem in Xubuntu with the follow thread running:

[http://ubuntuforums.org/showthread.php?t=407528](http://ubuntuforums.org/showthread.php?t=407528)

Maybe some info there to help

---

### Post by flossgeek on 2007-04-13
Install RealPlayer and all should be fine. 

[https://help.ubuntu.com/community/RealplayerInstallationMethods?action=show&redirect=RealPlayerInstallationMethods](https://help.ubuntu.com/community/RealplayerInstallationMethods?action=show&redirect=RealPlayerInstallationMethods)

However Real is proprietry formats, BBC should be frowned upon for supplying these formats!

---

### Post by whitefort on 2007-04-13
> **flossgeek said:**
> Install RealPlayer and all should be fine. !

I've got Realpayer 10 installed, but for some reason it won't play those BBC vids.

---

### Post by AndyCooll on 2007-04-13
I've had this problem in the past. To resolve this I installed mozilla-mplayer.

You then also have to disable the totem plugins. Unfortunately I'm at work at the moment and haven't got access to the link which I used explaining howto do this. I'll post it when I get home.

:cool:

---

### Post by flossgeek on 2007-04-13
Hmm, okay try installing the media connectivity plugin for firefox. You can get this from here:-

[https://addons.mozilla.org/en-US/firefox/search?q=media+player+connectivity&status=4](https://addons.mozilla.org/en-US/firefox/search?q=media+player+connectivity&status=4)

Configure it to use realplayer for real media. Now when you see web pages where media is you will see a black box this is the media connectivity plugin. Click this and it should launch realplayer and play your video. 

I have had no issues with the method above.

---

### Post by Maestro23 on 2007-04-13
Running Feisty w/FF 2.0.0.3 and mplayer plugin.  Plays the BBC vids fine on my machine.

---

### Post by anaconda on 2007-04-13
kongueror with kmplayer-konq-plugins
can also play those videos.

---

### Post by Big Dave on 2007-04-13
> **staib said:**
> But cannot get the videos on the [BBC news pages]("http://news.bbc.co.uk/") to playback...    Is there an easy fix here?

If you install RealPlayer through Automatix2 (see the link in my sig), you should be able to then watch the videos in RealPlayer format. That works for me.

You could also try installing [IEs4Linux](http://www.tatanka.com.br/ies4linux/page/Main_Page), which is very useful if you want to view a page which requires IE.

---

### Post by Obor on 2007-04-13
i use totem mozzila plugin and the windows media stream works fine (in both edgy and feisty)
[https://help.ubuntu.com/community/RestrictedFormats/StreamingVideo](https://help.ubuntu.com/community/RestrictedFormats/StreamingVideo)
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Bloch on 2007-04-13
To answer the OP's question: 

No, No, No, we cannot all play the BBC News clips.

Many if not most people have problems with streaming video. Sorry for sounding a little frustrated, but I wasted plenty of time trying to get these things to work (I like the BBC and also [www.rte.ie](www.rte.ie), Ireland's national broadcaster has good news clips)

Finally realplayer worked for the BBC. Then a week later it didn't work. Then I tries the moz-plugger and it broke my system. 
One solution I tried meant clips worked on BBC but not on RTE.
Suddenly, with no action on my part, BBC clips started working again.

Then later there were several posts coming in at the same time saying an update killed the ability to play BBC clips.
[http://ubuntuforums.org/showthread.php?t=388876&highlight=bbc](http://ubuntuforums.org/showthread.php?t=388876&highlight=bbc)

I asked in the Cafe if anyone could throw light on the issue - was it the BBC paying no heed to linux users or was it Realplayer not bothering to test their software enough.
In the brief informal survey (and others I have seen) up to 50% of people have big problems in playing streaming real media.
[http://ubuntuforums.org/showthread.php?t=363806&highlight=bbc](http://ubuntuforums.org/showthread.php?t=363806&highlight=bbc)
 

Wehen it comes to streaming media ubuntu feels like linux back in 1998 - some solutions work for some people, others find their own way, no-one elses advice will work on your system.


Before writing this post, I tested the RTE real news clips (which has played sound but no image for several weeks now) and lo and behold, it's back playing both now.
I can also play the BBC clips by downloading the .ram file to the desktop. But  just because it works for me doesn't mean it will work for you. I know because realplayer works and then doesn't work like . . . I don't know, a stubborn mule, or the Irish weather or whatever.

---

### Post by AndyCooll on 2007-04-13
> **AndyCooll said:**
> I've had this problem in the past. To resolve this I installed mozilla-mplayer.

You then also have to disable the totem plugins. Unfortunately I'm at work at the moment and haven't got access to the link which I used explaining howto do this. I'll post it when I get home.

:cool:

Continuing what I started before:
```
sudo -s (to login as root)
cd /usr/lib/mozilla-firefox/plugins
mkdir oldtotemfiles
mv libtotem* oldtotemfiles
apt-get install mozilla-mplayer
exit
```

:cool:

---

### Post by floke on 2007-04-13
After complaining to the BBC about their lack of support for non-proprietary software I was told that 'This issue was addressed by our 'Newswatch' programme' and that the item can be viewed at 

[http://search.bbc.co.uk/cgi-bin/search/results.pl?scope=all&edition=d&q=newswatch+microsoft](http://search.bbc.co.uk/cgi-bin/search/results.pl?scope=all&edition=d&q=newswatch+microsoft)

Unfortunately I have not been able to view it since I need Realplayer.

So, in response to a complaint about proprietary formats they send me an answer in a proprietary format :D

---

### Post by bx2 on 2007-04-21
Hi, After getting 7.04 installed yesterday, (worked very smoothly!) took awhile though, I noticed I had the same problem with the BBC as before, I'm using MPlayer.  When the BBC player window opened I clicked on preferences, and chose Win Media instead of Real Player then i was able for the first time to actually view BBC videos.  So far, I am Win Free and loving every minute of it baby!!

---

### Post by Bloch on 2007-04-21
I confirm that.

I updated to Feisty on the day of release. I followed the multimedia guides posted as a sticky at the top of the beginner forum.

BBC works when you choose "play with windows media player" and is handled by mplayer.

The RTE news site which offers only realplayer clips doesn't work however. . . . . but I'll find a way

---

