---
title: "Best way to convert huge sound library?"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by staticvoid on 2007-12-17
I did a search for *.wma then I drag and dropped those into soundconverter and told it to convert them to mp3z and replace existing file.

wierd stuff happened, from broken files, to not deleting the wma to making new folders and puting the files in there.

Whats the best or better way to do this? I have a mix of wma and mp3 files. I want them all to be mp3 :)

thanks


sv

---

### Post by sonofusion82 on 2007-12-17
if some of the wma are DRM protected, then i m not sure if you can easily convert it to mp3.
you might need to use Windows Media Player to burn it to CD and rip the CD to mp3

---

### Post by mozetti on 2007-12-17
I think ffmpeg can decode wma, but not sure. If so, your best bet is to look for an existing BASH script to do it, or write your own (or have someone else do it for you).

---

### Post by kpkeerthi on 2007-12-17
[http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Convert_WMA_to_MP3](http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Convert_WMA_to_MP3)
That should get you started. You may want to tweak LAME options (for quality) to suit your taste.

---

### Post by staticvoid on 2007-12-17
Ok,

Thanks a ton.

So soundconverter... bad for large quantity?

Writing my own bash file sounds like a ton of fun :D

I'll post it if I make one. for like recursive conversion to .mp3 or to .ogg

that would be neato. Like if you download music from gnutella and then when it goes into the music folder have it automatically converted to mp3 or .ogg


sv

by the way, any tut on doing a BASH?

thanks for the link kpkeerthi :)

---

### Post by kpkeerthi on 2007-12-17
You are welcome.

[BASH Programming - Introduction]("http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html")
[Advanced BASH Scripting Guide]("http://tldp.org/LDP/abs/html/")

---

### Post by staticvoid on 2007-12-17
oh hahaha,

you just gave me a tutorial. thanks :) I can edit the bash script for my own purposes I guess.


sv

EDIT: ok, well thanks again for those :D

---

### Post by staticvoid on 2007-12-17
What do the first lines do?
Does this keep the same output file name?
Can I run this command on an entire directory? 
How does wma keep the information of the file, artist, album stuff, and how can I transfer it to mp3 ID3 tags?
That would be so cool, just to be able to run this command on a directory and keep everything (quality, name, ID3 info) the same, but make it an mp3.

> #!/bin/bash

current_directory=$( pwd )

#remove spaces
for i in *.wma; do mv "$i" `echo $i | tr ' ' '_'`; done

#remove uppercase
for i in *.[Ww][Mm][Aa]; do mv "$i" `echo $i | tr '[A-Z]' '[a-z]'`; done

#Rip with Mplayer / encode with LAME
for i in *.wma ; do mplayer -vo null -vc dummy -af resample=44100 -ao pcm -waveheader $i && lame -m s audiodump.wav -o $i; done

#convert file names
for i in *.wma; do mv "$i" "`basename "$i" .wma`.mp3"; done

rm audiodump.wav

thanks!

Static Void

---

### Post by staticvoid on 2007-12-17
When I ran this file on a test .wma:

terminal output:
> nathan@victor:~/Desktop$ wmamp3
MPlayer 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) M processor 1000MHz (Family: 6, Model: 9, Stepping: 5)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Creating config file: /home/nathan/.mplayer/config
-waveheader is deprecated. Use -ao pcm:waveheader instead.
rm: cannot remove `audiodump.wav': No such file or directory
nathan@victor:~/Desktop$


It converted it, at least it seemed like it did, but when I tried to open the file,
[IMG]http://i71.photobucket.com/albums/i123/broinjc/Screenshot-12.png[/IMG]


hmm... how can I edit the BASH script to make it work?

Static Void

---

### Post by CatKiller on 2007-12-17
> **staticvoid said:**
> So soundconverter... bad for large quantity?

Not really. And the directories and filenames that Sound Converter uses can be changed in the Preferences dialogue, as can whether it deletes the original file. DRM'd files are always going to be a problem, whichever method you use, since the entire purpose of the DRM is to stop you doing what you're trying to do.

---

### Post by staticvoid on 2007-12-17
aha, ok..

i still don;t get it though.. why it screwed up my encoding, the mplayer script a few posts up






sv

---

