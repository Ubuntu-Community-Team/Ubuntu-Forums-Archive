---
title: "New 5.10 install, grinds to a halt after 6-8 hours?"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by bigkahuna on 2006-06-03
This is kind of wierd and dissappointing:

I did a fresh install of Ubuntu 5.10, including connecting to my DSL router modem and samba network to my Windoze box last week.  My Ubuntu box is a Sony Vaio, AMD Duron notebook with 256 MB RAM and I gave it a 7 gb partition with 500 mb swap space.  I previously had Kanotix (Debian Sid) installed on it without any real problems.

When I ran Ubuntu, it did the automatic update thingy (cool) and so I'm guessing I'm as up to date as can be.  The only applications I use are Firefox (latest) and Thunderbird (latest) both installed from the repository. 

My daily routine is to boot up Ubuntu first thing in the morning and leave it, Firefox and Thunderbird running all day.  The problem I'm having is that by the end of the day, everything seems to slow down to a grinding halt.  Firefox and Thunderbird become unresponsive and I can't switch desktops in Ubuntu.

Is this normal for Ubuntu?  Seems awefully unstable, is there some way of fixing this?

---

### Post by Nano Geek on 2006-06-03
You should try Ubuntu 6.06. It just came out a couple days ago and it's pretty cool.

---

### Post by bigkahuna on 2006-06-03
Well, before I install a new OS, I'd rather know if this sort of thing is normal for Ubuntu.  If every 5.10 user has the same problem that I do, I doubt very much if there'd be so many users.  I guess my point is this:  is there a "memory leak" issue in 5.10 or perhaps the Ubuntu version of Firefox/Thunderbird?  Or has Ubuntu grown so much that it no longer can be run effectively on a 3 year old machine?  I mean this is a brand new, clean install and the only apps I'm running are Samba, Firefox and Thunderbird.  Pretty simple and clean IMHO.

I use Linux for 2 reasons:  stability and security while using the internet.  If I can't rely on Ubuntu for 1 of those two reasons, perhaps it's time for another distro?

If that's the case I'll be sorry, but I'll make the change.  I love the Gnome look of Ubuntu and the community, but this problem is a major issue for me.

---

### Post by Nano Geek on 2006-06-03
I would try doing a clean install of Dapper on your computer, just make sure that you backup your data in case anything goes wrong. I have used Thunderbird before and I use Firefox alot on my computer and have never had a problem. If it keeps doing that you could try using Evolution insteed of Thunderbird and see if it makes a diffrence.

---

### Post by skinnygmg on 2006-06-03
installing a new os is not the answer here.  something is configured wrong, or something like that.  i have a similar laptop w/out this problem.  do you have a broadband connection, and maybe a bittorrent client running?  or any p2p software?  do you leave thunderbird open?

---

### Post by bigkahuna on 2006-06-03
Ok, I'm back with a quick update and some info:

Against my better judgement (nobody to blame but me) I went ahead and updated to Ubuntu 6.06.  Didn't get any error messages along the way, but after the first reboot I launched Thunderbird, checked mail, launched Firefox, loaded a couple pages and -CRASH-!  The entire system locked up solid... argh...  I've just rebooted and am going to give it a bit more of a workout before I start "sweating bullets".

To answer your questions, I'm not running any other software other than Samba (to network eth1 to my Windows machine, eth0 is connected to my ADSL router/modem), Thunderbird and Firefox.  That's it, nothing else.

I switched from Evolution to Thunderbird because that's what I've been using for the last couple of years (T-bird that is), never had any problems with it before this (although I was always using KDE, not Gnome).

I'm gonna give this a bit more time, but if it crashes like that again, sorry to say but I'm gonna dump Ubuntu.  I know how hard it is and how long it can take to track down an elusive problem like this.  Usually a clean install will fix this, but since I only installed this on a clean hard drive a week ago (and I did a full upgrade to 6.06 just minutes ago), I'm not real excited to go through all that again... and if I have to do it again, it'll probably be with a different distro...

---

### Post by nanotube on 2006-06-04
from your symptoms, sounds like it could be a memory problem. try running memtest (from the grub menu)?

also, to see what processes are using up resources, you could fire up a terminal and type "top"
or you could use the gui-based system monitor (find it in the menus. i'm running breezy, so don't know where they hide it unded dapper :)

---

### Post by bigkahuna on 2006-06-04
Thanks nanotube, I'm running the system monitor as I'm typing this ;)  Yeah, I agree that the problem behaved like a memory problem, but since I didn't have that problem before I assumed that it was a software problem.  I'll run memtest just to make sure.

I've got about 30 minutes with 6.06 so far... no crashes yet (fingers and toes are crossed).  I've got to admit that Ubuntu, and now 6.06, is one of the prettiest distros I've ever seen.  I'm definitely a visual-oriented kind of guy, so I like the new look.

I'll post again with an update after I've had a change to give it more of a work-out.

---

### Post by Raavea on 2006-06-04
Just thought I'd add a little note: My PC is pretty old, re-built it except for good ol' Bernard *pats her original HD* about two to four years back, and I haven't had any crashes.

 I do occasionally have some sort of odd glitch where Firefox closes. But I think that's part of my 1.5 install of FF, rather than the system, and I have a little memory graph and the crashes never involve high usage... I've confused myself.

 My point was: I'm pretty sure it should work fine on even very very old PCs. *nods sagely*

EDIT: If you like pretty things, might I point you to my website? Recently uploaded three shots of my secksie set-up. (You can find the link in my profile if you wish, I don't want to spam...)

---

### Post by skinnygmg on 2006-06-04
sounds like this guy is working on the same problem, and he thinks it may have something to do with python

[http://www.ubuntuforums.org/showthread.php?t=188322](http://www.ubuntuforums.org/showthread.php?t=188322)

btw, the eyecandy in kubuntu is suposed to be nicer.

---

### Post by bigkahuna on 2006-06-04
Thanks for the link to the thread skinnygmg, sounds like I'm not alone...

Latest update:  I have yet to run my system for more than a couple hours, but will try to leave it running today to test it.  The initial crashes were pretty wierd, but I think that might be related to my hardware.  While using Kanotix (Debian Sid & KDE) the sound drivers wouldn't load correctly if I didn't do a cold boot (power off / on) and the power management drivers seemed a bit flakey (I attributed that to the fact that my notebook's battery is dead, so I only use the system when it's plugged in).  Yesterday, the sound drivers didn't load and then a few minutes later the system locked up.  I did a cold boot, and the sound drivers loaded correctly and everything seemed to work fine for maybe 5 hours or so.  This morning, when I powered up, the sound drivers loaded correctly and, for the first time since I upgraded to Dapper, the power management icon appeared.  I'd almost rather disable power management since I have no plans to ever run this thing off a battery, but that's a task for another day.  Everything seems to run OK so far today.

As far as Gnome vs KDE goes, I've spent some time with both and I just like the look of Gnome better (even though I think KDE is in some ways more complete).  Gnome has more of an "artsy" feel to it.

---

### Post by bigkahuna on 2006-06-05
Ok, last post on this topic.  I ran my system for about 10 hours yesterday, no problems to report.  I've already run it about 3 hours today, some slowing but no more than I might expect.  It appears that whatever the problem was, it's gone and my Ubuntu 6.06 install seems to be working OK.

So the moral to the story for me was to upgrade to 6.06...

---

### Post by [HUN]Levente on 2006-06-05
Same problem here, 5.10, after 2-3 days it slows down, and after about a week it slows down so much, that only reset helps... I thought it could be Firefox, because I often have 20-25 tabs open, but next week I install 6.06, and I hope it solves the problem, because it's quite annoying...

---

### Post by djheadley on 2006-06-05
I'm running Breezy on a 433mhz Celeron and the only time my machine slows down is when I've been on the net for awhile, and my machine is on 24/7.  About once a day I boot into Windows for some games I haven't gotten to run under wine and haven't found suitable replacements.  BTW as soon as I get off the net, everything returns to normal.

---

