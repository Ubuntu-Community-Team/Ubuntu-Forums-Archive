---
title: "Flash, Google vid, YouTube, audio works... doesn't work, etc."
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by Carbonfish on 2006-08-18
Hi again all,

Well, I thought that I had the audio problem licked after following the step-by-step in the Restricted Formats wiki, but no such luck. I installed Automatix about a week ago and thought that I had all of the commonly needed codecs etc. installed for good and all, but I go to various places with the type of content that I wish to view (You Tube, anyplace with flash video, Google video etc., and everything works. Then I shut down and move on with my life and a couple of hours later, no sound in certain media types.

I don't get it. I thought that by making the changes in the terminal that I would solve this, but I guess not.  ](*,) 

If anyone could point me in the right direction I would greatly appreciate it.

Oh yeah, is there any way to see what Automatix has installed besides the log file, or better yet, how do I see what is currently installed generally as far as my multimedia stuff is concerned?

Thanx,

Kent

---

### Post by Carbonfish on 2006-08-18
Anybody want to take a shot at this??

No?

KC

---

### Post by p.i.m.p on 2006-08-18
hey.. this is my first shot at ubuntu and i managed to get everything working by following the unofficial ubuntu guide using apt-get

[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

---

### Post by tralfaz on 2006-08-18
Me too.
I have been fooling with this for a couple weeks and have failed to get any embedded media to play. period. Mplayer, for instance, will look like it is doing something, but after loading the file, firefox crashes. I too went the Automatix route, but I haven't had any success (I was able to get an internet radio station to work that wouldn't before). This, more than anything, has been frustrating in the process of using Ubuntu. It has breathed new life into my G3 iMac 400DV, but I have to go elsewhere to look at video content.

---

### Post by toykilla on 2006-08-18
I am in the same boat:

[http://www.ubuntuforums.org/showthread.php?p=1396192#post1396192](http://www.ubuntuforums.org/showthread.php?p=1396192#post1396192)

---

### Post by Carbonfish on 2006-08-19
Well, like I said in the first post, I got most (all I think) of the embedded *video* to play, mostly by first using Automatix, and then when that didn't fix everything, and after doing a bunch of reading, I went through this:  [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

and this:   [http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

with a fine tooth comb, and was able to get the video *and* audio working for pretty much everything I tested. But then, I would shut down and when I restarted, nine times out of ten, the audio in some things wouldn't work anymore, while the audio in others would work fine. If I went back to Automatix and had it attempt to re-install the "most commonly needed plug-ins and codecs", it would and everything would work again. But if I look in the Automatix install log, it makes me look like I have alzheimers or something because it shows that I am  installing the same packages over and over. 

I'll be dipped in Ubuntu if I can figure out what to do next.

I'll take any and all suggestions seriously (except the ones that are crazier than the ones I have contemplated).

Thanks again fo your support and feeling my pain,

KC

---

### Post by tralfaz on 2006-08-19
Well, I tried the unofficial guide. I had most everything already installed. When adding a repository something went wrong and I cannot get Add/Remove to open at all. The error message:

[B]Malformed line 33 in source list /etc/apt/sources.list (dist)
[/B]

I figured out how to look at the file with a text editor, but I don't know how to make the changes (it won't let me save it in the text editor). This is where I truly need some help. How do I get into the sources.list so I can delete or make them comments?

[COLOR="Blue"]FOUND THE ANSWER:sudo gedit /etc/apt/sources.list[/COLOR]

Line 33 (and 34):
[B]deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf)
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf)[/B]

> **p.i.m.p said:**
> hey.. this is my first shot at ubuntu and i managed to get everything working by following the unofficial ubuntu guide using apt-get

[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

---

### Post by Carbonfish on 2006-08-19
The same thing happened to me. Don't *worry*! I just took a deep breath, and opened the source list with gksudo gedit, and removed that line (or you could just comment it out if it makes you nervous to remove it). That should take care of the warning and allow you to open Synaptic, or add/remove or whatever you want. After I removed the offending line, I restarted to make sure that the change "took". But I don't know if that is really necessary.

I panicked when it happened, but it was a straightforward fix to just remove the line it says is "Malformed".

KC

---

### Post by Carbonfish on 2006-08-19
Bump.

Okay, back to business. Anybody have any insights into a fix for this intermittent sound problem?  :confused: 

It seems sort of silly to have to re-install the plug-ins/codecs evey time I restart my laptop. It is a *laptop* after all. I turn the thing on and off about 30 times a day.

I would be thrilled if anybody has an answer to this issue. I'll even take guesses!

Kent

---

### Post by Carbonfish on 2006-08-19
I'll bump this for the last time today. I hate to resign myself to thinking that this problem is beyond the combined resources of the entire Ubuntu Community. While I realize that we are in part, limited to the tools that are made available to us by the proprietary nature of the plugins and other software needed to make some of these things work, I still find it a bit inconceivable that I cannot install the codecs and plugins that *are* available to the OS community and have them work repeatably.

I am left in the uncomfortable position of not knowing whether I am just not being thorough, or whethter this is a problem that is not yet solvable in this iteration of Ubuntu.

I don't consider myself to be a *terribly* needy person, but a little positive reinforcement would be welcome.

If I don't hear from anybody today I'll bump this once more tomorrow and then I'll probably give up...

Sad.

Kent

---

### Post by armandg on 2006-08-20
go [here]("https://help.ubuntu.com/community/FirefoxAMD64FlashJava") and do "10 - Check if your new Firefox is working with flash"
worked for me! =)

---

### Post by Carbonfish on 2006-08-20
> **armandg said:**
> go [here]("https://help.ubuntu.com/community/FirefoxAMD64FlashJava") and do "10 - Check if your new Firefox is working with flash"
worked for me! =)

Thanks, Even though I don't have a 64 bit processor I'll try it.   ;)  At this point I'll try about anything.

KC

---

### Post by septikus on 2006-08-21
I've had similar problems with Flash streaming videos (like youTube and Google Video) working but the sound will randomly not work. I have found a solution although I'm still looking for a more permanent solution. 

If you go here: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

There is one part where it says to get sound working you need to do this:
```
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

ln -s /tmp/.esd-1000 /tmp/.esd
```

The first line you probably do not need to do as the link doesn't disappear. But I've found that the second line will work sucessfully (meaning the link didn't exist before and was created) after reboots and such.

Anyways I've found that executing that second line and then killing firefox (waiting a few seconds) and bringing it back up will get the sound working for that session. 

Don't know if this will work for you but let me know if it does. I'm still looking for a more permnanet solution then having to type that into the terminal each time.

Good luck!

---

### Post by CanonD on 2006-08-21
not sure if this has been posted, in this thread, but i followed the directions in another thread about a week ago to get it working.

in the terminal:

sudo gedit /etc/firefox/firefoxrc

replace: 
FIREFOX_DSP-”none”

with:
FIREFOX_DSP-”aoss”

---

### Post by Carbonfish on 2006-08-21
Hi CanonD and septikus,

I have tried both of those "fixes" without getting a positive outcome. That's the frustrating part about all this. I seem to be chasing my tail. I have just about every wiki and how-to there is (that I know about) bookmarked, and have been through them all what seems like a hundred times.  ](*,) 

I'll keep at it though. ;) 

When I started down this road, I did it with the intention of learning a some of the benefits and limitations of OSS. *It's working!!* Ha, ha.

Anybody with more suggestions please chime in.

Thanks, 

Kent

---

