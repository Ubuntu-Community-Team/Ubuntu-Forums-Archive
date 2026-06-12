---
title: "[SOLVED] What's the execute command?"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by xshagy on 2007-12-18
How can i execute files from the terminal?
I want to play mp3s with ssh. I've got speakers hooked up to the ubuntu computer.

sudo do song.mp3
sudo open song.mp3
sudo exec song.mp3

Tried these commands but they don't exist.  Well, you get the idea. What's the command? Thanks

---

### Post by jrharvey on 2007-12-18
I Have no idea how to play an MP3 from the terminal but i am just really curious why you would want to. Do you not like to use a GUI to manage your songs?

---

### Post by lucia_engel on 2007-12-18
mpg321 *.mp3 perhaps?

You'll have to install the program first of course.

mpg321 is a commandline mp3 player.

However, doing a little digging on google, most seem to recommend using "sshfs" to mount your remote file system first so the music would play much better. Not an expert on sshfs though. This may help 

[http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/]("http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/")

---

### Post by betes on 2007-12-18
Depends on what programs you have installed.  If you have mplayer you can type:

mplayer path/to/mp3.mp3

but that will work the same with totem or rhythmbox if your replace mplayer with the name of whichever one you want to use.

---

### Post by Rhubarb on 2007-12-18
```
play song.mp3
```
This will not work through a ssh session.

---

### Post by betes on 2007-12-18
> **jrharvey said:**
> I Have no idea how to play an MP3 from the terminal but i am just really curious why you would want to. Do you not like to use a GUI to manage your songs?

The OP is trying to play it from another computer if I understood correctly, so he has only a terminal connection to the other computer.  But you might also play songs from the command line because it uses far less memory than opening a program like rhythmbox, exaile, amarok, etc.  With my collection those programs take about 50-70mb of Ram while using mplayer in the command line takes about 4-7mb.

---

### Post by tyggna1 on 2007-12-18
Normally, the most common way to run a self-executing file from the command line is by typing in a ./ before the file name.  e.g. ./tremulous-installer.bin

But, in practice, you just need to know what program you're using, and what programs can handle certain file types.

Since you're playing in a terminal, installing orpheus would be your best bet--as it runs within the terminal.

---

### Post by xshagy on 2007-12-18
Thanks for the quick answers.  I installed mplayer and that worked great.  I'm playing songs from a different computer.  My real motivation is to play songs on the server from a webpage on a different computer.

What i was thinking was using the perl system command...

system("mplayer song.mp3");

This just outputs a bunch of crap on the webpage that seems never ending.  Any ideas?

MPlayer 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4800+ (Family: 15, Model: 107, Stepping: 1) CPUflags: MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1 Compiled with runtime CPU detection. Terminal type `unknown' is not defined. Playing song.mp3. Audio file file format detected. ========================================================================== Forced audio codec: mad Opening audio decoder: [libmad] libmad mpeg audio decoder AUDIO: 44100 Hz, 2 ch, s16le, 192.0 kbit/13.61% (ratio: 24000->176400) Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3) ========================================================================== [AO SDL] Samplerate: 44100Hz Channels: Stereo Format s16le Opening /dev/dvb/adapter0/audio0 AO: [null] 44100Hz 2ch s16le (2 bytes per sample) Video: no video Starting playback... A: 0.0 (00.0) of 175.0 (02:55.0) ??,?% A: 0.0 (00.0) of 175.0 (02:55.0) ??,?% A: 0.0 (00.0) of 175.0 (02:55.0) ??,?% A: 0.1 (00.0) of 175.0 (02:55.0) ??,?% A: 0.1 (00.0) of 175.0 (02:55.0) ??,?% A: 0.1 (00.1) of 175.0 (02:55.0) ??,?% A: 0.1 (00.1) of 175.0 (02:55.0) ??,?% A: 0.1 (00.1) of 175.0 (02:55.0) 1.1% A: 0.2 (00.1) of 175.0 (02:55.0) 1.1%.....................

This continues for awhile.

---

### Post by RomeReactor on 2007-12-18
Hi. I would suggest [Cplay]("http://mask.tf.hut.fi/~flu/cplay/"). Or, for something with a few more features, [MP3Blaster]("http://mp3blaster.sourceforge.net/"). Both are available in the repositories. Personally, I like Cplay.

---

