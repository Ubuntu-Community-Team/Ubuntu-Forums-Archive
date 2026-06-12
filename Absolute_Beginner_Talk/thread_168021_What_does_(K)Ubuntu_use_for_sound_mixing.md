---
title: "What does (K)Ubuntu use for sound mixing?"
date: 2006-04-29
forum: Absolute Beginner Talk
---

### Post by ronly on 2006-04-29
I have a problem with jerky playback in xmms and when I started looking for the cause I noticed that (K)Ubuntu has mixing of multiple sources implemented somehow but I don't know how. Neither arts nor esound is running and I don't have an ~/.asoundrc or /etc/asound.conf and as far as I can tell jack isn't running either but I can have two instances of mplayer playing simultaneously or xmms and mplayer etc. I have tried both the alsa output plugin and the oss driver in xmms and both work (but esound obviously doesn't since esound isn't running) but I get jerky playback and am trying to find the cause (it's ridiculous - opening a new tab in firefox causes playback to stop momentarily even though my system is 2.4 GHz with 1 GB of RAM). 
lsof /dev/dsp shows:
lsof: WARNING: can't stat() ext3 file system /dev/.static/dev
      Output information may be incomplete.
and lsof /dev/dsp shows the same error message but then followed by the right information (i.e. that xmms is using controlC0 etc.)
fuser /dev/dsp shows nothing but fuser /dev/snd/* shows what it should.
So what should I take a look at to track down this problem?

---

### Post by htinn on 2006-04-29
Try this:

```
sudo hdparm /dev/whateveryourharddriveis
```

Look at the using_dma and the IO_support variables.

---

### Post by ronly on 2006-04-29
This is what I get (it's a sata drive):
/dev/sda:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 24321/255/63, sectors = 390721968, start = 0

Nothing about using_dma.

---

### Post by htinn on 2006-04-29
I'm not sure about SATA but there reports here and there about performance issues. The hdparm command won't work on that, so you'll just have to search around for a solution (if that is the problem).

---

### Post by ronly on 2006-04-29
I don't think it's a problem with the harddrive, I can e.g. watch TV recordings that I've made with mplayer -dumpstream just fine and that should cause the heaviest hd load of all media (I can even record one file whilst watching another). It could be something with xmms but as I said I don't know how Ubuntu mixes the sound and I suspect that this problem has something to do with that. I tried playing the mp3s with mplayer and that seems to work fine but it can't possibly be due to the lessened load without the xmms gui - I can open and close apps and move the xmms gui around whilst mplayer is playing and it doesn't get jerky at all.

---

### Post by htinn on 2006-04-29
At this point I'm thinking there's some flaky interaction between SDL and whatever sound drivers you're using.

---

### Post by ronly on 2006-04-29
Can you suggest anything that I should try to solve this? Since as I've said I don't really have any idea what the cause could be and thus don't know what to try or what docs to read or search for on Google. And I think it would help if I knew how Ubuntu implements the mixing. An additional observation I've done is that both the alsa output plugin and the oss driver in xmms in Ubuntu have a rather large buffer (3000 ms) by default - I don't know whether that affects anything but IIRC my previous xmms installation didn't have that (or at least it did stop immediately when I pressed pause, unlike now).

---

### Post by ronly on 2006-05-03
Is anybody able to answer my question? I could do more to track down this problem myself if I knew how Ubuntu implements the mixing? I have fiddled with asound.conf (or ~/.asoundrc) and arts before (when I used another distribution) but I don't know what to do now that neither one of those apply (and not jack either).

---

### Post by ronly on 2006-05-04
I have to bump this once more since this question should be really easy to answer for people that are familiar with Ubuntu: What does Ubuntu use for mixing? I know that the drivers are alsa and that arts, jack and esound are installed but none of them is in use and there's no /etc/asound.conf or ~/.asoundrc so how is it implemented? Those are all the mixing implementations in Linux that I know of so now I'm stuck since I simply don't know what to look at - I cannot figure out anything from "ps aux" either (I confess that I don't know what all the processes are but I think that only Linux gurus do). I've tried Googling but cannot come up with anything useful - I find plenty of pages with people describing various problems with all of the aforementioned and xmms but it's pretty pointless to look at those since I know that none of them is in use. I'd really like to test playback without mixing so that I could see whether the jerkiness goes away then since then I'd be able to both know what causes the problem and thus try to solve it but whilst mixing multiple sounds is neat I don't need it if it results in jerky playback.

---

### Post by Harleen on 2006-05-04
It shouldn't be that hard to figure out which sound server you are using. Usually it's arts for KDE (and thus Kubuntu) and esd for GNOME (ubuntu).
If arts is running you should see a process named artsd.

```
$ ps aux | grep arts
harleen     5815  0.0  0.5  43036 12288 ?        S    19:25   0:02 /usr/bin/artsd -F 10 -S 4096 -s 60 -m artsmessage -c drkonqi -l 3 -f
harleen    10411  0.0  0.0   1636   544 pts/1    R+   22:58   0:00 grep arts
```

I don't know the process name for esd, but I'd assume it can be found with "ps aux | grep esd". But you have to have a playback running for this to work, because the sound servers close themselfes, if they aren't used for a certain time period.
If neither is running on your system but you are still able to play more sounds at once, your sound card may support hardware mixing under Linux and doesn't need a sound server. As far as I know only cards using the emu10k1 and emu10k2 chip (Soundblaster Live, Audigy and later) are capable of doing that.

---

### Post by ronly on 2006-05-04
Neither esound nor arts is running (as I noted in my first post). I have, however, found out something more since I last posted - I've tried playing different files and noticed that whilst mplayer plays mp3s fine with alsa (but xmms doesn't), mplayer has problems with wav files - I get "alsa-space: xrun of at least 0.007 msecs. resetting stream", which is a apparently a common problem. However, playing wav files with mplayer with -ao oss, i.e. oss through emulation works (but there's no difference between oss and alsa in xmms). Then I found out that the dmix settings, which my previous distro had in /etc/asound.conf or ~/.asoundrc exist, can be found in /usr/share/alsa/pcm/dmix.conf and tried setting the default rate to 44100 instead of 48000, since some people had apparently managed to solve the "alsa-space..." problem that way but unfortunately that didn't make any difference (and I did reboot just to make sure that the settings did apply). Now, I, however, presume that Ubuntu uses dmix and I know where to find the settings so I can try something.

---

### Post by ronly on 2006-05-04
I'm still stuck with this - I disabled dmix by removing /usr/share/alsa/pcm/dmix.conf since by default alsa doesn't have any mixing (and I tested to make sure that mplayer did complain about /dev/dsp being busy). So apparently dmix doesn't cause this - as far as I can tell whilst listening to several sounds simultaneously xmms sounds just as jerky regardless of how many other sounds are playing. So what else can I try? Currently mplayer can play mp3 files perfectly but I'd really like to use xmms and xmms sounds jerky if I do anything else on the computer when it's playing but ironically xmms plays wav files better than mplayer since then I get the "alsa-space: xrun of at least 8.839 msecs. resetting stream" messages and playback is even worse and the latter problem seems to be quite common but I don't know if the problems are related. The solutions I have found have been to modify asound.conf, or dmix.conf, which apparently contains those settings now (changing the default rate 48000 to 44100) but doing that hasn't worked in my case. Any ideas what I could try?

---

### Post by ronly on 2006-05-16
I managed to solve this to some extent so I'll reply just in case somebody else has a similar problem: Once I had tried everything that seemed sane to try I decided just to test the oss driver built into the crossfade plugin and presumed that the result would be terrible but surprisingly that worked - I have no idea why but apparently that and mplayer with "-ao oss" take exclusive access to the sound card and work. The alsa problem "alsa-space: xrun of at least..." might have something to do with this but whilst native alsa doesn't work and I cannot play several sounds simultaneously oss emulation works so I'm happy now that I can finally listen to music with xmms. Thanks to everybody that tried to help me with this!

---

### Post by ronly on 2006-05-18
This is starting to drive me nuts. Now I'm getting jerky playback again even though I haven't changed a thing - in order to help others with similar problems I was about to post that the reason why playback worked with the crossfade plugin but not with the oss driver could be that the plugin allows setting the sample rate for playback to 48000 whilst the oss driver doesn't have such a setting. But now that the problem has reappeared even though I haven't changed any settings at all or upgraded any packages this is even more mysterious - the only thing I've done was to boot into Windows once to play a game but that couldn't possibly affect this or could it? So once again I have to ask if anybody has any advice to give me? What could I do to find out what is causing this?

---

