---
title: "New Electric Sheep Client, 2.7 beta"
date: 2008-06-11
forum: Art &amp; Design
---

### Post by spotspot on 2008-06-11
Dear Users,

For the past couple of years I have been primarily working on the High Fidelity end of [Electric Sheep]("http://electricsheep.org").  Development of a so-new-it's-incompatible version of the free screen-saver has gone on behind the scenes.  Finally version 2.7 is in public beta, and Ubuntu is the primary platform.

Get it [here]("http://community.electricsheep.org/node/237").

Reports of any problems or bugs as well as successes are most welcome.   Thanks!  You can comment on either forum, or send [me]("http://scottdraves.com") email.

We have noticed that sometimes mplayer and electricsheep processes get left hanging and blocking it from working.  Killall -9 these processes somestimes fixes it.  Or restarting the X server...  we don't know what's going on yet, so if you are capable, please poke around and let me know what you think the problem is.  Thanks.

You can browse the [new flock]("http://v2d7b.sheepserver.net/cgi/status.cgi") here even without the client.  Note that this flock is at 1/10th quality since there are hardly any users yet.  I'll crank it up as people join.  The advantage of few users though is it starts in seconds :)

Main improvements are: a more expressive visual language, a dynamic filter in the renderer to smooth out the dust, and h264 of double the pixels per sheep (800*600*160/(640*480*128) = 1.95).

Thank you so much, -Sp0t

ps.  credits are all the [web page]("http://electricsheep.org/index.cgi?&menu=credit") but special shout-outs to keffo sandberg, erik reckase, and daniel summer for this release.

---

### Post by EReckase on 2008-06-27
Note that there is now a Launchpad repository for the electricsheep and flam3 packages!  Simply add this apt source to sources.list or using the synaptic package manager:

deb [http://ppa.launchpad.net/flam3/ubuntu](http://ppa.launchpad.net/flam3/ubuntu) hardy main

Update your package list, install electricsheep, and go!

--Erik

---

### Post by Windsurfer619 on 2008-06-28
Cool! I used to have many gigabytes of electric sheep on my computer, but was previously dissapointed with the resolution. I'll try the new version!

---

