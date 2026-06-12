---
title: "Need a road map"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by maddmic on 2008-02-07
Ok all, I'm not foreign to Linux, but everything in the past has been work related and was long ago.  Therefore, I need some advised on which direction to proceed in.

I have read on here in some threads that there's a bit of concern with the stability of 7.10.  Being somebody who needs documentation for assistance and would like a very user friendly approach to Linux, would I be better off loading 7.04?

My current machine is an oldie, as I don't want to drop this on my "main" machine until I'm certain I can get all of my windoze apps to run correctly.  So, the machine I'm going to run this on is an XP1800 with 1GB of ram and an FX5200.  Basically I want this machine to house our movies for playback in H264 format since my 2.5 year old daughter LOVES to handle the DVDs I make for her.  I'm tired of making backups of her movies because she scratches them and would prefer for them to be in a format that she can't physically touch.

I am enamored with LinuxMCE, but the router issue is not practical for me at this point in time.  Therefore, I believe what I would like is a functional file server/media repository/sandbox that I can play around in w/o messing anything up too badly.

Now, the reason I ask about the versions is because I have had some issues with 7.10.  Well, one particular issue.  I read about streaming video and the flash update for YouTube, etc.  The problem is that after installing the flash update, whenever I visit YouTube, it causes my system to become really unresponsive.  As clicks are recognized after about 5 or 6 minutes if ever.  Is this a result of my hardware, YouTube, or my choice in OS combine with my hardware?

On a side note, once I get these things ironed out, I'll be getting a SUN raid array that I'll be installing, so I'll be heading back here for help on that too.  :)

---

### Post by maddmic on 2008-02-07
Ugh....I forgot to add this to the book above.  I'm having an issue with adding the universe and multiverse repositories.  

I saw this:  [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

But it looks as though that's for 6.06 and 6.10.  I went ahead and tried to follow it and my screens look nothing like those in the examples (I know, different versions, etc....)  So, i'm guessing that the only way to do it would be via command line?

[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

I know, I'm such a n00b.  Any assistance would be greatly appreciated.....

---

### Post by kesman on 2008-02-07
For the repositories, in 7.10 go to system -> administration -> software sources and check every one of them and remove cd-rom if it's still there. In 7.06, I'm not sure, but it's easy to edit the sources.list manually. All you have to do is open up terminal and:
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list-back

```
to make a backup just in case... Then:
```

sudo nano /etc/apt/sources.list

```
and remove the # -characters from the universe and multiverse lines. After that, hit ctrl+x to exit and answer yes to save the file. Then update the apt-cache with:
```

sudo apt-get update

```
And you're done!

---

### Post by laidback on 2008-02-07
I have recently installed 7.10 on an old Athlon XP1800 socket A (I think) 768Mb Ram, 2x ATI Graphics card (shared memory) for a friend to borrow. It doesn't run Compiz but so far everthing else seems fine. BBC iplayer, mp3s, you tube, ipods (Amarok) etc. I do find that you tube hangs up on me, but this happens on my main machine too. It's as I try to back out of a video once it's finished. Sometimes Firefox just looses the plot and spins doing nothing. I've found that I need quite a pause before attempting a back arrow click once the video has finished.  Shutting down FF and restarting seems to help too, next time it's more friendly. I installed the extra Codecs via Synaptic, Real player for the BBC iplayer option. It even allows me to adjust the screen size in the BBC iplayer, not an option that I have on the main pc as it's still running 7.04 most of the time. If I put my 7.10 play installation on the main pc then BBC iplayer does allow screen size adjustment. Think this is due to an updated version of the plugin.
So I'd say it's stable, at least that's my impression. I'm so pleased with it I'm thinking of upgrading my day to day 7.04 version to 7.10. Compiz is such fun, boot times are good and shutdown is really quick.

---

### Post by maddmic on 2008-02-07
Can I get a brief description of Compiz?

When I say I've been out of touch, I mean since like 2002ish.  :)

---

### Post by Whiffle on 2008-02-07
Compiz makes pretty animations on your desktop.  Search for them on youtube, a video is worth a gazillion words.

I'm actually using 7.04 because I had an initially very poor experience with 7.10.  7.04 is pretty much flawless on my laptop though, runs like a top.

---

### Post by laidback on 2008-02-07
Compiz is desktop eyecandy, rotating cubes ( or more complex forms, it depends on how many workspaces you have ) plus many more magic tricks. I didn't find it worked on my pc in 7.04 but it's flawless in 7.10.

---

### Post by emarkd on 2008-02-07
Most of the problems people have are caused by hardware that isn't Linux-friendly, usually video or wireless.  Have you tried the 7.10 Live CD?  If that works for you, you should be ready to go.  Even if it doesn't, you can often install from the alternate CD and then enable a few restricted drivers.

For what it's worth, I have a 9 or 10-year old desktop that I *think* has a 900 Mhz processor and 512 MB ram running 7.10 + MythTV as my Media Center.  It gives me zero problems.

---

### Post by laidback on 2008-02-07
Update to above comments on YouTube. I've just run through my 3 systems again and can report that 7.10 runs You Tube more reliably than 7.04. I can also get full screen in 7.10, I can't in 7.04 (same pc, identical equipment). Pause and go works in all systems. Stopping a video half way through and backing out to previous screen works fine in 7.10, not always in 7.04. The most reliable seems to be on my old Socket A Athlon 1800 XP system. I just couldn't trip that up no matter how hard I tried.
I think emarkd has a good point, your hardware probably has a marked bearing on performance. But if I had to choose, I'd go for 7.10. I often wonder whether the order in which things are installed can have a bearing.
emarkd: interesting to read about your MythTV, thanks for that.

---

### Post by maddmic on 2008-02-07
Thanks all for the replies thusfar.

I have though that there was an issue with the hardware.  Perhaps the video card.  Maybe I'll change her out this weekend and see what happens.  It's an XFX fx5200 w/ 128 ram.  Problem is the next best thing I have is a ti4600 w/ 64 ram.  

So then, Compiz is desktop eye candy?  Somewhat like Beryl?  The first time things locked up was after I turned on the "magic".  So I turned all of the special magic graphics off and still locked.  As for the live CD, things worked great.  In fact, its not a problem with the OS at all I don't think.  It's just streaming video sites I believe.  Unless I'm mistaken, there's really no way to check this out on the live CD though because I need certain plugins for FF to be installed before I would even be able to see the video, correct?

---

### Post by laidback on 2008-02-08
On my 7.04 system Compiz doesn't work properly. So I disabled it as it caused havoc with the screen. On 7.10 it works wonderfully well on the same hardware. Yes it's a combined Beryl and old Compiz, as I understand it anyway. If your current graphics card doesn't like it there's no reason to install it. When I installed 7.10 on the old socket A system Compiz just didn't get installed at all, guess the AGP 2x graphics card just isn't up to it. No problem run without.

---

### Post by maddmic on 2008-02-13
Well......update time.  Things are rolling along pretty well.  Still struggling with the streaming issue and having some difficulty setting up a DVD ripper to be "one-click easy".  Anybody have suggestions on that front?

I currently have K9copy, Acid, and am trying the VLC thing right now.  Thoughts?  Ideas?  Opinions?  Hints?  :)

---

