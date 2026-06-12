---
title: "Scheduled wake up call"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by onegreenparker on 2007-04-19
I've checked the crontab HOWTO's on a few sites, played with all sorts of option, made sure that I am using my own crontab, played a little with /etc/crontab all woithout success.
I lie, /etc/crontab run my mount/unmount scripts just fine.

However, what I am really trying to do is start either sound-juicer or rhythbox and play some tunes at 6am; you know as a wake up call. No matter what I have tried, i've had no success.

Perhaps crontab is the wrong direction?

I am running 6.06, installed from disk, no additions (no network at home yet)
:confused:

---

### Post by kidders on 2007-04-20
Hi there,

> **onegreenparker said:**
> However, what I am really trying to do is start either sound-juicer or rhythbox and play some tunes at 6am

As you probably know, getting cron to start applications that need access to X can be quite difficult. How are you handling it? (Perhaps you've overlooked something.)

> **onegreenparker said:**
> i've had no successCan you be more specific? What kinds of messages does cron throw at you?

---

### Post by Nik_Doof on 2007-04-20
Possibly one way (not sure with sound-jucier or rythm) is to run a start/stop command via the API, in Amarok for example you can do a DCOP call to make it play, ala:

> dcop amarok player play

No faffing with X sessions or anything :)

---

### Post by kidders on 2007-04-20
Assuming someone was logged in at the time, that would be a nice option. :-) Got to love dcop!

---

### Post by marko_4454 on 2007-04-20
Thats the way I wake up as well :)
It works awesome! 
I actually have a script though. Hopefully I remember to post it here once I get home.

---

### Post by marko_4454 on 2007-04-21
> **onegreenparker said:**
> I've checked the crontab HOWTO's on a few sites, played with all sorts of option, made sure that I am using my own crontab, played a little with /etc/crontab all woithout success.
I lie, /etc/crontab run my mount/unmount scripts just fine.

However, what I am really trying to do is start either sound-juicer or rhythbox and play some tunes at 6am; you know as a wake up call. No matter what I have tried, i've had no success.

Perhaps crontab is the wrong direction?

I am running 6.06, installed from disk, no additions (no network at home yet)
:confused:

OK, so this is my script:

```

#!/bin/sh                                     #Indicate script
export DISPLAY=':0.0'               #Feel free to change if you use Beryl
amarok &                                      #start amarok if its closed/maximizes if its open
sleep 30                                        #leave 30seconds to start amarok
amarok --play                              #let the music start!!!
sleep 10m && vlc /usr/share/sounds/k3b_success1.wav    #second wakeup call....its the military
                                                                                                          #style wakeup song (with trumpet)


```

---

### Post by jiminycricket on 2007-04-21
I think Kalarm can do this sort of thing too, if any newbies reading this aren't really sure about cron.

---

