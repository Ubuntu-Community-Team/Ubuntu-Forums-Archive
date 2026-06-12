---
title: "iBook G4 Sound Issue"
date: 2005-05-28
forum: Apple PPC Users
---

### Post by oliverwebb on 2005-05-28
Okay I got it installed works REALLY REALLY well, thanks guys. One issue though, the sound is painfully bad, yes it does actually give you a headache if you listen to music on it. I've tried both OSS and ALSA both are as bad as each other, perhaps it is a driver issue? I don't know, I just want a solution please.

Thanks a lot for any help in advance.

BTW: My Specs are:

iBook G4 12"
1.2GHz G4
512MB RAM
Radeon 9200 32MB
30GB HDD
All the usual crap

---

### Post by chascon on 2005-05-29
try reconfiguring alsa.  That worked for me on the same machine.  You'll have to net search the exact command as I don't recall.

---

### Post by spoetnik on 2005-05-31
I had the same issue.
I use KDE as my window manager, so i don't know how to solve this problem in Gnome.

In KDE openup you mixer, and open the "switches" tab.
Dissable DRC, and you sound is crispy clear, and of a normal volume.

Maybe someone with some command line knowledge knows how to solve this problem without the use of kmix??

UPDATE:
You can use the alsamixer command from the command line.

use you right arrow until you get to the DRC range. Set this range to a higher level with you up key. This should solve the problem. If it doesn't, dissable DRC.

Good Luck

---

### Post by ssam on 2005-05-31
gnome-volume-control is equivilent to kmix. you may need to edits preferences to show all the sliders.

you can right click on the volume applet in the panel and click "open volume control"

---

### Post by ripounet on 2005-06-02
[QUOTE=spoetnik]I had the same issue.
I use KDE as my window manager, so i don't know how to solve this problem in Gnome.

In KDE openup you mixer, and open the "switches" tab.
Dissable DRC, and you sound is crispy clear, and of a normal volume.

Maybe someone with some command line knowledge knows how to solve this problem without the use of kmix??

UPDATE:
You can use the alsamixer command from the command line.

use you right arrow until you get to the DRC range. Set this range to a higher level with you up key. This should solve the problem. If it doesn't, dissable DRC.

Good Luck[/QUOTE]
 Neither of all this mixer-tips worked for me.
As said in another thread, I got it to work by replacing "snd_powermac" by "dmasound_pmac" in the file /etc/modules  (be root).

iBook G4 933 white

---

### Post by mr.lamp on 2005-06-12
[QUOTE=ripounet]Neither of all this mixer-tips worked for me.
As said in another thread, I got it to work by replacing "snd_powermac" by "dmasound_pmac" in the file /etc/modules  (be root).

iBook G4 933 white[/QUOTE]
 i tried everything i found here.........but nothing REALLY helps. the sound is much better than before after i edited /etc/modules as ripounet said......but it is still bad. the sound in osx is much better


ibook g4 1ghz

---

### Post by pvz on 2005-06-12
Did you install alsa-base (apt-get install alsa-base) and then try to configure it from a terminal by typing alsaconf ? I have exactly the same iBook and sound works just fine for me.

---

### Post by Liakoni on 2005-06-13
I have some problems with sound too .
Rythmbox didn't find alsa. 
The last few days the sound didn't work very well  (Rythmbox didn't find alsa for examble, volume control didn't open) and i tried reinstalling alsa and some alsa-utils (alsaplayer, alsamixergui e.t.c.).

But i got this result :

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/a/alsaplayer/alsaplayer-esd_0.99.76-0.2ubuntu2_powerpc.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/a/alsaplayer/alsaplayer-esd_0.99.76-0.2ubuntu2_powerpc.deb)
  MD5Sum mismatch


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/a/alsaplayer/alsaplayer-common_0.99.76-0.2ubuntu2_powerpc.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/a/alsaplayer/alsaplayer-common_0.99.76-0.2ubuntu2_powerpc.deb)
  MD5Sum mismatch


The other packages installed buti didn't see any difference.

---

### Post by pvz on 2005-06-13
Try to change your mirrors in the /etc/apt/sources.list
I read somewhere that the us mirrors have problems.

---

### Post by Liakoni on 2005-06-28
My problems with sound continues...
When i try to play a movie with **vlc** i am getting :

[I]theodim@iBook:~$ vlc
VLC media player 0.8.1 Janus
[00000272] mpeg_audio decoder: MPGA channels:2 samplerate:48000 bitrate:128
ALSA lib confmisc.c:550:(snd_determine_driver) could not open control for card 0ALSA lib conf.c:3463:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:387:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3463:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:945:(snd_func_refer) error evaluating name
ALSA lib conf.c:3463:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3932:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2068:(snd_pcm_open_noupdate) Unknown PCM default[/I]

With mplayer i am getting ''YOUR SYSTEM IS TOO SLOW TO PLAY THIS MONIE''.

Rythmbox denies to play anything.

I tried reinstalling **ALSA** but it didn't make any difference.
Does anyone has any idea?

---

### Post by mr.lamp on 2005-07-18
Knows anyone now a solution that really works???

---

