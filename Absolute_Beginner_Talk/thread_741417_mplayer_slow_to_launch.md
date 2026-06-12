---
title: "mplayer slow to launch"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by uncannybuzzard on 2008-03-31
i'm running a p4 2.x box with mythtv running over gnome. i recently upgraded my video card. i uninstalled the nvidia drivers via Envy and replaced the card, reinstalled via Envy, blah blah. now, when i launch a video from myth or from the CLI, it lags about 10-20 seconds before it show's up.

when launching from the CLI, it hangs right after the line about gnome-screensaver being disabled. it appears as though ffmpeg is taking a long time to load, though i can't be certain.

any ideas?

---

### Post by eMxyzptlk on 2008-04-03
I have a similar problem, I'm running up-to-date Hardy, a couple of days ago mplayer started to have this weird behavior, it takes too long to start, hangs right after disable gnome screensaver...

I tried to debug it but I gave up, I created a test user, under that user it works nicely so i figured it's something in my environment, I removed .zshrc and .zlogin as well as .mplayer folder and it still hangs, the 2 users are members of the same groups, I can't figure out what's wrong!!

any ideas ??

---

### Post by Crafty Kisses on 2008-04-03
It could be a resource issue, post the following output:
```
top
```
Also how much RAM do you have?

---

### Post by eMxyzptlk on 2008-04-04
No it's not, it's something that's hanging.... The proof is that when I launch mplayer from the command line and it reaches the step where it hangs, I just hit Ctrl+C and it starts immediately, so mplayer tries to check something and it freezes on it, I can't figure out what though, but I know it's between Disabling the Gnome screensaver and activating the VO....

Oh and i have 1Gb RAM

---

### Post by uncannybuzzard on 2008-04-04
my problem has spontaneously cured itself. i read some other thread where the same thing happened to someone else, except his thread never got any replies.

i didn't really do anything at all as far as i know. the only thing i can recall was chmodding the .mythtv directory in ~ to 777 (since i didn't notice that prescaling wasn't being cached. i just thought it sucked).

yeah, this is definitely not a resource problem. nothing is running in top or processes for that matter that is out of the ordinary when this happens. i've had this happen once before and i ended up reinstalling the OS since i simply could not abide by xine as the myth player.

---

### Post by uncannybuzzard on 2008-04-04
> **eMxyzptlk said:**
> No it's not, it's something that's hanging.... The proof is that when I launch mplayer from the command line and it reaches the step where it hangs, I just hit Ctrl+C and it starts immediately, so mplayer tries to check something and it freezes on it, I can't figure out what though, but I know it's between Disabling the Gnome screensaver and activating the VO....

Oh and i have 1Gb RAM

are you using ffmpeg for codecs?

---

### Post by eMxyzptlk on 2008-04-06
No, I'm not, I'm using w32codecs...

---

### Post by eMxyzptlk on 2008-04-06
> **uncannybuzzard said:**
> i'm running a p4 2.x box with mythtv running over gnome. i recently upgraded my video card. i uninstalled the nvidia drivers via Envy and replaced the card, reinstalled via Envy, blah blah. now, when i launch a video from myth or from the CLI, it lags about 10-20 seconds before it show's up.

when launching from the CLI, it hangs right after the line about gnome-screensaver being disabled. it appears as though ffmpeg is taking a long time to load, though i can't be certain.

any ideas?

Could you try adding
```

stop-xscreensaver = no

``` to your ~/.mplayer/config ?? it worked for me on Arch Linux, I had the same problem and disabling the stop-xscreensaver worked....

---

### Post by uncannybuzzard on 2008-04-09
yeah, i added that just to be certain. however, the problem went away on it own :|

---

### Post by MonkeyZiggurat on 2008-04-17
I have exactly the same problem. Mplayer also used to give me an error dialogue whenever I launched a movie or changed aspect ratio and also when a movie came to an end. added the line mentiond above to my .mplayer/config file and that got fixed, but I still have the delay when opening up a movie. It's not the end of the world, but is a bit annoying.

btw, it says [SOLVED] in the title, but "the problem went away on it's own" doesn't seem like a viable solution to me. at least it's not one I can use ;-)

---

### Post by uncannybuzzard on 2008-04-18
fair enough

i still think it's something to do with an ffmpeg loading delay

---

### Post by MonkeyZiggurat on 2008-04-18
Sorry, didn't mean to sound like a sniffy bitch back there. As it happens, I am using ffmpeg, and all the other **** related to it. (I just searched in synaptic and saw a bunch of stuff to do with ffmpeg as well as the core package installed on my system) what do you reckon's a decent alternative?

---

### Post by 7/9 on 2008-04-23
> **eMxyzptlk said:**
> Could you try adding
```

stop-xscreensaver = no

``` to your ~/.mplayer/config ?? it worked for me on Arch Linux, I had the same problem and disabling the stop-xscreensaver worked....

This solved the problem in my case. However, I still have no idea what caused it in the first place...

---

### Post by sunitram on 2008-04-28
Hi, I have the same problem, here is what really happens (and how to find out):

I have started mplayer with **strace mplayer test.avi**. This shows that mplayer is hanging with something like

```
waitpid(8865, 
```

So its waiting for another program. Quickly run **ps faux** in another window and you'll see that the program it is waiting for is

```
sh -c dcop kdesktop KScreensaverIface isEnabled 2>/dev/null | sed 's/1/true/g' | grep true 2>/dev/null >/dev/null
```

So mplayer tries to disable the KDE screensaver. When you run **dcop kdesktop KScreensaverIface isEnabled** in the console you get the error message ```
DCOPClient::attachInternal. Attach failed Could not open network socket
``` A quick google for this message and you will find that the socket problem is because **dcopserver** is not running (it does not matter if kdesktop is installed)

So long story short, start **dcopserver** and the problem goes away :-)

---

### Post by arnab.bhaumik on 2008-05-06
stop-xscreensaver = no


worked for me ...................

had the same problem suddenly but this saved my day

arnab/vu2bpw

ps.- ubuntu linux is my primary os now for the last 4 years.......

---

### Post by neutro on 2008-05-12
Note to people attempting the fix: it's ```
stop-xscreensaver = "no"
``` (with the quote marks) in ~/.mplayer/config; and if like me the problem also affects gmplayer, you have to replace the yes for no in ~/.mplayer/gui.conf, where the option is written as ```
stopxscreensaver = "no"
```

Is that something which should be considered a bug and filed on launchpad? Was that already filed?

---

### Post by bryan.taylor on 2008-05-12
[quote=sunitram]A quick google for this message and you will find that the socket problem is because dcopserver is not running (it does not matter if kdesktop is installed)

So long story short, start dcopserver and the problem goes away[/quote]

Ok, so I wrote a little script to start and stop dcopserver when you run mplayer.  I just changed /usr/local/share/applications/mplayer.desktop so that it executes the script.

```
#!/bin/bash

ps -ef | grep dcopserver | grep -v grep 2>1 >/dev/null
if [ $? -eq 0 ]; then
        echo "dcopserver running"
else
        echo "dcopserver not running"
        dcopserver
fi

if [ $# -eq 0 ]; then
        echo "running gmplayer with no arguments"
        gmplayer
else
        echo "running gmplayer with $# arguments"
        gmplayer "$@"
fi

echo "killing dcopserver"
killall -9 dcopserver
```

It makes mplayer much more responsive.

---

### Post by mc-rpg on 2008-06-06
In MPlayer>Preferences>Misc Disable "Stop XScreenSaver"

That's suppose to stop the screensaver to show while you are watching a movie but if you're suffering from this delays at startup it doesn't seem to be working since MPlayer can't find it:

> xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled

---

### Post by ajopaul on 2008-06-26
> **bryan.taylor said:**
> Ok, so I wrote a little script to start and stop dcopserver when you run mplayer.  I just changed /usr/local/share/applications/mplayer.desktop so that it executes the script.

```
#!/bin/bash

ps -ef | grep dcopserver | grep -v grep 2>1 >/dev/null
if [ $? -eq 0 ]; then
        echo "dcopserver running"
else
        echo "dcopserver not running"
        dcopserver
fi

if [ $# -eq 0 ]; then
        echo "running gmplayer with no arguments"
        gmplayer
else
        echo "running gmplayer with $# arguments"
        gmplayer "$@"
fi

echo "killing dcopserver"
killall -9 dcopserver
```

It makes mplayer much more responsive.
starting dcopserver helped, realised this delay recently after installed Kubuntu..

---

