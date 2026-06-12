---
title: "gtkpod has to be the worst program ever written"
date: 2006-02-27
forum: Absolute Beginner Talk
---

### Post by jbmalone on 2006-02-27
Ok, I had my iPod working with gtkpod then today, I put my iPod in the dock, get ready to sync and get this error:

iPod Database Import Failed: 'Failed to read from file '/media/ipod/iPod_Control/iTunes/Play Counts': Input/output error'

I had so much trouble getting my iPod to work in the first place, that this has me going crazy.  Any suggestions on how to fix this so I can add music to my iPod again?

---

### Post by o_fortuna on 2006-02-27
[QUOTE=jbmalone]Ok, I had my iPod working with gtkpod then today, I put my iPod in the dock, get ready to sync and get this error:

iPod Database Import Failed: 'Failed to read from file '/media/ipod/iPod_Control/iTunes/Play Counts': Input/output error'

I had so much trouble getting my iPod to work in the first place, that this has me going crazy.  Any suggestions on how to fix this so I can add music to my iPod again?[/QUOTE]
I've started using banshee (it's in Synaptic). It allows you to sync with your iPod. It's just way too much of a pain to deal with gtkpod for me too. It always gave me strange errors :???:

---

### Post by Sandlst on 2006-02-27
I've had problems like this as well-it seems on my machine that the ipod sometimes mounts in /media/ipod sometimes in /media/ipod-1 or /media/ipod-0--the fun doesnt stop there though :-k  I have to browse physically to the folder /media and look in all the ipod entries (all three are always there) and make sure the folder ipod_control is there-after doing this, I have to change the mount point in the options area of gtkpod, but if I make a mistake (I usually do) it will give the same error, and then even when I change it to the right mount point it still wont let me read it until I restart gtk-pod......tons of fun-Ill be subscribing to this thread now I think, in hopes of a solution.  Until then, you can do the above provided its the same problem.....although its really, really annoying to do every time.

*EDIT* thank you o fortuna, installing banshee now :)

---

### Post by jbmalone on 2006-02-27
The worst part is that my mount point is correct.  /media/ipod and I still get the error.

---

### Post by jbmalone on 2006-02-27
Oh, and Banshee has never been a good answer for me.  It always locks up and freezes.

---

### Post by Edward The Bonobo on 2006-02-28
Did you load an iTunes database on your 'Pod in Windows/iTunes first?  I needed to do that before gtkpod would read it.

**However**... last night I upgraded from the v0.94 in the Breezy repos to v0.99.2 (from .debs linked from this forum).  Now...it won't read my database again :( 

I've also tried Banshee - but I can't see an obvious way of telling it to read from my iPod.  I was wondering if I need something newer than the version in the repos - but looking at their site, [http://www.banshee-project.org/](http://www.banshee-project.org/), I can't see anything from the screenshots either.  (And their manual is very much "work in progress").  Can anyone tell me what I'm meant to do?

---

### Post by megamania on 2006-02-28
[QUOTE=jbmalone]I had so much trouble getting my iPod to work in the first place, that this has me going crazy.  Any suggestions on how to fix this so I can add music to my iPod again?[/QUOTE]

Gtkpod is far away from my logics too.

I've never tried banshee, but I find yamipod extremely easy to use. You can download it from [www.yamipod.com](www.yamipod.com). There's no need to install, just double-click on the executable and use it.

---

### Post by Zodiac on 2006-02-28
As far as I am concerned, neither is a very good option just yet. Banshee is more user friendly, intuitive and cleaner than GTKpod, but locks up and crashes often.

GTKpod on the other hand doesn't crash or lock up (often) but rarely works as intended, and worse, in my opinion, it still relies on iTunes far too heavily.

If you are thinking about switching to Ubuntu full time and you need your iPod working (or wireless internet for that matter), I would not switch just yet.

Hold off until the tools get a little bit more mature, perhaps in the next release....

If you are using it now and are having problems... well... just pray someone is kind enough to take you under their wing and talk you through your problems for a couple hours. 

Good luck!

P.S. - A good hint for getting help right away is just go into the IRC channel and bash Ubuntu until someone helps you ;)

---

### Post by jbmalone on 2006-02-28
Yeah, I at one point cleaned my iPod out and reinstalled the DB from iTunes to get it working with gtkpod.  I think that, hoenstly, this is the biggest fall back to Ubuntu.  I have tried Yamipod, but the program would never open up, any suggestions on why that is?

---

### Post by megamania on 2006-03-01
[QUOTE=jbmalone]Yeah, I at one point cleaned my iPod out and reinstalled the DB from iTunes to get it working with gtkpod.  I think that, hoenstly, this is the biggest fall back to Ubuntu.  I have tried Yamipod, but the program would never open up, any suggestions on why that is?[/QUOTE]

hmmm, not really:

- download the latest release
- connect/mount your ipod before running the program.
- it may take a while before the program shows up, because it starts reading the ipod folders.

it works ok (only a bit slow) for me. Let me know if you manage to have it working or not.

---

### Post by Edward The Bonobo on 2006-03-01
Has anyone had any problems with databases not being read when going between gtkpod/Yamipod/Banshee?

Although I still can't work out what to click to get Banshee to read my iPod...

---

### Post by jbmalone on 2006-03-01
Yamipod kept on encountering an error last night.  It was saying that my iPod wasn't attached, when it was.

---

### Post by quietglow on 2006-03-01
No there are worse, believe me.

And IMHO, its still the fastest and easiest way to get media on your ipod in Linux--once you get its (rather odd, I admit) workflow down.

---

### Post by jbmalone on 2006-03-01
This is the most frustrating thing ever.

---

### Post by jbmalone on 2006-03-01
fff

---

### Post by %hMa@?b&lt;C on 2006-03-01
banshee works nicely for me and my shuffle
```
sudo apt-get install banshee
```
if you use KDE try amaroK
```
sudo apt-get install amarok
```

---

### Post by angkor on 2006-03-01
[QUOTE=Zodiac]If you are thinking about switching to Ubuntu full time and you need your iPod working (or wireless internet for that matter), I would not switch just yet.[/QUOTE]

:???: 

I've been using Ubuntu exclusively since early Hoary. I managed my ipod with gtkpod and since the last couple of weeks with amarok (1.4 from svn). Gtkpod worked fine for me yet occasionally it gave me an error concerning trouble writing the itunes database. This used to fix it for me (I have a windows formatted ipod):

```
sudo dosfsck -a /dev/sda2
```

Amarok 1.4 works surpisingly well with my ipod, I've been using it for the last couple of weeks and haven't encountered a problem so far.

---

### Post by quietglow on 2006-03-01
> I've been using Ubuntu exclusively since early Hoary. I managed my ipod with gtkpod and since the last couple of weeks with amarok (1.4 from svn). Gtkpod worked fine for me yet occasionally it gave me an error concerning trouble writing the itunes database. This used to fix it for me (I have a windows formatted ipod):



I agree wholeheartedly. I'm a HUGE ipod user. I have music and I currently listen/watch 33 podcasts of which 7 or 8 are video, and I do this all with OSS software. There is a lot of work to be done in getting things to "just work," but my system works pretty well--I'm pretty busy and make a decent test case of what counts as having to be dinked with too much.

In fact, the thing I miss most about itunes is actually the music management functionality. I have ~120g of mp3s so I really need something else taking care of what goes where. I sometimes crack and use itunes under crossover to keep thing in order:rolleyes:

**Note that your ipod must be connected and recognized BEFORE running gtkpod for it to work properly**

Check out our site listed in my sig for more OSS ipod info.

---

### Post by jbmalone on 2006-03-01
Any tutorials on how to get Amarok working with the iPod?

---

### Post by angkor on 2006-03-02
[http://www.ubuntuforums.org/showthread.php?t=80492](http://www.ubuntuforums.org/showthread.php?t=80492)

---

### Post by phen on 2006-03-02
use amarok with gnome! it works. for the ipod to work you might need other kde tools (you can install kubuntu-desktop, but it is rather big). with kde, using amarok with an ipod was all plug and play!

---

### Post by Edward The Bonobo on 2006-03-02
Well now...it looked like last night I'd finally got gtkpod to work.  It read my database and lulled me into a false sense of security.  So I copied some folders over and added some tags.  While I was there, I thought I might as well have a clean up and went through deleting unwanted stuff, re-tagging, etc.  All in all it took me about an hour.  Then I hit 'synch'.

Guess what?  It couldn't see a database/folders to synch to.

By the way...when I do a Read, it uploads at about 3 tracks per second.  Since I have about 1600 tracks, this is nearly 9 minutes.  Should I expect it to take so long? (Over USB, that is).  I can live with it...except if I do anything like adding sort tabs, it starts reading away again.

---

### Post by jbmalone on 2006-03-06
If you are on USB 1 then that is about right.  Today, I plugged my iPod in and everything starting working again.  Weird...

---

### Post by briguy on 2006-03-07
I agree about gtkpod really sucking.  What kind of interface is that?  Plus I couldn't get it to stop crashing.

Sorry for the rant.

---

### Post by Swab on 2006-03-07
[QUOTE=jbmalone]Ok, I had my iPod working with gtkpod then today, I put my iPod in the dock, get ready to sync and get this error:

iPod Database Import Failed: 'Failed to read from file '/media/ipod/iPod_Control/iTunes/Play Counts': Input/output error'

I had so much trouble getting my iPod to work in the first place, that this has me going crazy.  Any suggestions on how to fix this so I can add music to my iPod again?[/QUOTE]

I suggest making a donations to the gtkpod project...

---

### Post by Edward The Bonobo on 2006-03-07
I've finally got gtkpod to read from and synch to my iPod...mostly.  I often get error messages, as described by everyone above.  All I do is unplug the iPod and plug it back in again.  Eventually it works.  Ignore the 'Do not disconnect' message.  It doesn't seem to do any harm.

---

### Post by jbmalone on 2006-03-07
I don't know if I would feel comfortable doing that.  I would be more likely to donate to Ubuntu or some larger program that has proven success.

---

### Post by joncheyne on 2006-04-14
[QUOTE=jeffc313]banshee works nicely for me and my shuffle
[/QUOTE]

Is is fast? I have got gtkpod to work after much huffing and puffing and reformatting etc ](*,)  and am loathe to break the spell only it takes 15-25 minutes to sync after adding and deleting maybe 20 songs. 

I odn't recall it being that slow when windows was on here.

?

Jon

---

### Post by JungleBeast on 2006-04-19
Nice to know there are other people out there having the exact same problems as me! ](*,) ](*,) 

it's not really just the gtkpod software though.. i've stuck with it, sorted getting it to mount properly and all that, i've got sudo eject /dev/sde2 thing down.
I open gtkpod using sudo gtkpod &     I've completely reformatted my pod twice now using the firmware on windows. installed the basic files with both itunes and gtkpod systematically.     i've even chown'ed the files on there and all that, and i've used sudo dosfsck -a /dev/sde2   quite a few times , which was quite interesting. 
But at the heart of it I still get this  "  Input/output error  "   every once and a while! which then locks things up.   I find i can avoid this (most of the time anyway) by only uploading 4 directories or less, or maybe that's just statistics.
Out of frustration i installed amarok.   nice piece of software, works perfectly, lots of bells and whistles, but when i try and synch the ipod, again i get a "Input/output error" so it's not just gtkpod. 

So any ideas all you ipod owning linux gods out there?   It's a recurring problem, i've been recognising the same names in the forums with this same problem. JBMalone and ed the bonobo are just a couple i remember cropping up again and again.   and i'm sure they're the ones with the most patience who haven't just booted back into windows then itunes.    (Exactly like i'm about to do...)

So any ideas before i give up completely? :confused:

---

