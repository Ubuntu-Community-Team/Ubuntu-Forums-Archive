---
title: "Lost my youtube audio"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by kris2pe on 2006-07-19
I was able to work out the problem between flash audio in ubuntu & now its gone again!!!
At first the audio was still working & I notice that the audio was kinda the low & I tried to push the audio to full but the opposite happened! 
I lost my audio!!! But there's audio on other sites like google video

[IMG]http://img91.imageshack.us/img91/4299/youtubeah0.jpg[/IMG]

As indicated on the picture the volume scroll doesn't seem to appear & I think youtube has made some changes indicated the other red mark!!!

---

### Post by Teemu R on 2006-07-19
Same thing happened to me. Youtube probably updated their player which causes these issues.

---

### Post by kris2pe on 2006-07-19
Really so how do we do this? 
Coz my wine audio doesn't work!!!

---

### Post by catlett on 2006-07-19
I have been battling sound since the updates. The developers of Ubuntu have chabged the way Firefox deals with sound to make the system more stable. It has resulted in somepeople having no sound with flashplayer in firefox. This is a thread here with some ideas [http://www.ubuntuforums.org/showthread.php?t=216038&highlight=sound+firefox](http://www.ubuntuforums.org/showthread.php?t=216038&highlight=sound+firefox)
But to your issue. I have sound on you tube, the volume meter is mising just like yours but I have sound.
I don't have any real answers. I posted in the thread what worked for me but I still have an issue with soubd on startup. I justed wanted to give some feedback to the effect that sound works for me in you tube although the volume meter is missing.

---

### Post by kris2pe on 2006-07-19
As me now have learn we shouldn't touch the volume meter!!!

---

### Post by Teemu R on 2006-07-19
I tried all the fixes that were in that link and none of them helped. Since I can hear audio from other flash video sites like Google Video the problem is just in Youtube.
PS. If you really wanna see some video on Youtube I suggest you use the video downloader extension for Firefox. With it you can easily download flash videos from youtube and then play them using MPlayer.

---

### Post by madmetal on 2006-07-19
i use this plug in but i still have no sound at the downloaded videos..](*,)  before i had both on youtube and downloaded video..

---

### Post by kris2pe on 2006-07-19
Got mine fixed!!!

---

### Post by Admiral Valdemar on 2006-07-19
> **kris2pe said:**
> Got mine fixed!!!

Feel free to share how you did that, given this isn't an isolated problem. YouTube has changed for me over the last 24 hours as well.

---

### Post by greggh on 2006-07-19
I'm having the same problem. Since yesterday I only can see the very beginning of the volume bar on the youtube video window, and if I click anywhere on it or near it I lose the volume. If you lost your volume I figured out a quick fix to get it back. Go to any site that has an embedded youtube vid and raise the volume on it. For some reason the offsite embedded players still work fine. Then you can go back to Youtube, but don't click the volume bar again or you'll lose it again.

You can go to [http://thejapanesearecrazy.com/](http://thejapanesearecrazy.com/) for a  youtube embedded vid.

This is a stupid bug. Youtube should really fix this fast.

---

### Post by kris2pe on 2006-07-20
Like what gregh said I undone my mistake my accessing embeded youtube vids!

---

### Post by aeto on 2006-07-20
Whoa..hahah same problem here since yesterday. Same way it happened. I clicked on the incomplete volume bar coz it seemed, yes, incomplete to me. Well yeah i figured out mayb if i clicked on it it'd become complete :lol: 

[img]http://img155.imageshack.us/img155/5826/sounderrornv7.jpg[/img]

Then poof! no sound. Bloody hell..ran Wine Firefox no sound there either. Today tried again, this time clearing my cookies & all since i thought mayb it had something to do with my log in youtube. That proved successful in Wine Firefox only..didnt work in my Ubuntu Firefox.

So it looks like a major bug in youtube that many Linux users are facing..thanks for the problem solver. Should announce/sticky the solution or somethin hahahah..if its gonna b a long-term effect that is.

---

### Post by fuscia on 2006-07-20
me three. it worked until i messed with the volume.

---

### Post by ylikone on 2006-07-20
The temporary solution to this (until youtube fixes their end) is to go and delete the directory ~/.macromedia (the one in your home directory, for those that don't know what the squiggle means).  Then don't touch the broken volume control on any youtube video.

EVERYBODY CONTACT YOUTUBE ABOUT THIS PROBLEM!!!  Go here:

[http://youtube.com/contact]("http://youtube.com/contact")
 
If enough people complain, they will hopefully fix it!

---

### Post by barney_1 on 2006-07-20
The work-around that ylikone posted fixed my youtube sound.  Here's what I did:

Open a console window
```
cd ~
``` to make sure you're in the right directory
```
sudo mv .macromedia ~/Desktop
```to move the directory to the desktop

This will preserve the directory in case you need to set things right again.

---

### Post by ironfistchamp on 2006-07-20
Contacted YouTube and got this response

"Current Issue:

You may find that your volume, mute or resize buttons are missing from your video player. We are aware of the issue and are working to resolve it as quickly as possible. Thanks for your patience!"

Sounds good :D

---

### Post by greggh on 2006-07-20
Youtube is working for me now. Looks like they fixed the bug.

---

### Post by ylikone on 2006-07-20
Yup, fixed.  Back to normal.

---

### Post by fuscia on 2006-07-20
the volume controls are back, but i still have no sound.

---

### Post by ironfistchamp on 2006-07-21
Yep mine seems to work. Fuscia try typing killall esd at the terminal and restarting firefox (I assume you are using firefox). That does the trick when mine goes.

---

### Post by fuscia on 2006-07-21
> **ironfistchamp said:**
> Yep mine seems to work. Fuscia try typing killall esd at the terminal and restarting firefox (I assume you are using firefox). That does the trick when mine goes.

that did it. thanks.

---

### Post by kris2pe on 2006-07-21
Youtube has fixed this problem

---

### Post by the7thlover on 2006-07-23
This may sound carzy, but I was having the same issue as everyone else. System, XMMS sounds were working but no sound from Youtube, Google. However, it had worked once, so i tried to retrace my steps. Checked all my settings XMMS, etc, then logged out and back in. Voila sound!

Try rebooting. Check settings, xmms, etc, youtube, google. If sound does not work in youtube, google, etc., then log out and log back in, and check again. Hope this works for you guys.

---

### Post by ironfistchamp on 2006-07-24
the7thlover I had a problem like that. Have you tried opening a terminal and typing "killall esd" without the quotes. Then open the web browser and try youtube.

---

### Post by ickyb0d on 2006-07-24
> **ironfistchamp said:**
> the7thlover I had a problem like that. Have you tried opening a terminal and typing "killall esd" without the quotes. Then open the web browser and try youtube.


I first did the above suggestion of moving my macromedia directory, then restarting.  that didn't work.  however! killall esd, and restarting the browser worked perfect.  so i'm not sure if it was a combination of the two or just the killall esd.  at any rate, thanks!

---

### Post by ironfistchamp on 2006-07-25
Hehe glad it worked. I have heard a lot of people are unhappy with ESD. I really don't know what the problem is. Just wondering if there is an alternative.

---

### Post by aeto on 2006-07-25
> **kris2pe said:**
> Youtube has fixed this problem

yes and the volume bar is back! :mrgreen:

---

### Post by CitizenUnderdog on 2006-07-25
For what it is worth, I was able to get audio working for both YouTube and Google Videos with the instructions in this thread:
[http://www.ubuntuforums.org/showthread.php?t=180702a]("http://www.ubuntuforums.org/showthread.php?t=180702a")

Specifically the following was the fix for me:

From the Terminal (Ubuntu) (Applications > Accessories > Terminal):
```

sudo apt-get update

sudo apt-get install alsa-oss
```

From Konsole (Kubuntu) (Kmenu > System > Konsole):

```
kdesu apt-get update

kdesu apt-get install alsa-oss
```

Then I rebooted (not sure if this was totally necessary).

Thanks to [Sef]("http://www.ubuntuforums.org/member.php?u=57646") for posting this...

---

### Post by cpmiller2 on 2007-06-27
I had similar problems of no audio on youtube.  I tried the fix posted but it still didn't work.  After MANY hours I found that setting my default audio card finally fixed the problem.  This can be done typing:

sudo asoundconf set-default-card "card name"

For me the card is name is "Audigy2"

If you are not sure what your card name is you can use this command to verify:

cat /proc/asound/cards

After you do that and apply the DSP="aoss" fix above everything should work great.

---

