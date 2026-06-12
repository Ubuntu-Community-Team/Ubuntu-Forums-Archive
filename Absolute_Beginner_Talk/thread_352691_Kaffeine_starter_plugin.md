---
title: "Kaffeine starter plugin"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by nlow04 on 2007-02-03
I'm a newbie to Ubuntu 6.10.

When I try to play a video clip on a certain website, the message says Kaffeine Starter Plugin.

Can anyone advise me how to find this plugin and download it?

Please respond.  Thanks.

---

### Post by kebes on 2007-02-03
Go into the Synaptic package manager (Applictions > Add/Remove) and make sure that "kaffeine" is installed, and "kaffeine-xine." I believe if you want movies to open-up inside the web-browser, you need "kaffeine-mozilla" also.

Actually I use "mplayer" to play movies inside my web browser (firefox). If you want to go that route, install "mplayer" and "mozilla-mplayer" instead.

---

### Post by nlow04 on 2007-02-03
Kaffeine and kaffeine-xine are already installed when I checked the Synaptic package..  I played a dvd on kaffeine.  It only shows video and the sound is off.  My volume control is on.  The volume works on everything except when I play a dvd.

Plesae respond.  Thanks.:confused:

---

### Post by kebes on 2007-02-03
Hmm... I'm not sure. In Kaffeine if you go:
Player > Audio > Audio Channel >

Do you have any options? Maybe one will work?

Also, make sure that you close any other applications that may be using audio. They can often interfere with each other.

---

### Post by %hMa@?b&lt;C on 2007-02-03
kmplayer shoudl be the automatic in konqueror, it is ino my opeinon better to use thatn kaffeine as it is in the same window as konqueror.

---

### Post by nlow04 on 2007-02-03
Kaffeine can only play my audio cd's.  There are no options that you suggested.

Please reply.  Thanks.

---

### Post by nlow04 on 2007-02-04
I found out its probably my dvd disc.  It has a few scratches.  When I played another dvd, the video is fine and I can hear sound.  

When I play  an audio cd on Kaffeine, I can hear the sound.  

Can you advise me how to fix the problem?  My dvd works fine on my home dvd recorder.

Please respond.  Thanks.

---

### Post by kebes on 2007-02-04
Well if the DVD disk is scratched, you may be able to recover it by making a copy of it. Of course if this is a commercial DVD then it is (intentionally) difficult to do.

There are three programs I know of that let you extract DVD-video and audio tracks (i.e.: rip the disk):
[dvd::rip]("http://www2.exit1.org/dvdrip/") (listed as "dvdrip" in the Synaptic package manager)
[AcidRip]("http://untrepid.com/acidrip/")
[thoggen]("http://thoggen.net/")

All three of them are in the repositories, so you can install them with Synaptic (Applications > Add/Remove). I've used dvd::rip, and although the interface is 'ugly', it is a useful program.

After you've extracted the track(s), you can burn it to a new disk. You can also just transcode it into a video file (avi or whatever) on your hard-drive, and play it that way.

Hopefully one of those programs will be able to 'jump over' the defects in the disk, so that you can get a playable track.



P.S.: If you prefer the commandline, the program "mencoder" (part of the "mplayer" suite) can also be used to extract tracks from DVDs.

---

