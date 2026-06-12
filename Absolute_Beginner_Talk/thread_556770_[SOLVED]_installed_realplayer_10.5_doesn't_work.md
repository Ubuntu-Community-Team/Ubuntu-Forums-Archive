---
title: "[SOLVED] installed realplayer 10.5 doesn't work"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by DarinB on 2007-09-21
i installed real player 10.5 via cbs website i did the installation as it said in the installation instructions 
it installed on my \home\darin\Desktop by default
when i go into cbs  innertube to watch full episodes this is the error message.

"could not find an appropriate  appropriate hxplay or realplay in the system path to use as an embedded player."

i have no idea what to do next
help? 
i do miss my full episodes and don't want to go back to windows.

---

### Post by por100pre1 on 2007-09-21
Try locating and removing realplay folder and then install realplay for Feisty:


```
sudo su -c 'echo deb http://archive.canonical.com/ubuntu feisty-commercial main >> /etc/apt/sources.list'
```

```
sudo aptitude update && sudo aptitude install realplay
```

---

### Post by buntunub on 2007-09-21
I also have the same problem. Your suggestion does not do anything but install a base Realplayer which lacks any form of codec or gstreamer capabilities which are required for streaming video. Any suggestions to fix?

---

### Post by por100pre1 on 2007-09-21
> **buntunub said:**
> I also have the same problem. Your suggestion does not do anything but install a base Realplayer which lacks any form of codec or gstreamer capabilities which are required for streaming video. Any suggestions to fix?

Try checking everything [here]("http://ubuntuforums.org/showthread.php?t=413624") and add realplay as shown above. How did you installed your codecs?

---

### Post by buntunub on 2007-09-21
I just installed Realplayer as per your instructions above. I already have working codecs in Totem, VLC, and Mplayer and everything works fine in those. Do i have to reinstall all the codecs all over again to get Real player to work?

---

### Post by DarinB on 2007-09-21
i did what por100pre1 suggested thanks a lot whew! and now CBS works great and so does fox and NBC now if i can just get cw and abc to work i will be set for the season
any suggestions.?

---

### Post by DarinB on 2007-09-21
BTW i did have all the codex from before just not real player.
thanks again 
what about abc and cw???
gotta watch the blond on greys anat and superstition on cw

---

### Post by buntunub on 2007-09-21
Oh. Also I cant get sound to work in Realplayer unless I start it up in CLI with "aoss realplay"

---

### Post by por100pre1 on 2007-09-21
ABC is their fault, I think it could work, but the web page has some dumb scripts to detect Windows, so no Ugly Betty here. Lots of CSI episodes, no problem. I haven't tried CW.

---

### Post by por100pre1 on 2007-09-21
> **buntunub said:**
> Oh. Also I cant get sound to work in Realplayer unless I start it up in CLI with "aoss realplay"

Try checking your sound settings, try with ALSA or OSS. Real Player is not a winner in the sound configuration department, not even Windows version is actually.

---

### Post by DarinB on 2007-09-21
i had all the codex installed to get my dvd player etc. working and gstreamers and real player works like a charm. follow the instructions for the codex for totem vlc etc. and the dvd libraries you can find the gstreamer in synaptic and the dvd libraries online and in this forums i will look for them and if i find them i will post it there are two dvd lib files libdvdcss2_1.2.9-1_i386.deb, and libdvdcss2-dev_1.2.9-1_i386.deb
i fyou google it you may find it or put it in the search bar for this site.

---

### Post by LowSky on 2007-09-21
have you tried the helix player

---

### Post by DarinB on 2007-09-21
That might work. i did have a hell of a time with helix when i was a slave to m$, i am not sure why the above forum member can't get real player to work mine just installed like a champ using command line but i have tons of codex and libraries. good luck with it.

---

### Post by por100pre1 on 2007-09-21
> **DarinB said:**
> i had all the codex installed to get my dvd player etc. working and gstreamers and real player works like a charm. follow the instructions for the codex for totem vlc etc. and the dvd libraries you can find the gstreamer in synaptic and the dvd libraries online and in this forums i will look for them and if i find them i will post it there are two dvd lib files libdvdcss2_1.2.9-1_i386.deb, and libdvdcss2-dev_1.2.9-1_i386.deb
i fyou google it you may find it or put it in the search bar for this site.

For libdvdcss2 to add the [Medibuntu]("http://medibuntu.org") repository is an easy way. [Here's]("http://medibuntu.org/repository.php") how. Once the repository is added:

```
sudo apt-get update && sudo apt-get install libdvdcss2
```

EDIT: I checked CW and this is what I got:

> Thank you for your interest in The CW. This service is currently available to viewers living in the United States.

So no CW here, it's their fault.
[B]
Can somebody living in the Continental U.S. test CW and give some advice?[/B]

---

### Post by DarinB on 2007-09-21
is the abc issues that the same thing as the new ipods and the chechsum issues and windows itunes?

---

### Post by DarinB on 2007-09-21
i live in the us and the cw says we are now only available for windows and mac please check later for other os support

---

### Post by buntunub on 2007-09-23
I found the solution to my problem was with the linked libs. Feisty tends to load up the libstdc++5, which is required for Real Player 9. For Real Player 10, there is an updated libstdc++6, which when loaded up via Synaptic, solved every one of my issues.

---

### Post by por100pre1 on 2007-09-23
Glad to know everything is working fine now.

---

### Post by DarinB on 2007-09-29
i actually gave up and am using and old pIII laptop with 256 mb memory with xp just for abc and cwtv.
i is not my best choice. i did finally get them going with wine and firefox but it is choppy and not worth it. bummer!!!!!!
i have 768 of ram maybe that is not enough on my p4  2.4 Ghz i don't wantto spend any more money on ram for now.

---

