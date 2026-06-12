---
title: "Installed Audacious and lost system sounds"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by ricardisimo on 2006-12-21
I'm assuming the *Audacious* install is involved, given that the change was immediate, but who knows? I had customized startup.wav and logout.wav, but now neither plays, not even to test them in the "Sounds" dialog.
     In the "Devices" tab, everything but "Sound Capture" is set to Autodetect, and when I test the devices these are the sorts of responses I get:
Sound Events:```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Resource busy or not available.
```
Music & Movies:```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Resource busy or not available.
```
Audio Conferencing:```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Resource busy or not available.
```
     One more thing... previously Nautilus had that basic playback function that would give me a sample of any audio file over which the pointer would pass. No longer. It seems that all system access to sounds is gone now. I'd greatly appreciate any help. Thanks in advance.

---

### Post by Azakus on 2006-12-21
I'm having this problem now as well. Try this first.
```
rm ~/.asoundrc
```
That might work, although it will kill audacious' use of the ALSA driver (for now I don't know of a fix, but I'm working on it {possible fix with a restart}).

---

### Post by ricardisimo on 2006-12-21
> **Azakus said:**
> I'm having this problem now as well. Try this first.
```
rm ~/.asoundrc
```
That might work, although it will kill audacious' use of the ALSA driver (for now I don't know of a fix, but I'm working on it {possible fix with a restart}).

Not working [no such file or folder]... I'll look for that file later, but I'm curious what this is going to do. Am I removing a file or folder that I might want one day? Thanks.

---

### Post by ricardisimo on 2006-12-22
It's official: I appear to have lost all sounds not coming directly from Audacious. Anyone familiar enough with Audacious to know a quick fix here? Thanks again.

---

### Post by Azakus on 2006-12-22
I FIXED IT! I started having the same problem you did and here's the fix (at least on my end). Open Audacious and hit Control+P. Under Audio, switch the plugin to OSS. This will stop it from overriding the ALSA plugin that controls the system sounds. Next, in a terminal type "alsamixer" and raise all the volumes to 100% by using the arrow keys, press Esc to quit. Now you should have sound back.

---

### Post by ricardisimo on 2006-12-23
No luck. I've also had all sorts of other issues arising from trying to uninstall, and then reinstall Audacious, but that's another story. I can't select OSS because then Audacious won't play, so I chose PulseAudio, which is, in fact, the only Output Plugin that works at all with Audacious. I did set all of the mixer levels to 11, but no change. Still, the only system sound I get is the conga hit at login (which I can't reproduce later in the Test sounds dialog). Here's my sound card info:
```
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
        Subsystem: Elitegroup Computer Systems Unknown device a00b
        Flags: bus master, medium devsel, latency 64, IRQ 169
        I/O ports at e800 [size=256]
        I/O ports at ec00 [size=128]
        Capabilities: <access denied>
```

---

### Post by Azakus on 2006-12-23
Try this: [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449")

---

### Post by ricardisimo on 2006-12-25
> **Azakus said:**
> Try this: [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449")

Firstly, thanks for the link. I'm hoping that this problem will get resolved and eventually make it into the Guide. Secondly,... uggh. It's gone from bad to worse. Now I have NO sound. Out of desperation I tried LordRaiden's suugestion to uninstall and then reinstall linux-sound-base, alsa-base and alsa-utils. I'm totally at a loss now. To paraphrase our dearly departed James Brown, please, please, please help me!

---

### Post by ricardisimo on 2006-12-27
OK... I've been toying around with alsamixer and I think I've resolved the issue, but I'd like to make sure I haven't screwed things up worse down the stretch, so... would someone who's sound is behaving itself just fine open a terminal and type ```
alsamixer
``` and tell me exactly which channels they have muted and which are on. Thanks in advance.

---

### Post by ricardisimo on 2006-12-28
Can someone compare what their alsamixer levels look like compared with mine? Thanks in advance.

Master: On
Master Mono: 100%
PCM: 100%
Surround: 100%
Surround Jack Mode [Shared]
Center: 100%
LFE: 100%
Line: 100%
CD: 100%
Mic: 71%
Mic Boost (+20dB) [Off]
Mic Select [Mic1]
Video: 100%
Phone [Off] 100%
IEC958: On
IEC958 Capture Monitor [Off]
IEC958 Capture Valid [Off]
IEC958 Playback AC97-SPSA: 0%
IEC958 Playback Source [Analog]
PC Speaker: 100%
Aux [Off] 100%
Mono Output Select [Mix]
Channel Mode [2ch]
External Amplifier [Off]

Thanks again.

---

### Post by Azakus on 2007-01-01
Those levels look great and should work just fine. I really think that the fix would be switching to the Enlightenment Sound Daemon for all your audio. It is installed by default in Edgy, and most every program has an ESD plugin. ESD handles all the audio output through ALSA, but allows for multiple programs and prevents one from monopolizing the soundcard or messing with the alsamixer volume settings.

---

### Post by ricardisimo on 2007-01-03
> **Azakus said:**
> Those levels look great and should work just fine. I really think that the fix would be switching to the Enlightenment Sound Daemon for all your audio. It is installed by default in Edgy, and most every program has an ESD plugin. ESD handles all the audio output through ALSA, but allows for multiple programs and prevents one from monopolizing the soundcard or messing with the alsamixer volume settings.

OK. How do I do that? I have esound-common installed, but not esound (binaries), eterm or esound-clients. Should those be on?

---

### Post by Azakus on 2007-01-03
All the necessary components are already installed by default. All you need to do is switch the sound to use ESD for all sound output. Press System->Preferences->Sound and select ESD for all the options on the Devices tab. On the Sounds tab, press "Enable software sound mixing (ESD)" and select your default sound card on the bottom to your soundcard (if need be). Then, select the ESD plugin in Audacious in the Preferences tab, and in other programs, such as VLC and Mplayer, pick the esd plugin or option.

---

### Post by ricardisimo on 2007-01-10
Still nothing. I've tried so many things at this point that I don't know what's been done or undone or redone. I'm fairly certain that I either don't have a sound server up and running, or at the very least it's not running properly. This leads me to my next question: What the hell is a sound server? How do I get one or set one up? Thanks Az & everyone.

---

### Post by ricardisimo on 2007-01-10
Curiouser and curiouser, although I think it backs up my sound server theory: now even Audacious won't play IF another sound-related app is already running (like GnomeBaker, in this instance). Once again, any help with restoring my sound server would be greatly appreciated. thanks.

---

### Post by Azakus on 2007-01-10
{EDIT: Try this first, then the code below}
Adding the current user to the audio group


A very common cause for a user to not have sound is not having his/her username in the /etc/group.

Thanks to rustybutt for this simple check.

Code:

grep 'audio' /etc/group

You should see a line similar to
```
audio:x:29:
```

followed by a username i.e. if the username is "ubuntu" then you should see
```
audio:x:29:ubuntu
```

. If you see something else i.e.
```
audio:x:29:root
```

you should add your username to the file by doing
```
sudo nano /etc/group
```

. Now find the line that looks like
```
audio:x:29:root
```

and change it to
```
audio:x:29:root:yourusername
```

Hit CTRL + O to save, then CTRL + X to exit. That's the end of that 
===================================================
For the sake of arguement, let's try this (THIS WILL REBOOT YOUR COMPUTER)
```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop
sudo reboot
```

---

### Post by ricardisimo on 2007-01-11
Thanks Az, but no dice. All of my users are listed - including "pulse", which I thought was a bit odd, but perhaps it's part of pulseaudio's modus operandi to have itself listed as a user so as to have quick access to whatever resources it might need. Could this be the source of the problem?
Also, purging and reinstalling didn't work this time, nor the previous time I did it.
Currently, on Preferences > Sound > Devices I have ESD selected for "Sound Events", "Music and Movies" and the first half of "Audio Conferencing". The second half is my sound card, SiS SI 7012. Originally, "Autodetect" was selected. If I hit "Test" on any of these options, this is the sort of response I get:
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not establish connection to sound server
```
Once again, a million thanks to you, Az, and to anyone else who can help me fix this. Would appreciate any help.

---

### Post by Shoeberto on 2007-01-14
I have been getting this same error randomly.  The only cure for it has been to reboot my system, which is obviously not ideal.  I don't know what causes it.  I rebooted last night, for example, and all the sounds had been working fine until just about half an hour ago when I noticed I wasn't getting any playback.

I can only get things to play back if I select my sound card for all options under System > Preferences > Sound, but that only allows one audio stream at a time, and I've had programs that didn't exit clean stay in the background and hog that.

The only thing I could think of that has messed up my playback is Cinelerra, which I have been using for extended periods of time, but I'm not sure how it would break anything.  I really want to find a way to get my ALSA running properly again without having to resort to a reboot.

---

### Post by ricardisimo on 2007-01-17
Right now I'd take your situation over mine in a heartbeat. All I have is the conga hit at login and any song I'm playing on Audacious (and *only* Audacious). For a second I thought perhaps there was a problem with my card, but then I wouldn't have any sounds at all, correct? Still looking for any solution. Anyone with intimate knowledge of sound server setup, please lend a hand to a fellow (or fellows) in need. Thanks.

---

### Post by ricardisimo on 2007-01-17
By the way, I do often hear a sort of click in the speakers at what I know are certain sound events, and the click is sometimes accompanied by a beep from the tower's internal speaker. This leads me to believe that my comp is sending the right info, but nobody's home to receive it. Don't know if this helps to diagnose the problem. Thanks again.

---

### Post by ricardisimo on 2007-01-25
I'm still sans sound. I posted over on LinuxQuestions - Ubuntu as well, and nothing so far. Any help would be much appreciated. Thanks.

---

### Post by ricardisimo on 2007-01-26
Pretty please?

---

### Post by Azakus on 2007-01-27
I'm at a loss for why your sound isn't working. Unless your soundcard has fried or your alsa-utils are horribly off, I don't know what could be causing it. Sorry for the lack of help here.

---

### Post by ricardisimo on 2007-01-30
You've done wonders, Az, make no mistake. Something else is up, and I'm hoping someone else with powers and abilities far beyond yours and mine can help me out here. I can't imagine it being the card, since I still get sound, but who knows? Maybe.

---

### Post by ricardisimo on 2007-01-30
More info that hopefully someone can decode to tell me what to do...
Here's what I get when I run my other (non-Audacious) players from a terminal:
[LIST]
[*]VLC -  ```
wxvlc
VLC media player 0.8.6 Janus

** (.:7039): CRITICAL **: gtk_pizza_set_size: assertion `pizza != NULL' failed

** (.:7039): CRITICAL **: gtk_pizza_set_size: assertion `pizza != NULL' failed

** (.:7039): CRITICAL **: clearlooks_style_draw_focus: assertion `height >= -1' failed
ALSA lib pcm_dmix.c:862:(snd_pcm_dmix_open) unable to open slave
[00000556] oss audio output error: cannot open audio device (/dev/dsp)
Creating link /home/ricardo/.kde/socket-ricardo-desktop.
can't create mcop directory
```
[*]Rhythmbox - ```
rhythmbox


(rhythmbox:7561): Rhythmbox-WARNING **: Unable to start mDNS browsing: MDNS service is not running

(rhythmbox:7561): Rhythmbox-WARNING **: Unable to stop mDNS browsing: MDNS service is not running
```
[*]RealPlayer 10 - I get a popup dialog that says "Error - Cannot open the audio device. Another application may be using it."
[*]Listen - listen
Gstplayer error: Resource not found. gstfilesrc.c(975): gst_file_src_start (): /playbin0/source:
No such file "//home/ricardo/Downloads/Music/Latin/Cachao/01 INTRODUCTION (Orq#3320D8.mp3"

/home/ricardo/Downloads/Music/Latin/Los Van Van/Llegó Van Van
filter
filter finish
NB FILE TO LOAD 12
LOADING TIME: 0 s
Exit successful
Error in sys.excepthook:

Original exception was:
Error in sys.excepthook:

Original exception was:
Exception in thread Thread-1 (most likely raised during interpreter shutdown):
Traceback (most recent call last):
  File "threading.py", line 442, in __bootstrap
  File "threading.py", line 422, in run
  File "/usr/lib/listen/thread_queue.py", line 84, in process_queue
  File "/usr/lib/listen/context_web.py", line 313, in __link_clicked
exceptions.AttributeError: 'NoneType' object has no attribute 'idle_add'
Unhandled exception in thread started by 
Error in sys.excepthook:

Original exception was:

[*]Beep - Trying to load folder into library crashed the compootor... fortunately Firefox saved everything above. I did also get another popup dialog asking me to check that I have the correct output plugin selected; that no other program is blocking the soundcard; and that my soundcard is configured properly.
[*]Banshee - ```
banshee --play-enqueued --enqueue %U

(/usr/lib/banshee/banshee.exe:11971): GLib-GObject-WARNING **: value "128" of type `gint' is invalid or out of range for property `bitrate' of type `gint'
Debug: [1/30/2007 3:03:13 PM] (Default player engine) - GStreamer 0.10
Debug: [1/30/2007 3:03:13 PM] (Audio CD Core Initialized) - 
Setting MusicBrainz proxy to www.musicbrainz.org:80
Could not load: /home/ricardo/%U
shift: 96: can't shift that many
Setting IO Backend to Banshee.IO.Unix.IOConfig (unix)

```[/LIST]
The "shift 96" error in Banshee is one that I get elsewhere in terminal even with non-audio issues. It also started at roughly the same time as my audio problems, so I don't know if it's related. I'm very, very sorry if this is too much information, but the longer this goes on the more desperate I'm getting. Thanks again to Azakus and everyone for your input thus far.

---

### Post by ricardisimo on 2007-02-03
How about a show of hands regarding whether or not testing Feisty will solve the problem. Or, alternately, reinstalling Edgy. If the latter... from a CD or download?

---

### Post by Azakus on 2007-02-03
I would definately try out Feisty. It has a much greater amount of hardware drivers. Herd 3 beta image is out, so try it! :)

---

### Post by ricardisimo on 2007-02-08
Someone on LinuxQuestions suggested that the Edgy Live CD has some sort of "Fix Install" option, that is basically just a partial re-installation of just the components that are giving you difficulty. Is this true? Can I just reinstall all things sound-related on Edgy?

Second question: Is there one person or group of persons on the Ubuntu development team that is/are most intimately involved with the sound server, and how do I get in touch with them directly?

Can you tell I'm a little nervous about the Herd 3 install?

---

### Post by ricardisimo on 2007-02-09
Loaded Feisty and it seems to do the trick as far as sounds. However, Herd 3 can't operate my wireless card, so here I am back in Edgy. I think I'm just going to wait until Feisty comes out with all of its bells and whistles. I guess that's as close to a resolution to this problem as I'm going to get. It's a shame that we never really cracked it, but that's the breaks. Thanks Azakus and everyone else for bearing with me these past months.

---

### Post by Azakus on 2007-02-11
What wireless card are you using? It's rather easy to install wireless card drivers.

---

### Post by ricardisimo on 2007-02-12
Hey there Az,

I'm reassessing the situation a bit, remembering what has happened every single time I've toyed with my networking settings, whether in Windows or Ubuntu. I don't know if others have had this experience, but my connection stays strong and stable until I reset it or have to move the machine around and try to find old or new signals, then it just won't take... until it does, then it's golden. Twice now I've "fixed" the problem by walking away for two or three hours. It's just weird, and I don't think I'll have any problems for too long.

The real issue is the same: the sound server. I played the sample movies that come with Feisty (and Dapper, as I recall) of Nelson Mandela and I think there was another one, a cheesy Wyndham Hill-like video - they looked and sounded great. No problems. That was the first time I ran Live CD, and is where I got the idea that Feisty might fix the problem. Well, then I went back to work on the wireless problem, and while I'm there tried playing some of my mp3 files. Whatever the bundled player is (Totem?) said it needed a plugin for mp3s (gstreamer?). It tried finding and downloading the plugin, but of course, the wireless isn't working... It's never easy in Ricardolandia.

With or without an internet connection, I find it terribly difficult to believe that a player would be bundled with Feisty that couldn't play mp3s without help. Does anyone believe that's possible? Anyhow, getting connected is job #1 right now, then I'll continue testing Feisty with regards to my sound problem. Thanks again.

---

### Post by Azakus on 2007-02-12
Gstreamer doesn't include mp3 by default because of licensing issues (the MP3 format is held in copyright by Fraunhofer). You can get mp3 support by installing the gstreamer plugin for it.
```
sudo aptitude install gstreamer0.10-fluendo-mp3
```
{edit}
I'm pretty sure that your wireless card can be fixed with this guide: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by MaX on 2007-02-16
> **ricardisimo said:**
> Hey there Az,

I'm reassessing the situation a bit, remembering what has happened every single time I've toyed with my networking settings, whether in Windows or Ubuntu. I don't know if others have had this experience, but my connection stays strong and stable until I reset it or have to move the machine around and try to find old or new signals, then it just won't take... until it does, then it's golden. Twice now I've "fixed" the problem by walking away for two or three hours. It's just weird, and I don't think I'll have any problems for too long.

The real issue is the same: the sound server. I played the sample movies that come with Feisty (and Dapper, as I recall) of Nelson Mandela and I think there was another one, a cheesy Wyndham Hill-like video - they looked and sounded great. No problems. That was the first time I ran Live CD, and is where I got the idea that Feisty might fix the problem. Well, then I went back to work on the wireless problem, and while I'm there tried playing some of my mp3 files. Whatever the bundled player is (Totem?) said it needed a plugin for mp3s (gstreamer?). It tried finding and downloading the plugin, but of course, the wireless isn't working... It's never easy in Ricardolandia.

With or without an internet connection, I find it terribly difficult to believe that a player would be bundled with Feisty that couldn't play mp3s without help. Does anyone believe that's possible? Anyhow, getting connected is job #1 right now, then I'll continue testing Feisty with regards to my sound problem. Thanks again.

I'm running Feisty and I just got your problem. I got sound in Amarok after I switched it to use Pulseaudio.
It seems like gstreamer and VLC don't yet have support for Pulseaudio (in the Ubuntu builds at least)

---

### Post by ricardisimo on 2007-02-16
double-post. sorry.

---

### Post by ricardisimo on 2007-02-16
I just loaded Feisty this morning (fresh install - not an upgrade), and I'm happy to inform everyone that the problem is, well... not solved, of course, since I was never really able to determine what was wrong. Whatever, the problem is gone. Thanks once again to Az and the rest for helping so much with this.

Now it's on to a newer, feistier set of problems.

P.S. - Feisty doesn't appear to have that "preview" function for audio files, where you can here a sampling just by waving your magic wand over them. No big.

---

