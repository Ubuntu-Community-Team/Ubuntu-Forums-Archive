---
title: "what began with no sound for flash in firefox, is now no sound at all"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by brazilla ray on 2007-05-19
I recently upgraded to feisty, and had no sound for flash videos in firefox.  I searched around the posts here and tried many, many things, and nothing worked, until I tried these:

1)from [http://ubuntuforums.org/showthread.php?t=431465](http://ubuntuforums.org/showthread.php?t=431465)

> **jjbean said:**
> 

Install these packages: 
  pulseaudio
  pulseaudio-esound-compat
  libgstreamer-plugins-pulse0.1C
  libpulse-browse0
  libpulse-mainloop-glibo

I had to add myself to these groups:
  pulse
  pulse-rt
  pulse-access

Go to System > Preferences > Sound > Sound Tab. Make sure that Sound Events, Music and Movies, and Audio Conferencing are in **_Autodetect_**.

Make sure you leave ESD _**enabled**_ under System > Preferences > Sound  >Sound Tab.

Install the .deb file from this page. [COLOR=Red][http://pulseaudio.revolutionlinux.com/PulseAudio](http://pulseaudio.revolutionlinux.com/PulseAudio)[/COLOR]

Reboot.

I hope this helps some of you out. It worked well for me, but I cannot make any guarantees.

and 2)from [http://ubuntuforums.org/newreply.php?do=newreply&p=2601146](http://ubuntuforums.org/newreply.php?do=newreply&p=2601146)

> **orangep said:**
> There is a permissions problem involved here.
I was getting:
alsamixer: function snd_ctl_open failed for default: No such device
when I tried to run alsamixer.

Go to /dev/snd and
sudo chmod 666 *

I know that it shouldn't be necessary. If I put my name in the audio group,
I should have permission to read and write those devices. But it hasn't ever
worked, not in the 7 years that I've been running Debian.
So change the permissions, and suddenly you have ALSA and sound.

and

> **orangep said:**
> Correction:
I was overlooking the fact that I had already earlier changed the mode of
all of the audio devices in the main /dev subdirectory.

Do this:
cd /dev
ls -l /dev/* | grep audio

And make sure that everything you see has permissions like:
crw-rw-rw-

Not sure which made it work, but one or both of them did.  Then I rebooted after installing some fonts, and the sound was gone again in firefox.  So I tried doing all the chmod stuff again, but did sudo chmod 666 * in /dev, not /dev/snd, and I got locked out of /dev/snd.  I eventually sorted out the permissions so that now, when I do  

ls -l /dev/* | grep audio

 I get:

crw-rw-rw- 1 root audio    14,  12 2007-05-19 16:34 /dev/adsp
crw-rw-rw- 1 root audio    14,   4 2007-05-19 16:34 /dev/audio
crw-rw-rw- 1 root audio    14,   3 2007-05-19 16:34 /dev/dsp
crw-rw-rw- 1 root audio    14,   0 2007-05-19 16:34 /dev/mixer
crw-rw-rw- 1 root audio    10, 135 2007-05-19 12:34 /dev/rtc
crw-rw-rw- 1 root audio    14,   6 2007-05-19 17:59 /dev/sndstat
crw-rw-rw- 1 root audio 116, 9 2007-05-19 16:34 controlC0
crw-rw-rw- 1 root audio 116, 8 2007-05-19 16:34 pcmC0D0c
crw-rw-rw- 1 root audio 116, 7 2007-05-19 16:34 pcmC0D0p
crw-rw-rw- 1 root audio 116, 6 2007-05-19 16:34 pcmC0D1c
crw-rw-rw- 1 root audio 116, 5 2007-05-19 16:34 pcmC0D2c
crw-rw-rw- 1 root audio 116, 4 2007-05-19 16:34 pcmC0D3c
crw-rw-rw- 1 root audio 116, 3 2007-05-19 16:34 pcmC0D4p
crw-rw-rw- 1 root audio 116, 2 2007-05-19 16:34 timer


which I think is how it's supposed to be, but I have no sound in firefox, plus, when I try to play something in Kaffeine, it freezes.  Same with VLC.  Rythmbox closes as soon as I try to play something, and Amarok won't open.  So is it possible that I changed a permission somewhere in /dev that is now preventing sound from playing, and causing all the media players to fail? If so, what?  Any help would very much appreciated.

---

### Post by H.E. Pennypacker on 2007-05-19
You could try to figure out what is causing all these problems, but that may take a while to do.  You could, on the other hand, re-install Feisty (a fresh install, without formatting your home partition), and hopefully these problems will go away on their own.  

The Comprehensive Sound Problems (or Solutions) thread may be helpful.  I realize you already said you searched around.

---

### Post by brazilla ray on 2007-05-19
Thanks- the Comprhensive Sound Problems was one of the things I tried, but no luck there.  How would I go about doing a fresh install or reinstall of Feisty? and can I do it without losing anything important?  I'm plenty willing to get my hands dirty fixing this, but it helps having something to listen to.

---

### Post by H.E. Pennypacker on 2007-05-20
Well, before you begin, you should map out all of your partitions.  Install GParted, and see which partitions are valuable to you.  Decide on which ones they are, and when you are installing Feisty, make sure you DO NOT (again, DO NOT) format those IMPORTANT partitions.  

Just pop in the CD, and follow the installation procedure, but I warn you to NOT format IMPORTANT partitions.  

For everything else, follow this guide:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Formatting = getting rid of.

---

### Post by brazilla ray on 2007-05-20
Thanks, but it's the strangest thing- I turned on my computer this morning and everything was working the way it's supposed to.  Don't know what to make of it, but a good night's sleep fixes many things.

---

### Post by H.E. Pennypacker on 2007-05-21
> **brazilla ray said:**
> Thanks, but it's the strangest thing- I turned on my computer this morning and everything was working the way it's supposed to.  Don't know what to make of it, but a good night's sleep fixes many things.

Not at all surprised.  Strange things like that happen all the time.

---

### Post by hoarder on 2007-05-22
I ran into this error too, I was getting an error when running pulseaudio step, and I found this link:

[http://developer.novell.com/wiki/index.php/Feisty/HOWTO:_PulseAudio](http://developer.novell.com/wiki/index.php/Feisty/HOWTO:_PulseAudio)

the first apt-get command had 3 libraries that it installed, that seemed to fix my problem and I was able to start up the daemon and all my sound was working again.

---

